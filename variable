function get_products() {
  // 최종적으로 장바구니에 담기 위해 사용되는 변수
  var products = [];

  // table의 tbody를 순회하며 tr을 가져옴.
  $("#totalProducts > table > tbody").each(function (_, tbody) {
    // mac & chrome인 경우 displaynone table이 있음.. -> 이때는 무시해야 함
    if ($(tbody).css("display") === "none") return;
    $(tbody)
      .find("tr")
      .each(function (_, tr) {
        if ($(tr).hasClass("option_product")) {
          // 옵션이 있는 경우 (의류)
          var nameWithOption = $(tr).find("p.product").text();

          // '-' 를 기준으로 잘라서 옵션을 분리한다.
          var splitted = nameWithOption.split(" - ");
          var variant = splitted[1];

          // 각 항목 별 수량 추출
          var quantity = parseInt($(tr).find("input.quantity_opt").val());

          products.push({
            id: iProductNo,
            name: product_name,
            price: parseInt(product_price),
            category: iCategoryNo,
            variant: variant,
            quantity: quantity,
          });
        } else {
          // 옵션이 없는 경우 (의류 외)에는 수량만 별도로 추출한다.
          var quantity = parseInt($("input[id=quantity]").val());
          products.push({
            id: iProductNo,
            name: product_name,
            price: parseInt(product_sale_price),
            category: iCategoryNo,
            quantity: quantity,
          });
        }
      });
  });
  return products;
}

// 제품 상세 페이지에서의 제품명 출력
function get_product_name() {
  // cafe24에 의해 정의된 변수임.
  return product_name;
}

// 제품 수량 출력
// ex) 1 2 3
function get_quantity() {
  var products = get_products();
  var quantity = 0;
  for (var i = 0; i < products.length; i++) {
    quantity += products[i].quantity;
  }
  return quantity;
}

// 제품 옵션 출력
// ex) M S L
function get_option() {
  var products = get_products();
  var option = "";
  for (var i = 0; i < products.length; i++) {
    option += products[i].variant + " ";
  }
  return option;
}

// 제품 수량+옵션 조합으로 출력
// ex) M(1) S(2) L(3)
function get_option_info() {
  var products = get_products();
  var option = "";
  var info = [];
  for (var i = 0; i < products.length; i++) {
    if (products[i].hasOwnProperty("variant")) {
      // 옵션이 있는 상품의 경우.
      info.push(products[i].variant + "(" + String(products[i].quantity) + ")");
    } else {
      // 옵션이 없는 상품의 경우.
      info.push(String(products[i].quantity));
    }
  }
  return info.join(" ");
}

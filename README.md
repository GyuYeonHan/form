# thymeleaf와 Spring을 이용한 Form 사용법 정리

----------

##### 1. single checkbox
~~~
<div>
  <div class="form-check">
    <input type="checkbox" id="open" th:field="*{open}" class="form-check-input"/>
    <label for="open" class="form-check-label"></label>
  </div>
</div>
~~~
- th:field 가 자동으로 name, value 속성을 생성
- hidden input을 생성해 아무것도 선택되지 않을 떄 FALSE값이 넘어가도록 도와줌


##### 2. multi checkbox
~~~
<div>
    <div>등록 지역</div>
    <div th:each="region : ${regions}" class="form-check form-check-inline">
      <input type="checkbox" th:field="*{regions}" th:value="${region.key}" class="form-check-input">
      <label th:for="${#ids.prev('regions')}"
             th:text="${region.value}" class="form-check-label"></label>
    </div>
</div>
~~~

##### 3. radio
~~~
<div>
    <div>상품 종류</div>
    <div th:each="type : ${itemTypes}" class="form-check form-check-inline">
        <input type="radio" th:field="*{itemType}" th:value="${type.name()}" class="form-check-input">
        <label th:for="${#ids.prev('itemType')}" th:text="${type.description}" class="form-check-label"></label>
    </div>
</div>
~~~

##### 4. select
~~~
<div>
    <div>배송 방식</div>
    <select th:field="*{deliveryCode}" class="form-select">
        <option value="">==배송 방식 선택==</option>
        <option th:each="deliveryCode : ${deliveryCodes}" th:value="${deliveryCode.code}"
                th:text="${deliveryCode.displayName}"></option>
    </select>
</div>
~~~

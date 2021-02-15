---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: anonim tür bildirimlerinde özellik adlarını ve türleri Çıkarçıkar (Visual Basic)'
title: 'Nasıl yapılır: Anonim Türde Bildirimlerden Özellik Adları ve Türlerini Çıkarma'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: e4bff8cd8dd879b97618a3bc69e1eaf1c7c269b7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483904"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="a2971-103">Nasıl yapılır: Anonim Türde Bildirimlerden Özellik Adları ve Türlerini Çıkarma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2971-103">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>

<span data-ttu-id="a2971-104">Anonim türler, özelliklerin veri türlerini doğrudan belirtmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2971-104">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="a2971-105">Tüm özelliklerin türleri algılanır.</span><span class="sxs-lookup"><span data-stu-id="a2971-105">Types of all properties are inferred.</span></span> <span data-ttu-id="a2971-106">Aşağıdaki örnekte, türleri `Name` ve, `Price` bunları başlatmak için kullanılan değerlerden doğrudan algılanır.</span><span class="sxs-lookup"><span data-stu-id="a2971-106">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

<span data-ttu-id="a2971-107">Anonim türler Ayrıca diğer kaynaklardan özellik adlarını ve türlerini de çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="a2971-107">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="a2971-108">Aşağıdaki bölümler, çıkarım mümkün olduğu durumların bir listesini ve olmadığı durumlara örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2971-108">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>

## <a name="successful-inference"></a><span data-ttu-id="a2971-109">Başarılı çıkarım</span><span class="sxs-lookup"><span data-stu-id="a2971-109">Successful Inference</span></span>

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="a2971-110">Anonim türler, aşağıdaki kaynaklardan özellik adlarını ve türlerini çıkarabilir:</span><span class="sxs-lookup"><span data-stu-id="a2971-110">Anonymous types can infer property names and types from the following sources:</span></span>

- <span data-ttu-id="a2971-111">Değişken adlarından.</span><span class="sxs-lookup"><span data-stu-id="a2971-111">From variable names.</span></span> <span data-ttu-id="a2971-112">Anonim türün `anonProduct` iki özelliği `productName` ve olur `productPrice` .</span><span class="sxs-lookup"><span data-stu-id="a2971-112">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="a2971-113">Veri türleri, sırasıyla özgün değişkenlerle `String` ve `Double` , ve sırasıyla olur.</span><span class="sxs-lookup"><span data-stu-id="a2971-113">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- <span data-ttu-id="a2971-114">Diğer nesnelerin özelliğinden veya alan adlarından.</span><span class="sxs-lookup"><span data-stu-id="a2971-114">From property or field names of other objects.</span></span> <span data-ttu-id="a2971-115">Örneğin, `car` ve özelliklerini içeren bir türün nesnesini düşünün `CarClass` `Name` `ID` .</span><span class="sxs-lookup"><span data-stu-id="a2971-115">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="a2971-116">Yeni bir anonim tür örneği oluşturmak için, `car1` ve ile `Name` `ID` nesnesinden değerleri ile başlatılan özellikleri `car` , aşağıdakileri yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a2971-116">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  <span data-ttu-id="a2971-117">Önceki bildirim, anonim türü tanımlayan daha uzun kod satırıyla eşdeğerdir `car2` .</span><span class="sxs-lookup"><span data-stu-id="a2971-117">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- <span data-ttu-id="a2971-118">XML üye adlarından.</span><span class="sxs-lookup"><span data-stu-id="a2971-118">From XML member names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  <span data-ttu-id="a2971-119">İçin sonuç türünün, `anon` `Book` türünde <xref:System.Collections.IEnumerable> (XElement) bir özelliği olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a2971-119">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>

- <span data-ttu-id="a2971-120">Aşağıdaki örnekte olduğu gibi parametresi olmayan bir işlevden `SomeFunction` .</span><span class="sxs-lookup"><span data-stu-id="a2971-120">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  <span data-ttu-id="a2971-121">`anon2`Aşağıdaki kodda bulunan değişkeni, adlı bir karakter olan bir özelliğine sahip anonim bir türdür `First` .</span><span class="sxs-lookup"><span data-stu-id="a2971-121">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="a2971-122">Bu kod, işlevi tarafından döndürülen harfi "E" olarak görüntüler <xref:System.Linq.Enumerable.First%2A> .</span><span class="sxs-lookup"><span data-stu-id="a2971-122">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a><span data-ttu-id="a2971-123">Çıkarım arızaları</span><span class="sxs-lookup"><span data-stu-id="a2971-123">Inference Failures</span></span>

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="a2971-124">Ad çıkarımı, aşağıdakiler dahil olmak üzere birçok durumda başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="a2971-124">Name inference will fail in many circumstances, including the following:</span></span>

- <span data-ttu-id="a2971-125">Çıkarımı, bir yöntem, Oluşturucu veya bağımsız değişken gerektiren parametreli bir özellik çağrısından türetilir.</span><span class="sxs-lookup"><span data-stu-id="a2971-125">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="a2971-126">`anon1` `someFunction` Bir veya daha fazla bağımsız değişken varsa, önceki bir bildirimi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a2971-126">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  <span data-ttu-id="a2971-127">Yeni bir özellik adına atama sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="a2971-127">Assignment to a new property name solves the problem.</span></span>

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- <span data-ttu-id="a2971-128">Çıkarımı karmaşık bir ifadeden türetilir.</span><span class="sxs-lookup"><span data-stu-id="a2971-128">The inference derives from a complex expression.</span></span>

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  <span data-ttu-id="a2971-129">Hata, ifadenin sonucu bir özellik adına atanarak çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="a2971-129">The error can be resolved by assigning the result of the expression to a property name.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- <span data-ttu-id="a2971-130">Birden çok özellik için çıkarım aynı ada sahip iki veya daha fazla özellik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2971-130">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="a2971-131">Önceki örneklerde bildirimlere geri döndüğünüzde, hem hem de `product.Name` `car1.Name` aynı anonim türdeki özellikleri listelenemez.</span><span class="sxs-lookup"><span data-stu-id="a2971-131">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="a2971-132">Bunun nedeni, bunların her biri için gösterilen tanıtıcıdır `Name` .</span><span class="sxs-lookup"><span data-stu-id="a2971-132">This is because the inferred identifier for each of these would be `Name`.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  <span data-ttu-id="a2971-133">Bu sorun, değerler ayrı özellik adlarına atanarak çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="a2971-133">The problem can be solved by assigning the values to distinct property names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  <span data-ttu-id="a2971-134">Büyük/küçük harf ve küçük harfler arasındaki değişiklikler iki adı farklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a2971-134">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- <span data-ttu-id="a2971-135">Bir özelliğin başlangıç türü ve değeri henüz kurulu olmayan başka bir özelliğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a2971-135">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="a2971-136">Örneğin, `.IDName = .LastName` zaten başlatılmamış olduğu müddetçe anonim tür bildiriminde geçerli değildir `.LastName` .</span><span class="sxs-lookup"><span data-stu-id="a2971-136">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  <span data-ttu-id="a2971-137">Bu örnekte, özelliklerinin bildirildiği sırayı tersine çevirerek sorunu çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2971-137">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- <span data-ttu-id="a2971-138">Anonim türün Özellik adı bir üyesinin adı ile aynıdır <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="a2971-138">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="a2971-139">Örneğin, bir yöntemi olduğu için aşağıdaki bildirim başarısız olur `Equals` <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="a2971-139">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  <span data-ttu-id="a2971-140">Özellik adını değiştirerek sorunu çözebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a2971-140">You can fix the problem by changing the property name:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a><span data-ttu-id="a2971-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2971-141">See also</span></span>

- [<span data-ttu-id="a2971-142">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="a2971-142">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="a2971-143">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2971-143">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="a2971-144">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="a2971-144">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="a2971-145">Key</span><span class="sxs-lookup"><span data-stu-id="a2971-145">Key</span></span>](../../../language-reference/modifiers/key.md)

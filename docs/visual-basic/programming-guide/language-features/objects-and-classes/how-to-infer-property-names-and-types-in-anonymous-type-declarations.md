---
title: "Nasıl yapılır: Anonim Türde Bildirimlerden Özellik Adları ve Türlerini Çıkarma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 66b9f8c0346f74ff631969bda122de7913a551c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="95010-102">Nasıl yapılır: Anonim Türde Bildirimlerden Özellik Adları ve Türlerini Çıkarma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95010-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>
<span data-ttu-id="95010-103">Anonim türler doğrudan özellikleri veri türlerini belirtmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="95010-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="95010-104">Tüm özelliklerin türleri algılanır.</span><span class="sxs-lookup"><span data-stu-id="95010-104">Types of all properties are inferred.</span></span> <span data-ttu-id="95010-105">Aşağıdaki örnekte, türlerini `Name` ve `Price` doğrudan bunları başlatmak için kullanılan değerlerinden algılanır.</span><span class="sxs-lookup"><span data-stu-id="95010-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 <span data-ttu-id="95010-106">Anonim türler de özellik adları ve diğer kaynaklardan türlerinin çıkarımını.</span><span class="sxs-lookup"><span data-stu-id="95010-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="95010-107">Aşağıdaki bölümlerde çıkarım mümkün olduğu durumlarda ve değil olduğu durumlar örnekleri listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="95010-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>  
  
## <a name="successful-inference"></a><span data-ttu-id="95010-108">Başarılı çıkarımı</span><span class="sxs-lookup"><span data-stu-id="95010-108">Successful Inference</span></span>  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="95010-109">Anonim türleri, özellik adları ve türlerini aşağıdaki kaynaklardan çıkarımını:</span><span class="sxs-lookup"><span data-stu-id="95010-109">Anonymous types can infer property names and types from the following sources:</span></span>  
  
-   <span data-ttu-id="95010-110">Değişken adları.</span><span class="sxs-lookup"><span data-stu-id="95010-110">From variable names.</span></span> <span data-ttu-id="95010-111">Anonim tür `anonProduct` iki özelliği vardır `productName` ve `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="95010-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="95010-112">Veri türlerini olanlar özgün değişkenlerin olacaktır `String` ve `Double`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="95010-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   <span data-ttu-id="95010-113">Özellik veya alan adlarından diğer nesnelerin.</span><span class="sxs-lookup"><span data-stu-id="95010-113">From property or field names of other objects.</span></span> <span data-ttu-id="95010-114">Örneğin, göz önünde bulundurun bir `car` nesnesinin bir `CarClass` içeren türü `Name` ve `ID` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="95010-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="95010-115">Yeni bir anonim tür örneği oluşturmak için `car1`, ile `Name` ve `ID` değerlerle başlatılan özellikleri `car` nesnesi, aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="95010-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     <span data-ttu-id="95010-116">Uzun kod satırı ile anonim tür tanımlayan için yukarıdaki bildirimi eşdeğerdir `car2`.</span><span class="sxs-lookup"><span data-stu-id="95010-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   <span data-ttu-id="95010-117">XML üye adları.</span><span class="sxs-lookup"><span data-stu-id="95010-117">From XML member names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     <span data-ttu-id="95010-118">Sonuç türü için `anon` bir özellik olması gereken `Book`, türü <xref:System.Collections.IEnumerable>, (XElement).</span><span class="sxs-lookup"><span data-stu-id="95010-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>  
  
-   <span data-ttu-id="95010-119">Hiçbir parametre gibi sahip bir işlevden `SomeFunction` aşağıdaki örnekte.</span><span class="sxs-lookup"><span data-stu-id="95010-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     <span data-ttu-id="95010-120">Değişkeni `anon2` aşağıdaki kodda bir özellik, adlandırılmış bir karakter içeren bir anonim türüdür `First`.</span><span class="sxs-lookup"><span data-stu-id="95010-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="95010-121">Bu kodu bir harf "E", işlev tarafından döndürülen harf görüntüler <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="95010-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## <a name="inference-failures"></a><span data-ttu-id="95010-122">Çıkarım hataları</span><span class="sxs-lookup"><span data-stu-id="95010-122">Inference Failures</span></span>  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="95010-123">Ad çıkarım, aşağıdakiler de dahil olmak üzere çoğu durumda, başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="95010-123">Name inference will fail in many circumstances, including the following:</span></span>  
  
-   <span data-ttu-id="95010-124">Çıkarım bir yöntemi, bir oluşturucu ya da bağımsız değişkenler gerektirir parametreli bir özelliğin çağrısından türer.</span><span class="sxs-lookup"><span data-stu-id="95010-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="95010-125">Önceki bildirimi `anon1` başarısız olur `someFunction` bir veya daha fazla bağımsız değişkenlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95010-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     <span data-ttu-id="95010-126">Yeni bir özellik adı atamayı sorununu çözer.</span><span class="sxs-lookup"><span data-stu-id="95010-126">Assignment to a new property name solves the problem.</span></span>  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   <span data-ttu-id="95010-127">Çıkarım karmaşık bir ifade türer.</span><span class="sxs-lookup"><span data-stu-id="95010-127">The inference derives from a complex expression.</span></span>  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     <span data-ttu-id="95010-128">Hata, bir özellik adı ifadenin sonucu atayarak çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="95010-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   <span data-ttu-id="95010-129">Çıkarım birden çok özellikler için aynı ada sahip iki veya daha fazla özellik üretir.</span><span class="sxs-lookup"><span data-stu-id="95010-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="95010-130">Önceki örneklerde bildirimleri geri başvurma, her ikisi de listelenemiyor `product.Name` ve `car1.Name` özellikleri aynı anonim tür olarak.</span><span class="sxs-lookup"><span data-stu-id="95010-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="95010-131">Bunların her biri için oluşturulursa tanımlayıcı olacağından budur `Name`.</span><span class="sxs-lookup"><span data-stu-id="95010-131">This is because the inferred identifier for each of these would be `Name`.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     <span data-ttu-id="95010-132">Farklı özellik adları için değerler atayarak sorun çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="95010-132">The problem can be solved by assigning the values to distinct property names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     <span data-ttu-id="95010-133">(Büyük ve küçük harfler arasında) iki ad ayrı değişiklik yapmayın durumunda değişiklikler unutmayın.</span><span class="sxs-lookup"><span data-stu-id="95010-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   <span data-ttu-id="95010-134">Bir özelliğin değerini ve başlangıç türünü henüz kurulmadığı başka bir özellikte bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="95010-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="95010-135">Örneğin, `.IDName = .LastName` anonim tür bildiriminde geçersiz sürece `.LastName` zaten başlatılmış.</span><span class="sxs-lookup"><span data-stu-id="95010-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     <span data-ttu-id="95010-136">Bu örnekte, Özellikler bildirilen sıraya döndürerek sorunu düzeltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95010-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   <span data-ttu-id="95010-137">Anonim türün bir özellik adı adı bir üyesi olarak aynıdır <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="95010-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="95010-138">Örneğin, çünkü aşağıdaki bildirimi başarısız `Equals` bir yöntemi <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="95010-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     <span data-ttu-id="95010-139">Özellik adı değiştirerek sorunu düzeltebilir:</span><span class="sxs-lookup"><span data-stu-id="95010-139">You can fix the problem by changing the property name:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="95010-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95010-140">See Also</span></span>  
 [<span data-ttu-id="95010-141">Nesne başlatıcıları: Adlandırılmış ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="95010-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="95010-142">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="95010-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="95010-143">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="95010-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="95010-144">Anahtarı</span><span class="sxs-lookup"><span data-stu-id="95010-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)

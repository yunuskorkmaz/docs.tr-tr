---
title: 'Nasıl yapılır: Özellik adları ve türleri (Visual Basic) anonim türde bildirimlerden çıkarma'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 67cc9e85d249365a7b4b7636c99766087314622d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596870"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="05531-102">Nasıl yapılır: Özellik adları ve türleri (Visual Basic) anonim türde bildirimlerden çıkarma</span><span class="sxs-lookup"><span data-stu-id="05531-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>
<span data-ttu-id="05531-103">Anonim türler, doğrudan özellikleri veri türlerini belirtmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="05531-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="05531-104">Tüm özelliklerin türleri algılanır.</span><span class="sxs-lookup"><span data-stu-id="05531-104">Types of all properties are inferred.</span></span> <span data-ttu-id="05531-105">Aşağıdaki örnekte, türlerini `Name` ve `Price` doğrudan bunları başlatmak için kullanılan değerlerden algılanır.</span><span class="sxs-lookup"><span data-stu-id="05531-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 <span data-ttu-id="05531-106">Anonim türler, özellik adları ve türlerini diğer kaynaklardan da çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="05531-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="05531-107">Aşağıdaki bölümlerde, çıkarım mümkün olduğu durumlarda ve nerede durumlara örnek olarak listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="05531-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>  
  
## <a name="successful-inference"></a><span data-ttu-id="05531-108">Başarılı çıkarımı</span><span class="sxs-lookup"><span data-stu-id="05531-108">Successful Inference</span></span>  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="05531-109">Anonim türler, özellik adları ve türlerini aşağıdaki kaynaklardan çıkarabilir:</span><span class="sxs-lookup"><span data-stu-id="05531-109">Anonymous types can infer property names and types from the following sources:</span></span>  
  
-   <span data-ttu-id="05531-110">Değişken adları.</span><span class="sxs-lookup"><span data-stu-id="05531-110">From variable names.</span></span> <span data-ttu-id="05531-111">Anonim tür `anonProduct` iki özelliği vardır `productName` ve `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="05531-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="05531-112">Bu özgün değişkenlerin veri türlerini olacaktır `String` ve `Double`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="05531-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   <span data-ttu-id="05531-113">Özellik veya alan adlarından diğer nesne.</span><span class="sxs-lookup"><span data-stu-id="05531-113">From property or field names of other objects.</span></span> <span data-ttu-id="05531-114">Örneğin, bir `car` nesnesinin bir `CarClass` içeren tür `Name` ve `ID` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="05531-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="05531-115">Yeni bir anonim tür örneği oluşturmak için `car1`, ile `Name` ve `ID` değerlerle başlatılan özellikleri `car` nesnesi, aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="05531-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     <span data-ttu-id="05531-116">Uzun anonim türü tanımlayan bir kod satırına önceki bildirime eşdeğerdir `car2`.</span><span class="sxs-lookup"><span data-stu-id="05531-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   <span data-ttu-id="05531-117">XML üye adları.</span><span class="sxs-lookup"><span data-stu-id="05531-117">From XML member names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     <span data-ttu-id="05531-118">Sonuç türü `anon` bir özelliğe sahip `Book`, türü <xref:System.Collections.IEnumerable>, (XElement).</span><span class="sxs-lookup"><span data-stu-id="05531-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>  
  
-   <span data-ttu-id="05531-119">Hiçbir parametre gibi olan bir işlevden `SomeFunction` aşağıdaki örnekte.</span><span class="sxs-lookup"><span data-stu-id="05531-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     <span data-ttu-id="05531-120">Değişken `anon2` aşağıdaki kodda bir özellik, adlandırılmış bir karakter içeren bir anonim türdür `First`.</span><span class="sxs-lookup"><span data-stu-id="05531-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="05531-121">Bu kodu bir harf "E", işlev tarafından döndürülen harf görüntüler <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="05531-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## <a name="inference-failures"></a><span data-ttu-id="05531-122">Çıkarım hataları</span><span class="sxs-lookup"><span data-stu-id="05531-122">Inference Failures</span></span>  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="05531-123">Aşağıdakiler dahil olmak üzere çoğu durumda, adı anlam çıkarma başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="05531-123">Name inference will fail in many circumstances, including the following:</span></span>  
  
-   <span data-ttu-id="05531-124">Çıkarım bir yöntemi, bir oluşturucu veya bağımsız değişken gerektirir parametreli bir özellik çağrısından türetilir.</span><span class="sxs-lookup"><span data-stu-id="05531-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="05531-125">Önceki bildirimi `anon1` başarısız olur `someFunction` bir veya daha fazla bağımsız değişkenlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="05531-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     <span data-ttu-id="05531-126">Yeni bir özellik adı atama sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="05531-126">Assignment to a new property name solves the problem.</span></span>  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   <span data-ttu-id="05531-127">Çıkarım karmaşık bir ifadeden türetilir.</span><span class="sxs-lookup"><span data-stu-id="05531-127">The inference derives from a complex expression.</span></span>  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     <span data-ttu-id="05531-128">Hata, ifadenin sonucu bir özellik adına atayarak çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="05531-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   <span data-ttu-id="05531-129">Birden çok özellik için çıkarım aynı ada sahip iki veya daha fazla özellik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05531-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="05531-130">Geri bildirimleri önceki örneklerde başvuran, her ikisi de listelenemiyor `product.Name` ve `car1.Name` aynı anonim tür özellikleri.</span><span class="sxs-lookup"><span data-stu-id="05531-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="05531-131">Bunların her biri için çıkarsanan tanımlayıcı olacağından budur `Name`.</span><span class="sxs-lookup"><span data-stu-id="05531-131">This is because the inferred identifier for each of these would be `Name`.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     <span data-ttu-id="05531-132">Değerlerin benzersiz özellik adlarını atayarak sorun çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="05531-132">The problem can be solved by assigning the values to distinct property names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     <span data-ttu-id="05531-133">(Büyük ve küçük harfler arasında değişiklik) iki ad ayrı yapmayın durumunda değişiklikleri unutmayın.</span><span class="sxs-lookup"><span data-stu-id="05531-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   <span data-ttu-id="05531-134">Bir özelliğin değerini ve başlangıç türü henüz kurulmasa başka bir özellikte bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="05531-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="05531-135">Örneğin, `.IDName = .LastName` bir anonim tür bildiriminde geçerli değil sürece `.LastName` zaten başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="05531-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     <span data-ttu-id="05531-136">Bu örnekte, özelliklerini bildirilen sırasını ters çevirerek sorunu düzeltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05531-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   <span data-ttu-id="05531-137">Anonim türün bir özellik adı bir üyesinin adıyla aynı olduğu <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="05531-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="05531-138">Örneğin, aşağıdaki bildirimi nedeniyle başarısız `Equals` bir yöntemidir <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="05531-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     <span data-ttu-id="05531-139">Özellik adını değiştirerek sorunu düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="05531-139">You can fix the problem by changing the property name:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="05531-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05531-140">See also</span></span>
- [<span data-ttu-id="05531-141">Nesne başlatıcıları: Adlandırılmış ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="05531-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="05531-142">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="05531-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="05531-143">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="05531-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="05531-144">Key</span><span class="sxs-lookup"><span data-stu-id="05531-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)

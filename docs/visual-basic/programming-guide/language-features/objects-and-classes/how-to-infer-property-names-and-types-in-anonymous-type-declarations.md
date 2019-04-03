---
title: 'Nasıl yapılır: Özellik adları ve türleri (Visual Basic) anonim türde bildirimlerden çıkarma'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: be3c74e8f8c69eb9f0a1d0dda4d6c90dfd7e567a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824734"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="67581-102">Nasıl yapılır: Özellik adları ve türleri (Visual Basic) anonim türde bildirimlerden çıkarma</span><span class="sxs-lookup"><span data-stu-id="67581-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>
<span data-ttu-id="67581-103">Anonim türler, doğrudan özellikleri veri türlerini belirtmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="67581-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="67581-104">Tüm özelliklerin türleri algılanır.</span><span class="sxs-lookup"><span data-stu-id="67581-104">Types of all properties are inferred.</span></span> <span data-ttu-id="67581-105">Aşağıdaki örnekte, türlerini `Name` ve `Price` doğrudan bunları başlatmak için kullanılan değerlerden algılanır.</span><span class="sxs-lookup"><span data-stu-id="67581-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="67581-106">Anonim türler, özellik adları ve türlerini diğer kaynaklardan da çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="67581-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="67581-107">Aşağıdaki bölümlerde, çıkarım mümkün olduğu durumlarda ve nerede durumlara örnek olarak listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="67581-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>  
  
## <a name="successful-inference"></a><span data-ttu-id="67581-108">Başarılı çıkarımı</span><span class="sxs-lookup"><span data-stu-id="67581-108">Successful Inference</span></span>  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="67581-109">Anonim türler, özellik adları ve türlerini aşağıdaki kaynaklardan çıkarabilir:</span><span class="sxs-lookup"><span data-stu-id="67581-109">Anonymous types can infer property names and types from the following sources:</span></span>  
  
-   <span data-ttu-id="67581-110">Değişken adları.</span><span class="sxs-lookup"><span data-stu-id="67581-110">From variable names.</span></span> <span data-ttu-id="67581-111">Anonim tür `anonProduct` iki özelliği vardır `productName` ve `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="67581-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="67581-112">Bu özgün değişkenlerin veri türlerini olacaktır `String` ve `Double`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="67581-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]  
  
-   <span data-ttu-id="67581-113">Özellik veya alan adlarından diğer nesne.</span><span class="sxs-lookup"><span data-stu-id="67581-113">From property or field names of other objects.</span></span> <span data-ttu-id="67581-114">Örneğin, bir `car` nesnesinin bir `CarClass` içeren tür `Name` ve `ID` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="67581-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="67581-115">Yeni bir anonim tür örneği oluşturmak için `car1`, ile `Name` ve `ID` değerlerle başlatılan özellikleri `car` nesnesi, aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="67581-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]  
  
     <span data-ttu-id="67581-116">Uzun anonim türü tanımlayan bir kod satırına önceki bildirime eşdeğerdir `car2`.</span><span class="sxs-lookup"><span data-stu-id="67581-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]  
  
-   <span data-ttu-id="67581-117">XML üye adları.</span><span class="sxs-lookup"><span data-stu-id="67581-117">From XML member names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]  
  
     <span data-ttu-id="67581-118">Sonuç türü `anon` bir özelliğe sahip `Book`, türü <xref:System.Collections.IEnumerable>, (XElement).</span><span class="sxs-lookup"><span data-stu-id="67581-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>  
  
-   <span data-ttu-id="67581-119">Hiçbir parametre gibi olan bir işlevden `SomeFunction` aşağıdaki örnekte.</span><span class="sxs-lookup"><span data-stu-id="67581-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     <span data-ttu-id="67581-120">Değişken `anon2` aşağıdaki kodda bir özellik, adlandırılmış bir karakter içeren bir anonim türdür `First`.</span><span class="sxs-lookup"><span data-stu-id="67581-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="67581-121">Bu kodu bir harf "E", işlev tarafından döndürülen harf görüntüler <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="67581-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]  
  
## <a name="inference-failures"></a><span data-ttu-id="67581-122">Çıkarım hataları</span><span class="sxs-lookup"><span data-stu-id="67581-122">Inference Failures</span></span>  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="67581-123">Aşağıdakiler dahil olmak üzere çoğu durumda, adı anlam çıkarma başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="67581-123">Name inference will fail in many circumstances, including the following:</span></span>  
  
-   <span data-ttu-id="67581-124">Çıkarım bir yöntemi, bir oluşturucu veya bağımsız değişken gerektirir parametreli bir özellik çağrısından türetilir.</span><span class="sxs-lookup"><span data-stu-id="67581-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="67581-125">Önceki bildirimi `anon1` başarısız olur `someFunction` bir veya daha fazla bağımsız değişkenlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="67581-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     <span data-ttu-id="67581-126">Yeni bir özellik adı atama sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="67581-126">Assignment to a new property name solves the problem.</span></span>  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   <span data-ttu-id="67581-127">Çıkarım karmaşık bir ifadeden türetilir.</span><span class="sxs-lookup"><span data-stu-id="67581-127">The inference derives from a complex expression.</span></span>  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     <span data-ttu-id="67581-128">Hata, ifadenin sonucu bir özellik adına atayarak çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="67581-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]  
  
-   <span data-ttu-id="67581-129">Birden çok özellik için çıkarım aynı ada sahip iki veya daha fazla özellik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="67581-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="67581-130">Geri bildirimleri önceki örneklerde başvuran, her ikisi de listelenemiyor `product.Name` ve `car1.Name` aynı anonim tür özellikleri.</span><span class="sxs-lookup"><span data-stu-id="67581-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="67581-131">Bunların her biri için çıkarsanan tanımlayıcı olacağından budur `Name`.</span><span class="sxs-lookup"><span data-stu-id="67581-131">This is because the inferred identifier for each of these would be `Name`.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     <span data-ttu-id="67581-132">Değerlerin benzersiz özellik adlarını atayarak sorun çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="67581-132">The problem can be solved by assigning the values to distinct property names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]  
  
     <span data-ttu-id="67581-133">(Büyük ve küçük harfler arasında değişiklik) iki ad ayrı yapmayın durumunda değişiklikleri unutmayın.</span><span class="sxs-lookup"><span data-stu-id="67581-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   <span data-ttu-id="67581-134">Bir özelliğin değerini ve başlangıç türü henüz kurulmasa başka bir özellikte bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="67581-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="67581-135">Örneğin, `.IDName = .LastName` bir anonim tür bildiriminde geçerli değil sürece `.LastName` zaten başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="67581-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     <span data-ttu-id="67581-136">Bu örnekte, özelliklerini bildirilen sırasını ters çevirerek sorunu düzeltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67581-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]  
  
-   <span data-ttu-id="67581-137">Anonim türün bir özellik adı bir üyesinin adıyla aynı olduğu <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="67581-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="67581-138">Örneğin, aşağıdaki bildirimi nedeniyle başarısız `Equals` bir yöntemidir <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="67581-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     <span data-ttu-id="67581-139">Özellik adını değiştirerek sorunu düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="67581-139">You can fix the problem by changing the property name:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="67581-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67581-140">See also</span></span>

- [<span data-ttu-id="67581-141">Nesne başlatıcıları: Adlandırılmış ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="67581-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="67581-142">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="67581-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="67581-143">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="67581-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="67581-144">Key</span><span class="sxs-lookup"><span data-stu-id="67581-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)

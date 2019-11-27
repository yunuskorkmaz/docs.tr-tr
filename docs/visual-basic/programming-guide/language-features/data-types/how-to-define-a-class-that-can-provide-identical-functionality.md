---
title: 'Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: d80623d9e55358d37aa45f11f1525c80a09b91a6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350050"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="39ca4-102">Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39ca4-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="39ca4-103">Farklı veri türleri üzerinde özdeş işlevsellik sağlayan nesneler oluşturabileceğiniz bir sınıf tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39ca4-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="39ca4-104">Bunu yapmak için tanımda bir veya daha fazla *tür parametresi* belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39ca4-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="39ca4-105">Sınıf daha sonra çeşitli veri türlerini kullanan nesneler için bir şablon işlevi görebilir.</span><span class="sxs-lookup"><span data-stu-id="39ca4-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="39ca4-106">Bu şekilde tanımlanan bir sınıfa *Genel sınıf*denir.</span><span class="sxs-lookup"><span data-stu-id="39ca4-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="39ca4-107">Genel bir sınıf tanımlamanın avantajı bunu yalnızca bir kez tanımlamanız, kodunuzun çok çeşitli veri türlerini kullanan birçok nesne oluşturmak için bunu kullanmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39ca4-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="39ca4-108">Bu, `Object` türü ile sınıfının tanımlanmasıyla daha iyi performansa neden olur.</span><span class="sxs-lookup"><span data-stu-id="39ca4-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="39ca4-109">Sınıfların yanı sıra genel yapıları, arabirimleri, yordamları ve temsilcileri de tanımlayabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39ca4-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="39ca4-110">Bir tür parametresiyle bir sınıf tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="39ca4-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="39ca4-111">Sınıfı normal şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="39ca4-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="39ca4-112">Bir tür parametresi belirtmek için sınıf adından hemen sonra `(Of` *typeparameter*`)` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="39ca4-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="39ca4-113">Birden fazla tür parametreye sahipseniz, parantez içinde virgülle ayrılmış bir liste oluşturun.</span><span class="sxs-lookup"><span data-stu-id="39ca4-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="39ca4-114">`Of` anahtar sözcüğünü tekrarlamayın.</span><span class="sxs-lookup"><span data-stu-id="39ca4-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="39ca4-115">Kodunuz basit atama haricinde bir tür parametresinde işlemler gerçekleştiriyorsa, bir veya daha fazla *kısıtlama*eklemek için bu tür parametresini bir `As` yan tümcesiyle izleyin.</span><span class="sxs-lookup"><span data-stu-id="39ca4-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="39ca4-116">Bir kısıtlama, bu tür parametresi için sağlanan türün aşağıdakiler gibi bir gereksinime uygun olmasını sağlar:</span><span class="sxs-lookup"><span data-stu-id="39ca4-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    - <span data-ttu-id="39ca4-117">Kodunuzun gerçekleştirdiği `>`gibi bir işlemi destekler</span><span class="sxs-lookup"><span data-stu-id="39ca4-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    - <span data-ttu-id="39ca4-118">, Kodunuzun eriştiği, yöntemi gibi bir üyeyi destekler</span><span class="sxs-lookup"><span data-stu-id="39ca4-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    - <span data-ttu-id="39ca4-119">Parametresiz bir Oluşturucu sunar</span><span class="sxs-lookup"><span data-stu-id="39ca4-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="39ca4-120">Herhangi bir kısıtlama belirtmezseniz, kodunuzun kullanabileceği tek işlemler ve Üyeler [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)tarafından desteklenenler olabilir.</span><span class="sxs-lookup"><span data-stu-id="39ca4-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="39ca4-121">Daha fazla bilgi için bkz. [tür listesi](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="39ca4-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="39ca4-122">Sağlanan bir türle bildirildiği her sınıf üyesini tanımlayın ve `typeparameter``As` bildirin.</span><span class="sxs-lookup"><span data-stu-id="39ca4-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="39ca4-123">Bu iç depolama, yordam parametreleri ve dönüş değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="39ca4-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="39ca4-124">Kodunuzun yalnızca `itemType`sağlayabileceğinizden herhangi bir veri türü tarafından desteklenen işlemler ve Yöntemler kullandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="39ca4-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="39ca4-125">Aşağıdaki örnek, çok basit bir listeyi yöneten bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39ca4-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="39ca4-126">Bu, listenin iç dizi `items`barındırır ve using kodu, liste öğelerinin veri türünü bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="39ca4-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="39ca4-127">Parametreli bir Oluşturucu, kodun `items`üst sınırı ayarlamasına olanak tanır ve parametresiz Oluşturucu bunu 9 (Toplam 10 öğe için) olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="39ca4-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the parameterless constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="39ca4-128">Bir `simpleList` `Integer` değerlerinin listesini, `String` değerlerinin listesini tutacak başka bir sınıfı ve `Date` değerleri tutmak için başka bir sınıf bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39ca4-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="39ca4-129">Liste üyelerinin veri türü dışında, tüm bu sınıflardan oluşturulan nesneler aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="39ca4-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="39ca4-130">`itemType` kullanan tür bağımsız değişkeni `Boolean` veya `Double`, bir yapı, sabit listesi ya da uygulamanızın tanımladığı bir tür sınıf gibi bir iç tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="39ca4-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="39ca4-131">Sınıfı `simpleList` aşağıdaki kodla test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39ca4-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="39ca4-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39ca4-132">See also</span></span>

- [<span data-ttu-id="39ca4-133">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="39ca4-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="39ca4-134">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="39ca4-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="39ca4-135">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="39ca4-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="39ca4-136">Durumunu</span><span class="sxs-lookup"><span data-stu-id="39ca4-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="39ca4-137">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="39ca4-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="39ca4-138">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="39ca4-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="39ca4-139">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="39ca4-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

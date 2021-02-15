---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: farklı veri türlerinde özdeş Işlevsellik sağlayabilen bir sınıf tanımlama (Visual Basic)'
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
ms.openlocfilehash: 14be6c748ccb311c6a2974e8947b01a1c55a90b6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469753"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="c7e7e-103">Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7e7e-103">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>

<span data-ttu-id="c7e7e-104">Farklı veri türleri üzerinde özdeş işlevsellik sağlayan nesneler oluşturabileceğiniz bir sınıf tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-104">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="c7e7e-105">Bunu yapmak için tanımda bir veya daha fazla *tür parametresi* belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-105">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="c7e7e-106">Sınıf daha sonra çeşitli veri türlerini kullanan nesneler için bir şablon işlevi görebilir.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-106">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="c7e7e-107">Bu şekilde tanımlanan bir sınıfa *Genel sınıf* denir.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-107">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="c7e7e-108">Genel bir sınıf tanımlamanın avantajı bunu yalnızca bir kez tanımlamanız, kodunuzun çok çeşitli veri türlerini kullanan birçok nesne oluşturmak için bunu kullanmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-108">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="c7e7e-109">Bu, sınıfının türüyle tanımlanması gerekenden daha iyi performans elde ediyor `Object` .</span><span class="sxs-lookup"><span data-stu-id="c7e7e-109">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="c7e7e-110">Sınıfların yanı sıra genel yapıları, arabirimleri, yordamları ve temsilcileri de tanımlayabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-110">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="c7e7e-111">Bir tür parametresiyle bir sınıf tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="c7e7e-111">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="c7e7e-112">Sınıfı normal şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-112">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="c7e7e-113">`(Of`  `)` Bir tür parametresi belirtmek için sınıf adından hemen sonra typeparameter ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-113">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="c7e7e-114">Birden fazla tür parametreye sahipseniz, parantez içinde virgülle ayrılmış bir liste oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-114">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="c7e7e-115">Anahtar sözcüğünü tekrarlamayın `Of` .</span><span class="sxs-lookup"><span data-stu-id="c7e7e-115">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="c7e7e-116">Kodunuz basit atama haricinde bir tür parametresinde işlemler gerçekleştiriyorsa, `As` bir veya daha fazla *kısıtlama* eklemek için bu tür parametresini yan tümcesiyle birlikte izleyin.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-116">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="c7e7e-117">Bir kısıtlama, bu tür parametresi için sağlanan türün aşağıdakiler gibi bir gereksinime uygun olmasını sağlar:</span><span class="sxs-lookup"><span data-stu-id="c7e7e-117">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    - <span data-ttu-id="c7e7e-118">Kodunuzun gerçekleştirdiği gibi bir işlemi destekler `>`</span><span class="sxs-lookup"><span data-stu-id="c7e7e-118">Supports an operation, such as `>`, that your code performs</span></span>  
  
    - <span data-ttu-id="c7e7e-119">, Kodunuzun eriştiği, yöntemi gibi bir üyeyi destekler</span><span class="sxs-lookup"><span data-stu-id="c7e7e-119">Supports a member, such as a method, that your code accesses</span></span>  
  
    - <span data-ttu-id="c7e7e-120">Parametresiz bir Oluşturucu sunar</span><span class="sxs-lookup"><span data-stu-id="c7e7e-120">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="c7e7e-121">Herhangi bir kısıtlama belirtmezseniz, kodunuzun kullanabileceği tek işlemler ve Üyeler [nesne veri türü](../../../language-reference/data-types/object-data-type.md)tarafından desteklenenler olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-121">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="c7e7e-122">Daha fazla bilgi için bkz. [tür listesi](../../../language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="c7e7e-122">For more information, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="c7e7e-123">Sağlanan türle belirtilecek her sınıf üyesini tanımlayın ve bunu bildirin `As` `typeparameter` .</span><span class="sxs-lookup"><span data-stu-id="c7e7e-123">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="c7e7e-124">Bu iç depolama, yordam parametreleri ve dönüş değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-124">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="c7e7e-125">Kodunuzun yalnızca, sağlayatabileceği herhangi bir veri türü tarafından desteklenen işlemler ve Yöntemler kullandığından emin olun `itemType` .</span><span class="sxs-lookup"><span data-stu-id="c7e7e-125">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="c7e7e-126">Aşağıdaki örnek, çok basit bir listeyi yöneten bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-126">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="c7e7e-127">İç dizide listesini barındırır `items` ve using kodu liste öğelerinin veri türünü bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-127">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="c7e7e-128">Parametreli bir Oluşturucu, kodunun üst sınırı ayarlamasına olanak tanır `items` ve parametresiz Oluşturucu bunu 9 ' a (Toplam 10 öğe için) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-128">A parameterized constructor allows the using code to set the upper bound of `items`, and the parameterless constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="c7e7e-129">' Dan bir sınıf, bir değer listesi tutan `simpleList` başka bir `Integer` sınıf ve değerleri tutmak için başka bir sınıf bildirebilirsiniz `String` `Date` .</span><span class="sxs-lookup"><span data-stu-id="c7e7e-129">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="c7e7e-130">Liste üyelerinin veri türü dışında, tüm bu sınıflardan oluşturulan nesneler aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-130">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="c7e7e-131">Using kodunun sağladığı tür bağımsız değişkeni `itemType` `Boolean` , ya da `Double` , bir yapı, bir numaralandırma veya uygulamanızın tanımladığı bir sınıf türü gibi bir iç tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-131">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="c7e7e-132">Sınıfı aşağıdaki kodla test edebilirsiniz `simpleList` .</span><span class="sxs-lookup"><span data-stu-id="c7e7e-132">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="c7e7e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7e7e-133">See also</span></span>

- [<span data-ttu-id="c7e7e-134">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="c7e7e-134">Data Types</span></span>](index.md)
- [<span data-ttu-id="c7e7e-135">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="c7e7e-135">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="c7e7e-136">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="c7e7e-136">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="c7e7e-137">Durumunu</span><span class="sxs-lookup"><span data-stu-id="c7e7e-137">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="c7e7e-138">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="c7e7e-138">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="c7e7e-139">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="c7e7e-139">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="c7e7e-140">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c7e7e-140">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)

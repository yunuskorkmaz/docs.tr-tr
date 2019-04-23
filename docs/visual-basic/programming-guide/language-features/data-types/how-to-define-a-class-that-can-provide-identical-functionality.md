---
title: 'Nasıl yapılır: (Visual Basic) farklı veri türlerinde aynı işlevselliği sağlayabilen bir sınıf tanımlama'
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
ms.openlocfilehash: 9121041f936c091cda0e2af41b4f5be8d826d582
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318460"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="84ecd-102">Nasıl yapılır: (Visual Basic) farklı veri türlerinde aynı işlevselliği sağlayabilen bir sınıf tanımlama</span><span class="sxs-lookup"><span data-stu-id="84ecd-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="84ecd-103">Bir sınıf tanımlayabilir, farklı veri türlerinde aynı işlevselliği sağlayan nesneleri oluşturabileceğiniz öğesinden.</span><span class="sxs-lookup"><span data-stu-id="84ecd-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="84ecd-104">Bunu yapmak için bir veya daha fazla belirttiğiniz *tür parametrelerindeki* tanımında.</span><span class="sxs-lookup"><span data-stu-id="84ecd-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="84ecd-105">Sınıf çeşitli veri türlerini kullanan nesneler için bir şablon olarak hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="84ecd-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="84ecd-106">Bu şekilde tanımlanan bir sınıfa bir *genel sınıf*.</span><span class="sxs-lookup"><span data-stu-id="84ecd-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="84ecd-107">Genel bir sınıf tanımlamanın yararı, yalnızca bir kez tanımlayın ve kodunuzu çok çeşitli veri türleri kullanan birçok nesneler oluşturmak için kullanabilirsiniz ' dir.</span><span class="sxs-lookup"><span data-stu-id="84ecd-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="84ecd-108">Sınıf ile daha iyi performans sonuçlanır `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="84ecd-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="84ecd-109">Sınıflara ek olarak tanımlayabilir ve genel yapılar, arabirimler, yordamları ve temsilciler kullanın.</span><span class="sxs-lookup"><span data-stu-id="84ecd-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="84ecd-110">Bir tür parametresi ile bir sınıf tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="84ecd-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="84ecd-111">Normal bir şekilde tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="84ecd-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="84ecd-112">Ekleme `(Of` *typeparameter* `)` sonrasında hemen bir tür parametresi belirtmek için sınıf adı.</span><span class="sxs-lookup"><span data-stu-id="84ecd-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="84ecd-113">Birden fazla tür parametresi varsa, parantez içinde virgülle ayrılmış bir liste olun.</span><span class="sxs-lookup"><span data-stu-id="84ecd-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="84ecd-114">Yineleme `Of` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="84ecd-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="84ecd-115">Kodunuzu basit atama dışında bir tür parametresi üzerinde işlemler gerçekleştirirse, o tür parametreyle izleyin bir `As` yan tümcesi bir veya daha fazla eklemek için *kısıtlamaları*.</span><span class="sxs-lookup"><span data-stu-id="84ecd-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="84ecd-116">Kısıtlama türü, tür parametresi için sağlanan aşağıdaki gibi bir gereksinimi karşılayan garanti eder:</span><span class="sxs-lookup"><span data-stu-id="84ecd-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="84ecd-117">Bir işlem gibi destekleyen `>`, kodunuzu gerçekleştiren</span><span class="sxs-lookup"><span data-stu-id="84ecd-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="84ecd-118">Kodunuzu erişen bir yöntemi gibi bir üye destekler</span><span class="sxs-lookup"><span data-stu-id="84ecd-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="84ecd-119">Parametresiz bir Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="84ecd-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="84ecd-120">Kısıtlamalardan belirtmezseniz, yalnızca işlemler ve kodunuzu kullanabileceğiniz üyeleri tarafından desteklenen olanlardır [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="84ecd-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="84ecd-121">Daha fazla bilgi için [tür listesi](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="84ecd-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="84ecd-122">Sağlanan türüyle belirtilecek olan her sınıf üyesi tanımlamak ve bildirirken `As` `typeparameter`.</span><span class="sxs-lookup"><span data-stu-id="84ecd-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="84ecd-123">Bu, iç depolama alanı, yordam parametreleri ve dönüş değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="84ecd-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="84ecd-124">Kodunuzun kullandığı yalnızca işlemler ve için sağlayabilirler herhangi bir veri türü tarafından desteklenen yöntemleri mutlaka `itemType`.</span><span class="sxs-lookup"><span data-stu-id="84ecd-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="84ecd-125">Aşağıdaki örnek çok basit bir listeyi yöneten bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84ecd-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="84ecd-126">İç dizide listesini tutar `items`ve kod kullanarak liste öğelerini veri türünü bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84ecd-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="84ecd-127">Parametreli bir kurucu kullanarak sağlayan çokluğun ayarlamak üzere kod `items`, ve varsayılan oluşturucu, bu ayarlar 9 (için toplam 10 öğe).</span><span class="sxs-lookup"><span data-stu-id="84ecd-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="84ecd-128">Bir sınıftan bildirebilirsiniz `simpleList` listesini tutmak için `Integer` değerleri, bir listesi için başka bir sınıf `String` değerleri ve başka tutacak `Date` değerleri.</span><span class="sxs-lookup"><span data-stu-id="84ecd-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="84ecd-129">Üyeleri listele veri türünü hariç, tüm bu sınıflardan oluşturulan nesnelerin aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="84ecd-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="84ecd-130">Kod kullanarak tür bağımsız değişkeni için sağladığı `itemType` iç bir tür gibi olabilir `Boolean` veya `Double`, bir yapı, bir numaralandırma veya sınıf, uygulamanızı tanımlayan bir dahil olmak üzere herhangi bir türde.</span><span class="sxs-lookup"><span data-stu-id="84ecd-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="84ecd-131">Sınıf sınayabilirsiniz `simpleList` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="84ecd-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="84ecd-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84ecd-132">See also</span></span>

- [<span data-ttu-id="84ecd-133">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="84ecd-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="84ecd-134">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="84ecd-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="84ecd-135">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="84ecd-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="84ecd-136">,</span><span class="sxs-lookup"><span data-stu-id="84ecd-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="84ecd-137">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="84ecd-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="84ecd-138">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="84ecd-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="84ecd-139">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="84ecd-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

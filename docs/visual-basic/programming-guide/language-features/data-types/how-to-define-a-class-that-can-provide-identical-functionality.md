---
title: "Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c81d1f795b0c27f2eaf07832f2c1276b626f5ce1
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="389db-102">Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="389db-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="389db-103">Bir sınıf tanımlama öğesinden farklı veri türlerinde aynı işlevselliği sağlayan nesneleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="389db-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="389db-104">Bunu yapmak için bir veya daha fazla belirttiğiniz *tür parametrelerindeki* tanımında.</span><span class="sxs-lookup"><span data-stu-id="389db-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="389db-105">Sınıf çeşitli veri türlerini kullanan nesneler için bir şablon olarak hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="389db-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="389db-106">Bu şekilde tanımlanmış bir sınıf olarak adlandırılan bir *genel bir sınıf*.</span><span class="sxs-lookup"><span data-stu-id="389db-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="389db-107">Genel bir sınıf tanımlama avantajı, yalnızca bir kez tanımlayın ve kodunuzu çok çeşitli veri türleri kullanan çok sayıda nesne oluşturmak için kullanabilirsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="389db-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="389db-108">Bu sınıfı tanımlayan daha iyi performans sonuçları `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="389db-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="389db-109">Sınıfları yanı sıra tanımlayabilir ve genel yapılar, arabirimler, yordamlar ve temsilciler kullanın.</span><span class="sxs-lookup"><span data-stu-id="389db-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="389db-110">Tür parametresi bir sınıfla tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="389db-110">To define a class with a type parameter</span></span>  
  
1.  <span data-ttu-id="389db-111">Sınıf normal şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="389db-111">Define the class in the normal way.</span></span>  
  
2.  <span data-ttu-id="389db-112">Ekleme `(Of` *typeparameter* `)` sonra hemen bir tür parametresi belirlemek için sınıf adı.</span><span class="sxs-lookup"><span data-stu-id="389db-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3.  <span data-ttu-id="389db-113">Birden fazla tür parametresi varsa parantez içinde virgülle ayrılmış bir liste olun.</span><span class="sxs-lookup"><span data-stu-id="389db-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="389db-114">Yineleme `Of` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="389db-114">Do not repeat the `Of` keyword.</span></span>  
  
4.  <span data-ttu-id="389db-115">Kodunuzu bir tür parametresi basit atama dışındaki işlemleri gerçekleştirirse, o tür parametresi ile izleyin bir `As` bir veya daha fazla eklemek için yan tümcesi *kısıtlamaları*.</span><span class="sxs-lookup"><span data-stu-id="389db-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="389db-116">Bu tür parametresi için sağlanan türü aşağıdaki gibi bir gereksinimini karşılayan bir kısıtlama garanti eder:</span><span class="sxs-lookup"><span data-stu-id="389db-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="389db-117">Bir işlem gibi destekleyen `>`, kodunuzu gerçekleştiren</span><span class="sxs-lookup"><span data-stu-id="389db-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="389db-118">Kodunuzu erişen bir yöntem gibi bir üye destekler</span><span class="sxs-lookup"><span data-stu-id="389db-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="389db-119">Parametresiz bir kurucusu gösterir</span><span class="sxs-lookup"><span data-stu-id="389db-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="389db-120">Kısıtlamalar belirtmezseniz, yalnızca operations ve kodunuzu kullanabilirsiniz üyeleri tarafından desteklenen olanlardır [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="389db-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="389db-121">Daha fazla bilgi için bkz: [türü listesinde](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="389db-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5.  <span data-ttu-id="389db-122">Sağlanan türüyle belirtilecek olan her sınıf üyesi tanımlamak ve bildirirken `As` `typeparameter`.</span><span class="sxs-lookup"><span data-stu-id="389db-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="389db-123">Bu, dahili depolama, parametreler ve dönüş değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="389db-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6.  <span data-ttu-id="389db-124">Kodunuzu, yalnızca operations ve sağlamak için herhangi bir veri türü tarafından desteklenen yöntemleri kullandığından emin olmanız `itemType`.</span><span class="sxs-lookup"><span data-stu-id="389db-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="389db-125">Aşağıdaki örnek çok basit bir liste yöneten bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="389db-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="389db-126">İç dizisinde listesini tutar `items`ve kod kullanarak veri türü liste öğelerini bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="389db-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="389db-127">Parametreli Oluşturucusu kullanılarak sağlar üst sınırının ayarlamak için kod `items`, ve bu ayarlar varsayılan oluşturucu ile 9 (için 10 öğe toplamı).</span><span class="sxs-lookup"><span data-stu-id="389db-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     <span data-ttu-id="389db-128">Öğesinden bir sınıf bildirme `simpleList` listesini tutmak için `Integer` değerleri, listesini tutmak için başka bir sınıf `String` değerleri ve başka tutmak için `Date` değerleri.</span><span class="sxs-lookup"><span data-stu-id="389db-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="389db-129">Üyeleri listeleme veri türünü hariç, tüm bu sınıflardan oluşturulan nesneler aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="389db-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="389db-130">Kod kullanarak tür bağımsız değişkeni için sağladığı `itemType` geçerli bir tür gibi olabilir `Boolean` veya `Double`, bir yapı, numaralandırma veya sınıf, uygulamanızın tanımlayan bir de dahil olmak üzere herhangi bir türde.</span><span class="sxs-lookup"><span data-stu-id="389db-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="389db-131">Sınıfı test `simpleList` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="389db-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="389db-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="389db-132">See Also</span></span>  
 [<span data-ttu-id="389db-133">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="389db-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="389db-134">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="389db-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="389db-135">Dil bağımsızlığı ve dilden bağımsız bileşenler</span><span class="sxs-lookup"><span data-stu-id="389db-135">Language Independence and Language-Independent Components</span></span>](../../../../../docs/standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="389db-136">,</span><span class="sxs-lookup"><span data-stu-id="389db-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="389db-137">Tür listesi</span><span class="sxs-lookup"><span data-stu-id="389db-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="389db-138">Nasıl yapılır: genel bir sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="389db-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="389db-139">Nesne veri türü</span><span class="sxs-lookup"><span data-stu-id="389db-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

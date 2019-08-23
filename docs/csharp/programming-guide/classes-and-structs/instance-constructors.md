---
title: Örnek oluşturucular- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 198f9db1430226343fd3709c66d16b68e975ab3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922164"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="cc1f3-102">Örnek Oluşturucuları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cc1f3-102">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="cc1f3-103">Örnek oluşturucular, bir [sınıfın](../../language-reference/keywords/class.md)nesnesini oluşturmak için [Yeni](../../language-reference/operators/new-operator.md) ifadeyi kullandığınızda herhangi bir örnek üye değişkeni oluşturmak ve başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="cc1f3-104">Statik bir sınıf [](../../language-reference/keywords/static.md) veya statik değişkenleri statik olmayan bir sınıfta başlatmak için statik bir Oluşturucu tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-104">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="cc1f3-105">Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="cc1f3-105">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="cc1f3-106">Aşağıdaki örnek bir örnek Oluşturucu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="cc1f3-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="cc1f3-107">Açıklık için, bu sınıf ortak alanlar içerir.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="cc1f3-108">Ortak alanların kullanımı önerilen bir programlama uygulaması değildir çünkü bir programda herhangi bir yerde herhangi bir yerdeki herhangi bir yönteme izin verir ve bir nesnenin iç işleyişi için doğrulanmamış erişimdir.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="cc1f3-109">Veri üyeleri genellikle özel olmalıdır ve yalnızca sınıf yöntemleri ve özellikleri aracılığıyla erişilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="cc1f3-110">Bu örnek Oluşturucu, `Coords` sınıfı temel alan bir nesne oluşturulduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-110">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="cc1f3-111">Böyle bir bağımsız değişken alan bir Oluşturucu gibi bir oluşturucuya *parametresiz Oluşturucu*denir.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-111">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="cc1f3-112">Ancak, genellikle ek oluşturucular sağlamak yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="cc1f3-113">Örneğin, `Coords` sınıfa veri üyeleri için başlangıç değerlerini belirtmemizi sağlayan bir Oluşturucu ekleyebiliriz:</span><span class="sxs-lookup"><span data-stu-id="cc1f3-113">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="cc1f3-114">Bu, `Coords` nesnelerin varsayılan veya belirli başlangıç değerleriyle oluşturulmasına izin verir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="cc1f3-114">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="cc1f3-115">Bir sınıfın Oluşturucusu yoksa, parametresiz bir Oluşturucu otomatik olarak oluşturulur ve nesne alanlarını başlatmak için varsayılan değerler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-115">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="cc1f3-116">Örneğin, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) 0 olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-116">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="cc1f3-117">Varsayılan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="cc1f3-117">For more information on default values, see [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="cc1f3-118">Bu nedenle, `Coords` parametresiz bir Oluşturucu tüm veri üyelerini sıfıra başlattığında, sınıfın çalışma biçimini değiştirmeden tamamen kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-118">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="cc1f3-119">Bu konunun ilerleyen kısımlarında örnek 1 ' de birden çok Oluşturucu kullanan bir örnek verilmiştir ve örnek 2 ' de otomatik olarak oluşturulan bir oluşturucuya örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="cc1f3-120">Örnek oluşturucular, temel sınıfların örnek oluşturucularını çağırmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="cc1f3-121">Sınıf oluşturucusu, aşağıdaki gibi, başlatıcı aracılığıyla temel sınıfın oluşturucusunu çağırabilir:</span><span class="sxs-lookup"><span data-stu-id="cc1f3-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="cc1f3-122">Bu örnekte, `Circle` sınıfı, RADIUS ve yüksekliği temsil eden değerleri, öğesinden `Circle` türetilmiş tarafından `Shape` sunulan oluşturucuya geçirir.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="cc1f3-123">`Shape` Ve`Circle` bu konuda örnek 3 olarak görünen bir örnek.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="cc1f3-124">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="cc1f3-124">Example 1</span></span>  
 <span data-ttu-id="cc1f3-125">Aşağıdaki örnek, bağımsız değişkenler olmadan biri ve iki bağımsız değişken içeren iki sınıf oluşturucusuna sahip bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="cc1f3-126">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="cc1f3-126">Example 2</span></span>  
 <span data-ttu-id="cc1f3-127">Bu örnekte, sınıfın `Person` herhangi bir Oluşturucusu yoktur, bu durumda parametresiz bir Oluşturucu otomatik olarak sağlanır ve alanlar varsayılan değerlerine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-127">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="cc1f3-128">`age` Varsayılan değerinin `0` vevarsayılan`null`değerinin olduğunu unutmayın. `name`</span><span class="sxs-lookup"><span data-stu-id="cc1f3-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span> <span data-ttu-id="cc1f3-129">Varsayılan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="cc1f3-129">For more information on default values, see [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="cc1f3-130">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="cc1f3-130">Example 3</span></span>  
 <span data-ttu-id="cc1f3-131">Aşağıdaki örnek, temel sınıf başlatıcısının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="cc1f3-132">Sınıfı genel sınıftan `Shape`türetilir ve `Cylinder` sınıfı `Circle` sınıfından türetilir. `Circle`</span><span class="sxs-lookup"><span data-stu-id="cc1f3-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="cc1f3-133">Türetilmiş her sınıftaki Oluşturucu kendi temel sınıf başlatıcısını kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="cc1f3-134">Temel sınıf oluşturucularını çağırma hakkında daha fazla örnek için bkz. [sanal](../../language-reference/keywords/virtual.md), [geçersiz kılma](../../language-reference/keywords/override.md)ve [temel](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="cc1f3-134">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc1f3-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc1f3-135">See also</span></span>

- [<span data-ttu-id="cc1f3-136">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cc1f3-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cc1f3-137">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="cc1f3-137">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="cc1f3-138">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="cc1f3-138">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="cc1f3-139">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="cc1f3-139">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="cc1f3-140">static</span><span class="sxs-lookup"><span data-stu-id="cc1f3-140">static</span></span>](../../language-reference/keywords/static.md)

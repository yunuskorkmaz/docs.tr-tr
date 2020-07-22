---
title: Örnek oluşturucular-C# Programlama Kılavuzu
description: C# ' deki örnek oluşturucular, bir sınıfın nesnesini oluşturmak için yeni ifadeyi kullandığınızda herhangi bir örnek üye değişkenlerini oluşturur ve başlatır.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: d70e786446fb198afb4e0311757cacb65b706f47
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864208"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="a526c-103">Örnek Oluşturucuları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a526c-103">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="a526c-104">Örnek oluşturucular, bir [sınıfın](../../language-reference/keywords/class.md)nesnesini oluşturmak için [Yeni](../../language-reference/operators/new-operator.md) ifadeyi kullandığınızda herhangi bir örnek üye değişkeni oluşturmak ve başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a526c-104">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="a526c-105">Statik [bir sınıf veya](../../language-reference/keywords/static.md) statik değişkenleri statik olmayan bir sınıfta başlatmak için statik bir Oluşturucu tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="a526c-105">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="a526c-106">Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="a526c-106">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="a526c-107">Aşağıdaki örnek bir örnek Oluşturucu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="a526c-107">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="a526c-108">Açıklık için, bu sınıf ortak alanlar içerir.</span><span class="sxs-lookup"><span data-stu-id="a526c-108">For clarity, this class contains public fields.</span></span> <span data-ttu-id="a526c-109">Ortak alanların kullanımı önerilen bir programlama uygulaması değildir çünkü bir programda herhangi bir yerde herhangi bir yerdeki herhangi bir yönteme izin verir ve bir nesnenin iç işleyişi için doğrulanmamış erişimdir.</span><span class="sxs-lookup"><span data-stu-id="a526c-109">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="a526c-110">Veri üyeleri genellikle özel olmalıdır ve yalnızca sınıf yöntemleri ve özellikleri aracılığıyla erişilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a526c-110">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="a526c-111">Bu örnek Oluşturucu, sınıfı temel alan bir nesne oluşturulduğunda çağrılır `Coords` .</span><span class="sxs-lookup"><span data-stu-id="a526c-111">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="a526c-112">Böyle bir bağımsız değişken alan bir Oluşturucu gibi bir oluşturucuya *parametresiz Oluşturucu*denir.</span><span class="sxs-lookup"><span data-stu-id="a526c-112">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="a526c-113">Ancak, genellikle ek oluşturucular sağlamak yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="a526c-113">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="a526c-114">Örneğin, `Coords` sınıfa veri üyeleri için başlangıç değerlerini belirtmemizi sağlayan bir Oluşturucu ekleyebiliriz:</span><span class="sxs-lookup"><span data-stu-id="a526c-114">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="a526c-115">Bu `Coords` , nesnelerin varsayılan veya belirli başlangıç değerleriyle oluşturulmasına izin verir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="a526c-115">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="a526c-116">Bir sınıfın Oluşturucusu yoksa, parametresiz bir Oluşturucu otomatik olarak oluşturulur ve nesne alanlarını başlatmak için varsayılan değerler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a526c-116">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="a526c-117">Örneğin, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) 0 olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a526c-117">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="a526c-118">Tür varsayılan değerleri hakkında daha fazla bilgi için bkz. [C# türlerin varsayılan değerleri](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="a526c-118">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="a526c-119">Bu nedenle, `Coords` parametresiz bir Oluşturucu tüm veri üyelerini sıfıra başlattığında, sınıfın çalışma biçimini değiştirmeden tamamen kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a526c-119">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="a526c-120">Bu konunun ilerleyen kısımlarında örnek 1 ' de birden çok Oluşturucu kullanan bir örnek verilmiştir ve örnek 2 ' de otomatik olarak oluşturulan bir oluşturucuya örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a526c-120">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="a526c-121">Örnek oluşturucular, temel sınıfların örnek oluşturucularını çağırmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a526c-121">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="a526c-122">Sınıf oluşturucusu, aşağıdaki gibi, başlatıcı aracılığıyla temel sınıfın oluşturucusunu çağırabilir:</span><span class="sxs-lookup"><span data-stu-id="a526c-122">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="a526c-123">Bu örnekte, sınıfı, `Circle` RADIUS ve yüksekliği temsil eden değerleri, öğesinden türetilmiş tarafından sunulan oluşturucuya geçirir `Shape` `Circle` .</span><span class="sxs-lookup"><span data-stu-id="a526c-123">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="a526c-124">`Shape`Ve `Circle` Bu konuda örnek 3 olarak görünen bir örnek.</span><span class="sxs-lookup"><span data-stu-id="a526c-124">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="a526c-125">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="a526c-125">Example 1</span></span>  
 <span data-ttu-id="a526c-126">Aşağıdaki örnek, bağımsız değişkenler olmadan biri ve iki bağımsız değişken içeren iki sınıf oluşturucusuna sahip bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a526c-126">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="a526c-127">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="a526c-127">Example 2</span></span>  
 <span data-ttu-id="a526c-128">Bu örnekte, sınıfın `Person` herhangi bir Oluşturucusu yoktur, bu durumda parametresiz bir Oluşturucu otomatik olarak sağlanır ve alanlar varsayılan değerlerine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a526c-128">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="a526c-129">Varsayılan değerinin ve varsayılan değerinin olduğunu `age` unutmayın `0` `name` `null` .</span><span class="sxs-lookup"><span data-stu-id="a526c-129">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="a526c-130">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="a526c-130">Example 3</span></span>  
 <span data-ttu-id="a526c-131">Aşağıdaki örnek, temel sınıf başlatıcısının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a526c-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="a526c-132">`Circle`Sınıfı genel sınıftan türetilir `Shape` ve sınıfı `Cylinder` `Circle` sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="a526c-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="a526c-133">Türetilmiş her sınıftaki Oluşturucu kendi temel sınıf başlatıcısını kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="a526c-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="a526c-134">Temel sınıf oluşturucularını çağırma hakkında daha fazla örnek için bkz. [sanal](../../language-reference/keywords/virtual.md), [geçersiz kılma](../../language-reference/keywords/override.md)ve [temel](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="a526c-134">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a526c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a526c-135">See also</span></span>

- [<span data-ttu-id="a526c-136">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a526c-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a526c-137">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="a526c-137">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="a526c-138">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a526c-138">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="a526c-139">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="a526c-139">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="a526c-140">static</span><span class="sxs-lookup"><span data-stu-id="a526c-140">static</span></span>](../../language-reference/keywords/static.md)

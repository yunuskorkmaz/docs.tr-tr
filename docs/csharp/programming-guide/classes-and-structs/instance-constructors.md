---
title: Örnek Oluşturucular - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 621b8ca7510b0b9916c9c46f201ff77402c3c655
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964722"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="a873f-102">Örnek Oluşturucuları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a873f-102">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="a873f-103">Örnek oluşturucular, bir [sınıfın](../../language-reference/keywords/class.md)nesnesini oluşturmak için [yeni](../../language-reference/operators/new-operator.md) ifadeyi kullandığınızda herhangi bir örnek üye değişken oluşturmak ve başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a873f-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="a873f-104">[Statik](../../language-reference/keywords/static.md) olmayan bir sınıfta statik bir sınıf veya statik değişkenler başlatma, statik bir oluşturucu tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="a873f-104">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="a873f-105">Daha fazla bilgi için Statik [Oluşturucular'a](./static-constructors.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a873f-105">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="a873f-106">Aşağıdaki örnek oluşturucu bir örneği gösterir:</span><span class="sxs-lookup"><span data-stu-id="a873f-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="a873f-107">Açıklık için, bu sınıf ortak alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="a873f-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="a873f-108">Ortak alanların kullanımı, bir programın herhangi bir yerindeki herhangi bir yöntemin nesnenin iç işleyişine sınırsız ve doğrulanmamış erişime izin verdiği için önerilen bir programlama uygulaması değildir.</span><span class="sxs-lookup"><span data-stu-id="a873f-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="a873f-109">Veri üyeleri genellikle özel olmalı ve yalnızca sınıf yöntemleri ve özellikleri ile erişilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a873f-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="a873f-110">Bu örnek `Coords` oluşturucu, sınıfa dayalı bir nesne oluşturulduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a873f-110">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="a873f-111">Bunun gibi hiçbir bağımsız değişken alan bir yapıcıya *parametresiz yapıcı*denir.</span><span class="sxs-lookup"><span data-stu-id="a873f-111">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="a873f-112">Ancak, genellikle ek oluşturucular sağlamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a873f-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="a873f-113">Örneğin, `Coords` sınıfa veri üyeleri için başlangıç değerlerini belirtmemizi sağlayan bir oluşturucu ekleyebiliriz:</span><span class="sxs-lookup"><span data-stu-id="a873f-113">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="a873f-114">Bu, `Coords` nesnelerin varsayılan veya belirli başlangıç değerleri yle oluşturulmasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="a873f-114">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="a873f-115">Bir sınıfın oluşturucusu yoksa, parametresiz bir oluşturucu otomatik olarak oluşturulur ve nesne alanlarını başlatmak için varsayılan değerler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a873f-115">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="a873f-116">Örneğin, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) 0'a başharfle başlanır.</span><span class="sxs-lookup"><span data-stu-id="a873f-116">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="a873f-117">Tür varsayılan değerleri hakkında bilgi için [C# türlerinin Varsayılan değerlerine](../../language-reference/builtin-types/default-values.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a873f-117">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="a873f-118">Bu nedenle, `Coords` sınıf parametresiz oluşturucu tüm veri üyelerini sıfıra indirdiği için, sınıfın çalışma şeklini değiştirmeden tamamen kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a873f-118">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="a873f-119">Bu konunun ilerleyen saatlerinde Örnek 1'de birden çok oluşturucu kullanılarak tam bir örnek verilmiştir ve Örnek 2'de otomatik olarak oluşturulan bir oluşturucu örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a873f-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="a873f-120">Örnek oluşturucular, taban sınıfların örnek oluşturucularını çağırmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a873f-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="a873f-121">Sınıf oluşturucu, taban sınıfın oluşturucusu başlatıcısı aracılığıyla aşağıdaki gibi çağırabilir:</span><span class="sxs-lookup"><span data-stu-id="a873f-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="a873f-122">Bu örnekte, `Circle` sınıf yarıçapı ve yüksekliği temsil eden `Shape` değerleri `Circle` türetildiği tarafından sağlanan oluşturucuya geçirir.</span><span class="sxs-lookup"><span data-stu-id="a873f-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="a873f-123">Tam bir `Shape` örnek `Circle` kullanarak ve örnek 3 olarak bu konu görünür.</span><span class="sxs-lookup"><span data-stu-id="a873f-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="a873f-124">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="a873f-124">Example 1</span></span>  
 <span data-ttu-id="a873f-125">Aşağıdaki örnek, biri bağımsız, diğeri iki bağımsız değişkenli olmak üzere iki sınıf oluşturucusu olan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a873f-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="a873f-126">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="a873f-126">Example 2</span></span>  
 <span data-ttu-id="a873f-127">Bu örnekte, `Person` sınıfın herhangi bir oluşturucusu yoktur, bu durumda parametresiz bir oluşturucu otomatik olarak sağlanır ve alanlar varsayılan değerlerine başolarak başlar.</span><span class="sxs-lookup"><span data-stu-id="a873f-127">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="a873f-128">Varsayılan değerin `age` ve `0` varsayılan değerinin `name` . `null`</span><span class="sxs-lookup"><span data-stu-id="a873f-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="a873f-129">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="a873f-129">Example 3</span></span>  
 <span data-ttu-id="a873f-130">Aşağıdaki örnek, taban sınıf baş harflerini kullanarak gösteriş gösterir.</span><span class="sxs-lookup"><span data-stu-id="a873f-130">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="a873f-131">Sınıf `Circle` genel sınıftan `Shape`türetilir `Cylinder` ve sınıf `Circle` sınıftan türetilir.</span><span class="sxs-lookup"><span data-stu-id="a873f-131">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="a873f-132">Her türemiş sınıfın oluşturucusu taban sınıf baş harflerini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="a873f-132">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="a873f-133">Taban sınıf oluşturucuları çağırmak la ilgili daha fazla örnek için [sanal,](../../language-reference/keywords/virtual.md) [geçersiz kılma](../../language-reference/keywords/override.md)ve [taban'a](../../language-reference/keywords/base.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a873f-133">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a873f-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a873f-134">See also</span></span>

- [<span data-ttu-id="a873f-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a873f-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a873f-136">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="a873f-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="a873f-137">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a873f-137">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="a873f-138">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="a873f-138">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="a873f-139">Statik</span><span class="sxs-lookup"><span data-stu-id="a873f-139">static</span></span>](../../language-reference/keywords/static.md)

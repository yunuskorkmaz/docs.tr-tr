---
title: "Genel Sınıflar (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: afeca9fc49221551470f90f6f57d1b40e0142521
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2018
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="5533a-102">Genel Sınıflar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5533a-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="5533a-103">Genel sınıflar belirli veri türüne özgü olmayan işlemler kapsüller.</span><span class="sxs-lookup"><span data-stu-id="5533a-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="5533a-104">Bağlantılı listeleri, karma tabloları, yığınları, kuyruklar, ağaçlar ve benzeri gibi koleksiyonlarıyla genel sınıfları için en yaygın kullanımı içindir.</span><span class="sxs-lookup"><span data-stu-id="5533a-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="5533a-105">Öğeler ekleme ve koleksiyondan kaldırma gibi işlemleri temelde aynı şekilde depolanmasını veri türü bağımsız olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5533a-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="5533a-106">Koleksiyon sınıfları gerektiren çoğu senaryolar için .NET sınıf kitaplığı'nda sağlanan olanları kullanmak önerilen yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="5533a-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="5533a-107">Bu sınıfları kullanma hakkında daha fazla bilgi için bkz: [.NET içinde genel koleksiyonlar](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="5533a-107">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="5533a-108">Genellikle, varolan bir somut sınıfı ile başlatarak ve en iyi dengeyi Genelleştirme ve kullanılabilirlik ulaşana kadar aynı anda bir tür parametreleri türlerini değiştirme genel sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5533a-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="5533a-109">Genel sınıflarınızı oluştururken, önemli noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5533a-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
-   <span data-ttu-id="5533a-110">Tür parametreleri genelleştirmek için hangi tür.</span><span class="sxs-lookup"><span data-stu-id="5533a-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="5533a-111">Bir kural, Parametreleştirme daha fazla türleri, daha esnek ve yeniden kullanılabilir kodunuzu haline gelir.</span><span class="sxs-lookup"><span data-stu-id="5533a-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="5533a-112">Ancak, çok fazla Genelleştirme okumak veya anlamak diğer geliştiriciler için zordur kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5533a-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
-   <span data-ttu-id="5533a-113">Tür parametreleri uygulamak için varsa hangi kısıtlamaları (bkz [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="5533a-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="5533a-114">Hala işlemesi gerekir türleri işlemenize olanak sağlayacak maksimum kısıtlamaları olası uygulamak iyi bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="5533a-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="5533a-115">Başvuru türleri yalnızca kullanmaya genel sınıfınız yönelik biliyorsanız, örneğin, sınıf kısıtlaması uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5533a-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="5533a-116">Değer türleri ile sınıfınız istenmeyen kullanımını engeller ve kullanmanıza olanak tanır `as` işlecinin `T`ve null değerler denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5533a-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
-   <span data-ttu-id="5533a-117">Temel sınıflar ve alt sınıfların genel davranış faktörü görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5533a-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="5533a-118">Genel sınıflar temel sınıf olarak kullanılabileceği için aynı tasarım konuları burada geçerli olarak genel olmayan sınıflarla.</span><span class="sxs-lookup"><span data-stu-id="5533a-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="5533a-119">Bu konunun ilerleyen bölümlerinde genel temel sınıflardan devralan hakkında kurallar konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="5533a-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
-   <span data-ttu-id="5533a-120">Bir veya daha fazla genel arabirimlerini görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5533a-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="5533a-121">Örneğin, bir genel türler tabanlı koleksiyon öğeleri oluşturmak için kullanılan bir sınıfı tanımlıyorsanız, bir arabirim gibi uygulama gerekebilir <xref:System.IComparable%601> burada `T` sınıfınız türüdür.</span><span class="sxs-lookup"><span data-stu-id="5533a-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="5533a-122">Basit genel bir sınıf örneği için bkz: [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="5533a-122">For an example of a simple generic class, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span>  
  
 <span data-ttu-id="5533a-123">Tür parametreleri ve kısıtlamalar için kuralları, özellikle devralma ve üye erişilebilirlik ile ilgili genel bir sınıf davranışı için birkaç etkiler.</span><span class="sxs-lookup"><span data-stu-id="5533a-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="5533a-124">Devam etmeden önce bazı koşulları anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5533a-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="5533a-125">Genel bir sınıf için `Node<T>,` istemci kodu sınıfı başvuru ya da kapalı oluşturulan türü oluşturmak için bir tür bağımsız değişkeni belirterek (`Node<int>`).</span><span class="sxs-lookup"><span data-stu-id="5533a-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="5533a-126">Alternatif olarak, genel bir taban sınıfı belirtin, örneğin belirtilmeyen tür parametresi bırakabilirsiniz, açık bir oluşturmak için türü oluşturulan (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="5533a-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="5533a-127">Genel sınıflar somut, kapalı oluşturulan veya açık oluşturulan temel sınıflardan devrettiği:</span><span class="sxs-lookup"><span data-stu-id="5533a-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]  
  
 <span data-ttu-id="5533a-128">Genel olmayan başka bir deyişle, somut, sınıflar devral kapalı oluşturulan temel sınıfları, ancak olmayan sınıflardan açık oluşturulan veya tür parametreleri örneği oluşturmak için gerekli tür bağımsız değişkeni sağlamak istemci kodu için çalışma zamanında hiçbir şekilde olduğundan temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="5533a-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]  
  
 <span data-ttu-id="5533a-129">Açık oluşturulan türler devralınan genel sınıflar, aşağıdaki kodda gösterildiği gibi türetilen sınıf tarafından paylaşılmayan herhangi bir temel sınıf türü parametre için tür bağımsız değişkenleri sağlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="5533a-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]  
  
 <span data-ttu-id="5533a-130">Açık oluşturulan türler devralınan genel sınıflar bir alt kümesi olan kısıtlamaları belirtir veya gelmez, temel türü kısıtlamalar:</span><span class="sxs-lookup"><span data-stu-id="5533a-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]  
  
 <span data-ttu-id="5533a-131">Genel türler birden çok tür parametreleri ve kısıtlamaları, aşağıdaki gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5533a-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]  
  
 <span data-ttu-id="5533a-132">Açık oluşturulan ve kapalı oluşturulan türler yöntem parametreleri olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5533a-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]  
  
 <span data-ttu-id="5533a-133">Genel bir sınıf bir arabirim uygularsa, bu sınıfın tüm örnekleri için bu arabirimi çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5533a-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="5533a-134">Genel sınıflar değişmez.</span><span class="sxs-lookup"><span data-stu-id="5533a-134">Generic classes are invariant.</span></span> <span data-ttu-id="5533a-135">Diğer bir deyişle, bir giriş parametresi belirtiyorsa bir `List<BaseClass>`, sağlamak çalışırsa, bir derleme zamanı hatası alırsınız bir `List<DerivedClass>`.</span><span class="sxs-lookup"><span data-stu-id="5533a-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5533a-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5533a-136">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="5533a-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5533a-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5533a-138">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="5533a-138">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="5533a-139">Numaralandırmalar durumunu kaydetme</span><span class="sxs-lookup"><span data-stu-id="5533a-139">Saving the State of Enumerators</span></span>](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)  
 [<span data-ttu-id="5533a-140">Bir devralma Bulmacanın bölüm bir</span><span class="sxs-lookup"><span data-stu-id="5533a-140">An Inheritance Puzzle, Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)

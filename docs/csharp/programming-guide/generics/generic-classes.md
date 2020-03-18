---
title: Genel Sınıflar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 1fdfaa833ad32428d341b6f3a61cc7f638036183
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937512"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="50bb0-102">Genel Sınıflar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="50bb0-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="50bb0-103">Genel sınıflar, belirli bir veri türüne özgü olmayan işlemleri kapsüller.</span><span class="sxs-lookup"><span data-stu-id="50bb0-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="50bb0-104">Genel sınıflar için en yaygın kullanım, bağlantılı listeler, karma tablolar, yığınlar, kuyruklar, ağaçlar ve benzeri koleksiyonlarla yapılır.</span><span class="sxs-lookup"><span data-stu-id="50bb0-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="50bb0-105">Koleksiyondan madde ekleme ve kaldırma gibi işlemler, depolanan veri türüne bakılmaksızın temelde aynı şekilde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="50bb0-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="50bb0-106">Toplama sınıfları gerektiren çoğu senaryoda, önerilen yaklaşım .NET sınıf kitaplığında sağlananları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="50bb0-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="50bb0-107">Bu sınıfları kullanma hakkında daha fazla bilgi için [.NET'teki Genel Koleksiyonlar'a](../../../standard/generics/collections.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="50bb0-107">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="50bb0-108">Genellikle, varolan bir somut sınıfla başlayarak ve genelleme ve kullanılabilirlik en uygun dengeye ulaşana kadar türleri teker teker tür parametrelerine dönüştürerek genel sınıflar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="50bb0-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="50bb0-109">Kendi genel sınıflarınızı oluştururken önemli noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="50bb0-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="50bb0-110">Tür parametrelerine genelleme yapmak için hangi türleri.</span><span class="sxs-lookup"><span data-stu-id="50bb0-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="50bb0-111">Kural olarak, parametrenize ne kadar çok tür varsa, kodunuz o kadar esnek ve yeniden kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="50bb0-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="50bb0-112">Ancak, çok fazla genelleme diğer geliştiriciler için okumak veya anlamak zor kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50bb0-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="50bb0-113">Tür parametrelerine uygulanacak kısıtlamalar nelerdir [(Bkz. Tür Parametreleri Üzerindeki Kısıtlamalar).](./constraints-on-type-parameters.md)</span><span class="sxs-lookup"><span data-stu-id="50bb0-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](./constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="50bb0-114">İyi bir kural, yine de işlemeniz gereken türleri işlemenize izin verecek mümkün olan maksimum kısıtlamaları uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="50bb0-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="50bb0-115">Örneğin, genel sınıfınızın yalnızca başvuru türleri ile kullanılmak üzere tasarlandığını biliyorsanız, sınıf kısıtlamasını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="50bb0-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="50bb0-116">Bu, sınıfınızın değer türleri ile istenmeyen kullanımını önler ve `as` işleci `T`üzerinde kullanmanızı ve null değerlerini denetlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="50bb0-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="50bb0-117">Genel davranışı temel sınıflara ve alt sınıflara dahil edip etmeme.</span><span class="sxs-lookup"><span data-stu-id="50bb0-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="50bb0-118">Genel sınıflar temel sınıflar olarak hizmet verebildiği için, genel olmayan sınıflarda olduğu gibi burada da aynı tasarım konuları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="50bb0-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="50bb0-119">Bu konunun ilerleyen saatlerinde genel temel sınıflardan devralma yla ilgili kurallara bakın.</span><span class="sxs-lookup"><span data-stu-id="50bb0-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="50bb0-120">Bir veya daha fazla genel arabirim uygulayıp uygulamamak.</span><span class="sxs-lookup"><span data-stu-id="50bb0-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="50bb0-121">Örneğin, genel tabanlı bir koleksiyonda öğeler oluşturmak için kullanılacak bir sınıf tasarlıyorsanız, sınıfınızın türü <xref:System.IComparable%601> nerede `T` olduğu gibi bir arabirim uygulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="50bb0-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="50bb0-122">Basit bir genel sınıf örneği için [bkz.](./index.md)</span><span class="sxs-lookup"><span data-stu-id="50bb0-122">For an example of a simple generic class, see [Introduction to Generics](./index.md).</span></span>  
  
 <span data-ttu-id="50bb0-123">Tür parametreleri ve kısıtlamaları için kurallar, özellikle devralma ve üye erişilebilirliği ile ilgili genel sınıf davranışı için çeşitli etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="50bb0-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="50bb0-124">Devam etmeden önce, bazı terimleri anlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="50bb0-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="50bb0-125">Genel bir `Node<T>,` sınıf istemci kodu için kapalı bir yapıt türü oluşturmak için,`Node<int>`bir tür bağımsız değişkeni belirterek sınıf başvuru olabilir ( . .</span><span class="sxs-lookup"><span data-stu-id="50bb0-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="50bb0-126">Alternatif olarak, örneğin genel bir taban sınıfı belirttiğinizde, açık yapılı bir tür (`Node<T>`oluşturmak için tür parametresini belirtilmemiş bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="50bb0-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="50bb0-127">Genel sınıflar, beton, kapalı inşa edilmiş veya açık yapılı taban sınıflarından devralınabilir:</span><span class="sxs-lookup"><span data-stu-id="50bb0-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="50bb0-128">Genel olmayan, diğer bir deyişle, somut, sınıflar kapalı yapılı taban sınıflarından devralabilir, ancak istemci kodunun anında kullanılabilir şekilde tür bağımsız değişkenini sağlaması için çalışma zamanında hiçbir yol bulunmadığından, açık yapılandırılan sınıflardan veya tür parametrelerinden devralınabilir taban sınıf.</span><span class="sxs-lookup"><span data-stu-id="50bb0-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="50bb0-129">Açık yapılandırılan türlerden devralan genel sınıflar, aşağıdaki kodda gösterildiği gibi, devralan sınıf tarafından paylaşılmayan herhangi bir taban sınıf türü parametreleri için tür bağımsız değişkenleri sağlamalıdır:</span><span class="sxs-lookup"><span data-stu-id="50bb0-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="50bb0-130">Açık yapılandırılan türlerden devralan genel sınıflar, temel türdeki kısıtlamaların bir üst kümesi olan veya ima eden kısıtlamaları belirtmelidir:</span><span class="sxs-lookup"><span data-stu-id="50bb0-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="50bb0-131">Genel türler aşağıdaki gibi birden çok tür parametreleri ve kısıtlamaları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50bb0-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="50bb0-132">Açık yapılı ve kapalı yapılı türler yöntem parametreleri olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="50bb0-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="50bb0-133">Genel bir sınıf bir arabirim uygularsa, bu sınıfın tüm örnekleri bu arabirime döküm olabilir.</span><span class="sxs-lookup"><span data-stu-id="50bb0-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="50bb0-134">Genel sınıflar değişmez.</span><span class="sxs-lookup"><span data-stu-id="50bb0-134">Generic classes are invariant.</span></span> <span data-ttu-id="50bb0-135">Başka bir deyişle, bir giriş parametresi `List<BaseClass>`bir , bir ' sağlamak için çalışırsanız `List<DerivedClass>`bir derleme-zaman hatası alırsınız belirtirse .</span><span class="sxs-lookup"><span data-stu-id="50bb0-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50bb0-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50bb0-136">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="50bb0-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="50bb0-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="50bb0-138">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="50bb0-138">Generics</span></span>](./index.md)
- [<span data-ttu-id="50bb0-139">Tümumeratörlerin Durumunu Kurtarmak</span><span class="sxs-lookup"><span data-stu-id="50bb0-139">Saving the State of Enumerators</span></span>](https://docs.microsoft.com/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [<span data-ttu-id="50bb0-140">Bir Miras Bulmaca, Bölüm Bir</span><span class="sxs-lookup"><span data-stu-id="50bb0-140">An Inheritance Puzzle, Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)

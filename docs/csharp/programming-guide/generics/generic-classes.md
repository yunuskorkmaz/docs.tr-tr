---
title: Genel sınıflar- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 13a1ca2d85be0c61b9d0f09c0c5cb670b49f5625
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703227"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="9cb3a-102">Genel Sınıflar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9cb3a-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="9cb3a-103">Genel sınıflar, belirli bir veri türüne özgü olmayan işlemleri kapsültir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="9cb3a-104">Genel sınıflar için en yaygın kullanım, bağlantılı listeler, karma tablolar, yığınlar, kuyruklar, ağaçlar vb. gibi koleksiyonlardır.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="9cb3a-105">Koleksiyondan öğe ekleme ve kaldırma gibi işlemler, depolanan verilerin türüne bakılmaksızın temelde aynı şekilde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="9cb3a-106">Koleksiyon sınıfları gerektiren çoğu senaryo için önerilen yaklaşım, .NET sınıf kitaplığı 'nda sağlananları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="9cb3a-107">Bu sınıfların kullanımı hakkında daha fazla bilgi için bkz. [.net 'Teki genel Koleksiyonlar](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="9cb3a-107">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="9cb3a-108">Genellikle, mevcut bir somut sınıfla başlayarak genel sınıflar oluşturur ve en iyi Genelleştirme ve kullanılabilirlik bakiyesine ulaşana kadar, türleri tek seferde tür parametrelerine değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="9cb3a-109">Kendi genel sınıflarınızı oluştururken, önemli noktalara şunlar dahildir:</span><span class="sxs-lookup"><span data-stu-id="9cb3a-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="9cb3a-110">Tür parametrelerine genelleştiriedilecek türler.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="9cb3a-111">Kural olarak, ne kadar çok tür parametreleştirebilirsiniz, kodunuzun daha esnek ve yeniden kullanılabilir hale gelmesi de olur.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="9cb3a-112">Ancak, çok fazla Genelleştirme, diğer geliştiricilerin okuması veya anlaşılması zor olan kodlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="9cb3a-113">Varsa tür parametrelerine uygulanacak kısıtlamalar (bkz. [tür parametrelerine yönelik kısıtlamalar](./constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="9cb3a-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](./constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="9cb3a-114">İşlenmesi gereken türleri işleyebilmeniz için mümkün olan en yüksek kısıtlamaları uygulamak iyi bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="9cb3a-115">Örneğin, genel sınıfınızın yalnızca başvuru türleriyle kullanılması amaçlandığını biliyorsanız, sınıf kısıtlamasını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="9cb3a-116">Bu, sınıfınızın değer türleriyle istenmeden kullanımını engeller ve `T``as` işlecini kullanmanıza ve null değerleri denetlemeye olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="9cb3a-117">Genel davranışın temel sınıflar ve alt sınıflara göre çarpanının yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="9cb3a-118">Genel sınıflar temel sınıf olarak işlev sağladığından, genel olmayan sınıflarda olduğu gibi aynı tasarım konuları da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="9cb3a-119">Bu konunun ilerleyen kısımlarında genel temel sınıflardan devralma kurallarını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="9cb3a-120">Bir veya daha fazla genel arabirim uygulanıp etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="9cb3a-121">Örneğin, genel türler tabanlı bir koleksiyonda öğe oluşturmak için kullanılacak bir sınıf tasarlıyorsanız, `T` sınıfınızın türü olduğu <xref:System.IComparable%601> gibi bir arabirim uygulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="9cb3a-122">Basit bir genel sınıf örneği için bkz. Genel türlere [giriş](./index.md).</span><span class="sxs-lookup"><span data-stu-id="9cb3a-122">For an example of a simple generic class, see [Introduction to Generics](./index.md).</span></span>  
  
 <span data-ttu-id="9cb3a-123">Tür parametreleri ve kısıtlamaları için kurallar, özellikle devralma ve üye erişilebilirliği ile ilgili genel sınıf davranışı için çeşitli etkilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="9cb3a-124">Devam etmeden önce bazı terimleri anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="9cb3a-125">Bir genel sınıf için `Node<T>,` istemci kodu bir tür bağımsız değişkeni belirterek, Kapalı oluşturulmuş bir tür (`Node<int>`) oluşturmak için sınıfa başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="9cb3a-126">Alternatif olarak, tür parametresi belirtilmemiş olabilir, örneğin, bir genel temel sınıf belirttiğinizde, açık bir oluşturulan tür (`Node<T>`) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="9cb3a-127">Genel sınıflar somut, Kapalı oluşturulmuş veya açık oluşturulmuş temel sınıflardan kalýtýmla alabilir:</span><span class="sxs-lookup"><span data-stu-id="9cb3a-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="9cb3a-128">Genel olmayan, diğer bir deyişle, somut, sınıflar, açık oluşturulmuş sınıflardan veya tür parametrelerinden devralınabilir, çünkü bu durum, istemci kodu için çalışma zamanında, temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="9cb3a-129">Açık oluşturulmuş türlerden devralan genel sınıflar, aşağıdaki kodda gösterildiği gibi, devralan sınıf tarafından paylaşılmayan herhangi bir temel sınıf türü parametre için tür bağımsız değişkenleri sağlamalıdır:</span><span class="sxs-lookup"><span data-stu-id="9cb3a-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="9cb3a-130">Açık oluşturulmuş türlerden devraldığı genel sınıflar, temel türdeki kısıtlamaların bir üst kümesi veya sayısı olan kısıtlamaları belirtmelidir:</span><span class="sxs-lookup"><span data-stu-id="9cb3a-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="9cb3a-131">Genel türler, birden çok tür parametrelerini ve kısıtlamalarını şu şekilde kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="9cb3a-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="9cb3a-132">Açık oluşturulmuş ve kapalı oluşturulmuş türler, yöntem parametreleri olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9cb3a-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="9cb3a-133">Bir genel sınıf bir arabirim uygularsa, bu sınıfın tüm örnekleri bu arabirime eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="9cb3a-134">Genel sınıflar sabit.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-134">Generic classes are invariant.</span></span> <span data-ttu-id="9cb3a-135">Diğer bir deyişle, bir giriş parametresi bir `List<BaseClass>`belirtiyorsa, bir `List<DerivedClass>`sağlamaya çalışırsanız derleme zamanı hatası alırsınız.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb3a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cb3a-136">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="9cb3a-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9cb3a-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9cb3a-138">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="9cb3a-138">Generics</span></span>](./index.md)
- [<span data-ttu-id="9cb3a-139">Numaralandırıcıların durumunu kaydetme</span><span class="sxs-lookup"><span data-stu-id="9cb3a-139">Saving the State of Enumerators</span></span>](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)
- [<span data-ttu-id="9cb3a-140">Devralma bulmaca, birinci bölüm</span><span class="sxs-lookup"><span data-stu-id="9cb3a-140">An Inheritance Puzzle, Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)

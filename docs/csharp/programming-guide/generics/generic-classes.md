---
title: Genel sınıflar-C# Programlama Kılavuzu
description: Bağlantılı listeler, karma tablolar, yığınlar, kuyruklar ve ağaçlar gibi koleksiyonlarda kullanılan genel sınıflar hakkında bilgi edinin.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 308f4328540e1001018942738d931be3d8be53ed
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301924"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="b9063-103">Genel Sınıflar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b9063-103">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="b9063-104">Genel sınıflar, belirli bir veri türüne özgü olmayan işlemleri kapsültir.</span><span class="sxs-lookup"><span data-stu-id="b9063-104">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="b9063-105">Genel sınıflar için en yaygın kullanım, bağlantılı listeler, karma tablolar, yığınlar, kuyruklar, ağaçlar vb. gibi koleksiyonlardır.</span><span class="sxs-lookup"><span data-stu-id="b9063-105">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="b9063-106">Koleksiyondan öğe ekleme ve kaldırma gibi işlemler, depolanan verilerin türüne bakılmaksızın temelde aynı şekilde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b9063-106">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="b9063-107">Koleksiyon sınıfları gerektiren çoğu senaryo için önerilen yaklaşım, .NET sınıf kitaplığı 'nda sağlananları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b9063-107">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="b9063-108">Bu sınıfların kullanımı hakkında daha fazla bilgi için bkz. [.net 'Teki genel Koleksiyonlar](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="b9063-108">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="b9063-109">Genellikle, mevcut bir somut sınıfla başlayarak genel sınıflar oluşturur ve en iyi Genelleştirme ve kullanılabilirlik bakiyesine ulaşana kadar, türleri tek seferde tür parametrelerine değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="b9063-109">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="b9063-110">Kendi genel sınıflarınızı oluştururken, önemli noktalara şunlar dahildir:</span><span class="sxs-lookup"><span data-stu-id="b9063-110">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="b9063-111">Tür parametrelerine genelleştiriedilecek türler.</span><span class="sxs-lookup"><span data-stu-id="b9063-111">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="b9063-112">Kural olarak, ne kadar çok tür parametreleştirebilirsiniz, kodunuzun daha esnek ve yeniden kullanılabilir hale gelmesi de olur.</span><span class="sxs-lookup"><span data-stu-id="b9063-112">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="b9063-113">Ancak, çok fazla Genelleştirme, diğer geliştiricilerin okuması veya anlaşılması zor olan kodlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b9063-113">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="b9063-114">Varsa tür parametrelerine uygulanacak kısıtlamalar (bkz. [tür parametrelerine yönelik kısıtlamalar](./constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="b9063-114">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](./constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="b9063-115">İşlenmesi gereken türleri işleyebilmeniz için mümkün olan en yüksek kısıtlamaları uygulamak iyi bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="b9063-115">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="b9063-116">Örneğin, genel sınıfınızın yalnızca başvuru türleriyle kullanılması amaçlandığını biliyorsanız, sınıf kısıtlamasını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b9063-116">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="b9063-117">Bu, sınıfınızın değer türleriyle istenmeden kullanımını engeller ve üzerinde işlecini kullanmanıza olanak sağlar `as` `T` ve null değerler olup olmadığını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="b9063-117">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="b9063-118">Genel davranışın temel sınıflar ve alt sınıflara göre çarpanının yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9063-118">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="b9063-119">Genel sınıflar temel sınıf olarak işlev sağladığından, genel olmayan sınıflarda olduğu gibi aynı tasarım konuları da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b9063-119">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="b9063-120">Bu konunun ilerleyen kısımlarında genel temel sınıflardan devralma kurallarını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="b9063-120">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="b9063-121">Bir veya daha fazla genel arabirim uygulanıp etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9063-121">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="b9063-122">Örneğin, genel türler tabanlı bir koleksiyonda öğe oluşturmak için kullanılacak bir sınıf tasarlıyorsanız, sınıfınızın türü olduğu gibi bir arabirim uygulamanız gerekebilir <xref:System.IComparable%601> `T` .</span><span class="sxs-lookup"><span data-stu-id="b9063-122">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="b9063-123">Basit bir genel sınıf örneği için bkz. Genel türlere [giriş](./index.md).</span><span class="sxs-lookup"><span data-stu-id="b9063-123">For an example of a simple generic class, see [Introduction to Generics](./index.md).</span></span>  
  
 <span data-ttu-id="b9063-124">Tür parametreleri ve kısıtlamaları için kurallar, özellikle devralma ve üye erişilebilirliği ile ilgili genel sınıf davranışı için çeşitli etkilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b9063-124">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="b9063-125">Devam etmeden önce bazı terimleri anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b9063-125">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="b9063-126">Bir genel sınıf `Node<T>,` istemci kodu için, bir tür bağımsız değişkeni belirterek, kapalı bir oluşturulmuş tür () oluşturmak üzere sınıfına başvurabilir `Node<int>` .</span><span class="sxs-lookup"><span data-stu-id="b9063-126">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="b9063-127">Alternatif olarak, tür parametresi belirtilmemiş olabilir, örneğin, bir genel temel sınıf belirttiğinizde açık bir oluşturulan tür ( `Node<T>` ) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9063-127">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="b9063-128">Genel sınıflar somut, Kapalı oluşturulmuş veya açık oluşturulmuş temel sınıflardan kalýtýmla alabilir:</span><span class="sxs-lookup"><span data-stu-id="b9063-128">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="b9063-129">Genel olmayan, diğer bir deyişle, somut, sınıflar, açık oluşturulmuş sınıflardan veya tür parametrelerinden devralınabilir, çünkü istemci kodunun temel sınıfı oluşturmak için gereken tür bağımsız değişkenini sağlaması için çalışma zamanında hiçbir yol yoktur.</span><span class="sxs-lookup"><span data-stu-id="b9063-129">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="b9063-130">Açık oluşturulmuş türlerden devralan genel sınıflar, aşağıdaki kodda gösterildiği gibi, devralan sınıf tarafından paylaşılmayan herhangi bir temel sınıf türü parametre için tür bağımsız değişkenleri sağlamalıdır:</span><span class="sxs-lookup"><span data-stu-id="b9063-130">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="b9063-131">Açık oluşturulmuş türlerden devraldığı genel sınıflar, temel türdeki kısıtlamaların bir üst kümesi veya sayısı olan kısıtlamaları belirtmelidir:</span><span class="sxs-lookup"><span data-stu-id="b9063-131">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="b9063-132">Genel türler, birden çok tür parametrelerini ve kısıtlamalarını şu şekilde kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="b9063-132">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="b9063-133">Açık oluşturulmuş ve kapalı oluşturulmuş türler, yöntem parametreleri olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b9063-133">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="b9063-134">Bir genel sınıf bir arabirim uygularsa, bu sınıfın tüm örnekleri bu arabirime eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="b9063-134">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="b9063-135">Genel sınıflar sabit.</span><span class="sxs-lookup"><span data-stu-id="b9063-135">Generic classes are invariant.</span></span> <span data-ttu-id="b9063-136">Diğer bir deyişle, bir giriş parametresi bir belirtiyorsa `List<BaseClass>` , sağlamaya çalışırsanız derleme zamanı hatası alırsınız `List<DerivedClass>` .</span><span class="sxs-lookup"><span data-stu-id="b9063-136">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9063-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9063-137">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="b9063-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b9063-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b9063-139">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="b9063-139">Generics</span></span>](./index.md)
- [<span data-ttu-id="b9063-140">Numaralandırıcıların durumunu kaydetme</span><span class="sxs-lookup"><span data-stu-id="b9063-140">Saving the State of Enumerators</span></span>](https://docs.microsoft.com/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [<span data-ttu-id="b9063-141">Devralma bulmaca, birinci bölüm</span><span class="sxs-lookup"><span data-stu-id="b9063-141">An Inheritance Puzzle, Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)

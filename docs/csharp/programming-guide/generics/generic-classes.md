---
title: Genel sınıflar - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 2115b0be2ee2e989b10d2d1834a51efb0b7e2ebb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651792"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="31b1c-102">Genel Sınıflar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="31b1c-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="31b1c-103">Genel sınıflar, belirli veri türüne özgü olmayan işlemler kapsüller.</span><span class="sxs-lookup"><span data-stu-id="31b1c-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="31b1c-104">En yaygın Genel sınıflar için bağlantılı liste, karma tabloları, yığınlar, kuyruklar, ağaçlar ve benzeri gibi koleksiyonlar ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31b1c-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="31b1c-105">Ekleme ve koleksiyondan öğeleri kaldırma gibi işlemler temel olarak aynı şekilde depolanmakta olan veri türünden bağımsız olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="31b1c-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="31b1c-106">Koleksiyon sınıfları gerektiren çoğu senaryo için önerilen yaklaşım .NET sınıf kitaplığı'nda sağlanan olanları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="31b1c-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="31b1c-107">Bu sınıflar kullanma hakkında daha fazla bilgi için bkz. [. NET'te genel koleksiyonlar](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="31b1c-107">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="31b1c-108">Genellikle, varolan bir somut sınıf ile başlayan ve türlerini bir tür parametreleri ile Genelleştirme ve kullanılabilirlik en iyi dengeyi ulaşana kadar aynı anda değiştirme genel sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="31b1c-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="31b1c-109">Genel sınıflarınızı oluştururken önemli noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="31b1c-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
-   <span data-ttu-id="31b1c-110">İçine genelleştirmek için hangi türlerin tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="31b1c-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="31b1c-111">Bir kural, parametreleştirebilirsiniz türlerinin, daha esnek ve yeniden kullanılabilir kodunuzu haline gelir.</span><span class="sxs-lookup"><span data-stu-id="31b1c-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="31b1c-112">Ancak, çok fazla Genelleştirme diğer geliştiriciler için okuma veya anlamak zordur kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31b1c-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
-   <span data-ttu-id="31b1c-113">Hangi kısıtlamalar varsa için tür parametreleri uygulamak için (bkz [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="31b1c-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="31b1c-114">Hala işlemesi gerekir türleri işlemenize olanak sağlayacak en yüksek kısıtlamalara olası uygulamak iyi bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="31b1c-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="31b1c-115">Örneğin, genel, sınıf yalnızca başvuru türleri ile kullanıma yöneliktir biliyorsanız, sınıf kısıtlaması uygulayın.</span><span class="sxs-lookup"><span data-stu-id="31b1c-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="31b1c-116">Değer türleri ile sınıfınıza istenmeyen kullanımını engeller ve kullanmanıza olanak tanıyacak `as` işlecinin `T`ve null değerleri için onay.</span><span class="sxs-lookup"><span data-stu-id="31b1c-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
-   <span data-ttu-id="31b1c-117">Temel sınıflar ve alt sınıfların faktörü genel davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="31b1c-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="31b1c-118">Genel sınıflar temel sınıf olarak hizmet verebilen çünkü aynı tasarım konuları burada geçerli gibi genel olmayan sınıflar.</span><span class="sxs-lookup"><span data-stu-id="31b1c-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="31b1c-119">Bu konunun ilerleyen bölümlerinde genel temel sınıflardan devralan hakkında kurallar bakın.</span><span class="sxs-lookup"><span data-stu-id="31b1c-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
-   <span data-ttu-id="31b1c-120">Bir veya daha fazla genel arabirimi uygulayan verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="31b1c-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="31b1c-121">Örneğin, bir genel türler tabanlı koleksiyon öğeleri oluşturmak için kullanılan bir sınıfı tasarlıyorsanız, arabirimi gibi uygulama gerekebilir <xref:System.IComparable%601> burada `T` sınıfınıza türüdür.</span><span class="sxs-lookup"><span data-stu-id="31b1c-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="31b1c-122">Basit bir genel sınıfın bir örneği için bkz [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="31b1c-122">For an example of a simple generic class, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span>  
  
 <span data-ttu-id="31b1c-123">Tür parametreleri ve kısıtlamalar için kuralları, özellikle devralma ve üye erişilebilirliği ile ilgili genel bir sınıf davranışı için birkaç etkiler.</span><span class="sxs-lookup"><span data-stu-id="31b1c-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="31b1c-124">Devam etmeden önce bazı terimler anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31b1c-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="31b1c-125">Genel bir sınıf için `Node<T>,` istemci kodu sınıf ya da kapalı bir oluşturulmuş tür oluşturmak için bir tür bağımsız değişkeni belirterek başvurabilir (`Node<int>`).</span><span class="sxs-lookup"><span data-stu-id="31b1c-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="31b1c-126">Alternatif olarak, tür parametresi, genel bir temel sınıf belirttiğinizde örneğin belirtilmemiş bırakabilirsiniz, açık bir oluşturma türü oluşturulan (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="31b1c-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="31b1c-127">Genel sınıflar somut, kapalı oluşturulmuş veya açık oluşturulmuş taban sınıflardan devralınabilir:</span><span class="sxs-lookup"><span data-stu-id="31b1c-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]  
  
 <span data-ttu-id="31b1c-128">Genel olmayan başka bir deyişle, somut, sınıflar devral kapalı oluşturulmuş taban sınıflarına, ancak değil açık oluşturulan sınıflar veya tür parametreleri istemci kodu oluşturmak için gerekli tür bağımsız değişkeni sağlamak için çalışma zamanında hiçbir yolu olmadığından temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="31b1c-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]  
  
 <span data-ttu-id="31b1c-129">Açık oluşturulan türlerinden devraldığına Genel sınıflar türetilen sınıf tarafından paylaşılmayan herhangi bir temel sınıf türü parametre türü bağımsız değişkenler aşağıdaki kodda gösterildiği gibi sağlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="31b1c-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]  
  
 <span data-ttu-id="31b1c-130">Açık oluşturulan türlerinden devraldığına Genel sınıflar bir alt kümesi olan kısıtlamaları belirtir veya yaptığından, temel tür kısıtlamalar:</span><span class="sxs-lookup"><span data-stu-id="31b1c-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]  
  
 <span data-ttu-id="31b1c-131">Genel türler birden çok tür parametreleri ve kısıtlamalar, şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="31b1c-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]  
  
 <span data-ttu-id="31b1c-132">Açık oluşturulan ve kapalı oluşturulan türler, yöntem parametreleri olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="31b1c-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]  
  
 <span data-ttu-id="31b1c-133">Genel bir sınıf, arabirim uygularsa, bu sınıfın tüm örnekleri o arabirimine çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31b1c-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="31b1c-134">Genel sınıflar değişmez.</span><span class="sxs-lookup"><span data-stu-id="31b1c-134">Generic classes are invariant.</span></span> <span data-ttu-id="31b1c-135">Diğer bir deyişle, bir giriş parametresi belirtiyorsa bir `List<BaseClass>`, sağlamak çalışırsanız bir derleme zamanı hatası alırsınız bir `List<DerivedClass>`.</span><span class="sxs-lookup"><span data-stu-id="31b1c-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b1c-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31b1c-136">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="31b1c-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="31b1c-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="31b1c-138">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="31b1c-138">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="31b1c-139">Numaralandırıcılar durumunu kaydetme</span><span class="sxs-lookup"><span data-stu-id="31b1c-139">Saving the State of Enumerators</span></span>](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)
- [<span data-ttu-id="31b1c-140">Bir devralma Bulmacanın birinci bölüm</span><span class="sxs-lookup"><span data-stu-id="31b1c-140">An Inheritance Puzzle, Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)

---
title: Genel Arayüzler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 4cce23da7579e30ecff80b3afb92a5a58795c1bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712214"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="3b210-102">Genel Arabirimler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3b210-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="3b210-103">Genel koleksiyon sınıfları veya koleksiyondaki öğeleri temsil eden genel sınıflar için arabirimleri tanımlamak genellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b210-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="3b210-104">Genel sınıflar için tercih, değer türlerinde <xref:System.IComparable%601> kutulama <xref:System.IComparable>ve kutulamayı önleme işlemlerini önlemek için, "kutulama ve kutulamayı önleme" yerine genel arabirimler kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3b210-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="3b210-105">.NET Framework sınıf <xref:System.Collections.Generic> kitaplığı, ad alanındaki koleksiyon sınıflarıyla kullanılmak üzere birkaç genel arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b210-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="3b210-106">Bir arabirim, bir tür parametresi üzerinde bir kısıtlama olarak belirtildiğinde, yalnızca arabirimi uygulayan türler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b210-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="3b210-107">Aşağıdaki kod `SortedList<T>` `GenericList<T>` örneği, sınıftan türeyen bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b210-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="3b210-108">Daha fazla bilgi için [jeneriklere giriş](./index.md)ebakına bakın.</span><span class="sxs-lookup"><span data-stu-id="3b210-108">For more information, see [Introduction to Generics](./index.md).</span></span> <span data-ttu-id="3b210-109">`SortedList<T>`kısıtlama `where T : IComparable<T>`ekler.</span><span class="sxs-lookup"><span data-stu-id="3b210-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="3b210-110">Bu, liste `BubbleSort` öğelerinde genel `SortedList<T>` <xref:System.IComparable%601.CompareTo%2A> yöntemi kullanmak için yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b210-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="3b210-111">Bu örnekte, liste öğeleri basit `Person`bir sınıf, bu `IComparable<Person>`uygular.</span><span class="sxs-lookup"><span data-stu-id="3b210-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="3b210-112">Birden çok arabirim, aşağıdaki gibi, tek bir tür üzerinde kısıtlamalar olarak belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="3b210-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="3b210-113">Arabirim, aşağıdaki gibi birden fazla tür parametresi tanımlayabilir:</span><span class="sxs-lookup"><span data-stu-id="3b210-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="3b210-114">Sınıflar için geçerli olan devralma kuralları arabirimler için de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="3b210-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="3b210-115">Genel arabirim, genel arabirim karşıtsa genel olmayan arabirimlerden devralınabilir, bu da yalnızca tür parametresini iade değeri olarak kullandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3b210-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="3b210-116">.NET <xref:System.Collections.Generic.IEnumerable%601> Framework sınıf kitaplığında, <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> yalnızca `T` <xref:System.Collections.Generic.IEnumerator%601.Current%2A> mülk sahibinin <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ve mülk sahibinin iade değerinde kullandığı için devralır.</span><span class="sxs-lookup"><span data-stu-id="3b210-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="3b210-117">Beton sınıfları aşağıdaki gibi kapalı inşa arayüzleri uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b210-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="3b210-118">Genel sınıflar, sınıf parametre listesi arabirim tarafından gerekli olan tüm bağımsız değişkenleri sağladığı sürece genel arabirimleri veya kapalı oluşturulmuş arabirimleri aşağıdaki gibi uygulayabilir:</span><span class="sxs-lookup"><span data-stu-id="3b210-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="3b210-119">Yöntemaşırı yüklemeyi denetleyen kurallar, genel sınıflar, genel yapı veya genel arabirimlerdeki yöntemler için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3b210-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="3b210-120">Daha fazla bilgi için [Genel Yöntemler'e](./generic-methods.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3b210-120">For more information, see [Generic Methods](./generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b210-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b210-121">See also</span></span>

- [<span data-ttu-id="3b210-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3b210-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3b210-123">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="3b210-123">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="3b210-124">Arabirim</span><span class="sxs-lookup"><span data-stu-id="3b210-124">interface</span></span>](../../language-reference/keywords/interface.md)
- [<span data-ttu-id="3b210-125">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="3b210-125">Generics</span></span>](../../../standard/generics/index.md)

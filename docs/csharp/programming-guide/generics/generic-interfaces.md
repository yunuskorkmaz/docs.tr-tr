---
title: Genel arabirimler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 4cce23da7579e30ecff80b3afb92a5a58795c1bd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712214"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="4a931-102">Genel Arabirimler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4a931-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="4a931-103">Genel koleksiyon sınıfları için ya da koleksiyondaki öğeleri temsil eden genel sınıflar için arabirim tanımlamak genellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4a931-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="4a931-104">Genel sınıfların tercihi, değer türlerinde kutulamayı ve kutudan çıkarma işlemlerini önlemek için <xref:System.IComparable>yerine <xref:System.IComparable%601> gibi genel arabirimleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4a931-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="4a931-105">.NET Framework sınıf kitaplığı, <xref:System.Collections.Generic> ad alanındaki koleksiyon sınıflarıyla kullanılmak üzere çeşitli genel arabirimler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a931-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="4a931-106">Bir arabirim bir tür parametresinde kısıtlama olarak belirtildiğinde, yalnızca arabirimini uygulayan türler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a931-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="4a931-107">Aşağıdaki kod örneği, `GenericList<T>` sınıfından türetilen bir `SortedList<T>` sınıfını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a931-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="4a931-108">Daha fazla bilgi için bkz. [Genel türlere giriş](./index.md).</span><span class="sxs-lookup"><span data-stu-id="4a931-108">For more information, see [Introduction to Generics](./index.md).</span></span> <span data-ttu-id="4a931-109">`SortedList<T>` kısıtlama `where T : IComparable<T>`ekler.</span><span class="sxs-lookup"><span data-stu-id="4a931-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="4a931-110">Bu, `SortedList<T>` `BubbleSort` yönteminin liste öğelerinde genel <xref:System.IComparable%601.CompareTo%2A> yöntemini kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a931-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="4a931-111">Bu örnekte, liste öğeleri, `IComparable<Person>`uygulayan `Person`basit bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="4a931-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="4a931-112">Birden çok arabirim, tek bir tür üzerinde kısıtlamalar olarak belirtilebilir ve aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="4a931-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="4a931-113">Bir arabirim, aşağıdaki gibi birden fazla tür parametresi tanımlayabilir:</span><span class="sxs-lookup"><span data-stu-id="4a931-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="4a931-114">Sınıflar için uygulanan devralma kuralları arabirimler için de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="4a931-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="4a931-115">Genel arabirim değişken karşıtı ise genel arabirimler, genel olmayan arabirimlerden devralınabilir, bu da yalnızca kendi tür parametresini dönüş değeri olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a931-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="4a931-116">.NET Framework sınıf kitaplığında, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> devralır çünkü <xref:System.Collections.Generic.IEnumerable%601> yalnızca `T` dönüş değerindeki ve <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> özellik alıcısı içindeki <xref:System.Collections.Generic.IEnumerator%601.Current%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a931-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="4a931-117">Somut sınıflar, aşağıdaki gibi kapalı oluşturulmuş arabirimler uygulayabilir:</span><span class="sxs-lookup"><span data-stu-id="4a931-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="4a931-118">Genel sınıflar, sınıf parametresi listesi arabirimin gerektirdiği tüm bağımsız değişkenleri aşağıdaki şekilde sağladığı sürece genel arabirimleri veya kapalı oluşturulmuş arabirimleri uygulayabilir:</span><span class="sxs-lookup"><span data-stu-id="4a931-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="4a931-119">Yöntem aşırı yüklemesini denetleyen kurallar, genel sınıflar, genel yapılar veya genel arabirimler içindeki yöntemler için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4a931-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="4a931-120">Daha fazla bilgi için bkz. [Genel yöntemler](./generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4a931-120">For more information, see [Generic Methods](./generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a931-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a931-121">See also</span></span>

- [<span data-ttu-id="4a931-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4a931-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4a931-123">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="4a931-123">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="4a931-124">interface</span><span class="sxs-lookup"><span data-stu-id="4a931-124">interface</span></span>](../../language-reference/keywords/interface.md)
- [<span data-ttu-id="4a931-125">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="4a931-125">Generics</span></span>](../../../standard/generics/index.md)

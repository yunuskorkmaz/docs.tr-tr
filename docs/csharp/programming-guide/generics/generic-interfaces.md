---
title: Genel Arabirimler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 72f48aa1d70e6cf81b20adc547e2d418c4497256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323644"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="0d076-102">Genel Arabirimler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0d076-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="0d076-103">Genellikle, arabirimleri genel koleksiyon sınıfları, veya koleksiyondaki öğelerin temsil eden genel sınıfları tanımlamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0d076-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="0d076-104">Genel sınıflar için tercih genel arabirimler gibi kullanmaktır <xref:System.IComparable%601> yerine <xref:System.IComparable>, değer türleri kutulama ve kutudan çıkarma işlemlerini önlemek için.</span><span class="sxs-lookup"><span data-stu-id="0d076-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="0d076-105">Koleksiyon sınıfları ile kullanılmak üzere birkaç genel arabirimler .NET Framework sınıf kitaplığı tanımlar <xref:System.Collections.Generic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0d076-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="0d076-106">Arabirim tür parametresi bir kısıtlama olarak belirtildiğinde arabirimini uygulayan türleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d076-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="0d076-107">Aşağıdaki örnekte gösterildiği kod bir `SortedList<T>` öğesinden türetilen sınıf `GenericList<T>` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0d076-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="0d076-108">Daha fazla bilgi için bkz: [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="0d076-108">For more information, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span> <span data-ttu-id="0d076-109">`SortedList<T>` kısıtlama ekler `where T : IComparable<T>`.</span><span class="sxs-lookup"><span data-stu-id="0d076-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="0d076-110">Böylece `BubbleSort` yönteminde `SortedList<T>` genel kullanmak için <xref:System.IComparable%601.CompareTo%2A> liste öğelerini yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d076-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="0d076-111">Bu örnekte, liste öğelerini basit bir sınıf olan `Person`, uygulayan `IComparable<Person>`.</span><span class="sxs-lookup"><span data-stu-id="0d076-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 <span data-ttu-id="0d076-112">Birden çok arabirim olarak tek bir türü kısıtlamaları gibi belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="0d076-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 <span data-ttu-id="0d076-113">Arabirim birden fazla tür parametresi, aşağıdaki gibi tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0d076-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 <span data-ttu-id="0d076-114">Sınıfları için geçerli bir kurallar devralma arabirimleri için de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="0d076-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 <span data-ttu-id="0d076-115">Genel arabirimi dönüş değeri olarak yalnızca kendi tür parametresi kullandığı anlamı karşıt-variant ise genel arabirimler genel olmayan arabirimlerinden devralabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d076-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contra-variant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="0d076-116">.NET Framework Sınıf Kitaplığı'nda <xref:System.Collections.Generic.IEnumerable%601> devraldığı <xref:System.Collections.IEnumerable> çünkü <xref:System.Collections.Generic.IEnumerable%601> yalnızca kullanır `T` dönüş değeri olarak <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ve <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özellik Alıcısı.</span><span class="sxs-lookup"><span data-stu-id="0d076-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="0d076-117">Somut sınıflar kapalı oluşturulan arabirimleri, aşağıdaki gibi uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0d076-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 <span data-ttu-id="0d076-118">Genel sınıflar arabirimi tarafından gibi gerekli tüm bağımsız değişkenler sınıfı parametre listesi sağlayan sürece genel arabirimler veya kapalı yapılandırılmış arabirimlerini uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0d076-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 <span data-ttu-id="0d076-119">Genel sınıflar, yapılar genel veya genel arabirimler içinde yöntemlerini yöntemi aşırı yüklemesi denetleyen kurallar aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0d076-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="0d076-120">Daha fazla bilgi için bkz: [genel yöntemler](../../../csharp/programming-guide/generics/generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0d076-120">For more information, see [Generic Methods](../../../csharp/programming-guide/generics/generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d076-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d076-121">See Also</span></span>  
 [<span data-ttu-id="0d076-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0d076-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0d076-123">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="0d076-123">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="0d076-124">interface</span><span class="sxs-lookup"><span data-stu-id="0d076-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="0d076-125">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="0d076-125">Generics</span></span>](~/docs/standard/generics/index.md)

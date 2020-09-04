---
title: Genel arabirimler-C# Programlama Kılavuzu
description: C# dilinde genel arabirimleri kullanma hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: b7225e295268a3e46e4e9bd446372ae87bbbbb10
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466150"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="a0038-104">Genel Arabirimler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a0038-104">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="a0038-105">Genel koleksiyon sınıfları için ya da koleksiyondaki öğeleri temsil eden genel sınıflar için arabirim tanımlamak genellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a0038-105">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="a0038-106">Genel sınıfların tercihi, <xref:System.IComparable%601> <xref:System.IComparable> değer türlerinde kutulamayı ve kutudan çıkarma işlemlerini önlemek için yerine gibi genel arabirimleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="a0038-106">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="a0038-107">.NET sınıf kitaplığı, ad alanındaki koleksiyon sınıflarıyla kullanılmak üzere çeşitli genel arabirimler tanımlar <xref:System.Collections.Generic> .</span><span class="sxs-lookup"><span data-stu-id="a0038-107">The .NET class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="a0038-108">Bir arabirim bir tür parametresinde kısıtlama olarak belirtildiğinde, yalnızca arabirimini uygulayan türler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0038-108">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="a0038-109">Aşağıdaki kod örneğinde `SortedList<T>` sınıfından türetilen bir sınıf gösterilmektedir `GenericList<T>` .</span><span class="sxs-lookup"><span data-stu-id="a0038-109">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="a0038-110">Daha fazla bilgi için bkz. [Genel türlere giriş](./index.md).</span><span class="sxs-lookup"><span data-stu-id="a0038-110">For more information, see [Introduction to Generics](./index.md).</span></span> <span data-ttu-id="a0038-111">`SortedList<T>` kısıtlamayı ekler `where T : IComparable<T>` .</span><span class="sxs-lookup"><span data-stu-id="a0038-111">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="a0038-112">Bu, `BubbleSort` içindeki yönteminin `SortedList<T>` <xref:System.IComparable%601.CompareTo%2A> list öğelerinde genel yöntemini kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0038-112">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="a0038-113">Bu örnekte, liste öğeleri, uygulayan basit bir sınıftır `Person` `IComparable<Person>` .</span><span class="sxs-lookup"><span data-stu-id="a0038-113">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="a0038-114">Birden çok arabirim, tek bir tür üzerinde kısıtlamalar olarak belirtilebilir ve aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="a0038-114">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="a0038-115">Bir arabirim, aşağıdaki gibi birden fazla tür parametresi tanımlayabilir:</span><span class="sxs-lookup"><span data-stu-id="a0038-115">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="a0038-116">Sınıflar için uygulanan devralma kuralları arabirimler için de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="a0038-116">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="a0038-117">Genel arabirim değişken karşıtı ise genel arabirimler, genel olmayan arabirimlerden devralınabilir, bu da yalnızca kendi tür parametresini dönüş değeri olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0038-117">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="a0038-118">.NET sınıf kitaplığında <xref:System.Collections.Generic.IEnumerable%601> öğesinden devralır <xref:System.Collections.IEnumerable> çünkü <xref:System.Collections.Generic.IEnumerable%601> yalnızca `T` öğesinin dönüş değerinde <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ve <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özellik alıcısı içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0038-118">In the .NET class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="a0038-119">Somut sınıflar, aşağıdaki gibi kapalı oluşturulmuş arabirimler uygulayabilir:</span><span class="sxs-lookup"><span data-stu-id="a0038-119">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="a0038-120">Genel sınıflar, sınıf parametresi listesi arabirimin gerektirdiği tüm bağımsız değişkenleri aşağıdaki şekilde sağladığı sürece genel arabirimleri veya kapalı oluşturulmuş arabirimleri uygulayabilir:</span><span class="sxs-lookup"><span data-stu-id="a0038-120">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="a0038-121">Yöntem aşırı yüklemesini denetleyen kurallar, genel sınıflar, genel yapılar veya genel arabirimler içindeki yöntemler için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a0038-121">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="a0038-122">Daha fazla bilgi için bkz. [Genel yöntemler](./generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a0038-122">For more information, see [Generic Methods](./generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0038-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0038-123">See also</span></span>

- [<span data-ttu-id="a0038-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a0038-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a0038-125">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="a0038-125">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="a0038-126">arayüz</span><span class="sxs-lookup"><span data-stu-id="a0038-126">interface</span></span>](../../language-reference/keywords/interface.md)
- [<span data-ttu-id="a0038-127">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="a0038-127">Generics</span></span>](../../../standard/generics/index.md)

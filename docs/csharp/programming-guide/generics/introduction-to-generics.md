---
title: Genel türlere - giriş C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: fd53e0abaab4ff7d242b32d6f26be13e97f20c44
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239033"
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="45bfa-102">Genel Türlere Giriş (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="45bfa-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="45bfa-103">Genel sınıflar ve yöntemler çalışmalarında, tür güvenliği ve verimlilik genel olmayan karşılıkları edilemez bir şekilde birleştirin.</span><span class="sxs-lookup"><span data-stu-id="45bfa-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="45bfa-104">Genel türler, koleksiyonlar ve bunlar üzerinde çalışan yöntemleri ile sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45bfa-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="45bfa-105">.NET Framework sınıf kitaplığı 2.0 sürümünü sağlayan yeni bir ad alanı <xref:System.Collections.Generic>, birkaç yeni genel tabanlı koleksiyon sınıflarını içerir.</span><span class="sxs-lookup"><span data-stu-id="45bfa-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="45bfa-106">Tüm .NET Framework 2.0 ve daha sonra kullanmak yeni genel koleksiyon sınıfları yerine eski genel olmayan ortaklarınıza gibi hedefleyen uygulamalar, önerilen <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="45bfa-106">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="45bfa-107">Daha fazla bilgi için [.NET içindeki genel türler](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="45bfa-107">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="45bfa-108">Elbette, özel, genel türler de oluşturabilirsiniz ve kendi sağlamak için yöntemleri çözümleri ve tür açısından güvenli ve verimli tasarım desenleri genelleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="45bfa-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="45bfa-109">Aşağıdaki kod örneği, Tanıtım amaçlı basit bir genel bağlantılı liste sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="45bfa-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="45bfa-110">(Çoğu durumda, kullanmanız gereken <xref:System.Collections.Generic.List%601> sınıf kendi oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sağlanan.) Tür parametresi `T` çeşitli konumlarda burada somut bir türde normalde kullanılabilir listesinde depolanan öğenin türünü belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45bfa-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="45bfa-111">Bu, aşağıdaki şekillerde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="45bfa-111">It is used in the following ways:</span></span>  
  
-   <span data-ttu-id="45bfa-112">Bir yöntemin parametre türü olarak `AddHead` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45bfa-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
-   <span data-ttu-id="45bfa-113">Dönüş türü olarak `Data` iç içe özellik `Node` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="45bfa-113">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
-   <span data-ttu-id="45bfa-114">Özel üye türü olarak `data` içinde iç içe geçmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="45bfa-114">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="45bfa-115">T için iç içe geçmiş kullanılabilir olduğunu unutmayın `Node` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="45bfa-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="45bfa-116">Zaman `GenericList<T>` somut bir türde örneğin olarak Örneklendirilmiş bir `GenericList<int>`, her geçtiği `T` ile değiştirilecek `int`.</span><span class="sxs-lookup"><span data-stu-id="45bfa-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 <span data-ttu-id="45bfa-117">Aşağıdaki kod örneği, istemci kodu Genel nasıl kullandığını gösterir `GenericList<T>` tamsayı listesi oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="45bfa-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="45bfa-118">Basit tür bağımsız değişkeni değiştirerek aşağıdaki kodu kolayca dizeler veya başka herhangi bir özel tür listesini oluşturmak için değiştirilmesi:</span><span class="sxs-lookup"><span data-stu-id="45bfa-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="45bfa-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45bfa-119">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="45bfa-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="45bfa-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="45bfa-121">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="45bfa-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

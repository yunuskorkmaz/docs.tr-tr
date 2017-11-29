---
title: "Genel Türlere Giriş (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ec4fe9cc9fe7bf868fcc8afe4dc4e4234241e352
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="46362-102">Genel Türlere Giriş (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="46362-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="46362-103">Genel sınıflar ve yöntemler yeniden kullanılırlığı, tür güvenliği ve genel olmayan'dekiler edilemez şekilde verimliliği birleştirir.</span><span class="sxs-lookup"><span data-stu-id="46362-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="46362-104">Genel türler, koleksiyonlar ve bunlar üzerinde çalışan yöntemleri ile en sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46362-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="46362-105">.NET Framework sınıf kitaplığı 2.0 sürümünü sağlayan yeni bir ad alanı <xref:System.Collections.Generic>, birkaç yeni genel dayalı koleksiyon sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="46362-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="46362-106">Tüm uygulamalar hedef önerilir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 ve daha sonra yeni genel koleksiyon sınıfları yerine eski genel olmayan ortaklarınıza gibi kullandığınız <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="46362-106">It is recommended that all applications that target the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="46362-107">Daha fazla bilgi için bkz: [.NET Framework Sınıf Kitaplığı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="46362-107">For more information, see [Generics in the .NET Framework Class Library](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span></span>  
  
 <span data-ttu-id="46362-108">Elbette, ayrıca özel genel türleri oluşturabilir ve kendi sağlamak için yöntemleri çözümleri ve tür kullanımı uyumlu ve verimli tasarım desenleri genelleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="46362-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="46362-109">Aşağıdaki kod örneğinde tanıtım amacıyla basit bir genel bağlantılı liste sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="46362-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="46362-110">(Çoğu durumda, kullanmanız gereken <xref:System.Collections.Generic.List%601> kendi oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sağlanan sınıfı.) Tür parametresi `T` burada somut bir türde normalde kullanılabilir listede depolanan öğenin türünü belirtmek için çeşitli konumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46362-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="46362-111">Aşağıdaki yollarla kullanılır:</span><span class="sxs-lookup"><span data-stu-id="46362-111">It is used in the following ways:</span></span>  
  
-   <span data-ttu-id="46362-112">Bir yöntemin parametre türü olarak `AddHead` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="46362-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
-   <span data-ttu-id="46362-113">Genel yöntem dönüş türü olarak `GetNext` ve `Data` iç içe bir özellik `Node` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46362-113">As the return type of the public method `GetNext` and the `Data` property in the nested `Node` class.</span></span>  
  
-   <span data-ttu-id="46362-114">Özel üye verileri iç içe geçmiş sınıf türü.</span><span class="sxs-lookup"><span data-stu-id="46362-114">As the type of the private member data in the nested class.</span></span>  
  
 <span data-ttu-id="46362-115">T iç içe geçmiş için kullanılabilir olduğunu unutmayın `Node` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46362-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="46362-116">Zaman `GenericList<T>` somut bir türde ile örneğin olarak örneği bir `GenericList<int>`, her oluşumu `T` ile değiştirilecek `int`.</span><span class="sxs-lookup"><span data-stu-id="46362-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 <span data-ttu-id="46362-117">Aşağıdaki kod örneği, istemci kodu Genel nasıl kullandığını gösterir `GenericList<T>` tamsayı listesi oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="46362-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="46362-118">Yalnızca tür bağımsız değişkeni değiştirerek aşağıdaki kodu kolayca dizeyi veya herhangi bir özel tür listesi oluşturmak için değiştirilmesi:</span><span class="sxs-lookup"><span data-stu-id="46362-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="46362-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46362-119">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="46362-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="46362-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="46362-121">Genel türler</span><span class="sxs-lookup"><span data-stu-id="46362-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

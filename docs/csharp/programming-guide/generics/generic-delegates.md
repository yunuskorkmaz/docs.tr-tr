---
title: Genel Temsilciler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: a9f06dcf608a83b53e894310f20810182cf6daa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332913"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="aa5d6-102">Genel Temsilciler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="aa5d6-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="aa5d6-103">A [temsilci](../../../csharp/language-reference/keywords/delegate.md) kendi tür parametreleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa5d6-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="aa5d6-104">Kod başvurularını ne zaman gibi kapalı oluşturulan türü oluşturmak için tür bağımsız değişkeni genel temsilcisi belirtebilirsiniz genel bir sınıf örneği veya aşağıdaki örnekte gösterildiği gibi genel bir yöntemini çağırmadan:</span><span class="sxs-lookup"><span data-stu-id="aa5d6-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 <span data-ttu-id="aa5d6-105">C# sürüm 2.0 somut yanı sıra Genel temsilci türleri için geçerlidir ve bu Basitleştirilmiş söz dizimi önceki satırla yazmanızı sağlar yöntemi Grup Dönüştürme adlı yeni bir özellik vardır:</span><span class="sxs-lookup"><span data-stu-id="aa5d6-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 <span data-ttu-id="aa5d6-106">Genel bir sınıf içinde tanımlanan temsilcileri ve genel bir sınıf türü parametrelerine sınıfı yöntemleri yapan aynı şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa5d6-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 <span data-ttu-id="aa5d6-107">Temsilci başvuran kodu içeren sınıfının tür bağımsız değişkeni aşağıdaki gibi belirtmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="aa5d6-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 <span data-ttu-id="aa5d6-108">Genel temsilciler gönderici bağımsız kesin türü belirtilmiş olmalıdır ve artık ve ondan dönüştürme olduğundan tipik tasarım deseni temel alınarak olayları tanımlama özellikle yararlı <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="aa5d6-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="aa5d6-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa5d6-109">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="aa5d6-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aa5d6-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aa5d6-111">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="aa5d6-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="aa5d6-112">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aa5d6-112">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
 [<span data-ttu-id="aa5d6-113">Genel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="aa5d6-113">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
 [<span data-ttu-id="aa5d6-114">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="aa5d6-114">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [<span data-ttu-id="aa5d6-115">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="aa5d6-115">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="aa5d6-116">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="aa5d6-116">Generics</span></span>](~/docs/standard/generics/index.md)

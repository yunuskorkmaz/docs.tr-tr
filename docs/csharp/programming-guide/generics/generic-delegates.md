---
title: "Genel Temsilciler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1377723f18d6dd0e984538b530acbc7aa8d52feb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="6d174-102">Genel Temsilciler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6d174-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="6d174-103">A [temsilci](../../../csharp/language-reference/keywords/delegate.md) kendi tür parametreleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d174-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="6d174-104">Kod başvurularını ne zaman gibi kapalı oluşturulan türü oluşturmak için tür bağımsız değişkeni genel temsilcisi belirtebilirsiniz genel bir sınıf örneği veya aşağıdaki örnekte gösterildiği gibi genel bir yöntemini çağırmadan:</span><span class="sxs-lookup"><span data-stu-id="6d174-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 <span data-ttu-id="6d174-105">C# sürüm 2.0 somut yanı sıra Genel temsilci türleri için geçerlidir ve bu Basitleştirilmiş söz dizimi önceki satırla yazmanızı sağlar yöntemi Grup Dönüştürme adlı yeni bir özellik vardır:</span><span class="sxs-lookup"><span data-stu-id="6d174-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 <span data-ttu-id="6d174-106">Genel bir sınıf içinde tanımlanan temsilcileri ve genel bir sınıf türü parametrelerine sınıfı yöntemleri yapan aynı şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d174-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 <span data-ttu-id="6d174-107">Temsilci başvuran kodu içeren sınıfının tür bağımsız değişkeni aşağıdaki gibi belirtmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="6d174-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 <span data-ttu-id="6d174-108">Genel temsilciler gönderici bağımsız kesin türü belirtilmiş olmalıdır ve artık ve ondan dönüştürme olduğundan tipik tasarım deseni temel alınarak olayları tanımlama özellikle yararlı <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="6d174-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6d174-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d174-109">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="6d174-110">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6d174-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6d174-111">Genel türlere giriş</span><span class="sxs-lookup"><span data-stu-id="6d174-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="6d174-112">Genel yöntemler</span><span class="sxs-lookup"><span data-stu-id="6d174-112">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
 [<span data-ttu-id="6d174-113">Genel sınıflar</span><span class="sxs-lookup"><span data-stu-id="6d174-113">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
 [<span data-ttu-id="6d174-114">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="6d174-114">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [<span data-ttu-id="6d174-115">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="6d174-115">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="6d174-116">Genel türler</span><span class="sxs-lookup"><span data-stu-id="6d174-116">Generics</span></span>](~/docs/standard/generics/index.md)

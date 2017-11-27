---
title: "Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e02ae26000057e4e7323a777a6a0e1ca6fd8871b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="7cb84-102">Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7cb84-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="7cb84-103">Bu örnek bildiren bir [arabirimi](../../../csharp/language-reference/keywords/interface.md), `IDimensions`ve sınıfı, bir `Box`, arabirim üyelerini açıkça uygulayan `getLength` ve `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="7cb84-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="7cb84-104">Üyeler arabirim örneğinin erişilen `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="7cb84-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cb84-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="7cb84-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7cb84-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="7cb84-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="7cb84-107">Aşağıdaki satırları, içinde bildirim `Main` yöntemi, derleme hataları msgıd çünkü dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="7cb84-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="7cb84-108">Açıkça gerçekleştirilen bir arabirim üyesini gelen erişilemez bir [sınıfı](../../../csharp/language-reference/keywords/class.md) örneği:</span><span class="sxs-lookup"><span data-stu-id="7cb84-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   <span data-ttu-id="7cb84-109">Ayrıca, aşağıdaki satırları dikkat `Main` yöntemi, bir arabirim örneğinden yöntemleri adlı çünkü başarıyla yazdırma kutusunun boyutları:</span><span class="sxs-lookup"><span data-stu-id="7cb84-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7cb84-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7cb84-110">See Also</span></span>  
 [<span data-ttu-id="7cb84-111">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7cb84-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7cb84-112">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="7cb84-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="7cb84-113">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7cb84-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="7cb84-114">Nasıl yapılır: iki arabirimin üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="7cb84-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)

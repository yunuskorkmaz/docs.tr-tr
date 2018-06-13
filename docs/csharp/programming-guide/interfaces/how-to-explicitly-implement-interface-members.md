---
title: 'Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5f7ae6bae46cdf6596b206abbdeeb94b5c21a13f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332192"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="8ab1b-102">Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8ab1b-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="8ab1b-103">Bu örnek bildiren bir [arabirimi](../../../csharp/language-reference/keywords/interface.md), `IDimensions`ve sınıfı, bir `Box`, arabirim üyelerini açıkça uygulayan `getLength` ve `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="8ab1b-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="8ab1b-104">Üyeler arabirim örneğinin erişilen `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="8ab1b-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ab1b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ab1b-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8ab1b-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8ab1b-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="8ab1b-107">Aşağıdaki satırları, içinde bildirim `Main` yöntemi, derleme hataları msgıd çünkü dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="8ab1b-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="8ab1b-108">Açıkça gerçekleştirilen bir arabirim üyesini gelen erişilemez bir [sınıfı](../../../csharp/language-reference/keywords/class.md) örneği:</span><span class="sxs-lookup"><span data-stu-id="8ab1b-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   <span data-ttu-id="8ab1b-109">Ayrıca, aşağıdaki satırları dikkat `Main` yöntemi, bir arabirim örneğinden yöntemleri adlı çünkü başarıyla yazdırma kutusunun boyutları:</span><span class="sxs-lookup"><span data-stu-id="8ab1b-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8ab1b-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ab1b-110">See Also</span></span>  
 [<span data-ttu-id="8ab1b-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8ab1b-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8ab1b-112">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="8ab1b-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="8ab1b-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="8ab1b-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="8ab1b-114">Nasıl yapılır: İki Arabirimin Üyelerini Açıkça Uygulama</span><span class="sxs-lookup"><span data-stu-id="8ab1b-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)

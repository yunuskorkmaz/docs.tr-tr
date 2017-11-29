---
title: "Gerçek Koordinat Dönüştürmesini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5b2a8de0644e71a5e6ae1a5ca796f580f0c4f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-world-transformation"></a><span data-ttu-id="4652f-102">Gerçek Koordinat Dönüştürmesini Kullanma</span><span class="sxs-lookup"><span data-stu-id="4652f-102">Using the World Transformation</span></span>
<span data-ttu-id="4652f-103">Dünya dönüşümü özelliğidir <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4652f-103">The world transformation is a property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="4652f-104">Dünya dönüşümü belirtin sayıları depolanmış bir <xref:System.Drawing.Drawing2D.Matrix> 3 × 3 matris temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="4652f-104">The numbers that specify the world transformation are stored in a <xref:System.Drawing.Drawing2D.Matrix> object, which represents a 3×3 matrix.</span></span> <span data-ttu-id="4652f-105"><xref:System.Drawing.Drawing2D.Matrix> Ve <xref:System.Drawing.Graphics> sınıflarının sayıları world dönüştürme matrisini ayarlamak için çeşitli yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="4652f-105">The <xref:System.Drawing.Drawing2D.Matrix> and <xref:System.Drawing.Graphics> classes have several methods for setting the numbers in the world transformation matrix.</span></span>  
  
## <a name="different-types-of-transformations"></a><span data-ttu-id="4652f-106">Farklı tür dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="4652f-106">Different Types of Transformations</span></span>  
 <span data-ttu-id="4652f-107">Aşağıdaki örnekte, kod ilk 50 × 50 Dikdörtgen oluşturur ve başlangıç (0, 0) bulur.</span><span class="sxs-lookup"><span data-stu-id="4652f-107">In the following example, the code first creates a 50×50 rectangle and locates it at the origin (0, 0).</span></span> <span data-ttu-id="4652f-108">Kaynak istemci alanını sol üst köşesinde ' dir.</span><span class="sxs-lookup"><span data-stu-id="4652f-108">The origin is at the upper-left corner of the client area.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 <span data-ttu-id="4652f-109">Aşağıdaki kod dikdörtgen x yönünde 1.75 faktörüyle genişleyen veya y yönünde 0,5 faktörüyle dikdörtgen bir ölçeklendirme dönüştürmesi uygular:</span><span class="sxs-lookup"><span data-stu-id="4652f-109">The following code applies a scaling transformation that expands the rectangle by a factor of 1.75 in the x direction and shrinks the rectangle by a factor of 0.5 in the y direction:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 <span data-ttu-id="4652f-110">X yönünde uzun ve özgün daha y yönünde kısa bir dikdörtgen sonucudur.</span><span class="sxs-lookup"><span data-stu-id="4652f-110">The result is a rectangle that is longer in the x direction and shorter in the y direction than the original.</span></span>  
  
 <span data-ttu-id="4652f-111">Ölçeklendirme yerine dikdörtgeni döndürmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="4652f-111">To rotate the rectangle instead of scaling it, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 <span data-ttu-id="4652f-112">Dikdörtgen çevirmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="4652f-112">To translate the rectangle, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="4652f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4652f-113">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [<span data-ttu-id="4652f-114">Koordinat sistemleri ve dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="4652f-114">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="4652f-115">Yönetilen GDI +'da dönüştürmeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="4652f-115">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)

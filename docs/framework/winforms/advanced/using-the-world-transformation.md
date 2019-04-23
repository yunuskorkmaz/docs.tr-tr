---
title: Gerçek Koordinat Dönüştürmesini Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
ms.openlocfilehash: f40d7e8cb814344365e8b88c2659751903b79d77
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139964"
---
# <a name="using-the-world-transformation"></a><span data-ttu-id="a0265-102">Gerçek Koordinat Dönüştürmesini Kullanma</span><span class="sxs-lookup"><span data-stu-id="a0265-102">Using the World Transformation</span></span>
<span data-ttu-id="a0265-103">Gerçek koordinat dönüştürmesini parçasıdır <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0265-103">The world transformation is a property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="a0265-104">Gerçek koordinat dönüştürmesini belirtin sayıları depolanan bir <xref:System.Drawing.Drawing2D.Matrix> 3 × 3 matrisi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="a0265-104">The numbers that specify the world transformation are stored in a <xref:System.Drawing.Drawing2D.Matrix> object, which represents a 3×3 matrix.</span></span> <span data-ttu-id="a0265-105"><xref:System.Drawing.Drawing2D.Matrix> Ve <xref:System.Drawing.Graphics> sınıflarının sayıları dünya dönüşümü matriste ayarlamak için çeşitli yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="a0265-105">The <xref:System.Drawing.Drawing2D.Matrix> and <xref:System.Drawing.Graphics> classes have several methods for setting the numbers in the world transformation matrix.</span></span>  
  
## <a name="different-types-of-transformations"></a><span data-ttu-id="a0265-106">Farklı tür dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="a0265-106">Different Types of Transformations</span></span>  
 <span data-ttu-id="a0265-107">Aşağıdaki örnekte, kod ilk 50 x 50 Dikdörtgen oluşturur ve kaynak (0, 0) bulur.</span><span class="sxs-lookup"><span data-stu-id="a0265-107">In the following example, the code first creates a 50×50 rectangle and locates it at the origin (0, 0).</span></span> <span data-ttu-id="a0265-108">Kaynak istemci alanını sol üst köşesinde ' dir.</span><span class="sxs-lookup"><span data-stu-id="a0265-108">The origin is at the upper-left corner of the client area.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 <span data-ttu-id="a0265-109">Aşağıdaki kod, dikdörtgen x yönünde 1.75 faktörüyle genişleyen veya 0,5 y yönünde faktörüyle dikdörtgen bir ölçekleme dönüşümü geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="a0265-109">The following code applies a scaling transformation that expands the rectangle by a factor of 1.75 in the x direction and shrinks the rectangle by a factor of 0.5 in the y direction:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 <span data-ttu-id="a0265-110">X yönünde uzun ve kısa y yönünde özgün bir dikdörtgen sonucudur.</span><span class="sxs-lookup"><span data-stu-id="a0265-110">The result is a rectangle that is longer in the x direction and shorter in the y direction than the original.</span></span>  
  
 <span data-ttu-id="a0265-111">Ölçeklendirme yerine dikdörtgen döndürmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a0265-111">To rotate the rectangle instead of scaling it, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 <span data-ttu-id="a0265-112">Dikdörtgen çevirmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a0265-112">To translate the rectangle, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="a0265-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0265-113">See also</span></span>

- <xref:System.Drawing.Drawing2D.Matrix>
- [<span data-ttu-id="a0265-114">Koordinat Sistemleri ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="a0265-114">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="a0265-115">Yönetilen GDI+'da Dönüştürmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="a0265-115">Using Transformations in Managed GDI+</span></span>](using-transformations-in-managed-gdi.md)

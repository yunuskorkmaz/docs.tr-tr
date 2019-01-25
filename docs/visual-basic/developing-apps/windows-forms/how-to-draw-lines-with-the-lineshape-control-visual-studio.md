---
title: 'Nasıl yapılır: (Visual Studio) LineShape denetimiyle çizgi çizme'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
ms.openlocfilehash: 46360c01dfaf2c6fe199725a9ecfba2248c72d6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596234"
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="3a142-102">Nasıl yapılır: (Visual Studio) LineShape denetimiyle çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="3a142-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="3a142-103">Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.LineShape> yatay, dikey ya da çapraz satır bir form veya kapsayıcı, hem tasarım zamanında hem de çalışma zamanında çizmek için denetimi.</span><span class="sxs-lookup"><span data-stu-id="3a142-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="3a142-104">**Not** bilgisayarınız farklı adlar veya konumlar için bazı Visual Studio kullanıcı arabirimi öğeleri aşağıdaki yönergelerde yer gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3a142-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="3a142-105">Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler.</span><span class="sxs-lookup"><span data-stu-id="3a142-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="3a142-106">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="3a142-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="3a142-107">Tasarım zamanında bir çizgi çizmek için</span><span class="sxs-lookup"><span data-stu-id="3a142-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="3a142-108">Sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.LineShape> denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetimi sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="3a142-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="3a142-109">Boyutlandırma sürükleyin ve boyut ve satırın konumunu için tutamaçlarını taşıyın.</span><span class="sxs-lookup"><span data-stu-id="3a142-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="3a142-110">Ayrıca boyutu ve değiştirerek satırın konumunu `X1`, `X2`, `Y1`, ve `Y2` özelliklerinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="3a142-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="3a142-111">İçinde **özellikleri** penceresinde isteğe bağlı olarak ek özelliklerini ayarlama gibi `BorderStyle` veya `BorderColor` satır görünümünü değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="3a142-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="3a142-112">Çalışma zamanında bir çizgi çizmek için</span><span class="sxs-lookup"><span data-stu-id="3a142-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="3a142-113">Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="3a142-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="3a142-114">İçinde **Başvuru Ekle** iletişim kutusunda **Microsoft.VisualBasic.PowerPacks.VS**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="3a142-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="3a142-115">İçinde **Kod Düzenleyicisi**, ekleme bir `Imports` veya `using` üst modülünün deyimi:</span><span class="sxs-lookup"><span data-stu-id="3a142-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="3a142-116">Aşağıdaki kodu ekleyin bir `Event` yordam:</span><span class="sxs-lookup"><span data-stu-id="3a142-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3a142-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a142-117">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.LineShape>
- [<span data-ttu-id="3a142-118">Çizgi ve Şekil Denetimlerine Giriş</span><span class="sxs-lookup"><span data-stu-id="3a142-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [<span data-ttu-id="3a142-119">Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle şekil çizme</span><span class="sxs-lookup"><span data-stu-id="3a142-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)

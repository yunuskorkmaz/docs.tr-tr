---
title: 'Nasıl Yapılır: LineShape Denetimiyle Çizgi Çizme (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
ms.openlocfilehash: 5e1a837578aab4b4609a58ffee46406b022b8f97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587351"
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="97cdd-102">Nasıl Yapılır: LineShape Denetimiyle Çizgi Çizme (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="97cdd-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="97cdd-103">Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.LineShape> yatay, dikey veya çapraz çizgiler bir form veya kapsayıcı, hem tasarım zamanında hem de çalışma zamanında çizmek için denetim.</span><span class="sxs-lookup"><span data-stu-id="97cdd-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="97cdd-104">**Not** bilgisayarınızın bazı Visual Studio kullanıcı için farklı adlar veya konumlar arabirimi öğelerinden aşağıdaki yönergelerde yer gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="97cdd-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="97cdd-105">Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler.</span><span class="sxs-lookup"><span data-stu-id="97cdd-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="97cdd-106">Daha fazla bilgi için bkz: [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="97cdd-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="97cdd-107">Tasarım zamanında bir çizgi çizmek için</span><span class="sxs-lookup"><span data-stu-id="97cdd-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="97cdd-108">Sürükleme <xref:Microsoft.VisualBasic.PowerPacks.LineShape> gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetimi sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="97cdd-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="97cdd-109">Boyutlandırma sürükleyin ve boyut ve satırın konumunu tanıtıcıları taşıyın.</span><span class="sxs-lookup"><span data-stu-id="97cdd-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="97cdd-110">Ayrıca boyut ve değiştirerek satırın konumunu `X1`, `X2`, `Y1`, ve `Y2` özelliklerinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="97cdd-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="97cdd-111">İçinde **özellikleri** penceresinde, isteğe bağlı olarak ek özelliklerini ayarlama gibi `BorderStyle` veya `BorderColor` çizginin görünümünü değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="97cdd-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="97cdd-112">Çalışma zamanında bir çizgi çizmek için</span><span class="sxs-lookup"><span data-stu-id="97cdd-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="97cdd-113">Üzerinde **proje** menüsünde tıklatın **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="97cdd-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="97cdd-114">İçinde **Başvuru Ekle** iletişim kutusunda **Microsoft.VisualBasic.PowerPacks.VS**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="97cdd-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="97cdd-115">İçinde **Kod düzenleyicisinde**, ekleme bir `Imports` veya `using` deyimini dosyanın üst Modülü:</span><span class="sxs-lookup"><span data-stu-id="97cdd-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="97cdd-116">Aşağıdaki kodu ekleyin bir `Event` yordam:</span><span class="sxs-lookup"><span data-stu-id="97cdd-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="97cdd-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97cdd-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [<span data-ttu-id="97cdd-118">Çizgi ve Şekil Denetimlerine Giriş</span><span class="sxs-lookup"><span data-stu-id="97cdd-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="97cdd-119">Nasıl Yapılır: OvalShape ve RectangleShape Denetimleriyle Şekil Çizme</span><span class="sxs-lookup"><span data-stu-id="97cdd-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)

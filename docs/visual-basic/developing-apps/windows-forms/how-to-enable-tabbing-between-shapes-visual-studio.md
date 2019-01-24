---
title: 'Nasıl yapılır: (Visual Studio) şekiller arasında sekmeyle gitmeyi etkinleştirme'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
ms.openlocfilehash: c47d94317008af57907b747e53bd13ae7ca229f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498287"
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="e4797-102">Nasıl yapılır: (Visual Studio) şekiller arasında sekmeyle gitmeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e4797-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="e4797-103">Çizgi ve Şekil denetimleri yok `TabStop` veya `TabIndex` özellikleri, ancak yine de etkinleştirebilirsiniz bunlar arasında sekmeyle gitmeyi.</span><span class="sxs-lookup"><span data-stu-id="e4797-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="e4797-104">Aşağıdaki örnekte hem sekme tuşlarını, hem de CTRL tuşuna basarak şekiller arasında gezinileceğini; Sekme tuşuna basarak düğmeleri arasında sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="e4797-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4797-105">Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="e4797-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="e4797-106">Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler.</span><span class="sxs-lookup"><span data-stu-id="e4797-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="e4797-107">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="e4797-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="e4797-108">Şekiller arasında sekmeyle gitmeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e4797-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="e4797-109">Üç sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kontrol eder ve iki <xref:System.Windows.Forms.Button> denetimler **araç kutusu** bir forma.</span><span class="sxs-lookup"><span data-stu-id="e4797-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="e4797-110">İçinde **Kod Düzenleyicisi**, ekleme bir `Imports` veya `using` üst modülünün deyimi:</span><span class="sxs-lookup"><span data-stu-id="e4797-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="e4797-111">Bir olay yordamda aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e4797-111">Add the following code in an event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  <span data-ttu-id="e4797-112">Aşağıdaki kodu ekleyin `Button1_PreviewKeyDown` olay yordam:</span><span class="sxs-lookup"><span data-stu-id="e4797-112">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e4797-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4797-113">See also</span></span>
- [<span data-ttu-id="e4797-114">Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle şekil çizme</span><span class="sxs-lookup"><span data-stu-id="e4797-114">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
- [<span data-ttu-id="e4797-115">Nasıl yapılır: LineShape denetimiyle çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="e4797-115">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
- [<span data-ttu-id="e4797-116">Çizgi ve Şekil Denetimlerine Giriş</span><span class="sxs-lookup"><span data-stu-id="e4797-116">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)

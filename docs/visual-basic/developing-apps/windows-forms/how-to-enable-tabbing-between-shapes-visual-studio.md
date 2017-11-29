---
title: "Nasıl Yapılır: Şekiller Arasında Sekmeyle Gitmeyi Etkinleştirme (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a39957ffaa67d6abeb6d394ae9826d42ad2230de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="9378e-102">Nasıl Yapılır: Şekiller Arasında Sekmeyle Gitmeyi Etkinleştirme (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="9378e-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="9378e-103">Çizgi ve Şekil denetimleri yok `TabStop` veya `TabIndex` özellikleri, ancak hala etkinleştirebilir bunlar arasında sekmeyle gitmeyi.</span><span class="sxs-lookup"><span data-stu-id="9378e-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="9378e-104">Aşağıdaki örnekte, CTRL ve sekme tuşlarını tuşuna basarak şekiller arasında sekmeyle; yalnızca SEKME tuşuna basarak düğmeleri arasında sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="9378e-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9378e-105">Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9378e-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="9378e-106">Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler.</span><span class="sxs-lookup"><span data-stu-id="9378e-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="9378e-107">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="9378e-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="9378e-108">Şekiller arasında sekmeyle gitmeyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="9378e-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="9378e-109">Üç sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimleri ve iki <xref:System.Windows.Forms.Button> gelen denetimleri **araç** bir forma.</span><span class="sxs-lookup"><span data-stu-id="9378e-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="9378e-110">İçinde **Kod düzenleyicisinde**, ekleme bir `Imports` veya `using` deyimini dosyanın üst Modülü:</span><span class="sxs-lookup"><span data-stu-id="9378e-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="9378e-111">Bir olay yordamında aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9378e-111">Add the following code in an event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  <span data-ttu-id="9378e-112">Aşağıdaki kodu ekleyin `Button1_PreviewKeyDown` olay yordamı:</span><span class="sxs-lookup"><span data-stu-id="9378e-112">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9378e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9378e-113">See Also</span></span>  
 [<span data-ttu-id="9378e-114">Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle şekil çizme</span><span class="sxs-lookup"><span data-stu-id="9378e-114">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [<span data-ttu-id="9378e-115">Nasıl yapılır: LineShape denetimiyle</span><span class="sxs-lookup"><span data-stu-id="9378e-115">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [<span data-ttu-id="9378e-116">Çizgi ve Şekil denetimlerine giriş</span><span class="sxs-lookup"><span data-stu-id="9378e-116">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)

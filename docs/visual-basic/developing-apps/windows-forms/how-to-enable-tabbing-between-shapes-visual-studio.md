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
ms.openlocfilehash: 0b1e8b0378e65becd80324491632ecd8dbffdbbf
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="5ffce-102">Nasıl Yapılır: Şekiller Arasında Sekmeyle Gitmeyi Etkinleştirme (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5ffce-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="5ffce-103">Çizgi ve Şekil denetimleri yok `TabStop` veya `TabIndex` özellikleri, ancak hala etkinleştirebilir bunlar arasında sekmeyle gitmeyi.</span><span class="sxs-lookup"><span data-stu-id="5ffce-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="5ffce-104">Aşağıdaki örnekte, CTRL ve sekme tuşlarını tuşuna basarak şekiller arasında sekmeyle; yalnızca SEKME tuşuna basarak düğmeleri arasında sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="5ffce-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ffce-105">Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5ffce-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="5ffce-106">Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler.</span><span class="sxs-lookup"><span data-stu-id="5ffce-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="5ffce-107">Daha fazla bilgi için bkz: [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="5ffce-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="5ffce-108">Şekiller arasında sekmeyle gitmeyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="5ffce-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="5ffce-109">Üç sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimleri ve iki <xref:System.Windows.Forms.Button> gelen denetimleri **araç** bir forma.</span><span class="sxs-lookup"><span data-stu-id="5ffce-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="5ffce-110">İçinde **Kod düzenleyicisinde**, ekleme bir `Imports` veya `using` deyimini dosyanın üst Modülü:</span><span class="sxs-lookup"><span data-stu-id="5ffce-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="5ffce-111">Bir olay yordamında aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5ffce-111">Add the following code in an event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  <span data-ttu-id="5ffce-112">Aşağıdaki kodu ekleyin `Button1_PreviewKeyDown` olay yordamı:</span><span class="sxs-lookup"><span data-stu-id="5ffce-112">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5ffce-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ffce-113">See Also</span></span>  
 [<span data-ttu-id="5ffce-114">Nasıl Yapılır: OvalShape ve RectangleShape Denetimleriyle Şekil Çizme</span><span class="sxs-lookup"><span data-stu-id="5ffce-114">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [<span data-ttu-id="5ffce-115">Nasıl Yapılır: LineShape Denetimiyle Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="5ffce-115">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [<span data-ttu-id="5ffce-116">Çizgi ve Şekil Denetimlerine Giriş</span><span class="sxs-lookup"><span data-stu-id="5ffce-116">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)

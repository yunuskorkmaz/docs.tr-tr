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
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a>Nasıl yapılır: (Visual Studio) şekiller arasında sekmeyle gitmeyi etkinleştirme
Çizgi ve Şekil denetimleri yok `TabStop` veya `TabIndex` özellikleri, ancak yine de etkinleştirebilirsiniz bunlar arasında sekmeyle gitmeyi. Aşağıdaki örnekte hem sekme tuşlarını, hem de CTRL tuşuna basarak şekiller arasında gezinileceğini; Sekme tuşuna basarak düğmeleri arasında sekmesinde.  
  
> [!NOTE]
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="to-enable-tabbing-among-shapes"></a>Şekiller arasında sekmeyle gitmeyi etkinleştirme  
  
1.  Üç sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kontrol eder ve iki <xref:System.Windows.Forms.Button> denetimler **araç kutusu** bir forma.  
  
2.  İçinde **Kod Düzenleyicisi**, ekleme bir `Imports` veya `using` üst modülünün deyimi:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  Bir olay yordamda aşağıdaki kodu ekleyin:  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  Aşağıdaki kodu ekleyin `Button1_PreviewKeyDown` olay yordam:  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle şekil çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
- [Nasıl yapılır: LineShape denetimiyle çizgi çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
- [Çizgi ve Şekil Denetimlerine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)

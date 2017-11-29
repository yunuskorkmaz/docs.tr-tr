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
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a>Nasıl Yapılır: Şekiller Arasında Sekmeyle Gitmeyi Etkinleştirme (Visual Studio)
Çizgi ve Şekil denetimleri yok `TabStop` veya `TabIndex` özellikleri, ancak hala etkinleştirebilir bunlar arasında sekmeyle gitmeyi. Aşağıdaki örnekte, CTRL ve sekme tuşlarını tuşuna basarak şekiller arasında sekmeyle; yalnızca SEKME tuşuna basarak düğmeleri arasında sekmesinde.  
  
> [!NOTE]
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="to-enable-tabbing-among-shapes"></a>Şekiller arasında sekmeyle gitmeyi etkinleştirmek için  
  
1.  Üç sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimleri ve iki <xref:System.Windows.Forms.Button> gelen denetimleri **araç** bir forma.  
  
2.  İçinde **Kod düzenleyicisinde**, ekleme bir `Imports` veya `using` deyimini dosyanın üst Modülü:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  Bir olay yordamında aşağıdaki kodu ekleyin:  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  Aşağıdaki kodu ekleyin `Button1_PreviewKeyDown` olay yordamı:  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle şekil çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [Nasıl yapılır: LineShape denetimiyle](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [Çizgi ve Şekil denetimlerine giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)

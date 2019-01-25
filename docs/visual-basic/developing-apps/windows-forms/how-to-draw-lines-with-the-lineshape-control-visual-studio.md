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
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Nasıl yapılır: (Visual Studio) LineShape denetimiyle çizgi çizme
Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.LineShape> yatay, dikey ya da çapraz satır bir form veya kapsayıcı, hem tasarım zamanında hem de çalışma zamanında çizmek için denetimi.  
  
 **Not** bilgisayarınız farklı adlar veya konumlar için bazı Visual Studio kullanıcı arabirimi öğeleri aşağıdaki yönergelerde yer gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-line-at-design-time"></a>Tasarım zamanında bir çizgi çizmek için  
  
1.  Sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.LineShape> denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetimi sürükleyin.  
  
2.  Boyutlandırma sürükleyin ve boyut ve satırın konumunu için tutamaçlarını taşıyın.  
  
     Ayrıca boyutu ve değiştirerek satırın konumunu `X1`, `X2`, `Y1`, ve `Y2` özelliklerinde **özellikleri** penceresi.  
  
3.  İçinde **özellikleri** penceresinde isteğe bağlı olarak ek özelliklerini ayarlama gibi `BorderStyle` veya `BorderColor` satır görünümünü değiştirmek için.  
  
### <a name="to-draw-a-line-at-run-time"></a>Çalışma zamanında bir çizgi çizmek için  
  
1.  Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusunda **Microsoft.VisualBasic.PowerPacks.VS**ve ardından **Tamam**.  
  
3.  İçinde **Kod Düzenleyicisi**, ekleme bir `Imports` veya `using` üst modülünün deyimi:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Aşağıdaki kodu ekleyin bir `Event` yordam:  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.PowerPacks.LineShape>
- [Çizgi ve Şekil Denetimlerine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle şekil çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)

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
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Nasıl Yapılır: LineShape Denetimiyle Çizgi Çizme (Visual Studio)
Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.LineShape> yatay, dikey veya çapraz çizgiler bir form veya kapsayıcı, hem tasarım zamanında hem de çalışma zamanında çizmek için denetim.  
  
 **Not** bilgisayarınızın bazı Visual Studio kullanıcı için farklı adlar veya konumlar arabirimi öğelerinden aşağıdaki yönergelerde yer gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz: [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-line-at-design-time"></a>Tasarım zamanında bir çizgi çizmek için  
  
1.  Sürükleme <xref:Microsoft.VisualBasic.PowerPacks.LineShape> gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetimi sürükleyin.  
  
2.  Boyutlandırma sürükleyin ve boyut ve satırın konumunu tanıtıcıları taşıyın.  
  
     Ayrıca boyut ve değiştirerek satırın konumunu `X1`, `X2`, `Y1`, ve `Y2` özelliklerinde **özellikleri** penceresi.  
  
3.  İçinde **özellikleri** penceresinde, isteğe bağlı olarak ek özelliklerini ayarlama gibi `BorderStyle` veya `BorderColor` çizginin görünümünü değiştirmek için.  
  
### <a name="to-draw-a-line-at-run-time"></a>Çalışma zamanında bir çizgi çizmek için  
  
1.  Üzerinde **proje** menüsünde tıklatın **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusunda **Microsoft.VisualBasic.PowerPacks.VS**ve ardından **Tamam**.  
  
3.  İçinde **Kod düzenleyicisinde**, ekleme bir `Imports` veya `using` deyimini dosyanın üst Modülü:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Aşağıdaki kodu ekleyin bir `Event` yordam:  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [Çizgi ve Şekil Denetimlerine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Nasıl Yapılır: OvalShape ve RectangleShape Denetimleriyle Şekil Çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)

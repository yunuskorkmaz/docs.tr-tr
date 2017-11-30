---
title: "Nasıl Yapılır: LineShape Denetimiyle Çizgi Çizme (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f170250dde2f6db31ed68908936c0e9714a7e846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Nasıl Yapılır: LineShape Denetimiyle Çizgi Çizme (Visual Studio)
Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.LineShape> yatay, dikey veya çapraz çizgiler bir form veya kapsayıcı, hem tasarım zamanında hem de çalışma zamanında çizmek için denetim.  
  
 **Not** bilgisayarınızın bazı Visual Studio kullanıcı için farklı adlar veya konumlar arabirimi öğelerinden aşağıdaki yönergelerde yer gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
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
 [Çizgi ve Şekil denetimlerine giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle şekil çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)

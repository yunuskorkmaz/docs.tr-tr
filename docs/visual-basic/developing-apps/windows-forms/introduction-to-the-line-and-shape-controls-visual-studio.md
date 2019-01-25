---
title: Çizgi ve Şekil Denetimlerine Giriş (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
ms.openlocfilehash: 3623c2363f39150fd4bb202ba61ebd51df383ca8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699928"
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Çizgi ve Şekil Denetimlerine Giriş (Visual Studio)
Visual Basic Power Packs çizgi ve Şekil denetimleri, formlar ve kapsayıcıları çizgiler ve şekiller çizmek sağlayan üç grafik denetimleri kümesidir. <xref:Microsoft.VisualBasic.PowerPacks.LineShape> Denetimi, yatay, dikey ve çapraz çizgi çizmek için kullanılır. <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> Denetimi, daire ve elips, çizmek için kullanılır ve <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimi dikdörtgenler ve kareler çizin için kullanılır.  
  
## <a name="line-and-shape-controls"></a>Çizgi ve Şekil Denetimleri  
 Çizgi ve Şekil denetimleri birçok bulunan grafik yöntemleri kapsülleyen <xref:System.Drawing> ad alanı. Grafik nesneleri, kalemler ve Fırçalar oluşturmak zorunda kalmadan tek bir adımda çizgiler ve şekiller çizmek sağlar. Gradyan Dolgu gibi karmaşık grafik teknikler, bazı özellikleri ayarlayarak gerçekleştirilebilir.  
  
 Ayrıca grafik yöntemlerini kullanarak çizgiler ve şekiller çizmek mümkün olsa da çizgi ve Şekil denetimleri kullanarak çeşitli avantajları vardır:  
  
-   Grafik yöntemleri, yalnızca çalışma zamanında çağrılabilir. Çizgi ve Şekil denetimleri tasarım zamanında bir forma eklenebilir. Bu, nasıl göründüğünü görmek için ve tam olarak konumuna sağlar; Çalışma zamanında da eklenebilir.  
  
-   Çizgi ve Şekil denetimleri seçilebilir çalışma zamanında olaylar gibi sağlayarak <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> ve <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>. Grafik yöntemlerini çıkışlarına seçilemeyen ve olayları sağlamaz.  
  
-   Çizgi ve Şekil denetimleri sağlar <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> ve <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> tasarım zamanında ve çalışma zamanında, z düzenini denetlemenize olanak tanıyan yöntemler. Grafik yöntemlerin z düzenini, yalnızca yürütme zamanında, sıralarını değiştirerek denetlenebilir.  
  
-   Çizgi ve Şekil denetimleri penceresiz denetimlerdir; Bunlar hiçbir penceresi tanıtıcıları içeren ve bu nedenle daha az sistem kaynağı kullanın.  
  
### <a name="object-model"></a>Nesne modeli  
 Türetilen bir temel çizgi ve Şekil denetimleri <xref:Microsoft.VisualBasic.PowerPacks.Shape> kendi paylaşılan özellikleri, yöntemleri ve olayları tanımlayan sınıf.  
  
 Çizgi ve Şekil nesne hiyerarşisi aşağıda gösterilmiştir.  
  
 ![Çizgi ve Şekil nesne hiyerarşisi diyagramını](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Çizgi ve Şekil nesne hiyerarşisi  
  
 Türetilmiş <xref:Microsoft.VisualBasic.PowerPacks.LineShape> sınıfı özellikleri, yöntemleri ve satırları benzersiz olayları içerir. Türetilmiş <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> için temel sınıfı <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ve <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; özellikleri, yöntemleri ve olayları tüm şekiller için ortak içerir. Ayrıca türetebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> kendi `Shape` kontrol eder.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> Ve <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> sınıfları, daire, elips, dikdörtgenler ve yuvarlak köşeli dikdörtgen çizmek için kullanılabilir.  
  
 Çizgi veya şekil bir denetim için bir form veya kapsayıcı, bir görünmez eklendiğinde <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> nesnesi oluşturulur. <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> Şekilleri her kapsayıcı denetimi içinde bir tuval görür; her <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> karşılık gelen <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> çizgi ve Şekil denetimleri yineleme yapmak etkinleştirir. Şekiller bir kapsayıcıdan diğerine sürükleyip bırakarak veya Kes ve Yapıştır kullanarak taşıyabilirsiniz. Son şekil bir kapsayıcıdan kaldırıldığında <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> de kaldırılır.  
  
> [!NOTE]
>  Tüm kapsayıcı denetimleri, çizgi ve Şekil denetimleri destekler. Üzerinde bir çizgi veya şekil denetimi barındıramaz bir <xref:System.Windows.Forms.TableLayoutPanel> veya <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.PowerPacks>
- [Nasıl yapılır: LineShape denetimiyle çizgi çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
- [Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle şekil çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
- [Nasıl yapılır: Şekiller arasında sekmeyle gitmeyi etkinleştirme](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)

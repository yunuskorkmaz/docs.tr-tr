---
title: Çizgi ve Şekil Denetimlerine Giriş (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
ms.openlocfilehash: 3ad740f7dd15194830959a5493970b4ba54ce142
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590744"
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Çizgi ve Şekil Denetimlerine Giriş (Visual Studio)
Visual Basic Power Packs çizgi ve Şekil denetimleri, formlar ve kapsayıcıları çizgiler ve şekiller çizme sağlayan üç grafik denetimleri kümesidir. <xref:Microsoft.VisualBasic.PowerPacks.LineShape> Denetimi yatay, dikey ve çapraz çizgi çizmek için kullanılır. <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> Denetimi daire ve Oval, çizmek için kullanılır ve <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimi dikdörtgenler ve kareler çizmek için kullanılır.  
  
## <a name="line-and-shape-controls"></a>Çizgi ve Şekil Denetimleri  
 Çizgi ve Şekil denetimleri kapsülleyen birçok bulunan grafik yöntem <xref:System.Drawing> ad alanı. Grafik nesneleri, kalemler ve Fırçalar oluşturmak zorunda kalmadan tek bir adımda çizgiler ve şekiller çizmek sağlar. Gradyan dolgular gibi karmaşık grafik teknikler yalnızca bazı özellikleri ayarlayarak gerçekleştirilebilir.  
  
 Grafik yöntemlerini kullanarak çizgiler ve şekiller çizmek mümkündür olmasa da, çizgi ve Şekil denetimleri kullanarak çeşitli avantajları vardır:  
  
-   Grafik yöntemlerini yalnızca çalışma zamanında çağrılabilir. Çizgi ve Şekil denetimleri form Tasarım zamanında eklenebilir. Bu, nasıl göründüğünü görmek için ve tam olarak konumlandırmak için sağlar; Çalışma zamanında da eklenebilir.  
  
-   Çizgi ve Şekil denetimleri seçilebilir çalışma zamanında olaylar gibi sağlayarak <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> ve <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>. Grafik yöntemlerini çıkışları seçilemeyen ve olayları sağlamaz.  
  
-   Çizgi ve Şekil denetimleri sağlar <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> ve <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> z-sıralarına tasarım zamanında ve çalışma zamanında denetlemenize olanak sağlayan yöntemler. Grafik yöntemlerini z-sıralamasını yalnızca çalışma zamanında yürütme, sıralarını değiştirerek denetlenebilir.  
  
-   Çizgi ve Şekil denetimleri penceresiz denetimleridir; Bunlar hiçbir pencere işleyicileri sahip ve bu nedenle daha az sistem kaynağı kullanın.  
  
### <a name="object-model"></a>Nesne modeli  
 Çizgi ve Şekil denetimleri türetilen bir taban <xref:Microsoft.VisualBasic.PowerPacks.Shape> kendi paylaşılan özellikleri, yöntemleri ve olayları tanımlayan sınıf.  
  
 Çizgi ve Şekil nesne hiyerarşisi aşağıda gösterilmektedir.  
  
 ![Çizgi ve Şekil nesne hiyerarşisi diyagramı](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Çizgi ve Şekil nesne hiyerarşisi  
  
 Türetilmiş <xref:Microsoft.VisualBasic.PowerPacks.LineShape> sınıfı özellikleri, yöntemleri ve satırlarına benzersiz olaylarını içerir. Türetilmiş <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> sınıf için temel sınıfı olan <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ve <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; özellikleri, yöntemleri ve olayları tüm şekiller için ortak içerir. Öğesinden türetilen <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> kendi oluşturmak için `Shape` kontrol eder.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> Ve <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> sınıfları, daireler, Oval, dikdörtgenler ve yuvarlak köşeli dikdörtgen çizmek için kullanılabilir.  
  
 Çizgi veya şekil denetimi bir form veya kapsayıcı, bir görünmez eklendiğinde <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> nesnesi oluşturulur. <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> Şekilleri her kapsayıcı denetimi içinde bir tuval görür; her <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> karşılık gelen <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> çizgi ve Şekil denetimleri yinelemek olanak sağlar. Şekiller bir kapsayıcıdan diğerine sürükleyip bırakarak veya kesme ve yapıştırma işlemlerini kullanarak taşıyabilirsiniz. Son şekli bir kapsayıcıdan kaldırıldığında <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> de kaldırılır.  
  
> [!NOTE]
>  Tüm kapsayıcı denetimleri çizgi ve Şekil denetimleri destekler. Üzerinde bir çizgi veya şekil denetimi barındıramaz bir <xref:System.Windows.Forms.TableLayoutPanel> veya <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks>  
 [Nasıl Yapılır: LineShape Denetimiyle Çizgi Çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [Nasıl Yapılır: OvalShape ve RectangleShape Denetimleriyle Şekil Çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [Nasıl Yapılır: Şekiller Arasında Sekmeyle Gitmeyi Etkinleştirme](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)

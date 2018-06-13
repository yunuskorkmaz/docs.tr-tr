---
title: Vektör Grafiklerine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
ms.openlocfilehash: 31fec6d0d3769251d21783b4657d00b06431e942
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528358"
---
# <a name="vector-graphics-overview"></a>Vektör Grafiklerine Genel Bakış
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizgiler, dikdörtgenler ve diğer şekiller bir koordinat sistemi çizer. Koordinat sistemleri çeşitli arasından seçebilirsiniz, ancak varsayılan koordinat sistemi kaynağını sol üst köşedeki sağa ve aşağı işaret eden y ekseni işaret eden x eksenine sahip. Piksel varsayılan koordinat sistemi ölçü birimidir.  
  
## <a name="the-building-blocks-of-gdi"></a>GDI + yapı taşları  
 ![Vektör grafik](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 Bir bilgisayar monitörü resim öğelerinin veya piksel olarak adlandırılan nokta dikdörtgen bir dizi görünümünü oluşturur. Sonraki bir izleyiciden ekrandaki piksel sayısı değişir ve tek tek bir monitörde görünür piksel sayısı genellikle bir ölçüde kullanıcı tarafından yapılandırılabilir.  
  
 ![Vektör grafik](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 Kullandığınızda [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizgi, dikdörtgen veya eğri çizmek için çizilecek öğeyle ilgili anahtar bazı bilgiler sağlar. Örneğin, bir satır, iki nokta sağlayarak belirtebilir ve bir nokta, yükseklik ve genişlik sağlayarak bir dikdörtgen belirtebilirsiniz. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Satır, dikdörtgende veya eğri göstermek için hangi piksel açılmalıdır belirlemek için görüntüleme sürücü yazılımı ile birlikte çalışır. Aşağıdaki çizimde bir satır (4, 2) noktadan noktaya (12, 8) görüntülemek için açık piksel gösterir.  
  
 ![Vektör grafik](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 Zaman içinde iki boyutlu resimler oluşturmak için en kullanışlı olması için bazı temel yapı taşlarının kanıtlanmış. Tarafından desteklenen tüm bu yapı taşları, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], aşağıdaki listede verilir:  
  
-   satırları  
  
-   Dikdörtgenler  
  
-   Üç nokta  
  
-   Yaylar  
  
-   Çokgenler  
  
-   Ana Eğriler  
  
-   Bezier eğrileri  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>Bir grafik nesnesi ile çizim için yöntemleri  
 <xref:System.Drawing.Graphics> Sınıfını [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] önceki listedeki öğeleri çizmek için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (için ana Eğriler), ve <xref:System.Drawing.Graphics.DrawBezier%2A>. Bu yöntemlerin her biri aşırı yüklendi; diğer bir deyişle, her bir yöntemin birkaç farklı parametre listesi destekler. Örneğin, bir çeşitlemesi <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi alır bir <xref:System.Drawing.Pen> nesne ve başka bir çeşitlemesi sırasında dört tamsayılar <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi alır bir <xref:System.Drawing.Pen> nesne ve iki <xref:System.Drawing.Point> nesneleri.  
  
 Tek bir çağrısında birden çok öğe çizin çoğul yardımcı yöntemler çizgiler, dikdörtgenler ve Bézier eğrisi çizme yöntemleri vardır: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, ve <xref:System.Drawing.Graphics.DrawBeziers%2A>. Ayrıca, <xref:System.Drawing.Graphics.DrawCurve%2A> yöntemi sahip bir yardımcı yöntem <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, kapandığında başlatmaya eğrinin bitiş noktasına bağlanarak eğri noktası.  
  
 Tüm çizim yöntemlerinden birini <xref:System.Drawing.Graphics> sınıfı ile birlikte çalışma bir <xref:System.Drawing.Pen> nesnesi. Herhangi bir şey çizmek için en az iki nesne oluşturmanız gerekir: bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Pen> Nesnesi çizgi genişliğini ve çizilecek öğesinin rengini gibi özniteliklerini depolar. <xref:System.Drawing.Pen> Nesnesi, çizim yöntemi için bağımsız değişkenlerden biri geçirilir. Örneğin, bir çeşitlemesi <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi alır bir <xref:System.Drawing.Pen> nesne ve 100, 50 yüksekliğini ve sol üst köşesindeki genişliği ile bir dikdörtgen çizer aşağıdaki örnekte gösterildiği gibi dört tamsayılar (20, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)

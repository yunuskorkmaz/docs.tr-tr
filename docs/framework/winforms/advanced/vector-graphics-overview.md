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
ms.openlocfilehash: d424254839db6c403bafe779f475c0e344918a5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087969"
---
# <a name="vector-graphics-overview"></a>Vektör Grafiklerine Genel Bakış
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizgiler ve dikdörtgenler diğer şekiller üzerinde bir koordinat sistemi çizer. Koordinat sistemleri çeşitli arasından seçim yapabilirsiniz, ancak varsayılan koordinat sistemi kaynağını sağa ve aşağı işaret eden y ekseni işaret eden x ekseni ile sol üst köşedeki sahiptir. Piksel varsayılan koordinat sisteminde ölçü birimidir.  
  
## <a name="the-building-blocks-of-gdi"></a>GDI +'ın yapı taşlarını  
 ![Vektör grafik](./media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 Bir bilgisayar monitörü, resim öğeleri veya piksel olarak adlandırılan noktalardan dikdörtgen bir dizi görünümünü oluşturur. Ekrandaki piksel sayısı bir İzleyici'den sonraki değişir ve tek bir monitörde görünen piksel sayısı genellikle bir dereceye kadar kullanıcı tarafından yapılandırılabilir.  
  
 ![Vektör grafik](./media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 Kullanırken [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] satır, dikdörtgende veya eğri çizme için çizilecek öğeyle ilgili belirli bir anahtar bilgileri sağlayın. Örneğin, bir satır, iki nokta sağlayarak belirtebilir ve bir dikdörtgen bir nokta, yükseklik ve genişlik sağlayarak belirtebilirsiniz. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Satır, dikdörtgende veya eğri göstermek için hangi piksel açılmalıdır belirlemek için görüntüleme sürücü yazılım ile birlikte çalışır. Aşağıdaki çizimde, bir satırı (4, 2) noktasından noktası (12, 8) görüntülemek için açık piksel gösterir.  
  
 ![Vektör grafik](./media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 Zamanla, iki boyutlu bir resim oluşturmaya yönelik en yararlı olacak bazı temel yapı taşlarını kanıtlanmış. Tarafından desteklenen tüm bu yapı taşlarını, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], aşağıdaki listede verilir:  
  
-   satırları  
  
-   Dikdörtgenler  
  
-   Ellipses  
  
-   Yay  
  
-   Çokgenler  
  
-   Ana Eğriler  
  
-   Bezier eğrileri  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>Çizim ile bir grafik nesnesinin yöntemleri  
 <xref:System.Drawing.Graphics> Sınıfını [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] önceki listede öğeleri çizmek için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (için ana Eğriler), ve <xref:System.Drawing.Graphics.DrawBezier%2A>. Bu yöntemlerin her biri aşırı yüklendi; diğer bir deyişle, her bir yöntemin birkaç farklı parametre listelerini destekler. Örneğin, bir çeşitlemesi <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi alır bir <xref:System.Drawing.Pen> nesne ve başka bir çeşitlemesi sırasında dört tamsayının <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi alır bir <xref:System.Drawing.Pen> nesne ve iki <xref:System.Drawing.Point> nesneleri.  
  
 Çeşitli öğeleri tek bir çağrıda çizmek çoğul yardımcı yöntemler çizgiler ve dikdörtgenler Bézier eğrileri çizmek için yöntemleri vardır: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, ve <xref:System.Drawing.Graphics.DrawBeziers%2A>. Ayrıca, <xref:System.Drawing.Graphics.DrawCurve%2A> bir yardımcı yöntem, has yöntemi <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, kapanır başlatmaya eğrinin bitiş noktasına bağlanarak eğri noktası.  
  
 Tüm çizim yöntemlerinden birini <xref:System.Drawing.Graphics> sınıfı ile birlikte çalışma bir <xref:System.Drawing.Pen> nesne. Herhangi bir şey çizmek için en az iki nesneleri oluşturmanız gerekir: bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Pen> Nesnesi gibi çizgi genişliği ve rengine, çizilecek öğesinin özniteliklerini depolar. <xref:System.Drawing.Pen> Nesne, çizim yönteme bağımsız değişkenlerden biri geçirilir. Örneğin, bir çeşitlemesi <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi alır bir <xref:System.Drawing.Pen> nesne ve 100, 50 yüksekliğini ve bir sol üst köşesinde genişliği ile bir dikdörtgen çizer aşağıdaki örnekte gösterildiği gibi dört tamsayının (20, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#11](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](how-to-create-graphics-objects-for-drawing.md)

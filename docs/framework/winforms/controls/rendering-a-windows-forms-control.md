---
title: Bir denetimi işleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
ms.openlocfilehash: 0e1a7ca5dc0414d518c081b1db2dca5477d4f743
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742391"
---
# <a name="rendering-a-windows-forms-control"></a>Windows Forms Denetimini İşleme
İşleme, kullanıcının ekranında görsel bir gösterim oluşturma işlemini ifade eder. Windows Forms, işleme için GDI (yeni Windows grafik kitaplığı) kullanır. GDI 'a erişim sağlayan yönetilen sınıflar, <xref:System.Drawing?displayProperty=nameWithType> ad alanında ve alt ad alanlarında yer alan.  
  
 Aşağıdaki öğeler denetim işlemeye dahil değildir:  
  
- Temel sınıf tarafından sunulan çizim işlevselliği <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
- GDI Grafik kitaplığının temel öğeleri.  
  
- Çizim bölgesinin geometrisi.  
  
- Grafik kaynaklarını boşaltma yordamı.  
  
## <a name="drawing-functionality-provided-by-control"></a>Denetim tarafından sunulan çizim Işlevselliği  
 Temel sınıf <xref:System.Windows.Forms.Control>, <xref:System.Windows.Forms.Control.Paint> olayı aracılığıyla çizim işlevselliği sağlar. Bir denetim, görüntüsünü güncelleştirmek her gerektiğinde <xref:System.Windows.Forms.Control.Paint> olayını başlatır. .NET Framework olaylar hakkında daha fazla bilgi için bkz. [olayları işleme ve](../../../standard/events/index.md)oluşturma.  
  
 <xref:System.Windows.Forms.Control.Paint> olayı için olay veri sınıfı, <xref:System.Windows.Forms.PaintEventArgs>, bir denetim çizmek için gereken verileri (grafik nesnesine yönelik bir tanıtıcı ve içinde çizilecek bölgeyi temsil eden dikdörtgen bir nesne) barındırır. Bu nesneler aşağıdaki kod parçasında kalın olarak gösterilmiştir.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <xref:System.Drawing.Graphics>, bu konunun ilerleyen kısımlarında bulunan GDI 'un tartışmasında açıklandığı şekilde, çizim işlevlerini kapsülleyen yönetilen bir sınıftır. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>, <xref:System.Drawing.Rectangle> yapısının bir örneğidir ve denetimin çizebileceği kullanılabilir alanı tanımlar. Denetim geliştiricisi, bu konunun ilerleyen kısımlarında açıklanan şekilde, bir denetimin <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliğini kullanarak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> işlem yapabilir.  
  
 Bir denetim, <xref:System.Windows.Forms.Control>devraldığı <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi geçersiz kılarak işleme mantığını sağlamalıdır. <xref:System.Windows.Forms.Control.OnPaint%2A>, bir grafik nesnesine ve bir dikdörtgene, <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> ve kendisine geçirilen <xref:System.Windows.Forms.PaintEventArgs> örneğinin <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliklerine erişim sağlar.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 Temel <xref:System.Windows.Forms.Control> sınıfının <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi herhangi bir çizim işlevi uygulamaz, ancak yalnızca <xref:System.Windows.Forms.Control.Paint> olayına kayıtlı olan olay temsilcilerini çağırır. <xref:System.Windows.Forms.Control.OnPaint%2A>geçersiz kıldığınızda, kayıtlı temsilcilerin <xref:System.Windows.Forms.Control.Paint> olayını alabilmesi için genellikle temel sınıfın <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini çağırmanız gerekir. Ancak, bu titreşimi sunan, tüm yüzeylerine ait olan, taban sınıfın <xref:System.Windows.Forms.Control.OnPaint%2A>çağırmamalıdır. <xref:System.Windows.Forms.Control.OnPaint%2A> olayını geçersiz kılma hakkında bir örnek için bkz. [nasıl yapılır: bir Windows Forms denetimi oluşturma Ilerlemeyi gösterir](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
> <xref:System.Windows.Forms.Control.OnPaint%2A> doğrudan denetiinizden çağırmayın; Bunun yerine, <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemini (<xref:System.Windows.Forms.Control>devralınmış) veya <xref:System.Windows.Forms.Control.Invalidate%2A>çağıran başka bir yöntemi çağırın. <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemi <xref:System.Windows.Forms.Control.OnPaint%2A>çağırır. <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemi aşırı yüklenmiştir ve <xref:System.Windows.Forms.Control.Invalidate%2A> `e`sağlanan bağımsız değişkenlere bağlı olarak bir denetim, ekran alanının bazılarını veya tümünü yeniden çizer.  
  
 Temel <xref:System.Windows.Forms.Control> sınıfı, çizim için yararlı olan başka bir yöntemi tanımlar — <xref:System.Windows.Forms.Control.OnPaintBackground%2A> yöntemi.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>, pencerenin arka planını (ve dolayısıyla şeklini) boyar ve hızlı olması garantilenir, ancak tek tek boyama istekleri yeniden çizilmek zorunda olan tek bir <xref:System.Windows.Forms.Control.Paint> olayda birleştirileceğinden, <xref:System.Windows.Forms.Control.OnPaint%2A> ayrıntıları boyar ve daha yavaş olabilir. Örneğin, denetiminiz için gradyan renkli bir arka plan çizmek istiyorsanız <xref:System.Windows.Forms.Control.OnPaintBackground%2A> çağırmak isteyebilirsiniz.  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> olay benzeri bir terminolojisi vardır ve `OnPaint` yöntemiyle aynı bağımsız değişkeni alır <xref:System.Windows.Forms.Control.OnPaintBackground%2A>, doğru bir olay yöntemi değildir. `PaintBackground` olay yok ve <xref:System.Windows.Forms.Control.OnPaintBackground%2A> olay temsilcileri çağırmıyor. <xref:System.Windows.Forms.Control.OnPaintBackground%2A> yöntemi geçersiz kılınırken, kendi temel sınıfının <xref:System.Windows.Forms.Control.OnPaintBackground%2A> yöntemini çağırmak için türetilmiş bir sınıf gerekli değildir.  
  
## <a name="gdi-basics"></a>GDI+ temel kavramları  
 <xref:System.Drawing.Graphics> sınıfı, daireler, üçgenler, yaylar ve üç nokta gibi çeşitli şekilleri çizmek için yöntemler ve metin görüntülemek için yöntemler sağlar. <xref:System.Drawing?displayProperty=nameWithType> ad alanı ve alt ad alanları, şekiller (daireler, dikdörtgenler, yaylar ve diğerleri), renkler, yazı tipleri, Fırçalar vb. gibi grafik öğelerini kapsülleyen sınıflar içerir. GDI hakkında daha fazla bilgi için bkz. [yönetilen grafik sınıflarını kullanma](../advanced/using-managed-graphics-classes.md). GDI 'nın temelleri de bkz. [nasıl yapılır: Ilerleme durumunu gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Çizim bölgesinin geometrisi  
 Bir denetimin <xref:System.Windows.Forms.Control.ClientRectangle%2A> özelliği, kullanıcının ekranındaki denetim için kullanılabilen dikdörtgen bölgeyi belirtir, ancak <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliği gerçekten boyanmış olan alanı belirtir. (Bir <xref:System.Windows.Forms.PaintEventArgs> örneğini bağımsız değişkeni olarak alan <xref:System.Windows.Forms.Control.Paint> olay yönteminde boyama yapıldığını unutmayın. Bir denetimin, denetimin ekran değişikliklerinin küçük bir bölümünde olduğu gibi, kullanılabilir alanının yalnızca bir kısmını boyamak gerekebilir. Bu durumlarda, bir denetim geliştiricisi içinde çizim yapmak için gerçek dikdörtgeni hesaplamalıdır ve <xref:System.Windows.Forms.Control.Invalidate%2A>. Bağımsız değişken olarak <xref:System.Drawing.Rectangle> veya <xref:System.Drawing.Region> alan <xref:System.Windows.Forms.Control.Invalidate%2A> aşırı yüklenmiş sürümleri, <xref:System.Windows.Forms.PaintEventArgs><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliğini oluşturmak için bu bağımsız değişkeni kullanır.  
  
 Aşağıdaki kod parçası, `FlashTrackBar` özel denetiminin çizim için dikdörtgen alanını nasıl hesaplakullandığını gösterir. `client` değişkeni <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliğini gösterir. Tüm bir örnek için bkz. [nasıl yapılır: Ilerlemeyi gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Grafik kaynaklarını boşaltma  
 Grafik nesneleri, sistem kaynaklarını kullandıkları için pahalıdır. Bu tür nesneler, <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>ve diğer grafik sınıflarının örneklerinin yanı sıra <xref:System.Drawing.Graphics?displayProperty=nameWithType> sınıfının örneklerini içerir. Yalnızca ihtiyacınız olduğunda bir grafik kaynağı oluşturmanız ve bunu kullanmayı bitirdikten sonra serbest bırakmanız önemlidir. <xref:System.IDisposable> arabirimini uygulayan bir tür oluşturursanız, kaynakların serbest olması için işiniz bittiğinde <xref:System.IDisposable.Dispose%2A> yöntemini çağırın.  
  
 Aşağıdaki kod parçası, `FlashTrackBar` özel denetimin bir <xref:System.Drawing.Brush> kaynağını nasıl oluşturduğunu ve yayınoluşturduğunu gösterir. Tüm kaynak kodu için bkz. [nasıl yapılır: Ilerlemeyi gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İlerleme Durumunu Gösteren Windows Forms Denetimi Oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md)

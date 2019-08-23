---
title: Windows Forms Denetimini İşleme
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
ms.openlocfilehash: b24fbefac0dcfb666e25ad1d1726ef2cf8a5d84e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968268"
---
# <a name="rendering-a-windows-forms-control"></a>Windows Forms Denetimini İşleme
İşleme, kullanıcının ekranında görsel bir gösterim oluşturma işlemini ifade eder. Windows Forms, işleme için GDI (yeni Windows grafik kitaplığı) kullanır. GDI 'ya erişim sağlayan yönetilen sınıflar <xref:System.Drawing?displayProperty=nameWithType> ad alanında ve alt ad alanlarında bulunur.  
  
 Aşağıdaki öğeler denetim işlemeye dahil değildir:  
  
- Temel sınıf <xref:System.Windows.Forms.Control?displayProperty=nameWithType>tarafından sunulan çizim işlevselliği.  
  
- GDI Grafik kitaplığının temel öğeleri.  
  
- Çizim bölgesinin geometrisi.  
  
- Grafik kaynaklarını boşaltma yordamı.  
  
## <a name="drawing-functionality-provided-by-control"></a>Denetim tarafından sunulan çizim Işlevselliği  
 Temel sınıf <xref:System.Windows.Forms.Control> , <xref:System.Windows.Forms.Control.Paint> olay aracılığıyla çizim işlevselliği sağlar. Bir denetim, <xref:System.Windows.Forms.Control.Paint> görünümü güncelleştirmek her gerektiğinde olayı başlatır. .NET Framework olaylar hakkında daha fazla bilgi için bkz. [olayları işleme ve](../../../standard/events/index.md)oluşturma.  
  
 <xref:System.Windows.Forms.Control.Paint> Olay için olay veri sınıfı, bir denetim çizmek için gereken verileri (grafik nesnesine yönelik bir tanıtıcı ve içinde çizilecek bölgeyi temsil eden dikdörtgen bir nesne) barındırır. <xref:System.Windows.Forms.PaintEventArgs> Bu nesneler aşağıdaki kod parçasında kalın olarak gösterilmiştir.  
  
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
  
 <xref:System.Drawing.Graphics>, bu konunun ilerleyen kısımlarında bulunan GDI 'un tartışmasında açıklandığı şekilde, çizim işlevlerini kapsülleyen yönetilen bir sınıftır. , <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> <xref:System.Drawing.Rectangle> Yapısının bir örneğidir ve bir denetimin çizebileceği kullanılabilir alanı tanımlar. Bir denetim geliştiricisi, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> bu konunun ilerleyen kısımlarında açıklanan şekilde, bir denetimin <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliğini kullanarak işlem yapabilir.  
  
 Bir denetim, <xref:System.Windows.Forms.Control.OnPaint%2A> <xref:System.Windows.Forms.Control>devraldığı yöntemi geçersiz kılarak işleme mantığını sağlamalıdır. <xref:System.Windows.Forms.Control.OnPaint%2A>bir grafik nesnesine ve içine, <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> içine geçirilen <xref:System.Windows.Forms.PaintEventArgs> örneğin <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliklerine ve içine çizim yapmak için bir dikdörtgene erişim sağlar.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.Paint> Temel <xref:System.Windows.Forms.Control.OnPaint%2A> sınıfınyöntemiherhangibirçizimişleviuygulamaz,ancakyalnızcaolayakayıtlıolanolaytemsilcileriniçağırır.<xref:System.Windows.Forms.Control> Geçersiz kıldığınızda <xref:System.Windows.Forms.Control.OnPaint%2A>, kayıtlı temsilcilerin <xref:System.Windows.Forms.Control.Paint> olayı alabilmesi için <xref:System.Windows.Forms.Control.OnPaint%2A> genellikle temel sınıfın yöntemini çağırmanız gerekir. Ancak, bu titreşimi sunan, tüm yüzeylerine ait olan ve temel sınıfın <xref:System.Windows.Forms.Control.OnPaint%2A>çağırmamalıdır. <xref:System.Windows.Forms.Control.OnPaint%2A> Olayı geçersiz kılma örneği için [bkz. nasıl yapılır: Ilerleme durumunu](how-to-create-a-windows-forms-control-that-shows-progress.md)gösteren bir Windows Forms denetimi oluşturun.  
  
> [!NOTE]
> Doğrudan denetiinizden <xref:System.Windows.Forms.Control.OnPaint%2A> çağırmayın; bunun yerine <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemi (öğesinden <xref:System.Windows.Forms.Control>devralınmış) veya çağıran <xref:System.Windows.Forms.Control.Invalidate%2A>başka bir yöntemi çağırın. İçindeki yöntemi sırasıyla çağırır <xref:System.Windows.Forms.Control.OnPaint%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Yöntemi aşırı yüklendi ve ' de <xref:System.Windows.Forms.Control.Invalidate%2A> `e`sağlanan bağımsız değişkenlere bağlı olarak bir denetim, ekran alanının bazılarını veya tümünü yeniden çizer. <xref:System.Windows.Forms.Control.Invalidate%2A>  
  
 Taban <xref:System.Windows.Forms.Control> sınıfı, çizim için yararlı olan başka bir yöntemi tanımlar <xref:System.Windows.Forms.Control.OnPaintBackground%2A> — yöntemi.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>pencerenin arka planını (ve dolayısıyla şeklini) boyar ve hızlı olması garantilenir, ancak <xref:System.Windows.Forms.Control.OnPaint%2A> tek tek boyama istekleri, her türlü alanı kapsamakta olan bir <xref:System.Windows.Forms.Control.Paint> olayda birleştirileceğinden, ayrıntıları boyar ve daha yavaş olabilir. düzenlenen. Örneğin, denetiminiz için gradyan renkli <xref:System.Windows.Forms.Control.OnPaintBackground%2A> bir arka plan çizmek istiyorsanız öğesini çağırmak isteyebilirsiniz.  
  
 , Olay benzeri bir terminolojisi `OnPaint` <xref:System.Windows.Forms.Control.OnPaintBackground%2A>vardırve yöntemiyle aynı bağımsız değişkeni alır, doğru bir olay yöntemi değildir. <xref:System.Windows.Forms.Control.OnPaintBackground%2A> Hiçbir `PaintBackground` olay yoktur ve <xref:System.Windows.Forms.Control.OnPaintBackground%2A> olay temsilcileri çağırmaz. <xref:System.Windows.Forms.Control.OnPaintBackground%2A> Yöntemi geçersiz kıldığınızda, kendi temel sınıfının <xref:System.Windows.Forms.Control.OnPaintBackground%2A> yöntemini çağırmak için türetilmiş bir sınıf gerekli değildir.  
  
## <a name="gdi-basics"></a>GDI+ temel kavramları  
 <xref:System.Drawing.Graphics> Sınıfı, daireler, üçgenler, yaylar ve üç nokta gibi çeşitli şekilleri çizmek için yöntemler ve metin görüntülemek için yöntemler sağlar. <xref:System.Drawing?displayProperty=nameWithType> Ad alanı ve alt ad alanları, şekiller (daireler, dikdörtgenler, yaylar ve diğerleri), renkler, yazı tipleri, Fırçalar vb. gibi grafik öğelerini kapsülleyen sınıflar içerir. GDI hakkında daha fazla bilgi için bkz. [yönetilen grafik sınıflarını kullanma](../advanced/using-managed-graphics-classes.md). GDI 'nın temel bileşenleri ayrıca [nasıl yapılır: Ilerleme durumunu](how-to-create-a-windows-forms-control-that-shows-progress.md)gösteren bir Windows Forms denetimi oluşturun.  
  
## <a name="geometry-of-the-drawing-region"></a>Çizim bölgesinin geometrisi  
 Bir denetimin <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> <xref:System.Windows.Forms.PaintEventArgs> özelliği, kullanıcının ekranındaki denetimin kullanabildiği dikdörtgen bölgeyi belirtir, ancak özelliği gerçekten boyanmış olan alanı belirtir. <xref:System.Windows.Forms.Control.ClientRectangle%2A> (Bir <xref:System.Windows.Forms.Control.Paint> <xref:System.Windows.Forms.PaintEventArgs> örneği bağımsız değişkeni olarak alan olay yönteminde boyama yapıldığını unutmayın). Bir denetimin, denetimin ekran değişikliklerinin küçük bir bölümünde olduğu gibi, kullanılabilir alanının yalnızca bir kısmını boyamak gerekebilir. Bu durumlarda, bir denetim geliştiricisi içinde çizim yapmak ve bunu geçirmek <xref:System.Windows.Forms.Control.Invalidate%2A>için gerçek dikdörtgeni hesaplamalıdır. Bağımsız değişkeni bir <xref:System.Drawing.Rectangle> veya <xref:System.Windows.Forms.Control.Invalidate%2A> <xref:System.Drawing.Region> olarak alan aşırı yüklenmiş sürümleri, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliği oluşturmak için bu bağımsız değişkeni <xref:System.Windows.Forms.PaintEventArgs>kullanır.  
  
 Aşağıdaki kod parçası, `FlashTrackBar` özel denetimin çizim için dikdörtgen alanı nasıl hesaplakullandığını gösterir. `client` Değişkeni özelliği<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> gösterir. Tüm bir örnek için bkz [. nasıl yapılır: Ilerleme durumunu](how-to-create-a-windows-forms-control-that-shows-progress.md)gösteren bir Windows Forms denetimi oluşturun.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Grafik kaynaklarını boşaltma  
 Grafik nesneleri, sistem kaynaklarını kullandıkları için pahalıdır. Bu tür nesneler, <xref:System.Drawing.Graphics?displayProperty=nameWithType> sınıfının örneklerinin yanı sıra <xref:System.Drawing.Brush?displayProperty=nameWithType> <xref:System.Drawing.Pen?displayProperty=nameWithType>, ve diğer grafik sınıflarının örneklerini içerir. Yalnızca ihtiyacınız olduğunda bir grafik kaynağı oluşturmanız ve bunu kullanmayı bitirdikten sonra serbest bırakmanız önemlidir. <xref:System.IDisposable> Arabirimini uygulayan bir tür oluşturursanız, kaynakların serbest olması için işiniz bittiğinde <xref:System.IDisposable.Dispose%2A> yöntemini çağırın.  
  
 Aşağıdaki kod parçası, `FlashTrackBar` özel denetimin bir <xref:System.Drawing.Brush> kaynağı nasıl oluşturduğunu ve yayınoluşturduğunu gösterir. Tüm kaynak kodu için bkz [. nasıl yapılır: Ilerleme durumunu](how-to-create-a-windows-forms-control-that-shows-progress.md)gösteren bir Windows Forms denetimi oluşturun.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Ilerleme durumunu gösteren bir Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md)

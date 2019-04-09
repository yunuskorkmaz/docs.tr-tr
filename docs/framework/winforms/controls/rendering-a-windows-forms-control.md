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
ms.openlocfilehash: 8de87e17d1baedccfe18bfded3ccab7ab59f0a09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125690"
---
# <a name="rendering-a-windows-forms-control"></a>Windows Forms Denetimini İşleme
İşleme görsel bir temsili bir kullanıcının ekranda oluşturma işlemini gösterir. Windows Forms kullanan [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (yeni Windows grafik kitaplığının) işleme için. Erişim sağlayan bir yönetilen sınıflar [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] bulunan <xref:System.Drawing?displayProperty=nameWithType> ad alanı ve bunun alt ad boşlukları.  
  
 Aşağıdaki öğeler denetimi işlemede ilgilidir:  
  
-   Taban sınıfı tarafından sağlanan çizim işlevselliği <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
-   Temel öğelerini [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] grafik kitaplığı.  
  
-   Çizim bölge geometrisi.  
  
-   Grafik kaynakları serbest bırakma yordamı.  
  
## <a name="drawing-functionality-provided-by-control"></a>Denetimi tarafından sağlanan işlevselliği çizme  
 Temel sınıf <xref:System.Windows.Forms.Control> aracılığıyla çizim işlevselliği sağlar, <xref:System.Windows.Forms.Control.Paint> olay. Bir denetim oluşturur <xref:System.Windows.Forms.Control.Paint> görünümünü güncelleştirmek gerektiğinde olay. .NET Framework içindeki olaylar hakkında daha fazla bilgi için bkz. [Handling and Raising Events](../../../standard/events/index.md).  
  
 Olay veri sınıfı için <xref:System.Windows.Forms.Control.Paint> olay <xref:System.Windows.Forms.PaintEventArgs>, bir denetim çizmek için gerekli olan verileri tutar — bir grafik nesnesinin ve çizim bölgeyi temsil eden bir dikdörtgen nesnesi için bir tanıtıcı. Bu nesneler gösterilir aşağıdaki kod parçası kalın.  
  
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
  
 <xref:System.Drawing.Graphics> Çizim işlevi kapsülleyen bir yönetilen sınıf tartışmalarına açıklandığı olan [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] bu konuda. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Örneğidir <xref:System.Drawing.Rectangle> yapı ve denetim çizebilir kullanılabilir alanı tanımlar. Bir denetim geliştiricisi hesaplayabilirsiniz <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> kullanarak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> tartışma geometrisinin bu konunun ilerleyen bölümlerinde açıklandığı gibi bir denetimin özellik.  
  
 Bir denetim işleme mantığı geçersiz kılarak sağlamalısınız <xref:System.Windows.Forms.Control.OnPaint%2A> devraldığı yöntemi <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> bir grafik nesnesinin ve bir dikdörtgen çizin aracılığıyla erişimi alır <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> ve <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliklerini <xref:System.Windows.Forms.PaintEventArgs> kendisine geçirilen örneği.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemi temel <xref:System.Windows.Forms.Control> sınıf herhangi bir çizim işlevselliğini gerçekleştirmemesi ancak yalnızca kayıtlı olay temsilcilerini çağırır <xref:System.Windows.Forms.Control.Paint> olay. Ne zaman geçersiz kılmanız <xref:System.Windows.Forms.Control.OnPaint%2A>, genellikle çağırması gereken <xref:System.Windows.Forms.Control.OnPaint%2A> temsilciler kayıtlı için temel sınıf yönteminde <xref:System.Windows.Forms.Control.Paint> olay. Tüm bunların surface boyama denetimleri temel sınıfın ancak, çağırmalıdır değil <xref:System.Windows.Forms.Control.OnPaint%2A>gibi bu titreşimini tanıtır. Geçersiz kılma örneği için <xref:System.Windows.Forms.Control.OnPaint%2A> olay bkz [nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  Değil çağırma <xref:System.Windows.Forms.Control.OnPaint%2A> , denetiminden; bunun yerine, doğrudan çağırma <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemi (devralınan <xref:System.Windows.Forms.Control>) veya çağıran başka bir yöntem <xref:System.Windows.Forms.Control.Invalidate%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Sırayla yöntemini çağıran <xref:System.Windows.Forms.Control.OnPaint%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Yöntemi aşırı yüklüdür ve bağımsız değişkenler üzerinde bağlı olarak sağlanan için <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, bazı veya tüm ekran alanı, bir denetimi yeniden çizer.  
  
 Temel <xref:System.Windows.Forms.Control> sınıfı çizim için yararlı olan başka bir yöntem tanımlar — <xref:System.Windows.Forms.Control.OnPaintBackground%2A> yöntemi.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> arka plan boyar (ve dolayısıyla şekli) penceresinin ve sırasında daha hızlı olmasını garanti <xref:System.Windows.Forms.Control.OnPaint%2A> ayrıntılarını boyar ve tek tek Boya istekleri birine birleştirilir daha yavaş olabilir çünkü <xref:System.Windows.Forms.Control.Paint> olması için tüm alanları kapsar olay yeniden çizilir. Çağrılacak isteyebileceğiniz <xref:System.Windows.Forms.Control.OnPaintBackground%2A> örneği için bir gradyan renkli arka plan denetiminizin çizmek istiyorsanız.  
  
 Sırada <xref:System.Windows.Forms.Control.OnPaintBackground%2A> aynı bağımsız değişken olarak alır ve bir olay benzeri terminolojisi sahip `OnPaint` yöntemi <xref:System.Windows.Forms.Control.OnPaintBackground%2A> true olay yöntemi değildir. Var olan hiçbir `PaintBackground` olay ve <xref:System.Windows.Forms.Control.OnPaintBackground%2A> olay temsilci çağrılmaz. Geçersiz kılarken <xref:System.Windows.Forms.Control.OnPaintBackground%2A> yöntem, türetilmiş bir sınıf değil çağırmak için gerekli <xref:System.Windows.Forms.Control.OnPaintBackground%2A> yöntemi kendi taban sınıfının.  
  
## <a name="gdi-basics"></a>GDI +'da temel bilgileri  
 <xref:System.Drawing.Graphics> Sınıfı yöntemleri metin görüntüleme için yanı sıra, daire, üçgen, yaylar ve elipsler gibi çeşitli şekiller çizmek için yöntemler sağlar. <xref:System.Drawing?displayProperty=nameWithType> Ad alanı ve bunun alt ad boşlukları grafik öğeleri şekilleri (daire, dikdörtgenler, yaylara ve diğerleri), renkleri, yazı tipleri, fırçaları ve benzeri gibi kapsayan sınıflar içerir. Hakkında daha fazla bilgi için [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], bkz: [yönetilen grafik sınıflarını kullanarak](../advanced/using-managed-graphics-classes.md). Temel bilgiler [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] da açıklanan [nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometri çizim bölgesi  
 <xref:System.Windows.Forms.Control.ClientRectangle%2A> Bir denetimin özellik dikdörtgen bölge yok kullanıcının ekranında, denetime belirtir ancak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliği <xref:System.Windows.Forms.PaintEventArgs> gerçekten boyanır alanı belirtir. (Boyama tamamlandı olduğunu unutmayın <xref:System.Windows.Forms.Control.Paint> alan olay yöntemi bir <xref:System.Windows.Forms.PaintEventArgs> örnek bağımsız olarak). Küçük bir bölümü, denetimin görüntü değişiklikleri olduğu gibi bir denetimin kendi kullanılabilir alanı yalnızca bir kısmını boyamak gerekebilir. Bu durumlarda, denetim geliştiricisi gerçek bir dikdörtgen çizin ve geçirebilirsiniz hesaplamanız gerekir <xref:System.Windows.Forms.Control.Invalidate%2A>. Aşırı yüklenmiş sürümlerini <xref:System.Windows.Forms.Control.Invalidate%2A> süren bir <xref:System.Drawing.Rectangle> veya <xref:System.Drawing.Region> oluşturmak için bu bağımsız değişken bağımsız değişken olarak kullanmak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliği <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Aşağıdaki kod parçası gösterir nasıl `FlashTrackBar` özel denetimi çizin dikdörtgen hesaplar. `client` Değişkeni gösterir <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliği. Eksiksiz bir örnek için bkz. [nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Grafik kaynakları serbest bırakma  
 Sistem kaynakları kullandıkları için grafik nesneleri pahalıdır. Örnekleri gibi nesnelerin dahil <xref:System.Drawing.Graphics?displayProperty=nameWithType> sınıf örneklerinin yanı sıra <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>ve diğer grafik sınıfları. Sadece gereksinim ve serbest bir grafik kaynak oluşturmak önemlidir kullanmayı bitirdikten hemen. Uygulayan türü oluşturursanız <xref:System.IDisposable> arabirim, çağrı kendi <xref:System.IDisposable.Dispose%2A> ücretsiz kaynaklar için ile işiniz bittiğinde yöntemi.  
  
 Aşağıdaki kod parçası gösterir nasıl `FlashTrackBar` özel denetimi oluşturur ve serbest bir <xref:System.Drawing.Brush> kaynak. Tam kaynak kodunu görmek [nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İlerleme Durumunu Gösteren Windows Forms Denetimi Oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md)

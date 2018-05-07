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
ms.openlocfilehash: a2d7a02e725e3f8065b80a6b30ea21158be43ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="rendering-a-windows-forms-control"></a>Windows Forms Denetimini İşleme
İşleme görsel bir kullanıcının ekranda oluşturma işleminin ifade eder. Windows Forms kullanan [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (yeni Windows grafik kitaplığına) işleme için. Erişim sağlayan yönetilen sınıflar [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] bulunan <xref:System.Drawing?displayProperty=nameWithType> ad alanı ve onun alt ad boşlukları.  
  
 Aşağıdaki öğeler Denetim işlemede oynayan:  
  
-   Temel sınıfı tarafından sağlanan çizim işlevleri <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
-   Temel öğelerini [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] grafik kitaplığı.  
  
-   Çizim bölge geometri.  
  
-   Grafik kaynakları serbest bırakma yordamı.  
  
## <a name="drawing-functionality-provided-by-control"></a>Denetim tarafından sağlanan işlevselliği çizme  
 Taban sınıfı <xref:System.Windows.Forms.Control> aracılığıyla çizim işlevselliği sağlar, <xref:System.Windows.Forms.Control.Paint> olay. Bir denetim başlatır <xref:System.Windows.Forms.Control.Paint> görünümünü güncelleştirmek gereken her olay. .NET Framework'teki olaylar hakkında daha fazla bilgi için bkz: [işleme ve olayları oluşturma](../../../../docs/standard/events/index.md).  
  
 Olay verileri sınıfı için <xref:System.Windows.Forms.Control.Paint> olay <xref:System.Windows.Forms.PaintEventArgs>, bir denetim çizim için gereken verileri tutan — bir grafik nesnesi ve çizim bölgeyi temsil eden bir dikdörtgen nesnesi için bir tanıtıcı. Bu nesneler gösterilir kalın aşağıdaki kod parçası olarak.  
  
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
  
 <xref:System.Drawing.Graphics> Çizim işlevselliğini kapsülleyen bir yönetilen tartışması içinde açıklandığı gibi sınıftır [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] bu konuda daha sonra. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Örneği <xref:System.Drawing.Rectangle> yapısı ve denetim çizebilir kullanılabilir alanı tanımlar. Bir denetim Geliştirici hesaplayabilirsiniz <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> kullanarak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> tartışma geometrinin bu konunun ilerleyen bölümlerinde açıklandığı gibi bir denetimin özelliği.  
  
 Bir denetim işleme mantığı kılarak sağlamalısınız <xref:System.Windows.Forms.Control.OnPaint%2A> öğesinden devralınan yöntemi <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> bir grafik nesnesi ve aracılığıyla çizmek için dikdörtgen erişim alır <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> ve <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliklerini <xref:System.Windows.Forms.PaintEventArgs> örneği kendisine geçirilen.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemi taban <xref:System.Windows.Forms.Control> sınıfı ile kayıtlı olay temsilcileri yalnızca çağırır ancak herhangi bir çizim işlevsellik uygulamaz <xref:System.Windows.Forms.Control.Paint> olay. Kıldığınızda <xref:System.Windows.Forms.Control.OnPaint%2A>, genellikle çağıracağı <xref:System.Windows.Forms.Control.OnPaint%2A> temsilciler kayıtlı için temel sınıf yöntemi alma <xref:System.Windows.Forms.Control.Paint> olay. Ancak, tüm kullanıcıların yüzeyini boyamak denetimleri temel sınıfın çağırma kullanılamaz <xref:System.Windows.Forms.Control.OnPaint%2A>gibi bu Titreşimi tanıtır. Geçersiz kılma bir örnek için <xref:System.Windows.Forms.Control.OnPaint%2A> olayı bkz [nasıl yapılır: Windows Forms denetimi olduğunu gösteren ilerlemesi oluşturmak](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  Çağrılamadı <xref:System.Windows.Forms.Control.OnPaint%2A> , denetiminden; bunun yerine, doğrudan çağırma <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemi (devralınan <xref:System.Windows.Forms.Control>) veya çağırır diğer bir yöntem <xref:System.Windows.Forms.Control.Invalidate%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Sırayla yöntemini çağıran <xref:System.Windows.Forms.Control.OnPaint%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Yöntemi aşırı yüklenmiş ve bağımsız değişkenler üzerinde bağlı olarak sağlanan <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, bir denetim bazı veya tüm kendi ekran alanının yeniden çizer.  
  
 Temel <xref:System.Windows.Forms.Control> sınıfı tanımlayan çizim için yararlı olan başka bir yöntem — <xref:System.Windows.Forms.Control.OnPaintBackground%2A> yöntemi.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> arka plan boyar (ve dolayısıyla şekli) penceresinin ve sırasında hızlı olması garanti <xref:System.Windows.Forms.Control.OnPaint%2A> ayrıntıları boyar ve tek tek boyama istekleri birine birleştirilir olduğundan daha yavaş olabilir <xref:System.Windows.Forms.Control.Paint> olmak zorunda tüm alanları kapsamaktadır olay yeniden çizilir. Çağrılacak isteyebilirsiniz <xref:System.Windows.Forms.Control.OnPaintBackground%2A> örneği için denetim için bir gradyan renkli arka plan çizmek istiyorsanız.  
  
 Sırada <xref:System.Windows.Forms.Control.OnPaintBackground%2A> bir olay benzeri terminolojisi varsa ve aynı bağımsız değişken olarak `OnPaint` yöntemi, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> true olay yöntemi değildir. Var olan hiçbir `PaintBackground` olay ve <xref:System.Windows.Forms.Control.OnPaintBackground%2A> olay temsilcileri çağrılmaz. Geçersiz kılarken <xref:System.Windows.Forms.Control.OnPaintBackground%2A> yöntemi, türetilmiş bir sınıf çağırmak için gerekli değildir <xref:System.Windows.Forms.Control.OnPaintBackground%2A> olduğu temel sınıfın yöntemi.  
  
## <a name="gdi-basics"></a>GDI + temelleri  
 <xref:System.Drawing.Graphics> Sınıfı, metin görüntüleme yöntemleri yanı sıra daire, üçgenler, yaylar ve üç nokta gibi çeşitli şekiller çizmek için yöntemleri sağlar. <xref:System.Drawing?displayProperty=nameWithType> Ad alanı ve onun alt ad boşlukları şekiller (daireler, dikdörtgenler, yaylar ve diğerleri), renkleri, yazı tipi, Fırçalar vb. gibi grafik öğeleri kapsülleyen sınıfları içerir. Hakkında daha fazla bilgi için [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], bkz: [yönetilen grafik sınıflarını kullanarak](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md). Temel bilgiler [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] da açıklanan [nasıl yapılır: Windows Forms denetimi olduğunu gösteren ilerlemesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Çizim alanının geometri  
 <xref:System.Windows.Forms.Control.ClientRectangle%2A> Denetimi özelliği, kullanıcının ekranda denetlemek için kullanılabilen dikdörtgen bölgesini belirtir sırada <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliği <xref:System.Windows.Forms.PaintEventArgs> gerçekten boyanır alanı belirtir. (Boyama Bitti olduğunu unutmayın <xref:System.Windows.Forms.Control.Paint> geçen olay yöntemi bir <xref:System.Windows.Forms.PaintEventArgs> örneği bağımsız değişkeni olarak). Küçük bir bölümü, denetimin görüntüleme değişiklikleri olduğu gibi bir denetim, kullanılabilir alanı yalnızca bir kısmını boyamak gerekebilir. Bu durumlarda, bir denetim Geliştirici çizim ve olarak geçirmek için gerçek dikdörtgeni işlem gerekir <xref:System.Windows.Forms.Control.Invalidate%2A>. Aşırı yüklenmiş sürümlerini <xref:System.Windows.Forms.Control.Invalidate%2A> süren bir <xref:System.Drawing.Rectangle> veya <xref:System.Drawing.Region> bağımsız değişken olarak oluşturmak için bu değişkeni kullanın <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliği <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Aşağıdaki kodda gösterildiği parçalara nasıl `FlashTrackBar` özel denetim çizim dikdörtgen hesaplar. `client` Değişkeni gösterir <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> özelliği. Tam bir örnek için bkz: [nasıl yapılır: Windows Forms denetimi olduğunu gösteren ilerlemesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Grafik kaynakları serbest bırakma  
 Grafik nesneleri, sistem kaynaklarını kullandığından maliyetlidir. Bu tür nesneleri örneklerini dahil <xref:System.Drawing.Graphics?displayProperty=nameWithType> sınıf örneklerini yanı sıra <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>ve diğer grafik sınıfları. Yalnızca ihtiyaç ve bunu serbest bıraktığınızda bir grafik kaynak oluşturmak önemlidir kullanmayı bitirdikten yakında. Uygulayan bir tür oluşturursanız <xref:System.IDisposable> arabirim, çağrı kendi <xref:System.IDisposable.Dispose%2A> kaynakları boşaltmak için ile bitirdiğinizde yöntemi.  
  
 Aşağıdaki kodda gösterildiği parçalara nasıl `FlashTrackBar` özel denetim oluşturur ve serbest bir <xref:System.Drawing.Brush> kaynak. Tam kaynak kodunu bkz [nasıl yapılır: Windows Forms denetimi olduğunu gösteren ilerlemesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: İlerleme Durumunu Gösteren Windows Forms Denetimi Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)

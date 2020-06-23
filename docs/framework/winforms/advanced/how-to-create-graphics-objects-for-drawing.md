---
title: 'Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma'
description: Çizgiler ve şekiller çizmek, metin oluşturmak veya GDI+ ile görüntüleri görüntülemek ve işlemek için gereken bir grafik nesnesi oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: 1a0884c1e9956dc6f4608e32372deeea24ef4670
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903213"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma
Çizgiler ve şekiller çizmeden, metin oluşturmadan veya GDI+ ile görüntüleri görüntüleyip işleyebilmeniz için önce bir nesnesi oluşturmanız gerekir <xref:System.Drawing.Graphics> . <xref:System.Drawing.Graphics>Nesnesi BIR GDI+ çizim yüzeyini temsil eder ve grafik görüntüleri oluşturmak için kullanılan nesnedir.  
  
 Grafiklerle çalışırken iki adım vardır:  
  
1. Nesne oluşturma <xref:System.Drawing.Graphics> .  
  
2. <xref:System.Drawing.Graphics>Çizgi ve şekil çizmek, metin oluşturmak veya görüntüleri görüntülemek ve işlemek için nesnesini kullanma.  
  
## <a name="creating-a-graphics-object"></a>Grafik nesnesi oluşturma  
 Grafik nesnesi çeşitli yollarla oluşturulabilir.  
  
#### <a name="to-create-a-graphics-object"></a>Grafik nesnesi oluşturmak için  
  
- Bir <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> form veya denetim olayında bir grafik nesnesine bir başvuru alın. Bu, genellikle bir denetim için boyama kodu oluştururken bir grafik nesnesine başvuru elde edersiniz. Benzer şekilde, bir grafik nesnesini, <xref:System.Drawing.Printing.PrintPageEventArgs> için olayını işlerken bir özelliği olarak da elde edebilirsiniz <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> .  
  
     -veya-  
  
- Denetim veya formun <xref:System.Windows.Forms.Control.CreateGraphics%2A> <xref:System.Drawing.Graphics> çizim yüzeyini temsil eden bir nesneye başvuru almak için bir denetimin veya formun yöntemini çağırın. Zaten var olan bir form veya denetim üzerine çizim yapmak istiyorsanız bu yöntemi kullanın.  
  
     -veya-  
  
- <xref:System.Drawing.Graphics>Öğesinden devralan herhangi bir nesneden bir nesne oluşturun <xref:System.Drawing.Image> . Bu yaklaşım, zaten varolan bir görüntüyü değiştirmek istediğinizde yararlıdır.  
  
     Aşağıdaki bölümler, bu işlemlerin her biri hakkında ayrıntılı bilgi verir.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>Paint olay Işleyicisindeki PaintEventArgs  
 <xref:System.Windows.Forms.PaintEventHandler>Denetimleri için veya için programlama yaparken, <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> veya özelliklerinden biri olarak bir grafik nesnesi sağlanır <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs> .  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Paint olaydaki PaintEventArgs 'dan bir grafik nesnesine başvuru almak için  
  
1. Nesneyi bildirin <xref:System.Drawing.Graphics> .  
  
2. <xref:System.Drawing.Graphics>Öğesinin bir parçası olarak geçirilen nesneye başvuracak değişkeni atayın <xref:System.Windows.Forms.PaintEventArgs> .  
  
3. Formu veya denetimi boyamak için kod ekleyin.  
  
     Aşağıdaki örnek, <xref:System.Drawing.Graphics> olaydaki öğesinden bir nesnesine nasıl başvurulacağını gösterir <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> :  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,
       System.Windows.Forms.PaintEventArgs pe)
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a>CreateGraphics yöntemi  
 <xref:System.Windows.Forms.Control.CreateGraphics%2A> <xref:System.Drawing.Graphics> Bu denetim veya formun çizim yüzeyini temsil eden bir nesneye başvuru almak için bir denetimin veya formun yöntemini de kullanabilirsiniz.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>CreateGraphics yöntemiyle bir grafik nesnesi oluşturmak için  
  
- <xref:System.Windows.Forms.Control.CreateGraphics%2A>Grafikleri işlemek istediğiniz formun veya denetimin yöntemini çağırın.  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a>Bir görüntü nesnesinden oluştur  
 Ayrıca, sınıfından türetilen herhangi bir nesneden bir grafik nesnesi oluşturabilirsiniz <xref:System.Drawing.Image> .  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Görüntüden bir grafik nesnesi oluşturmak için  
  
- <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>Nesne oluşturmak Istediğiniz görüntü değişkeninin adını sağlayarak yöntemini çağırın <xref:System.Drawing.Graphics> .  
  
     Aşağıdaki örnek, bir nesnesinin nasıl kullanılacağını gösterir <xref:System.Drawing.Bitmap> :  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
> Yalnızca <xref:System.Drawing.Graphics> dizinli olmayan. bmp dosyalarından (16 bit, 24 bit ve 32-bit. bmp dosyaları gibi) nesneler oluşturabilirsiniz. Dizinlenmemiş. bmp dosyalarının her pikseli, bir renk tablosuna bir dizin tutan dizinli. bmp dosyalarının piksel cinsinden bir renk tutar.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Şekilleri ve görüntüleri çizme ve düzenleme  
 Oluşturulduktan sonra, bir <xref:System.Drawing.Graphics> nesne çizgiler ve şekiller çizmek, metin oluşturmak veya görüntü görüntülemek ve işlemek için kullanılabilir. Nesnesiyle kullanılan asıl nesneler <xref:System.Drawing.Graphics> şunlardır:  
  
- <xref:System.Drawing.Pen>Sınıfı — çizgi çizme, şekil seviyelendirme veya diğer geometrik gösterimleri işleme Için kullanılır.  
  
- <xref:System.Drawing.Brush>Sınıfı — dolgulu şekiller, görüntüler veya metin gibi grafik alanlarının doldurulması Için kullanılır.  
  
- <xref:System.Drawing.Font>Sınıfı — metin işlenirken hangi şekillerin kullanılacağı hakkında bir açıklama sağlar.  
  
- <xref:System.Drawing.Color>Yapı — görüntülenecek farklı renkleri temsil eder.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Oluşturduğunuz grafik nesnesini kullanmak için  
  
- İhtiyacınız olan öğeleri çizmek için yukarıda listelenen uygun nesneyle çalışın.  
  
     Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
    |İşlemek için|Bkz.|  
    |---------------|---------|  
    |Satırlar|[Nasıl yapılır: Bir Windows Formunda Çizgi Çizme](how-to-draw-a-line-on-a-windows-form.md)|  
    |Şekiller|[Nasıl yapılır: Ana Hatlı Şekil Çizme](how-to-draw-an-outlined-shape.md)|  
    |Metin|[Nasıl yapılır: Bir Windows Formunda Metin Çizme](how-to-draw-text-on-a-windows-form.md)|  
    |Görüntüler|[Nasıl yapılır: GDI+ ile Görüntü İşleme](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Grafik Programlamaya Başlarken](getting-started-with-graphics-programming.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: GDI+ ile Görüntü İşleme](how-to-render-images-with-gdi.md)

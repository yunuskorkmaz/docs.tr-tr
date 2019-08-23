---
title: 'Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma'
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
ms.openlocfilehash: 3d3ab62896f6b799cd38a8180b90f33125a9929b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964336"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma
Çizgiler ve şekiller çizmeden, metin oluşturmadan veya GDI+ ile görüntüleri görüntüleyip işleyebilmeniz için önce bir <xref:System.Drawing.Graphics> nesnesi oluşturmanız gerekir. <xref:System.Drawing.Graphics> Nesnesi bir GDI+ çizim yüzeyini temsil eder ve grafik görüntüleri oluşturmak için kullanılan nesnedir.  
  
 Grafiklerle çalışırken iki adım vardır:  
  
1. <xref:System.Drawing.Graphics> Nesne oluşturma.  
  
2. Çizgi ve şekil çizmek, metin oluşturmak veya görüntüleri görüntülemek ve işlemek için nesnesinikullanma.<xref:System.Drawing.Graphics>  
  
## <a name="creating-a-graphics-object"></a>Grafik nesnesi oluşturma  
 Grafik nesnesi çeşitli yollarla oluşturulabilir.  
  
#### <a name="to-create-a-graphics-object"></a>Grafik nesnesi oluşturmak için  
  
- Bir form veya denetim <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olayında bir grafik nesnesine bir başvuru alın. Bu, genellikle bir denetim için boyama kodu oluştururken bir grafik nesnesine başvuru elde edersiniz. Benzer şekilde, bir <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument>grafik nesnesini, için <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayını işlerken bir özelliği olarak da elde edebilirsiniz.  
  
     -veya-  
  
- Denetim veya formun çizim yüzeyini temsil eden bir <xref:System.Drawing.Graphics> nesneye başvuru almak için bir denetimin veya formun yönteminiçağırın.<xref:System.Windows.Forms.Control.CreateGraphics%2A> Zaten var olan bir form veya denetim üzerine çizim yapmak istiyorsanız bu yöntemi kullanın.  
  
     -veya-  
  
- <xref:System.Drawing.Graphics> Öğesinden<xref:System.Drawing.Image>devralan herhangi bir nesneden bir nesne oluşturun. Bu yaklaşım, zaten varolan bir görüntüyü değiştirmek istediğinizde yararlıdır.  
  
     Aşağıdaki bölümler, bu işlemlerin her biri hakkında ayrıntılı bilgi verir.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>Paint olay Işleyicisindeki PaintEventArgs  
 Denetimleri <xref:System.Windows.Forms.PaintEventHandler> için <xref:System.Windows.Forms.PaintEventArgs> veya <xref:System.Drawing.Printing.PrintDocument.PrintPage> için<xref:System.Drawing.Printing.PrintDocument>programlama yaparken, veya<xref:System.Drawing.Printing.PrintPageEventArgs>özelliklerinden biri olarak bir grafik nesnesi sağlanır.  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Paint olaydaki PaintEventArgs 'dan bir grafik nesnesine başvuru almak için  
  
1. <xref:System.Drawing.Graphics> Nesneyi bildirin.  
  
2. Öğesinin bir parçası olarak geçirilen <xref:System.Drawing.Graphics> nesneye başvuracak değişkeni atayın. <xref:System.Windows.Forms.PaintEventArgs>  
  
3. Formu veya denetimi boyamak için kod ekleyin.  
  
     Aşağıdaki örnek, <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olaydaki öğesinden bir nesnesine nasıl başvurulacağını gösterir:  
  
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
 Bu denetim veya formun çizim <xref:System.Windows.Forms.Control.CreateGraphics%2A> yüzeyini temsil eden bir <xref:System.Drawing.Graphics> nesneye başvuru almak için bir denetimin veya formun yöntemini de kullanabilirsiniz.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>CreateGraphics yöntemiyle bir grafik nesnesi oluşturmak için  
  
- Grafikleri işlemek istediğiniz formun veya denetimin yönteminiçağırın.<xref:System.Windows.Forms.Control.CreateGraphics%2A>  
  
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
 Ayrıca, <xref:System.Drawing.Image> sınıfından türetilen herhangi bir nesneden bir grafik nesnesi oluşturabilirsiniz.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Görüntüden bir grafik nesnesi oluşturmak için  
  
- Nesne oluşturmak istediğiniz görüntü değişkeninin adını sağlayarak yönteminiçağırın.<xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> <xref:System.Drawing.Graphics>  
  
     Aşağıdaki örnek, bir <xref:System.Drawing.Bitmap> nesnesinin nasıl kullanılacağını gösterir:  
  
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
> Yalnızca dizinli olmayan. <xref:System.Drawing.Graphics> BMP dosyalarından (16 bit, 24 bit ve 32-bit. bmp dosyaları gibi) nesneler oluşturabilirsiniz. Dizinlenmemiş. bmp dosyalarının her pikseli, bir renk tablosuna bir dizin tutan dizinli. bmp dosyalarının piksel cinsinden bir renk tutar.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Şekilleri ve görüntüleri çizme ve düzenleme  
 Oluşturulduktan sonra, bir <xref:System.Drawing.Graphics> nesne çizgiler ve şekiller çizmek, metin oluşturmak veya görüntü görüntülemek ve işlemek için kullanılabilir. <xref:System.Drawing.Graphics> Nesnesiyle kullanılan asıl nesneler şunlardır:  
  
- <xref:System.Drawing.Pen> Sınıfı — çizgi çizme, şekil seviyelendirme veya diğer geometrik gösterimleri işleme için kullanılır.  
  
- <xref:System.Drawing.Brush> Sınıfı — dolgulu şekiller, görüntüler veya metin gibi grafik alanlarının doldurulması için kullanılır.  
  
- <xref:System.Drawing.Font> Sınıfı — metin işlenirken hangi şekillerin kullanılacağı hakkında bir açıklama sağlar.  
  
- <xref:System.Drawing.Color> Yapı — görüntülenecek farklı renkleri temsil eder.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Oluşturduğunuz grafik nesnesini kullanmak için  
  
- İhtiyacınız olan öğeleri çizmek için yukarıda listelenen uygun nesneyle çalışın.  
  
     Daha fazla bilgi için aşağıdaki konulara bakın:  
  
    |İşlemek için|Bkz.|  
    |---------------|---------|  
    |Satırları|[Nasıl yapılır: Bir Windows formunda çizgi çizme](how-to-draw-a-line-on-a-windows-form.md)|  
    |Şekiller|[Nasıl yapılır: Anahatları belirlenmiş bir şekil çiz](how-to-draw-an-outlined-shape.md)|  
    |Metin|[Nasıl yapılır: Bir Windows formunda metin çizme](how-to-draw-text-on-a-windows-form.md)|  
    |Görüntüler|[Nasıl yapılır: GDI+ ile görüntü işleme](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Grafik Programlamaya Başlarken](getting-started-with-graphics-programming.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: GDI+ ile görüntü işleme](how-to-render-images-with-gdi.md)

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
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142439"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma
Çizgiler ve şekiller çizebilmeniz, metni oluşturmadan veya GDI+ ile görüntüleri <xref:System.Drawing.Graphics> görüntülemeden ve işlemeden önce bir nesne oluşturmanız gerekir. Nesne <xref:System.Drawing.Graphics> GDI+ çizim yüzeyini temsil eder ve grafik görüntüler oluşturmak için kullanılan nesnedir.  
  
 Grafiklerle çalışmanın iki adımı vardır:  
  
1. Nesne <xref:System.Drawing.Graphics> oluşturma.  
  
2. <xref:System.Drawing.Graphics> Nesneleri kullanarak çizgiler ve şekiller çizmek, metni işlemek veya görüntüleri görüntülemek ve işlemek için.  
  
## <a name="creating-a-graphics-object"></a>Grafik Nesnesi Oluşturma  
 Grafik nesnesi çeşitli şekillerde oluşturulabilir.  
  
#### <a name="to-create-a-graphics-object"></a>Grafik nesnesi oluşturmak için  
  
- Bir form veya denetim <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> durumunda bir parçası olarak bir grafik nesnesine bir başvuru alın. Denetim için boyama kodu oluştururken genellikle grafik nesnesine başvuru yutmama şekliniz dir. Benzer şekilde, bir <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument.PrintPage> . <xref:System.Drawing.Printing.PrintDocument>  
  
     -veya-  
  
- Bu <xref:System.Windows.Forms.Control.CreateGraphics%2A> denetimveya formun çizim yüzeyini temsil <xref:System.Drawing.Graphics> eden bir nesneye başvuru almak için bir denetim veya form yöntemini arayın. Zaten var olan bir form veya denetim üzerinde çizmek istiyorsanız bu yöntemi kullanın.  
  
     -veya-  
  
- Devralan <xref:System.Drawing.Graphics> herhangi bir nesneden <xref:System.Drawing.Image>bir nesne oluşturun. Bu yaklaşım, zaten varolan bir görüntüyü değiştirmek istediğinizde yararlıdır.  
  
     Aşağıdaki bölümlerde bu işlemlerin her biri hakkında ayrıntılı bilgi verilmiştir.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventEtkinlikArgs Boya Olay Handleyici  
 <xref:System.Windows.Forms.PaintEventHandler> Ne zaman programlama denetimleri <xref:System.Drawing.Printing.PrintDocument.PrintPage> veya <xref:System.Drawing.Printing.PrintDocument>için , bir grafik nesnesi <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs>özelliklerinden biri olarak sağlanır veya .  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Paint olayındaki PaintEventArgs'tan grafik nesnesine referans almak için  
  
1. Nesneyi <xref:System.Drawing.Graphics> bildirin.  
  
2. Değişkeni, bir parçası <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs>olarak geçirilen nesneye başvurmak için ata.  
  
3. Formu veya denetimi boyamak için kod ekleyin.  
  
     Aşağıdaki örnek, <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olaydaki bir nesneye nasıl başvurulsüreceğini gösterir:  
  
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
  
## <a name="creategraphics-method"></a>CreateGraphics Yöntemi  
 Denetim veya formun çizim yüzeyini temsil eden <xref:System.Windows.Forms.Control.CreateGraphics%2A> bir <xref:System.Drawing.Graphics> nesneye başvuru almak için denetim veya form yöntemini de kullanabilirsiniz.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>CreateGraphics yöntemiyle grafik nesnesi oluşturmak için  
  
- Grafik <xref:System.Windows.Forms.Control.CreateGraphics%2A> oluşturmak istediğiniz form veya denetim yöntemini arayın.  
  
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
  
## <a name="create-from-an-image-object"></a>Görüntü Nesnesinden Oluşturma  
 Ayrıca, sınıftan türetilen herhangi bir nesneden bir <xref:System.Drawing.Image> grafik nesnesi oluşturabilirsiniz.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Görüntüden Grafik nesnesi oluşturmak için  
  
- Bir <xref:System.Drawing.Graphics> <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> nesne oluşturmak istediğiniz Görüntü değişkeninin adını sağlayarak yöntemi arayın.  
  
     Aşağıdaki örnek, bir <xref:System.Drawing.Bitmap> nesnenin nasıl kullanılacağını gösterir:  
  
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
> Yalnızca 16 <xref:System.Drawing.Graphics> bit, 24-bit ve 32 bit .bmp dosyaları gibi dizine eklenmemiş .bmp dosyalarından nesneler oluşturabilirsiniz. Dizine eklenmemiş .bmp dosyalarının her pikseli, renk tablosuna dizin tutan dizin ekinli .bmp dosyalarının piksellerinin aksine bir renk tutar.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Şekil ve Görüntüleri Çizme ve Manipüle Etme  
 Oluşturulduktan sonra, <xref:System.Drawing.Graphics> bir nesne çizgiler ve şekiller çizmek, metni işlemek veya görüntüleri görüntülemek ve işlemek için kullanılabilir. <xref:System.Drawing.Graphics> Nesne ile birlikte kullanılan temel nesneler şunlardır:  
  
- Sınıf-Çizgiler <xref:System.Drawing.Pen> çizmek, şekilleri özetleme veya diğer geometrik gösterimleri işlemek için kullanılır.  
  
- <xref:System.Drawing.Brush> Sınıf—Dolu şekiller, resimler veya metin gibi grafik alanlarını doldurmak için kullanılır.  
  
- Sınıf—Metni <xref:System.Drawing.Font> işlerken hangi şekillerin kullanılacağının açıklamasını sağlar.  
  
- Yapı-Görüntülenecek <xref:System.Drawing.Color> farklı renkleri temsil eder.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Oluşturduğunuz Grafik nesnesini kullanmak için  
  
- İhtiyacınız olanı çizmek için yukarıda listelenen uygun nesneyle çalışın.  
  
     Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
    |Işlemek için|Bkz.|  
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

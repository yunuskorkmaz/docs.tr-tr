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
ms.openlocfilehash: 5682b2f0183cbeb8bae377423bb76caa0fbaf7cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223634"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma
Çizgiler ve şekiller çizmek önce metin işlemek veya görüntülemek ve görüntülerle işlemek [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], oluşturmak gereken bir <xref:System.Drawing.Graphics> nesne. <xref:System.Drawing.Graphics> Nesnesini temsil eder bir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizim yüzeyi ve grafik görüntüleri oluşturmak için kullanılan nesne.  
  
 Grafiklerle çalışma iki adımı vardır:  
  
1.  Oluşturma bir <xref:System.Drawing.Graphics> nesne.  
  
2.  Kullanarak <xref:System.Drawing.Graphics> çizgiler ve şekiller çizmek, metin, işleme veya görüntülemek ve görüntüleri işlemek için nesne.  
  
## <a name="creating-a-graphics-object"></a>Bir grafik nesnesi oluşturma  
 Bir grafik nesnesinin çeşitli yollarla oluşturulabilir.  
  
#### <a name="to-create-a-graphics-object"></a>Bir grafik nesnesi oluşturmak için  
  
-   Bir parçası olarak bir grafik nesnesine bir başvuru alma <xref:System.Windows.Forms.PaintEventArgs> içinde <xref:System.Windows.Forms.Control.Paint> bir form veya denetim olayı. Bu, genellikle bir denetim boyama kodu oluştururken bir grafik nesnesine başvuru nasıl elde olur. Benzer şekilde, ayrıca bir grafik nesnesinin bir özelliği olarak alabilirsiniz <xref:System.Drawing.Printing.PrintPageEventArgs> işlerken <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay için bir <xref:System.Drawing.Printing.PrintDocument>.  
  
     -veya-  
  
-   Çağrı <xref:System.Windows.Forms.Control.CreateGraphics%2A> denetim veya formun bir başvuru almak için yöntemi bir <xref:System.Drawing.Graphics> çizim yüzeyi bu denetim veya formun temsil eden nesne. Bir form veya zaten bir denetim çizmek istiyorsanız bu yöntemi kullanın.  
  
     -veya-  
  
-   Oluşturma bir <xref:System.Drawing.Graphics> nesne öğesinden devralınan herhangi bir nesneden <xref:System.Drawing.Image>. Bu yaklaşım, zaten mevcut bir görüntüyü değiştirmek istediğinizde yararlıdır.  
  
     Aşağıdaki bölümlerde, bu işlemlerin her biri hakkında ayrıntılar verir.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>Boya olay işleyicisinde PaintEventArgs  
 Programlamada <xref:System.Windows.Forms.PaintEventHandler> denetimleri için veya <xref:System.Drawing.Printing.PrintDocument.PrintPage> için bir <xref:System.Drawing.Printing.PrintDocument>, bir grafik nesnesinin özelliklerinden biri olarak sağlanan <xref:System.Windows.Forms.PaintEventArgs> veya <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Boyama olayını içinde PaintEventArgs grafik nesnesine başvuru almak için  
  
1.  Bildirme <xref:System.Drawing.Graphics> nesne.  
  
2.  Başvurmak için değişkenine atayın <xref:System.Drawing.Graphics> nesnesinin bir parçası olarak geçirilen <xref:System.Windows.Forms.PaintEventArgs>.  
  
3.  Form veya denetim boyama için kodu ekleyin.  
  
     Aşağıdaki örnek nasıl başvurulacağını gösterir bir <xref:System.Drawing.Graphics> nesnesinden <xref:System.Windows.Forms.PaintEventArgs> içinde <xref:System.Windows.Forms.Control.Paint> olay:  
  
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
  
## <a name="creategraphics-method"></a>CreateGraphics metodu  
 Ayrıca <xref:System.Windows.Forms.Control.CreateGraphics%2A> denetim veya formun bir başvuru almak için yöntemi bir <xref:System.Drawing.Graphics> çizim yüzeyi bu denetim veya formun temsil eden nesne.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>CreateGraphics metodu bir grafik nesnesi oluşturmak için  
  
-   Çağrı <xref:System.Windows.Forms.Control.CreateGraphics%2A> üzerinde grafik işleme almak istediğiniz form veya denetim yöntemi.  
  
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
  
## <a name="create-from-an-image-object"></a>Bir görüntü nesneden oluşturun  
 Ayrıca, türetilen herhangi bir nesneden bir grafik nesnesinin oluşturabilirsiniz <xref:System.Drawing.Image> sınıfı.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Bir görüntüden bir grafik nesnesi oluşturmak için  
  
-   Çağrı <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> oluşturmak istediğiniz görüntü değişken adını sağlama yöntemi, bir <xref:System.Drawing.Graphics> nesne.  
  
     Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Drawing.Bitmap> nesnesi:  
  
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
>  Yalnızca oluşturabilirsiniz <xref:System.Drawing.Graphics> 16-bit, 24-bit ve 32-bit .bmp dosyaları gibi dizinlenmemiş .bmp dosyaları nesneleri. Her bir pikseli dizinlenmemiş .bmp dosyaları piksel bir renk tablosu için dizin tutun dizinli .bmp dosyaların aksine, bir renk tutar.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Çizim ve şekiller ve resimler düzenleme  
 Oluşturulduktan sonra bir <xref:System.Drawing.Graphics> nesne, çizgiler ve şekiller çizmek, metin, işleme veya görüntülemek ve görüntüleri işlemek için kullanılabilir. İle kullanılan asıl nesneleri <xref:System.Drawing.Graphics> nesnesi:  
  
-   <xref:System.Drawing.Pen> Sınıfı — satırlar çizme, şekiller anahat oluşturma veya diğer geometrik gösterimleri işleme için kullanılan.  
  
-   <xref:System.Drawing.Brush> Sınıfı — dolgulu şekiller, görüntü veya metin gibi grafik alanlarını doldurmak için kullanılır.  
  
-   <xref:System.Drawing.Font> Sınıfı — ne metin işlenirken kullanılacak şekilleri açıklamasını sağlar.  
  
-   <xref:System.Drawing.Color> Yapısı — görüntülemek için farklı renkler temsil eder.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Oluşturduğunuz grafik nesnesini kullanmak için  
  
-   Aradığınızı çizmek için yukarıda listelenen uygun nesne ile çalışır.  
  
     Daha fazla bilgi için aşağıdaki konulara bakın:  
  
    |İşlemek için|Bkz. |  
    |---------------|---------|  
    |satırları|[Nasıl yapılır: Windows Formunda Çizgi Çizme](how-to-draw-a-line-on-a-windows-form.md)|  
    |Şekiller|[Nasıl yapılır: Anahatlı Şekil Çizme](how-to-draw-an-outlined-shape.md)|  
    |Metin|[Nasıl yapılır: Bir Windows Formunda Metin Çizme](how-to-draw-text-on-a-windows-form.md)|  
    |Görüntüler|[Nasıl yapılır: GDI+ ile Resim İşleme](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Grafik Programlamaya Başlarken](getting-started-with-graphics-programming.md)
- [Windows Formlarında Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: GDI+ ile Resim İşleme](how-to-render-images-with-gdi.md)

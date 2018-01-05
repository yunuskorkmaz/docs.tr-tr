---
title: "Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4b626d3d87c6537b74b6d28e086303474ea2c3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma
Çizgiler ve şekiller çizme önce metin oluşturmak veya görüntülemek ve görüntülerle işlemek [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], oluşturmak gereken bir <xref:System.Drawing.Graphics> nesnesi. <xref:System.Drawing.Graphics> Nesne gösteren bir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizim yüzeyi ve grafik görüntüleri oluşturmak için kullanılan nesne.  
  
 Grafiklerle çalışma iki adımı vardır:  
  
1.  Oluşturma bir <xref:System.Drawing.Graphics> nesnesi.  
  
2.  Kullanarak <xref:System.Drawing.Graphics> çizgiler ve şekiller çizme, metin, oluşturmak veya görüntülemek ve resimleri işlemek için nesne.  
  
## <a name="creating-a-graphics-object"></a>Bir grafik nesnesi oluşturma  
 Bir grafik nesnesinin çeşitli yollarla oluşturulabilir.  
  
#### <a name="to-create-a-graphics-object"></a>Bir grafik nesnesi oluşturmak için  
  
-   Bir parçası olarak bir grafik nesnesine başvuru almak <xref:System.Windows.Forms.PaintEventArgs> içinde <xref:System.Windows.Forms.Control.Paint> bir form veya denetim olayı. Bu, genellikle bir denetim için boyama kod oluşturulurken bir grafik nesnesine başvuru nasıl elde olur. Benzer şekilde, bir grafik nesnesinin özelliği olarak edinebilirsiniz <xref:System.Drawing.Printing.PrintPageEventArgs> işlerken <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı için bir <xref:System.Drawing.Printing.PrintDocument>.  
  
     veya  
  
-   Çağrı <xref:System.Windows.Forms.Control.CreateGraphics%2A> yöntemi denetim veya formun bir başvuru almak için bir <xref:System.Drawing.Graphics> çizim yüzeyini bu denetim veya formun temsil eden nesne. Bir form veya zaten denetim çizmek istiyorsanız bu yöntemi kullanın.  
  
     veya  
  
-   Oluşturma bir <xref:System.Drawing.Graphics> nesne öğesinden devralınan herhangi bir nesneden <xref:System.Drawing.Image>. Bu yaklaşım, zaten varolan bir görüntü alter istediğinizde yararlıdır.  
  
     Aşağıdaki bölümlerde bu işlemlerin her biri hakkında ayrıntılar sağlar.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>Paint olay işleyicisi PaintEventArgs  
 Programlama zaman <xref:System.Windows.Forms.PaintEventHandler> denetimleri için veya <xref:System.Drawing.Printing.PrintDocument.PrintPage> için bir <xref:System.Drawing.Printing.PrintDocument>, bir grafik nesnesinin özelliklerini biri olarak sağlanan <xref:System.Windows.Forms.PaintEventArgs> veya <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Paint olayı PaintEventArgs grafik nesnesine başvuru almak için  
  
1.  Bildirme <xref:System.Drawing.Graphics> nesnesi.  
  
2.  Başvurmak için değişkenine atamak <xref:System.Drawing.Graphics> nesnesi geçirildi parçası olarak <xref:System.Windows.Forms.PaintEventArgs>.  
  
3.  Form veya denetim boyamak için kodu ekleyin.  
  
     Aşağıdaki örnek başvuru gösterilmektedir bir <xref:System.Drawing.Graphics> nesnesinin <xref:System.Windows.Forms.PaintEventArgs> içinde <xref:System.Windows.Forms.Control.Paint> olay:  
  
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
 Aynı zamanda <xref:System.Windows.Forms.Control.CreateGraphics%2A> yöntemi denetim veya formun bir başvuru almak için bir <xref:System.Drawing.Graphics> çizim yüzeyini bu denetim veya formun temsil eden nesne.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>CreateGraphics yöntemi ile bir grafik nesnesi oluşturmak için  
  
-   Çağrı <xref:System.Windows.Forms.Control.CreateGraphics%2A> sonra istediğiniz grafik işleme biçimi veya denetim yöntemi.  
  
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
 Ayrıca, türetilen herhangi bir nesneden bir grafik nesnesi oluşturabilirsiniz <xref:System.Drawing.Image> sınıfı.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Bir görüntüden bir grafik nesnesi oluşturmak için  
  
-   Çağrı <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> oluşturmak istediğiniz görüntü değişken adını sağlama yöntemi, bir <xref:System.Drawing.Graphics> nesnesi.  
  
     Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Drawing.Bitmap> nesnesi:  
  
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
>  Yalnızca oluşturabilirsiniz <xref:System.Drawing.Graphics> 16-bit, 24 bit ve 32-bit .bmp dosyaları gibi dizinlenmemiş .bmp dosyaları nesneleri. Her piksel dizinlenmemiş .bmp dosyaları bir renk tablosu için dizin tutun dizinli .bmp dosyaları piksel aksine bir renk tutar.  
  
-  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Çizim ve şekiller ve görüntüleri düzenleme  
 Oluşturulduktan sonra bir <xref:System.Drawing.Graphics> nesne çizgiler ve şekiller çizme, metin, oluşturmak veya görüntülemek ve resimleri işlemek için kullanılamaz. İle kullanılan asıl nesneleri <xref:System.Drawing.Graphics> nesnesi:  
  
-   <xref:System.Drawing.Pen> Sınıfı — satırlar çizme, şekiller anahat oluşturma veya diğer geometrik Beyanları çizmek için kullanılan.  
  
-   <xref:System.Drawing.Brush> Sınıfı — doldurulmuş şekiller, görüntü veya metin gibi grafik alanları doldurmak için kullanılır.  
  
-   <xref:System.Drawing.Font> Sınıfı — ne metin işlenirken şekilleri açıklamasını sağlar.  
  
-   <xref:System.Drawing.Color> Yapısı — görüntülemek için farklı renkleri temsil eder.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Oluşturduğunuz grafik nesnesi kullanmak için  
  
-   Gerekenler çizmek için yukarıda listelenen uygun nesnesiyle çalışır.  
  
     Daha fazla bilgi için aşağıdaki konulara bakın:  
  
    |Oluşturulacak|Bkz. |  
    |---------------|---------|  
    |satırları|[Nasıl yapılır: Bir Windows Formunda Çizgi Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |Şekiller|[Nasıl yapılır: Ana Hatlı Şekil Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |Metin|[Nasıl yapılır: Bir Windows Formunda Metin Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |Görüntüler|[Nasıl yapılır: GDI+ ile Görüntü İşleme](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafik Programlamaya Başlarken](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Nasıl yapılır: GDI+ ile Görüntü İşleme](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)

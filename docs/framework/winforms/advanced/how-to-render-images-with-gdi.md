---
title: 'Nasıl yapılır: GDI+ ile Görüntü İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: 6f5b139c6831a065c85e9d9889c259c859a649cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-render-images-with-gdi"></a>Nasıl yapılır: GDI+ ile Görüntü İşleme
Kullanabileceğiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] uygulamalarınızdaki dosyaları olarak mevcut resimleri işlemek için. Yeni bir nesne oluşturarak bunu bir <xref:System.Drawing.Image> sınıfı (gibi <xref:System.Drawing.Bitmap>), oluşturma bir <xref:System.Drawing.Graphics> kullanmak istediğiniz çizim yüzeyini başvuruyor nesne ve çağırma <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi <xref:System.Drawing.Graphics> nesnesi. Görüntü grafik sınıfı tarafından temsil edilen çizim yüzeyine boyandığında. Oluşturma ve tasarım zamanında resim dosyalarını düzenlemek için görüntü düzenleyicisi kullanın ve bunları işlemek [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çalışma zamanında. Daha fazla bilgi için bkz: [simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>GDI + ile görüntü oluşturmak için  
  
1.  Görüntülemek istediğiniz görüntüyü temsil eden bir nesne oluşturun. Bu nesne öğesinden devralınan bir sınıf üyesi olmalıdır <xref:System.Drawing.Image>, gibi <xref:System.Drawing.Bitmap> veya <xref:System.Drawing.Imaging.Metafile>. Bir örnek verilmiştir:  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the   
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2.  Oluşturma bir <xref:System.Drawing.Graphics> kullanmak istediğiniz çizim yüzeyini temsil eden nesne. Daha fazla bilgi için bkz: [nasıl yapılır: çizim için grafik nesneleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of   
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3.  Çağrı <xref:System.Drawing.Graphics.DrawImage%2A> görüntü oluşturmak için grafik nesnenizin. Çizilecek görüntü hem çizilecek olduğu koordinatları belirtmeniz gerekir.  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafik Programlamaya Başlarken](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [GDI+'da Kalemler, Çizgiler ve Dikdörtgenler](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 [Nasıl yapılır: Bir Windows Formunda Metin Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Çizim çizgi veya kapalı şekiller](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)  
 [Simgeler için Görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)

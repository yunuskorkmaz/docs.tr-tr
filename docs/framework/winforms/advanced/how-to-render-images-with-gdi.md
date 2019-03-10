---
title: 'Nasıl yapılır: GDI + ile görüntü işleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: d2c626f46862e5fdc7c51b509a6419a3d67c4102
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702834"
---
# <a name="how-to-render-images-with-gdi"></a>Nasıl yapılır: GDI + ile görüntü işleme
Kullanabileceğiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] uygulamalarınızdaki dosyaları olarak mevcut görüntülerini işlemek için. Yeni bir nesne oluşturarak bunu bir <xref:System.Drawing.Image> sınıfı (gibi <xref:System.Drawing.Bitmap>), oluşturma bir <xref:System.Drawing.Graphics> kullanmak istediğiniz çizim yüzeyi başvuran nesne ve çağırma <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi <xref:System.Drawing.Graphics> nesne. Görüntü grafik sınıfı tarafından temsil edilen çizim yüzeyine boyanacak. Oluşturma ve tasarım zamanında resim dosyalarını düzenlemek için görüntü Düzenleyicisi'ni kullanın ve bunları işlemek [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çalışma zamanında. Daha fazla bilgi için [simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>GDI + ile görüntü oluşturmak için  
  
1.  Görüntülemek istediğiniz görüntüyü temsil eden bir nesne oluşturun. Bu nesne öğesinden devralınan bir sınıf üyesi olmalıdır <xref:System.Drawing.Image>, gibi <xref:System.Drawing.Bitmap> veya <xref:System.Drawing.Imaging.Metafile>. Bir örnek gösterilir:  
  
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
  
2.  Oluşturma bir <xref:System.Drawing.Graphics> kullanmak istediğiniz çizim yüzeyi temsil eden nesne. Daha fazla bilgi için [nasıl yapılır: Çizim için grafik nesneleri oluşturma](how-to-create-graphics-objects-for-drawing.md).  
  
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
  
3.  Çağrı <xref:System.Drawing.Graphics.DrawImage%2A> görüntüsünü işlemek için grafik nesne. Çizilecek görüntü hem çizilecek olduğu koordinatları belirtmeniz gerekir.  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Grafik Programlamaya Başlarken](getting-started-with-graphics-programming.md)
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](how-to-create-graphics-objects-for-drawing.md)
- [GDI+'da Kalemler, Çizgiler ve Dikdörtgenler](pens-lines-and-rectangles-in-gdi.md)
- [Nasıl yapılır: Bir Windows formunda metin çizme](how-to-draw-text-on-a-windows-form.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizim çizgi veya kapalı şekiller](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [Simgeler için Görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)

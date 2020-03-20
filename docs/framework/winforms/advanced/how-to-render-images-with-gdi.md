---
title: 'Nasıl yapılır: GDI+ ile Resim İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: fffe1f1052d7323d234985b7e752866f2e89657d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182512"
---
# <a name="how-to-render-images-with-gdi"></a>Nasıl yapılır: GDI+ ile Resim İşleme
Uygulamalarınızda dosya olarak var olan görüntüleri işlemek için GDI+'yı kullanabilirsiniz. Bunu, bir sınıfın yeni bir <xref:System.Drawing.Image> nesnesini <xref:System.Drawing.Bitmap>(örneğin), <xref:System.Drawing.Graphics> kullanmak istediğiniz çizim yüzeyine başvuran bir nesne <xref:System.Drawing.Graphics.DrawImage%2A> oluşturarak <xref:System.Drawing.Graphics> ve nesnenin yöntemini çağırarak yaparsınız. Görüntü grafik sınıfı tarafından temsil edilen çizim yüzeyine boyanacaktır. Görüntü Düzenleyicisi'ni tasarım zamanında görüntü dosyalarını oluşturmak ve düzenlemek ve çalışma zamanında GDI+ ile işlemek için kullanabilirsiniz. Daha fazla bilgi [için Simgeler için Resim Düzenleyicisi'ne](/cpp/windows/image-editor-for-icons)bakın.  
  
### <a name="to-render-an-image-with-gdi"></a>GDI+ ile görüntü işlemek için  
  
1. Görüntülemek istediğiniz görüntüyü temsil eden bir nesne oluşturun. Bu nesne, devralan bir sınıfın üyesi <xref:System.Drawing.Image>olmalıdır <xref:System.Drawing.Bitmap> , <xref:System.Drawing.Imaging.Metafile>gibi veya . Bir örnek gösterilir:  
  
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
  
2. Kullanmak <xref:System.Drawing.Graphics> istediğiniz çizim yüzeyini temsil eden bir nesne oluşturun. Daha fazla bilgi için [bkz: Çizim için Grafik Nesneleri Oluşturma](how-to-create-graphics-objects-for-drawing.md).  
  
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
  
3. Görüntüyü <xref:System.Drawing.Graphics.DrawImage%2A> işlemek için grafik nesnenizi arayın. Hem çizilecek görüntüyü hem de çizilecek koordinatları belirtmeniz gerekir.  
  
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
- [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](how-to-create-graphics-objects-for-drawing.md)
- [GDI+'da Kalemler, Çizgiler ve Dikdörtgenler](pens-lines-and-rectangles-in-gdi.md)
- [Nasıl yapılır: Bir Windows Formunda Metin Çizme](how-to-draw-text-on-a-windows-form.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizim Çizgileri veya Kapalı Şekiller](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [Simgeler için Görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)

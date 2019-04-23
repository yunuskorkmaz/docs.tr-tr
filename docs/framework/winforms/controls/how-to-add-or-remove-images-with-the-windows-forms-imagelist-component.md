---
title: 'Nasıl yapılır: Windows Forms ImageList Bileşeni ile Resim Ekleme veya Kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
ms.openlocfilehash: 286b56cddc18589b936a7f053a12ed44c81a32b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072980"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Nasıl yapılır: Windows Forms ImageList Bileşeni ile Resim Ekleme veya Kaldırma
Windows Forms <xref:System.Windows.Forms.ImageList> bir denetimle ilişkili önce bileşeni ile görüntü genellikle doldurulur. Ancak, ekleyin ve görüntü listesi denetimi ile ilişkilendirdikten sonra görüntüleri kaldırın.  
  
> [!NOTE]
>  Görüntüleri kaldırdığınızda doğrulayın <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> ilişkili herhangi bir denetim özelliği hala geçerli.  
  
### <a name="to-add-images-programmatically"></a>Görüntüleri programsal olarak eklemek için  
  
-   Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> görüntü listenin yöntemi <xref:System.Windows.Forms.ImageList.Images%2A> özelliği.  
  
     Aşağıdaki kod örneğinde yolunu ayarlamak için görüntü konumunu **Belgelerim** klasör. Bu konum, Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü kullanılır. Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri daha fazla kullanıcı sağlar. Aşağıdaki kod örneği, bir form olmasını gerektirir bir <xref:System.Windows.Forms.ImageList> denetim zaten eklendi.  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the   
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =   
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample   
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as   
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =   
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### <a name="to-add-images-with-a-key-value"></a>Bir anahtar değeri ile görüntü eklemek için.  
  
-   Birini <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> görüntü listenin yöntemlerinin <xref:System.Windows.Forms.ImageList.Images%2A> bir anahtar değeri alan özelliği.  
  
     Aşağıdaki kod örneğinde yolunu ayarlamak için görüntü konumunu **Belgelerim** klasör. Bu konum, Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü kullanılır. Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri daha fazla kullanıcı sağlar. Aşağıdaki kod örneği, bir form olmasını gerektirir bir <xref:System.Windows.Forms.ImageList> denetim zaten eklendi.  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the   
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =   
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
```  
  
### <a name="to-remove-all-images-programmatically"></a>Tüm görüntüleri programlı bir şekilde kaldırmak için  
  
-   Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> tek bir görüntü kaldırmak için yöntemi  
  
     , - veya -  
  
     Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> görüntü listesi'ndaki tüm görüntüler temizlemek için yöntemi.  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
```  
  
### <a name="to-remove-images-by-key"></a>Anahtara göre görüntülerini kaldırmak için  
  
-   Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> anahtara göre tek bir görüntü kaldırmak için yöntemi.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ImageList Bileşeni](imagelist-component-windows-forms.md)
- [ImageList Bileşenine Genel Bakış](imagelist-component-overview-windows-forms.md)
- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../advanced/images-bitmaps-and-metafiles.md)

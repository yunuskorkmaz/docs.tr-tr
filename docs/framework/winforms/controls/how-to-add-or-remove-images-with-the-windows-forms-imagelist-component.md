---
title: ImageList Bileşeni ile Resim Ekleme veya Kaldırma
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
ms.openlocfilehash: e045be7ea9407bc379b0c22282fcd2184ff5db51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182295"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Nasıl yapılır: Windows Forms ImageList Bileşeni ile Resim Ekleme veya Kaldırma
Windows Forms <xref:System.Windows.Forms.ImageList> bileşeni genellikle bir denetimle ilişkilendirilmeden önce resimlerle doldurulur. Ancak, görüntü listesini bir denetimle ilişkilendirdikten sonra resim ekleyebilir ve kaldırabilirsiniz.  
  
> [!NOTE]
> Görüntüleri kaldırdığınızda, ilişkili <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> denetimlerin özelliğinin hala geçerli olduğunu doğrulayın.  
  
### <a name="to-add-images-programmatically"></a>Programlı görüntü eklemek için  
  
- Resim <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> listesinin <xref:System.Windows.Forms.ImageList.Images%2A> özelliğinin yöntemini kullanın.  
  
     Aşağıdaki kod örneğinde, görüntünün konumu için ayarlanan yol **Belgelerim** klasörüdür. Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içereceğini varsayabileceğiniziçin bu konum kullanılır. Bu konumu nseçilmesi, en az sistem erişim düzeyine sahip kullanıcıların uygulamayı daha güvenli bir şekilde çalıştırmalarını da sağlar. Aşağıdaki kod örneği, zaten eklemiş <xref:System.Windows.Forms.ImageList> bir denetime sahip bir formun uzun olması gerekir.  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>Önemli bir değere sahip görüntüler eklemek için.  
  
- Önemli bir <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> değer alan resim listesinin <xref:System.Windows.Forms.ImageList.Images%2A> özelliğinin yöntemlerinden birini kullanın.  
  
     Aşağıdaki kod örneğinde, görüntünün konumu için ayarlanan yol **Belgelerim** klasörüdür. Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içereceğini varsayabileceğiniziçin bu konum kullanılır. Bu konumu nseçilmesi, en az sistem erişim düzeyine sahip kullanıcıların uygulamayı daha güvenli bir şekilde çalıştırmalarını da sağlar. Aşağıdaki kod örneği, zaten eklemiş <xref:System.Windows.Forms.ImageList> bir denetime sahip bir formun uzun olması gerekir.  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>Tüm görüntüleri programlı olarak kaldırmak için  
  
- Tek <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> bir görüntüyü kaldırmak için yöntemi kullanma  
  
     ,-veya-  
  
     Görüntü <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> listesindeki tüm görüntüleri temizlemek için yöntemi kullanın.  
  
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
  
### <a name="to-remove-images-by-key"></a>Görüntüleri anahtarla kaldırmak için  
  
- Tek <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> bir görüntüyü anahtarıyla kaldırmak için yöntemi kullanın.  
  
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
- [Resimler, Bit Eşlemler ve Meta Dosyaları](../advanced/images-bitmaps-and-metafiles.md)

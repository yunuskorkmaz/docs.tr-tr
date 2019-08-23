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
ms.openlocfilehash: 430b7f573b115c21b9e2fa87f0ace74205717285
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925115"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Nasıl yapılır: Windows Forms ImageList Bileşeni ile Resim Ekleme veya Kaldırma
Windows Forms <xref:System.Windows.Forms.ImageList> bileşen, genellikle bir denetimle ilişkilendirilmeden önce görüntülerle doldurulur. Ancak, görüntü listesini bir denetimle ilişkilendirdikten sonra görüntüler ekleyebilir ve kaldırabilirsiniz.  
  
> [!NOTE]
> Görüntüleri kaldırdığınızda, ilişkili denetimlerin <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> özelliğinin hala geçerli olduğunu doğrulayın.  
  
### <a name="to-add-images-programmatically"></a>Görüntüleri programlı olarak eklemek için  
  
- <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> Görüntü listesinin<xref:System.Windows.Forms.ImageList.Images%2A> özelliğinin yöntemini kullanın.  
  
     Aşağıdaki kod örneğinde, görüntü konumu için ayarlanan yol Belgelerim klasörüdür. Bu konum, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içerdiğini varsaydığı için kullanılır. Bu konumun belirlenmesi, en az sistem erişim düzeylerine sahip olan kullanıcıların uygulamayı daha güvenli bir şekilde çalıştırmasını sağlar. Aşağıdaki kod örneği, zaten bir <xref:System.Windows.Forms.ImageList> denetim eklenmiş bir formunuz olmasını gerektirir.  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>Anahtar değeri olan görüntüler eklemek için.  
  
- Anahtar değerini alan görüntü <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> <xref:System.Windows.Forms.ImageList.Images%2A> listesi özelliğinin yöntemlerinden birini kullanın.  
  
     Aşağıdaki kod örneğinde, görüntü konumu için ayarlanan yol Belgelerim klasörüdür. Bu konum, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içerdiğini varsaydığı için kullanılır. Bu konumun belirlenmesi, en az sistem erişim düzeylerine sahip olan kullanıcıların uygulamayı daha güvenli bir şekilde çalıştırmasını sağlar. Aşağıdaki kod örneği, zaten bir <xref:System.Windows.Forms.ImageList> denetim eklenmiş bir formunuz olmasını gerektirir.  
  
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
  
- Tek bir görüntüyü kaldırmak için yönteminikullanın<xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A>  
  
     ,-veya-  
  
     Görüntü listesindeki tüm görüntüleri temizlemek için yönteminikullanın.<xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>  
  
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
  
### <a name="to-remove-images-by-key"></a>Görüntüleri anahtara göre kaldırmak için  
  
- Tek bir görüntüyü anahtarıyla kaldırmak için yönteminikullanın.<xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>  
  
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

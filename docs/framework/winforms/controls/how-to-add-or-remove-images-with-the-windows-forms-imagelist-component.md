---
title: "Nasıl yapılır: Windows Forms ImageList Bileşeni ile Görüntü Ekleme veya Kaldırma"
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
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e09448cb834453a4c8fce4494ab9fbb53eb0dc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Nasıl yapılır: Windows Forms ImageList Bileşeni ile Görüntü Ekleme veya Kaldırma
Windows Forms <xref:System.Windows.Forms.ImageList> denetimi ile ilişkili önce bileşen görüntülerle genellikle doldurulur. Ancak, Ekle ve görüntü listesi denetimi ile ilişkilendirdikten sonra görüntüleri kaldırın.  
  
> [!NOTE]
>  Görüntüleri kaldırdığınızda, doğrulayın <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> ilişkili denetimleri özelliktir hala geçerli.  
  
### <a name="to-add-images-programmatically"></a>Görüntüleri programlı olarak eklemek için  
  
-   Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> görüntü listenin yöntemi <xref:System.Windows.Forms.ImageList.Images%2A> özelliği.  
  
     Aşağıdaki kod örneğinde yolunu ayarlama görüntüsünün konumu için **Belgelerim** klasör. Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü bu konumu kullanılır. Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırın minimum sistem erişim düzeyleri daha fazla olan kullanıcıların sağlar. Aşağıdaki kod örneğinde bir formla sahip olmasını gerektiren bir <xref:System.Windows.Forms.ImageList> denetimi zaten eklendi.  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>Bir anahtar değeri ile görüntüleri eklemek için.  
  
-   Aşağıdakilerden birini kullanın <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> görüntü listenin yöntemlerinin <xref:System.Windows.Forms.ImageList.Images%2A> bir anahtar değeri alan özelliği.  
  
     Aşağıdaki kod örneğinde yolunu ayarlama görüntüsünün konumu için **Belgelerim** klasör. Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü bu konumu kullanılır. Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırın minimum sistem erişim düzeyleri daha fazla olan kullanıcıların sağlar. Aşağıdaki kod örneğinde bir formla sahip olmasını gerektiren bir <xref:System.Windows.Forms.ImageList> denetimi zaten eklendi.  
  
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
  
1.  
  
### <a name="to-remove-all-images-programmatically"></a>Tüm görüntüleri programlı olarak kaldırmak için  
  
-   Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> tek bir görüntü kaldırmak için yöntemi  
  
     , - veya -  
  
     Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> görüntü listesindeki tüm görüntülerini temizlemek için yöntem.  
  
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
  
### <a name="to-remove-images-by-key"></a>Anahtara göre görüntüleri kaldırmak için  
  
-   Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> anahtara göre tek bir görüntü kaldırmak için yöntem.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ImageList Bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 [ImageList Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)  
 [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)

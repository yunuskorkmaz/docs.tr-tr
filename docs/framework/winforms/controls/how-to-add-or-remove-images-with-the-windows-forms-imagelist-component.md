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
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="2c54b-102">Nasıl yapılır: Windows Forms ImageList Bileşeni ile Resim Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="2c54b-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="2c54b-103">Windows Forms <xref:System.Windows.Forms.ImageList> bileşeni genellikle bir denetimle ilişkilendirilmeden önce resimlerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="2c54b-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="2c54b-104">Ancak, görüntü listesini bir denetimle ilişkilendirdikten sonra resim ekleyebilir ve kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c54b-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c54b-105">Görüntüleri kaldırdığınızda, ilişkili <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> denetimlerin özelliğinin hala geçerli olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="2c54b-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="2c54b-106">Programlı görüntü eklemek için</span><span class="sxs-lookup"><span data-stu-id="2c54b-106">To add images programmatically</span></span>  
  
- <span data-ttu-id="2c54b-107">Resim <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> listesinin <xref:System.Windows.Forms.ImageList.Images%2A> özelliğinin yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c54b-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="2c54b-108">Aşağıdaki kod örneğinde, görüntünün konumu için ayarlanan yol **Belgelerim** klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="2c54b-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="2c54b-109">Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içereceğini varsayabileceğiniziçin bu konum kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c54b-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="2c54b-110">Bu konumu nseçilmesi, en az sistem erişim düzeyine sahip kullanıcıların uygulamayı daha güvenli bir şekilde çalıştırmalarını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c54b-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="2c54b-111">Aşağıdaki kod örneği, zaten eklemiş <xref:System.Windows.Forms.ImageList> bir denetime sahip bir formun uzun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c54b-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="2c54b-112">Önemli bir değere sahip görüntüler eklemek için.</span><span class="sxs-lookup"><span data-stu-id="2c54b-112">To add images with a key value.</span></span>  
  
- <span data-ttu-id="2c54b-113">Önemli bir <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> değer alan resim listesinin <xref:System.Windows.Forms.ImageList.Images%2A> özelliğinin yöntemlerinden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c54b-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="2c54b-114">Aşağıdaki kod örneğinde, görüntünün konumu için ayarlanan yol **Belgelerim** klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="2c54b-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="2c54b-115">Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içereceğini varsayabileceğiniziçin bu konum kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c54b-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="2c54b-116">Bu konumu nseçilmesi, en az sistem erişim düzeyine sahip kullanıcıların uygulamayı daha güvenli bir şekilde çalıştırmalarını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c54b-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="2c54b-117">Aşağıdaki kod örneği, zaten eklemiş <xref:System.Windows.Forms.ImageList> bir denetime sahip bir formun uzun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c54b-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="2c54b-118">Tüm görüntüleri programlı olarak kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="2c54b-118">To remove all images programmatically</span></span>  
  
- <span data-ttu-id="2c54b-119">Tek <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> bir görüntüyü kaldırmak için yöntemi kullanma</span><span class="sxs-lookup"><span data-stu-id="2c54b-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="2c54b-120">,-veya-</span><span class="sxs-lookup"><span data-stu-id="2c54b-120">,-or-</span></span>  
  
     <span data-ttu-id="2c54b-121">Görüntü <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> listesindeki tüm görüntüleri temizlemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c54b-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="2c54b-122">Görüntüleri anahtarla kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="2c54b-122">To remove images by key</span></span>  
  
- <span data-ttu-id="2c54b-123">Tek <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> bir görüntüyü anahtarıyla kaldırmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c54b-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c54b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c54b-124">See also</span></span>

- [<span data-ttu-id="2c54b-125">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="2c54b-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="2c54b-126">ImageList Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2c54b-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="2c54b-127">Resimler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="2c54b-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)

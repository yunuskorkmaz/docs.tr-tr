---
title: 'Nasıl yapılır: Windows Forms ImageList bileşeni ile görüntüleri eklemek veya kaldırmak'
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
ms.openlocfilehash: a81cf11ea5ca405e2013b7c7375a863aeb1f110f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609622"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="3440c-102">Nasıl yapılır: Windows Forms ImageList bileşeni ile görüntüleri eklemek veya kaldırmak</span><span class="sxs-lookup"><span data-stu-id="3440c-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="3440c-103">Windows Forms <xref:System.Windows.Forms.ImageList> bir denetimle ilişkili önce bileşeni ile görüntü genellikle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="3440c-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="3440c-104">Ancak, ekleyin ve görüntü listesi denetimi ile ilişkilendirdikten sonra görüntüleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3440c-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3440c-105">Görüntüleri kaldırdığınızda doğrulayın <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> ilişkili herhangi bir denetim özelliği hala geçerli.</span><span class="sxs-lookup"><span data-stu-id="3440c-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="3440c-106">Görüntüleri programsal olarak eklemek için</span><span class="sxs-lookup"><span data-stu-id="3440c-106">To add images programmatically</span></span>  
  
-   <span data-ttu-id="3440c-107">Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> görüntü listenin yöntemi <xref:System.Windows.Forms.ImageList.Images%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="3440c-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="3440c-108">Aşağıdaki kod örneğinde yolunu ayarlamak için görüntü konumunu **Belgelerim** klasör.</span><span class="sxs-lookup"><span data-stu-id="3440c-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="3440c-109">Bu konum, Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3440c-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="3440c-110">Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri daha fazla kullanıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3440c-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="3440c-111">Aşağıdaki kod örneği, bir form olmasını gerektirir bir <xref:System.Windows.Forms.ImageList> denetim zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="3440c-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="3440c-112">Bir anahtar değeri ile görüntü eklemek için.</span><span class="sxs-lookup"><span data-stu-id="3440c-112">To add images with a key value.</span></span>  
  
-   <span data-ttu-id="3440c-113">Birini <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> görüntü listenin yöntemlerinin <xref:System.Windows.Forms.ImageList.Images%2A> bir anahtar değeri alan özelliği.</span><span class="sxs-lookup"><span data-stu-id="3440c-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="3440c-114">Aşağıdaki kod örneğinde yolunu ayarlamak için görüntü konumunu **Belgelerim** klasör.</span><span class="sxs-lookup"><span data-stu-id="3440c-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="3440c-115">Bu konum, Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3440c-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="3440c-116">Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri daha fazla kullanıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3440c-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="3440c-117">Aşağıdaki kod örneği, bir form olmasını gerektirir bir <xref:System.Windows.Forms.ImageList> denetim zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="3440c-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="3440c-118">Tüm görüntüleri programlı bir şekilde kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="3440c-118">To remove all images programmatically</span></span>  
  
-   <span data-ttu-id="3440c-119">Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> tek bir görüntü kaldırmak için yöntemi</span><span class="sxs-lookup"><span data-stu-id="3440c-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="3440c-120">, - veya -</span><span class="sxs-lookup"><span data-stu-id="3440c-120">,-or-</span></span>  
  
     <span data-ttu-id="3440c-121">Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> görüntü listesi'ndaki tüm görüntüler temizlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3440c-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="3440c-122">Anahtara göre görüntülerini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="3440c-122">To remove images by key</span></span>  
  
-   <span data-ttu-id="3440c-123">Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> anahtara göre tek bir görüntü kaldırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3440c-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="3440c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3440c-124">See also</span></span>
- [<span data-ttu-id="3440c-125">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="3440c-125">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
- [<span data-ttu-id="3440c-126">ImageList Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3440c-126">ImageList Component Overview</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="3440c-127">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="3440c-127">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)

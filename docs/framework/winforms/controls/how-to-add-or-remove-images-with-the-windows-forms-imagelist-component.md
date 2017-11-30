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
ms.openlocfilehash: ce13ba3413c13ced7ff9a967e23d87622309feb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="22c1b-102">Nasıl yapılır: Windows Forms ImageList Bileşeni ile Görüntü Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="22c1b-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="22c1b-103">Windows Forms <xref:System.Windows.Forms.ImageList> denetimi ile ilişkili önce bileşen görüntülerle genellikle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="22c1b-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="22c1b-104">Ancak, Ekle ve görüntü listesi denetimi ile ilişkilendirdikten sonra görüntüleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="22c1b-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22c1b-105">Görüntüleri kaldırdığınızda, doğrulayın <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> ilişkili denetimleri özelliktir hala geçerli.</span><span class="sxs-lookup"><span data-stu-id="22c1b-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="22c1b-106">Görüntüleri programlı olarak eklemek için</span><span class="sxs-lookup"><span data-stu-id="22c1b-106">To add images programmatically</span></span>  
  
-   <span data-ttu-id="22c1b-107">Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> görüntü listenin yöntemi <xref:System.Windows.Forms.ImageList.Images%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="22c1b-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="22c1b-108">Aşağıdaki kod örneğinde yolunu ayarlama görüntüsünün konumu için **Belgelerim** klasör.</span><span class="sxs-lookup"><span data-stu-id="22c1b-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="22c1b-109">Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü bu konumu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22c1b-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="22c1b-110">Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırın minimum sistem erişim düzeyleri daha fazla olan kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="22c1b-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="22c1b-111">Aşağıdaki kod örneğinde bir formla sahip olmasını gerektiren bir <xref:System.Windows.Forms.ImageList> denetimi zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="22c1b-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="22c1b-112">Bir anahtar değeri ile görüntüleri eklemek için.</span><span class="sxs-lookup"><span data-stu-id="22c1b-112">To add images with a key value.</span></span>  
  
-   <span data-ttu-id="22c1b-113">Aşağıdakilerden birini kullanın <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> görüntü listenin yöntemlerinin <xref:System.Windows.Forms.ImageList.Images%2A> bir anahtar değeri alan özelliği.</span><span class="sxs-lookup"><span data-stu-id="22c1b-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="22c1b-114">Aşağıdaki kod örneğinde yolunu ayarlama görüntüsünün konumu için **Belgelerim** klasör.</span><span class="sxs-lookup"><span data-stu-id="22c1b-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="22c1b-115">Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü bu konumu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22c1b-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="22c1b-116">Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırın minimum sistem erişim düzeyleri daha fazla olan kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="22c1b-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="22c1b-117">Aşağıdaki kod örneğinde bir formla sahip olmasını gerektiren bir <xref:System.Windows.Forms.ImageList> denetimi zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="22c1b-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="22c1b-118">Tüm görüntüleri programlı olarak kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="22c1b-118">To remove all images programmatically</span></span>  
  
-   <span data-ttu-id="22c1b-119">Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> tek bir görüntü kaldırmak için yöntemi</span><span class="sxs-lookup"><span data-stu-id="22c1b-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="22c1b-120">, - veya -</span><span class="sxs-lookup"><span data-stu-id="22c1b-120">,-or-</span></span>  
  
     <span data-ttu-id="22c1b-121">Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> görüntü listesindeki tüm görüntülerini temizlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="22c1b-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="22c1b-122">Anahtara göre görüntüleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="22c1b-122">To remove images by key</span></span>  
  
-   <span data-ttu-id="22c1b-123">Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> anahtara göre tek bir görüntü kaldırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="22c1b-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="22c1b-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22c1b-124">See Also</span></span>  
 [<span data-ttu-id="22c1b-125">ImageList bileşeni</span><span class="sxs-lookup"><span data-stu-id="22c1b-125">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 [<span data-ttu-id="22c1b-126">ImageList bileşenine genel bakış</span><span class="sxs-lookup"><span data-stu-id="22c1b-126">ImageList Component Overview</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)  
 [<span data-ttu-id="22c1b-127">Resimler, bit eşlemler ve meta dosyaları</span><span class="sxs-lookup"><span data-stu-id="22c1b-127">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)

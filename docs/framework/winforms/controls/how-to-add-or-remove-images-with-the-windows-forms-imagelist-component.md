---
title: ImageList bileşeni ile görüntü ekleme veya kaldırma
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
ms.openlocfilehash: f531003377395bf219775e5ddb48ceb0822ff0ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741507"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="9892d-102">Nasıl yapılır: Windows Forms ImageList Bileşeni ile Resim Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="9892d-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="9892d-103">Windows Forms <xref:System.Windows.Forms.ImageList> bileşeni, genellikle bir denetimle ilişkilendirilmeden önce görüntülerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="9892d-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="9892d-104">Ancak, görüntü listesini bir denetimle ilişkilendirdikten sonra görüntüler ekleyebilir ve kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9892d-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9892d-105">Görüntüleri kaldırdığınızda, ilişkili denetimlerin <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> özelliğinin hala geçerli olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="9892d-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="9892d-106">Görüntüleri programlı olarak eklemek için</span><span class="sxs-lookup"><span data-stu-id="9892d-106">To add images programmatically</span></span>  
  
- <span data-ttu-id="9892d-107">Görüntü listesinin <xref:System.Windows.Forms.ImageList.Images%2A> özelliğinin <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9892d-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="9892d-108">Aşağıdaki kod örneğinde, görüntü konumu için ayarlanan yol **Belgelerim klasörüdür.**</span><span class="sxs-lookup"><span data-stu-id="9892d-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="9892d-109">Bu konum, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içerdiğini varsaydığı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9892d-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="9892d-110">Bu konumun belirlenmesi, en az sistem erişim düzeylerine sahip olan kullanıcıların uygulamayı daha güvenli bir şekilde çalıştırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9892d-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="9892d-111">Aşağıdaki kod örneği, zaten <xref:System.Windows.Forms.ImageList> denetimi eklenmiş bir formunuz olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9892d-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="9892d-112">Anahtar değeri olan görüntüler eklemek için.</span><span class="sxs-lookup"><span data-stu-id="9892d-112">To add images with a key value.</span></span>  
  
- <span data-ttu-id="9892d-113">Yansıma listesinin <xref:System.Windows.Forms.ImageList.Images%2A> özelliğinin bir anahtar değeri alan <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> yöntemlerinden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9892d-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="9892d-114">Aşağıdaki kod örneğinde, görüntü konumu için ayarlanan yol **Belgelerim klasörüdür.**</span><span class="sxs-lookup"><span data-stu-id="9892d-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="9892d-115">Bu konum, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içerdiğini varsaydığı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9892d-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="9892d-116">Bu konumun belirlenmesi, en az sistem erişim düzeylerine sahip olan kullanıcıların uygulamayı daha güvenli bir şekilde çalıştırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9892d-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="9892d-117">Aşağıdaki kod örneği, zaten <xref:System.Windows.Forms.ImageList> denetimi eklenmiş bir formunuz olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9892d-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="9892d-118">Tüm görüntüleri programlı olarak kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="9892d-118">To remove all images programmatically</span></span>  
  
- <span data-ttu-id="9892d-119">Tek bir görüntüyü kaldırmak için <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> yöntemini kullanma</span><span class="sxs-lookup"><span data-stu-id="9892d-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="9892d-120">,-veya-</span><span class="sxs-lookup"><span data-stu-id="9892d-120">,-or-</span></span>  
  
     <span data-ttu-id="9892d-121">Görüntü listesindeki tüm görüntüleri temizlemek için <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9892d-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="9892d-122">Görüntüleri anahtara göre kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="9892d-122">To remove images by key</span></span>  
  
- <span data-ttu-id="9892d-123">Tek bir görüntüyü anahtarıyla kaldırmak için <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9892d-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="9892d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9892d-124">See also</span></span>

- [<span data-ttu-id="9892d-125">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="9892d-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="9892d-126">ImageList Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9892d-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="9892d-127">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="9892d-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)

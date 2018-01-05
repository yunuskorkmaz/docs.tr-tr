---
title: "Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme (Windows Formları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ca3e3eef1aa9e7414d3c279de5943585703bf9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="da7be-102">Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme (Windows Formları)</span><span class="sxs-lookup"><span data-stu-id="da7be-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>
<span data-ttu-id="da7be-103">Windows Forms ile <xref:System.Windows.Forms.PictureBox> denetim, yüklemek ve bir resim, ayarlayarak tasarım zamanında bir formda görüntülemek <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği için geçerli bir resim.</span><span class="sxs-lookup"><span data-stu-id="da7be-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="da7be-104">Aşağıdaki tabloda, kabul edilebilir dosya türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da7be-104">The following table shows the acceptable file types.</span></span>  
  
|<span data-ttu-id="da7be-105">Tür</span><span class="sxs-lookup"><span data-stu-id="da7be-105">Type</span></span>|<span data-ttu-id="da7be-106">Dosya adı uzantısı</span><span class="sxs-lookup"><span data-stu-id="da7be-106">File name extension</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="da7be-107">Bit eşlem</span><span class="sxs-lookup"><span data-stu-id="da7be-107">Bitmap</span></span>|<span data-ttu-id="da7be-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="da7be-108">.bmp</span></span>|  
|<span data-ttu-id="da7be-109">Simge</span><span class="sxs-lookup"><span data-stu-id="da7be-109">Icon</span></span>|<span data-ttu-id="da7be-110">.ico</span><span class="sxs-lookup"><span data-stu-id="da7be-110">.ico</span></span>|  
|<span data-ttu-id="da7be-111">GIF</span><span class="sxs-lookup"><span data-stu-id="da7be-111">GIF</span></span>|<span data-ttu-id="da7be-112">.gif</span><span class="sxs-lookup"><span data-stu-id="da7be-112">.gif</span></span>|  
|<span data-ttu-id="da7be-113">Meta dosyası</span><span class="sxs-lookup"><span data-stu-id="da7be-113">Metafile</span></span>|<span data-ttu-id="da7be-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="da7be-114">.wmf</span></span>|  
|<span data-ttu-id="da7be-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="da7be-115">JPEG</span></span>|<span data-ttu-id="da7be-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="da7be-116">.jpg</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="da7be-117">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="da7be-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="da7be-118">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="da7be-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="da7be-119">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="da7be-119">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="da7be-120">Tasarım zamanında resim görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="da7be-120">To display a picture at design time</span></span>  
  
1.  <span data-ttu-id="da7be-121">Çizim bir <xref:System.Windows.Forms.PictureBox> bir form üzerinde denetim.</span><span class="sxs-lookup"><span data-stu-id="da7be-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="da7be-122">Özellikler penceresini üzerinde seçin <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği sonra görüntülemek için üç nokta düğmesini tıklatın **açık** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="da7be-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>  
  
3.  <span data-ttu-id="da7be-123">Belirli bir dosya türü için (örneğin, .gif dosyaları) arıyorsanız seçin **dosya türü** kutusu.</span><span class="sxs-lookup"><span data-stu-id="da7be-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>  
  
4.  <span data-ttu-id="da7be-124">Görüntülemek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="da7be-124">Select the file you want to display.</span></span>  
  
### <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="da7be-125">Tasarım zamanında resmin temizlemek için</span><span class="sxs-lookup"><span data-stu-id="da7be-125">To clear the picture at design time</span></span>  
  
1.  <span data-ttu-id="da7be-126">Üzerinde **özellikleri** penceresinde, seçin <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği ve sağ görüntü nesnesinin adını solunda görüntülenen küçük küçük resim.</span><span class="sxs-lookup"><span data-stu-id="da7be-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="da7be-127">Seçin **sıfırlama**.</span><span class="sxs-lookup"><span data-stu-id="da7be-127">Choose **Reset**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da7be-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da7be-128">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 [<span data-ttu-id="da7be-129">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="da7be-129">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="da7be-130">Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="da7be-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [<span data-ttu-id="da7be-131">Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="da7be-131">How to: Set Pictures at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [<span data-ttu-id="da7be-132">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="da7be-132">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)

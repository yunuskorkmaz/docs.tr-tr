---
title: 'Nasıl yapılır: (Windows Forms) tasarımcıyı kullanarak resim yükleme'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 5aa8ff1efa045d52382cc5c24a0cae1f0f1bb510
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127146"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="7ef73-102">Nasıl yapılır: (Windows Forms) tasarımcıyı kullanarak resim yükleme</span><span class="sxs-lookup"><span data-stu-id="7ef73-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>
<span data-ttu-id="7ef73-103">Windows Forms ile <xref:System.Windows.Forms.PictureBox> denetimi, yüklemek ve bir resim, ayarlayarak tasarım zamanında bir formda görüntülemek <xref:System.Windows.Forms.PictureBox.Image%2A> geçerli bir resim özelliği.</span><span class="sxs-lookup"><span data-stu-id="7ef73-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="7ef73-104">Aşağıdaki tabloda, kabul edilebilir dosya türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7ef73-104">The following table shows the acceptable file types.</span></span>  
  
|<span data-ttu-id="7ef73-105">Tür</span><span class="sxs-lookup"><span data-stu-id="7ef73-105">Type</span></span>|<span data-ttu-id="7ef73-106">Dosya adı uzantısı</span><span class="sxs-lookup"><span data-stu-id="7ef73-106">File name extension</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="7ef73-107">Bit eşlem</span><span class="sxs-lookup"><span data-stu-id="7ef73-107">Bitmap</span></span>|<span data-ttu-id="7ef73-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="7ef73-108">.bmp</span></span>|  
|<span data-ttu-id="7ef73-109">Simge</span><span class="sxs-lookup"><span data-stu-id="7ef73-109">Icon</span></span>|<span data-ttu-id="7ef73-110">.ico</span><span class="sxs-lookup"><span data-stu-id="7ef73-110">.ico</span></span>|  
|<span data-ttu-id="7ef73-111">GIF</span><span class="sxs-lookup"><span data-stu-id="7ef73-111">GIF</span></span>|<span data-ttu-id="7ef73-112">.gif</span><span class="sxs-lookup"><span data-stu-id="7ef73-112">.gif</span></span>|  
|<span data-ttu-id="7ef73-113">Meta dosyası</span><span class="sxs-lookup"><span data-stu-id="7ef73-113">Metafile</span></span>|<span data-ttu-id="7ef73-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="7ef73-114">.wmf</span></span>|  
|<span data-ttu-id="7ef73-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="7ef73-115">JPEG</span></span>|<span data-ttu-id="7ef73-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="7ef73-116">.jpg</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="7ef73-117">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7ef73-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7ef73-118">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7ef73-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7ef73-119">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7ef73-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="7ef73-120">Tasarım zamanında bir resim görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="7ef73-120">To display a picture at design time</span></span>  
  
1.  <span data-ttu-id="7ef73-121">Çizim bir <xref:System.Windows.Forms.PictureBox> form denetimi.</span><span class="sxs-lookup"><span data-stu-id="7ef73-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="7ef73-122">Özellikler penceresinde seçin <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği, sonra üç nokta düğmesini görüntülemek için tıklatın **açık** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="7ef73-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>  
  
3.  <span data-ttu-id="7ef73-123">Belirli bir dosya türü için (örneğin, .gif dosyaları) arıyorsanız, onu seçip **dosya türü** kutusu.</span><span class="sxs-lookup"><span data-stu-id="7ef73-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>  
  
4.  <span data-ttu-id="7ef73-124">Görüntülemek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="7ef73-124">Select the file you want to display.</span></span>  
  
### <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="7ef73-125">Tasarım zamanında resmi temizlemek için</span><span class="sxs-lookup"><span data-stu-id="7ef73-125">To clear the picture at design time</span></span>  
  
1.  <span data-ttu-id="7ef73-126">Üzerinde **özellikleri** penceresinde <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği ve sağ görüntü nesnesinin adını solunda görünür küçük resmine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef73-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="7ef73-127">Seçin **sıfırlama**.</span><span class="sxs-lookup"><span data-stu-id="7ef73-127">Choose **Reset**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ef73-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ef73-128">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="7ef73-129">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7ef73-129">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="7ef73-130">Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="7ef73-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="7ef73-131">Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="7ef73-131">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="7ef73-132">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="7ef73-132">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

---
title: 'Nasıl yapılır: Tasarımcıyı kullanarak resim yükleme (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 1d95d5baafa42c7dea40933ba837b684d90b7b2b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972367"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="8086f-102">Nasıl yapılır: Tasarımcıyı kullanarak resim yükleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8086f-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="8086f-103">Windows Forms <xref:System.Windows.Forms.PictureBox> denetimiyle, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği geçerli bir resim olarak ayarlayarak tasarım zamanında form üzerinde bir resim yükleyebilir ve görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8086f-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="8086f-104">Aşağıdaki tabloda, kabul edilebilir dosya türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8086f-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="8086f-105">Tür</span><span class="sxs-lookup"><span data-stu-id="8086f-105">Type</span></span>|<span data-ttu-id="8086f-106">Dosya adı uzantısı</span><span class="sxs-lookup"><span data-stu-id="8086f-106">File name extension</span></span>|
|----------|-------------------------|
|<span data-ttu-id="8086f-107">Biteş</span><span class="sxs-lookup"><span data-stu-id="8086f-107">Bitmap</span></span>|<span data-ttu-id="8086f-108">. bmp</span><span class="sxs-lookup"><span data-stu-id="8086f-108">.bmp</span></span>|
|<span data-ttu-id="8086f-109">Simge</span><span class="sxs-lookup"><span data-stu-id="8086f-109">Icon</span></span>|<span data-ttu-id="8086f-110">. ico</span><span class="sxs-lookup"><span data-stu-id="8086f-110">.ico</span></span>|
|<span data-ttu-id="8086f-111">GIF</span><span class="sxs-lookup"><span data-stu-id="8086f-111">GIF</span></span>|<span data-ttu-id="8086f-112">Resimler</span><span class="sxs-lookup"><span data-stu-id="8086f-112">.gif</span></span>|
|<span data-ttu-id="8086f-113">Dosyasına</span><span class="sxs-lookup"><span data-stu-id="8086f-113">Metafile</span></span>|<span data-ttu-id="8086f-114">. wmf</span><span class="sxs-lookup"><span data-stu-id="8086f-114">.wmf</span></span>|
|<span data-ttu-id="8086f-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="8086f-115">JPEG</span></span>|<span data-ttu-id="8086f-116">. jpg</span><span class="sxs-lookup"><span data-stu-id="8086f-116">.jpg</span></span>|

> [!NOTE]
>  <span data-ttu-id="8086f-117">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="8086f-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8086f-118">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="8086f-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8086f-119">Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="8086f-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="8086f-120">Tasarım zamanında resim görüntüleme</span><span class="sxs-lookup"><span data-stu-id="8086f-120">To display a picture at design time</span></span>

1. <span data-ttu-id="8086f-121">Form üzerinde <xref:System.Windows.Forms.PictureBox> bir denetim çizin.</span><span class="sxs-lookup"><span data-stu-id="8086f-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="8086f-122">Özellikler penceresi, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliğini seçin ve ardından **Aç** iletişim kutusunu göstermek için üç nokta düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8086f-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="8086f-123">Belirli bir dosya türünü arıyorsanız (örneğin,. gif dosyaları), bu **tür dosyalar** kutusunda seçin.</span><span class="sxs-lookup"><span data-stu-id="8086f-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="8086f-124">Göstermek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="8086f-124">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="8086f-125">Tasarım zamanında resmi temizlemek için</span><span class="sxs-lookup"><span data-stu-id="8086f-125">To clear the picture at design time</span></span>

1. <span data-ttu-id="8086f-126">**Özellikler** penceresinde, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği seçin ve görüntü nesnesinin adının solunda görünen küçük küçük resim resmine sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8086f-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="8086f-127">**Sıfırla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="8086f-127">Choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8086f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8086f-128">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="8086f-129">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8086f-129">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="8086f-130">Nasıl yapılır: Çalışma zamanında bir resmin boyutunu veya yerleşimini değiştirme</span><span class="sxs-lookup"><span data-stu-id="8086f-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="8086f-131">Nasıl yapılır: Çalışma zamanında resimleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="8086f-131">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="8086f-132">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="8086f-132">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

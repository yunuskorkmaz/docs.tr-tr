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
ms.openlocfilehash: 818bc63b5b3bea6c73804f716a72ba3cd1a62b4c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039689"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="ecd09-102">Nasıl yapılır: Tasarımcıyı kullanarak resim yükleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ecd09-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="ecd09-103">Windows Forms <xref:System.Windows.Forms.PictureBox> denetimiyle, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği geçerli bir resim olarak ayarlayarak tasarım zamanında form üzerinde bir resim yükleyebilir ve görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecd09-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="ecd09-104">Aşağıdaki tabloda, kabul edilebilir dosya türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ecd09-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="ecd09-105">Tür</span><span class="sxs-lookup"><span data-stu-id="ecd09-105">Type</span></span>|<span data-ttu-id="ecd09-106">Dosya adı uzantısı</span><span class="sxs-lookup"><span data-stu-id="ecd09-106">File name extension</span></span>|
|---|---|
|<span data-ttu-id="ecd09-107">Biteş</span><span class="sxs-lookup"><span data-stu-id="ecd09-107">Bitmap</span></span>|<span data-ttu-id="ecd09-108">. bmp</span><span class="sxs-lookup"><span data-stu-id="ecd09-108">.bmp</span></span>|
|<span data-ttu-id="ecd09-109">Simge</span><span class="sxs-lookup"><span data-stu-id="ecd09-109">Icon</span></span>|<span data-ttu-id="ecd09-110">. ico</span><span class="sxs-lookup"><span data-stu-id="ecd09-110">.ico</span></span>|
|<span data-ttu-id="ecd09-111">GIF</span><span class="sxs-lookup"><span data-stu-id="ecd09-111">GIF</span></span>|<span data-ttu-id="ecd09-112">Resimler</span><span class="sxs-lookup"><span data-stu-id="ecd09-112">.gif</span></span>|
|<span data-ttu-id="ecd09-113">Dosyasına</span><span class="sxs-lookup"><span data-stu-id="ecd09-113">Metafile</span></span>|<span data-ttu-id="ecd09-114">. wmf</span><span class="sxs-lookup"><span data-stu-id="ecd09-114">.wmf</span></span>|
|<span data-ttu-id="ecd09-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="ecd09-115">JPEG</span></span>|<span data-ttu-id="ecd09-116">. jpg</span><span class="sxs-lookup"><span data-stu-id="ecd09-116">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="ecd09-117">Tasarım zamanında resim görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ecd09-117">To display a picture at design time</span></span>

1. <span data-ttu-id="ecd09-118">Form üzerinde <xref:System.Windows.Forms.PictureBox> bir denetim çizin.</span><span class="sxs-lookup"><span data-stu-id="ecd09-118">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="ecd09-119">**Özellikler** penceresinde, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği seçin ve ardından **Aç** iletişim kutusunu göstermek için üç nokta düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ecd09-119">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="ecd09-120">Belirli bir dosya türünü arıyorsanız (örneğin,. gif dosyaları), bu **tür dosyalar** kutusunda seçin.</span><span class="sxs-lookup"><span data-stu-id="ecd09-120">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="ecd09-121">Göstermek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="ecd09-121">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="ecd09-122">Tasarım zamanında resmi temizlemek için</span><span class="sxs-lookup"><span data-stu-id="ecd09-122">To clear the picture at design time</span></span>

1. <span data-ttu-id="ecd09-123">**Özellikler** penceresinde, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği seçin.</span><span class="sxs-lookup"><span data-stu-id="ecd09-123">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="ecd09-124">Görüntü nesnesinin adının solunda görüntülenen küçük küçük resim resmine sağ tıklayın ve ardından **Sıfırla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="ecd09-124">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecd09-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecd09-125">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="ecd09-126">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ecd09-126">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="ecd09-127">Nasıl yapılır: Çalışma zamanında bir resmin boyutunu veya yerleşimini değiştirme</span><span class="sxs-lookup"><span data-stu-id="ecd09-127">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="ecd09-128">Nasıl yapılır: Çalışma zamanında resimleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="ecd09-128">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="ecd09-129">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="ecd09-129">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

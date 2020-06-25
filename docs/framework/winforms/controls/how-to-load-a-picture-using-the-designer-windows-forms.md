---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme'
description: Tasarım zamanında bir forma bir resim yüklemek ve göstermek için Windows Forms PictureBox denetimini nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325603"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="fae68-103">Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme (Windows Formları)</span><span class="sxs-lookup"><span data-stu-id="fae68-103">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="fae68-104">Windows Forms <xref:System.Windows.Forms.PictureBox> denetimiyle, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği geçerli bir resim olarak ayarlayarak tasarım zamanında form üzerinde bir resim yükleyebilir ve görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fae68-104">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="fae68-105">Aşağıdaki tabloda, kabul edilebilir dosya türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fae68-105">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="fae68-106">Tür</span><span class="sxs-lookup"><span data-stu-id="fae68-106">Type</span></span>|<span data-ttu-id="fae68-107">Dosya adı uzantısı</span><span class="sxs-lookup"><span data-stu-id="fae68-107">File name extension</span></span>|
|---|---|
|<span data-ttu-id="fae68-108">Biteş</span><span class="sxs-lookup"><span data-stu-id="fae68-108">Bitmap</span></span>|<span data-ttu-id="fae68-109">.bmp</span><span class="sxs-lookup"><span data-stu-id="fae68-109">.bmp</span></span>|
|<span data-ttu-id="fae68-110">Simge</span><span class="sxs-lookup"><span data-stu-id="fae68-110">Icon</span></span>|<span data-ttu-id="fae68-111">. ico</span><span class="sxs-lookup"><span data-stu-id="fae68-111">.ico</span></span>|
|<span data-ttu-id="fae68-112">GIF</span><span class="sxs-lookup"><span data-stu-id="fae68-112">GIF</span></span>|<span data-ttu-id="fae68-113">.gif</span><span class="sxs-lookup"><span data-stu-id="fae68-113">.gif</span></span>|
|<span data-ttu-id="fae68-114">Dosyasına</span><span class="sxs-lookup"><span data-stu-id="fae68-114">Metafile</span></span>|<span data-ttu-id="fae68-115">. wmf</span><span class="sxs-lookup"><span data-stu-id="fae68-115">.wmf</span></span>|
|<span data-ttu-id="fae68-116">JPEG</span><span class="sxs-lookup"><span data-stu-id="fae68-116">JPEG</span></span>|<span data-ttu-id="fae68-117">.jpg</span><span class="sxs-lookup"><span data-stu-id="fae68-117">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="fae68-118">Tasarım zamanında resim görüntüleme</span><span class="sxs-lookup"><span data-stu-id="fae68-118">To display a picture at design time</span></span>

1. <span data-ttu-id="fae68-119"><xref:System.Windows.Forms.PictureBox>Form üzerinde bir denetim çizin.</span><span class="sxs-lookup"><span data-stu-id="fae68-119">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="fae68-120">**Özellikler** penceresinde, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği seçin ve ardından **Aç** iletişim kutusunu göstermek için üç nokta düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="fae68-120">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="fae68-121">Belirli bir dosya türünü arıyorsanız (örneğin,. gif dosyaları), bu **tür dosyalar** kutusunda seçin.</span><span class="sxs-lookup"><span data-stu-id="fae68-121">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="fae68-122">Göstermek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="fae68-122">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="fae68-123">Tasarım zamanında resmi temizlemek için</span><span class="sxs-lookup"><span data-stu-id="fae68-123">To clear the picture at design time</span></span>

1. <span data-ttu-id="fae68-124">**Özellikler** penceresinde, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği seçin.</span><span class="sxs-lookup"><span data-stu-id="fae68-124">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="fae68-125">Görüntü nesnesinin adının solunda görüntülenen küçük küçük resim resmine sağ tıklayın ve ardından **Sıfırla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="fae68-125">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="fae68-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fae68-126">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="fae68-127">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fae68-127">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="fae68-128">Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="fae68-128">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="fae68-129">Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="fae68-129">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="fae68-130">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="fae68-130">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

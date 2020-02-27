---
title: "Nasıl yapılır: Tasarımcı ile ImageList' Görüntüleri Ekleme veya Kaldırma"
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: cdc7b563a0ee4f8779b99b4e9a6786e78f8d500f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628728"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="51c93-102">Nasıl yapılır: Tasarımcı ile ImageList' Görüntüleri Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="51c93-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="51c93-103"><xref:System.Windows.Forms.ImageList> bileşene birçok farklı yolla görüntü ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51c93-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="51c93-104"><xref:System.Windows.Forms.ImageList>ilişkili akıllı etiketi kullanarak görüntüleri çok hızlı bir şekilde ekleyebilir veya <xref:System.Windows.Forms.ImageList>başka birçok özellik ayarlıyorsanız, Özellikler penceresi görüntü eklemeye daha uygun bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51c93-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="51c93-105">Ayrıca, kod kullanarak da görüntü ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51c93-105">You can also add images by using code.</span></span> <span data-ttu-id="51c93-106">Kod içeren görüntüleri ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms ImageList bileşeni Ile görüntü ekleme veya kaldırma](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="51c93-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="51c93-107">Genellikle <xref:System.Windows.Forms.ImageList> bileşenini bir denetimle ilişkilendirilmeden önce görüntülerle doldurursunuz, ancak bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="51c93-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="51c93-108">Özellikler penceresi kullanarak görüntü eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="51c93-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="51c93-109"><xref:System.Windows.Forms.ImageList> bileşeni seçin veya bir form ekleyin.</span><span class="sxs-lookup"><span data-stu-id="51c93-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="51c93-110">Özellikler penceresi, <xref:System.Windows.Forms.ImageList.Images%2A> özelliğinin yanındaki üç nokta düğmesini (Visual Studio 'nun Özellikler penceresi](./media/visual-studio-ellipsis-button.png))![(...) üç nokta düğmesini (...) tıklayın.</span><span class="sxs-lookup"><span data-stu-id="51c93-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="51c93-111">**Görüntü koleksiyonu düzenleyicisinde**, listeden görüntü eklemek veya kaldırmak için **Ekle** veya **Kaldır** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="51c93-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="51c93-112">Akıllı etiketi kullanarak görüntü eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="51c93-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="51c93-113"><xref:System.Windows.Forms.ImageList> bileşeni seçin veya bir form ekleyin.</span><span class="sxs-lookup"><span data-stu-id="51c93-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="51c93-114">Tasarımcı eylemleri glifi (</span><span class="sxs-lookup"><span data-stu-id="51c93-114">Click the designer actions glyph (</span></span>![Küçük siyah ok](./media/designer-actions-glyph.gif)<span data-ttu-id="51c93-116">)</span><span class="sxs-lookup"><span data-stu-id="51c93-116">)</span></span>

3. <span data-ttu-id="51c93-117">**ImageList görevleri** Iletişim kutusunda **görüntüleri seçin**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="51c93-117">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="51c93-118">**Görüntüler koleksiyonu düzenleyicisinde** , listeden görüntü eklemek veya kaldırmak için **Ekle** veya **Kaldır** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="51c93-118">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="51c93-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51c93-119">See also</span></span>

- [<span data-ttu-id="51c93-120">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="51c93-120">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="51c93-121">İzlenecek yol: tasarımcı eylemlerini kullanarak ortak görevleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="51c93-121">Walkthrough: Perform common tasks using designer actions</span></span>](perform-common-tasks-design-actions.md)
- [<span data-ttu-id="51c93-122">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="51c93-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)

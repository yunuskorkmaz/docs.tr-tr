---
title: 'Nasıl yapılır: Tasarımcı ile ImageList Görüntüleri Ekleme veya Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 63692a797ad49f0adc3a0c5b0bfff1aebbc65257
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038275"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="a2351-102">Nasıl yapılır: Tasarımcı ile ImageList Görüntüleri Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="a2351-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="a2351-103">Bir <xref:System.Windows.Forms.ImageList> bileşene birçok farklı yolla görüntü ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2351-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="a2351-104">İle <xref:System.Windows.Forms.ImageList>ilişkili akıllı etiketi kullanarak görüntüleri çok hızlı bir şekilde ekleyebilirsiniz veya <xref:System.Windows.Forms.ImageList>üzerinde birkaç başka özellik ayarlıyorsanız, Özellikler penceresi görüntü eklemeye daha uygun bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2351-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="a2351-105">Ayrıca, kod kullanarak da görüntü ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2351-105">You can also add images by using code.</span></span> <span data-ttu-id="a2351-106">Kod içeren görüntüleri ekleme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms ImageList bileşeniyle](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)görüntü ekleyin veya kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a2351-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="a2351-107">Genellikle <xref:System.Windows.Forms.ImageList> bileşeni bir denetimle ilişkilendirilmeden önce görüntülerle doldurursunuz, ancak bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a2351-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>


### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="a2351-108">Özellikler penceresi kullanarak görüntü eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="a2351-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="a2351-109"><xref:System.Windows.Forms.ImageList> Bileşeni seçin veya bir form ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2351-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="a2351-110">Özellikler penceresi,![ özelliğin<xref:System.Windows.Forms.ImageList.Images%2A> yanındaki üç nokta düğmesini (Visual](./media/visual-studio-ellipsis-button.png)Studio Özellikler penceresi ' ın (...) üç nokta düğmesini (...) tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a2351-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="a2351-111">**Görüntü koleksiyonu düzenleyicisinde**, listeden görüntü eklemek veya kaldırmak için **Ekle** veya **Kaldır** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a2351-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="a2351-112">Akıllı etiketi kullanarak görüntü eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="a2351-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="a2351-113"><xref:System.Windows.Forms.ImageList> Bileşeni seçin veya bir form ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2351-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="a2351-114">Akıllı etiket glifi (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçeneğine tıklayın</span><span class="sxs-lookup"><span data-stu-id="a2351-114">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>

3. <span data-ttu-id="a2351-115">**ImageList görevleri** Iletişim kutusunda **görüntüleri seçin**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a2351-115">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="a2351-116">**Görüntüler koleksiyonu düzenleyicisinde** , listeden görüntü eklemek veya kaldırmak için **Ekle** veya **Kaldır** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a2351-116">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2351-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2351-117">See also</span></span>

- [<span data-ttu-id="a2351-118">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="a2351-118">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="a2351-119">İzlenecek yol: Windows Forms Denetimlerinde akıllı etiketleri kullanarak ortak görevleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="a2351-119">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="a2351-120">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="a2351-120">ImageList Component</span></span>](imagelist-component-windows-forms.md)

---
title: 'Nasıl yapılır: Tasarımcı ile ImageList Görüntüleri Ekleme veya Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 346d7107c9c17c5df06fa0e47f7a35355344f590
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880729"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="66608-102">Nasıl yapılır: Tasarımcı ile ImageList Görüntüleri Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="66608-102">How to: Add or Remove ImageList Images with the Designer</span></span>
<span data-ttu-id="66608-103">Görüntüleri ekleyebileceğiniz bir <xref:System.Windows.Forms.ImageList> bileşen birkaç farklı yol.</span><span class="sxs-lookup"><span data-stu-id="66608-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="66608-104">Akıllı etiket ile ilişkili kullanarak, çok hızlı bir şekilde bir görüntüleri ekleyebilirsiniz <xref:System.Windows.Forms.ImageList>, ya da diğer bazı özellikleri ayarlıyorsanız <xref:System.Windows.Forms.ImageList>, Özellikler penceresinde görüntülerle eklemek daha kullanışlı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66608-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="66608-105">Kod kullanarak, görüntüleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66608-105">You can also add images by using code.</span></span> <span data-ttu-id="66608-106">Kod ile görüntü ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Ekle veya Kaldır görüntülerle Windows Forms ImageList bileşeni](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="66608-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="66608-107">Genellikle, doldurmanız <xref:System.Windows.Forms.ImageList> bileşen görüntülerle önce bir denetimle ilişkilidir, ancak bu zorunlu değildir.</span><span class="sxs-lookup"><span data-stu-id="66608-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66608-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="66608-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="66608-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="66608-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="66608-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="66608-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="66608-111">Ekleme veya Özellikler penceresini kullanarak görüntüleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="66608-111">To add or remove images by using the Properties window</span></span>  
  
1. <span data-ttu-id="66608-112">Seçin <xref:System.Windows.Forms.ImageList> bileşeni veya forma bir tane ekleyin.</span><span class="sxs-lookup"><span data-stu-id="66608-112">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="66608-113">Özellikler penceresinde üç nokta düğmesini (![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/visual-studio-ellipsis-button.png)) yanındaki <xref:System.Windows.Forms.ImageList.Images%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="66608-113">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
3. <span data-ttu-id="66608-114">İçinde **görüntü Koleksiyonu Düzenleyicisi**, tıklayın **Ekle** veya **Kaldır** görüntüleri eklemek veya listeden kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="66608-114">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="66608-115">Akıllı etiket kullanarak görüntüleri eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="66608-115">To add or remove images using the smart tag</span></span>  
  
1. <span data-ttu-id="66608-116">Seçin <xref:System.Windows.Forms.ImageList> bileşeni veya forma bir tane ekleyin.</span><span class="sxs-lookup"><span data-stu-id="66608-116">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2. <span data-ttu-id="66608-117">Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="66608-117">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>  
  
3. <span data-ttu-id="66608-118">İçinde **ImageList görevleri** iletişim kutusunda **seçin görüntüleri**.</span><span class="sxs-lookup"><span data-stu-id="66608-118">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>  
  
4. <span data-ttu-id="66608-119">İçinde **Editor Kolekce Images** tıklayın **Ekle** veya **Kaldır** görüntüleri eklemek veya listeden kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="66608-119">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66608-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66608-120">See also</span></span>

- [<span data-ttu-id="66608-121">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="66608-121">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="66608-122">İzlenecek yol: Üzerinde Windows Forms denetimleri etiketleri akıllı kullanarak ortak görevleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="66608-122">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="66608-123">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="66608-123">ImageList Component</span></span>](imagelist-component-windows-forms.md)

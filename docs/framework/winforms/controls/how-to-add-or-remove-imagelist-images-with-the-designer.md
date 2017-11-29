---
title: "Nasıl yapılır: Tasarımcı ile ImageList' Görüntüleri Ekleme veya Kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71fa29fc36292bb6620ab458785abaabc749c38d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="8bc65-102">Nasıl yapılır: Tasarımcı ile ImageList' Görüntüleri Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="8bc65-102">How to: Add or Remove ImageList Images with the Designer</span></span>
<span data-ttu-id="8bc65-103">Görüntüleri ekleyebilirsiniz bir <xref:System.Windows.Forms.ImageList> bileşen birkaç farklı yolu.</span><span class="sxs-lookup"><span data-stu-id="8bc65-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="8bc65-104">İle ilişkili akıllı etiket kullanarak görüntüleri çok hızlı bir şekilde ekleyebilirsiniz <xref:System.Windows.Forms.ImageList>, ya da diğer bazı özellikleri ayarlıyorsanız <xref:System.Windows.Forms.ImageList>, daha kullanışlı Özellikler penceresini görüntülerle eklemek fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc65-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="8bc65-105">Kod kullanarak görüntüleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc65-105">You can also add images by using code.</span></span> <span data-ttu-id="8bc65-106">Kod görüntülerle ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntüleri ekleme veya kaldırma](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="8bc65-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="8bc65-107">Genellikle, doldurmak <xref:System.Windows.Forms.ImageList> denetimi ile ilişkilidir, ancak bu zorunlu değildir önce görüntülerle bileşen.</span><span class="sxs-lookup"><span data-stu-id="8bc65-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bc65-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="8bc65-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8bc65-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="8bc65-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8bc65-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8bc65-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="8bc65-111">Eklemek veya Özellikler penceresini kullanarak görüntüleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="8bc65-111">To add or remove images by using the Properties window</span></span>  
  
1.  <span data-ttu-id="8bc65-112">Seçin <xref:System.Windows.Forms.ImageList> bileşeni ya da form için bir tane ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bc65-112">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="8bc65-113">Özellikler penceresinde üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.ImageList.Images%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8bc65-113">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
3.  <span data-ttu-id="8bc65-114">İçinde **görüntü Koleksiyonu Düzenleyicisi**, tıklatın **Ekle** veya **kaldırmak** eklemek veya görüntüleri listesinden kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="8bc65-114">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="8bc65-115">Eklemek veya akıllı etiket kullanarak görüntüleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="8bc65-115">To add or remove images using the smart tag</span></span>  
  
1.  <span data-ttu-id="8bc65-116">Seçin <xref:System.Windows.Forms.ImageList> bileşeni ya da form için bir tane ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bc65-116">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="8bc65-117">Akıllı etiket karakteri tıklayın (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="8bc65-117">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>  
  
3.  <span data-ttu-id="8bc65-118">İçinde **ImageList görevleri** iletişim kutusunda **seçin görüntüleri**.</span><span class="sxs-lookup"><span data-stu-id="8bc65-118">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>  
  
4.  <span data-ttu-id="8bc65-119">İçinde **görüntüleri Koleksiyonu Düzenleyicisi** tıklatın **Ekle** veya **kaldırmak** eklemek veya görüntüleri listesinden kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="8bc65-119">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc65-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8bc65-120">See Also</span></span>  
 [<span data-ttu-id="8bc65-121">Resimler, bit eşlemler ve meta dosyaları</span><span class="sxs-lookup"><span data-stu-id="8bc65-121">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="8bc65-122">İzlenecek yol: Windows akıllı etiketleri kullanarak ortak görevleri gerçekleştirme Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="8bc65-122">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 [<span data-ttu-id="8bc65-123">ImageList bileşeni</span><span class="sxs-lookup"><span data-stu-id="8bc65-123">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)

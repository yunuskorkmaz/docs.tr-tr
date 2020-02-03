---
title: TabControl görünümünü değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746616"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="fc962-102">Nasıl yapılır: Windows Forms TabControl'nin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="fc962-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="fc962-103"><xref:System.Windows.Forms.TabControl> özelliklerini ve denetimdeki tek sekmeleri oluşturan <xref:System.Windows.Forms.TabPage> nesnelerini kullanarak Windows Forms sekmelerin görünümünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc962-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="fc962-104">Bu özellikleri ayarlayarak sekmeleri sekmelerde görüntüleyebilir, yatay olarak sekmeler üzerinde dikey olarak görüntüleyebilir, birden çok sekme satırını görüntüleyebilir ve sekmeleri programlı bir şekilde etkinleştirebilir veya devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc962-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="fc962-105">Bir sekmenin etiket bölümünde bir simge göstermek için</span><span class="sxs-lookup"><span data-stu-id="fc962-105">To display an icon on the label part of a tab</span></span>  
  
1. <span data-ttu-id="fc962-106">Forma <xref:System.Windows.Forms.ImageList> denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc962-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2. <span data-ttu-id="fc962-107">Görüntü listesine resim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc962-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="fc962-108">Görüntü listeleri hakkında daha fazla bilgi için bkz. [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntü ekleme veya kaldırma](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="fc962-108">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3. <span data-ttu-id="fc962-109"><xref:System.Windows.Forms.TabControl> <xref:System.Windows.Forms.TabControl.ImageList%2A> özelliğini <xref:System.Windows.Forms.ImageList> denetimine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc962-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4. <span data-ttu-id="fc962-110"><xref:System.Windows.Forms.TabPage> <xref:System.Windows.Forms.TabPage.ImageIndex%2A> özelliğini, listedeki uygun bir görüntünün dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc962-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="fc962-111">Birden çok sekme satırı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fc962-111">To create multiple rows of tabs</span></span>  
  
1. <span data-ttu-id="fc962-112">İstediğiniz sekme sayfası sayısını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc962-112">Add the number of tab pages you want.</span></span>  
  
2. <span data-ttu-id="fc962-113"><xref:System.Windows.Forms.TabControl> <xref:System.Windows.Forms.TabControl.Multiline%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc962-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3. <span data-ttu-id="fc962-114">Sekmeler zaten birden çok satırda görünmezse, <xref:System.Windows.Forms.TabControl> <xref:System.Windows.Forms.Control.Width%2A> özelliğini tüm sekmelerden daha dar olacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc962-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="fc962-115">Denetimin tarafındaki sekmeleri düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="fc962-115">To arrange tabs on the side of the control</span></span>  
  
- <span data-ttu-id="fc962-116"><xref:System.Windows.Forms.TabControl> <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliğini <xref:System.Windows.Forms.TabAlignment.Left> veya <xref:System.Windows.Forms.TabAlignment.Right>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc962-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="fc962-117">Bir sekmedeki tüm denetimleri programlı bir şekilde etkinleştirmek veya devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="fc962-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1. <span data-ttu-id="fc962-118"><xref:System.Windows.Forms.TabPage> <xref:System.Windows.Forms.TabPage.Enabled%2A> özelliğini `true` veya `false`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc962-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="fc962-119">Sekmeleri düğme olarak görüntüleme</span><span class="sxs-lookup"><span data-stu-id="fc962-119">To display tabs as buttons</span></span>  
  
- <span data-ttu-id="fc962-120"><xref:System.Windows.Forms.TabControl> <xref:System.Windows.Forms.TabControl.Appearance%2A> özelliğini <xref:System.Windows.Forms.TabAppearance.Buttons> veya <xref:System.Windows.Forms.TabAppearance.FlatButtons>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc962-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc962-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc962-121">See also</span></span>

- [<span data-ttu-id="fc962-122">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="fc962-122">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="fc962-123">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fc962-123">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="fc962-124">Nasıl yapılır: Sekme Sayfasına Denetim Ekleme</span><span class="sxs-lookup"><span data-stu-id="fc962-124">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="fc962-125">Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="fc962-125">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="fc962-126">Nasıl yapılır: Windows Forms TabControl ile Sekme Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="fc962-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)

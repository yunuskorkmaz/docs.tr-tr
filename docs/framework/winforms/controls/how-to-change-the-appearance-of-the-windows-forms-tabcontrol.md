---
title: "Nasıl yapılır: Windows Forms TabControl'nin Görünüşünü Değiştirme"
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
ms.openlocfilehash: 1ea2208229d790f69e517d55e2de5ee042bdfb03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531046"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="d4415-102">Nasıl yapılır: Windows Forms TabControl'nin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d4415-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="d4415-103">Özelliklerini kullanarak Windows Forms'ta sekmeler görünümünü değiştirebilirsiniz <xref:System.Windows.Forms.TabControl> ve <xref:System.Windows.Forms.TabPage> denetimi tek tek sekmelerinde oluşturan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d4415-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="d4415-104">Bu özellikleri ayarlayarak, görüntüleri sekmelerde görüntüleme, dikey yerine yatay sekmelerini görüntülemek, sekme, birden çok satır görüntüleme ve etkinleştirebilir veya sekmeleri program aracılığıyla devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="d4415-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="d4415-105">Simge bir sekme etiketi parçası görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="d4415-105">To display an icon on the label part of a tab</span></span>  
  
1.  <span data-ttu-id="d4415-106">Ekleme bir <xref:System.Windows.Forms.ImageList> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="d4415-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2.  <span data-ttu-id="d4415-107">Görüntüleri görüntü listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4415-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="d4415-108">Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntüleri ekleme veya kaldırma](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="d4415-108">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3.  <span data-ttu-id="d4415-109">Ayarlama <xref:System.Windows.Forms.TabControl.ImageList%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.ImageList> denetim.</span><span class="sxs-lookup"><span data-stu-id="d4415-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4.  <span data-ttu-id="d4415-110">Ayarlama <xref:System.Windows.Forms.TabPage.ImageIndex%2A> özelliği <xref:System.Windows.Forms.TabPage> listesinde uygun görüntünün dizin.</span><span class="sxs-lookup"><span data-stu-id="d4415-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="d4415-111">Birden çok satır sekmelerinin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d4415-111">To create multiple rows of tabs</span></span>  
  
1.  <span data-ttu-id="d4415-112">Sekme sayfaları istediğiniz sayısı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4415-112">Add the number of tab pages you want.</span></span>  
  
2.  <span data-ttu-id="d4415-113">Ayarlama <xref:System.Windows.Forms.TabControl.Multiline%2A> özelliği <xref:System.Windows.Forms.TabControl> için `true`.</span><span class="sxs-lookup"><span data-stu-id="d4415-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3.  <span data-ttu-id="d4415-114">Sekmeleri birden çok satır gösterilmezse ayarlamak <xref:System.Windows.Forms.Control.Width%2A> özelliği <xref:System.Windows.Forms.TabControl> sekmelerin dar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4415-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="d4415-115">Sekme denetimi yan tarafında düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="d4415-115">To arrange tabs on the side of the control</span></span>  
  
-   <span data-ttu-id="d4415-116">Ayarlama <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.TabAlignment.Left> veya <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="d4415-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="d4415-117">Program aracılığıyla etkinleştirmek veya bir sekmede tüm denetimleri devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="d4415-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1.  <span data-ttu-id="d4415-118">Ayarlama <xref:System.Windows.Forms.TabPage.Enabled%2A> özelliği <xref:System.Windows.Forms.TabPage> için `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="d4415-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="d4415-119">Düğme olarak sekmelerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="d4415-119">To display tabs as buttons</span></span>  
  
-   <span data-ttu-id="d4415-120">Ayarlama <xref:System.Windows.Forms.TabControl.Appearance%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.TabAppearance.Buttons> veya <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="d4415-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4415-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4415-121">See Also</span></span>  
 [<span data-ttu-id="d4415-122">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="d4415-122">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="d4415-123">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4415-123">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="d4415-124">Nasıl yapılır: Sekme Sayfasına Denetim Ekleme</span><span class="sxs-lookup"><span data-stu-id="d4415-124">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="d4415-125">Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="d4415-125">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="d4415-126">Nasıl yapılır: Windows Forms TabControl ile Sekme Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="d4415-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)

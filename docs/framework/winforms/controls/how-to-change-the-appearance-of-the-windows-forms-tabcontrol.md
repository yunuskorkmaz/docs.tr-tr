---
title: "Nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme"
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
ms.openlocfilehash: 1ed062b3991d7738269d30a6ff13cda3c80927c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630326"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="a9348-102">Nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="a9348-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="a9348-103">Özelliklerini kullanarak Windows Forms'da sekme görünümünü değiştirebilirsiniz <xref:System.Windows.Forms.TabControl> ve <xref:System.Windows.Forms.TabPage> ayrı sekmeler denetimi oluşturan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a9348-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="a9348-104">Bu özellikleri ayarlayarak sekmelerinde görüntüler, sekme dikey yerine yatay olarak görüntüler, sekme, birden çok satır görüntüleme ve etkinleştirebilir veya sekmeleri program aracılığıyla devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="a9348-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="a9348-105">Sekmenin etiketi parçası üzerinde bir simge görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="a9348-105">To display an icon on the label part of a tab</span></span>  
  
1.  <span data-ttu-id="a9348-106">Ekleme bir <xref:System.Windows.Forms.ImageList> forma.</span><span class="sxs-lookup"><span data-stu-id="a9348-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2.  <span data-ttu-id="a9348-107">Görüntüleri görüntü listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a9348-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="a9348-108">Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) ve [nasıl yapılır: Ekle veya Kaldır görüntülerle Windows Forms ImageList bileşeni](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="a9348-108">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3.  <span data-ttu-id="a9348-109">Ayarlama <xref:System.Windows.Forms.TabControl.ImageList%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.ImageList> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a9348-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4.  <span data-ttu-id="a9348-110">Ayarlama <xref:System.Windows.Forms.TabPage.ImageIndex%2A> özelliği <xref:System.Windows.Forms.TabPage> dizine listede uygun görüntü.</span><span class="sxs-lookup"><span data-stu-id="a9348-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="a9348-111">Sekmelerin çoklu satırları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a9348-111">To create multiple rows of tabs</span></span>  
  
1.  <span data-ttu-id="a9348-112">Sekme sayfaları, istediğiniz sayıda ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a9348-112">Add the number of tab pages you want.</span></span>  
  
2.  <span data-ttu-id="a9348-113">Ayarlama <xref:System.Windows.Forms.TabControl.Multiline%2A> özelliği <xref:System.Windows.Forms.TabControl> için `true`.</span><span class="sxs-lookup"><span data-stu-id="a9348-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3.  <span data-ttu-id="a9348-114">Sekmeleri birden çok satır içinde gösterilmezse ayarlamak <xref:System.Windows.Forms.Control.Width%2A> özelliği <xref:System.Windows.Forms.TabControl> tüm sekmeler dar olacak.</span><span class="sxs-lookup"><span data-stu-id="a9348-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="a9348-115">Denetim kenarındaki sekmelerin düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="a9348-115">To arrange tabs on the side of the control</span></span>  
  
-   <span data-ttu-id="a9348-116">Ayarlama <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.TabAlignment.Left> veya <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="a9348-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="a9348-117">Program aracılığıyla etkinleştirme veya bir sekme üzerindeki bütün denetimleri devre dışı</span><span class="sxs-lookup"><span data-stu-id="a9348-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1.  <span data-ttu-id="a9348-118">Ayarlama <xref:System.Windows.Forms.TabPage.Enabled%2A> özelliği <xref:System.Windows.Forms.TabPage> için `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="a9348-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="a9348-119">Düğme olarak sekmelerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="a9348-119">To display tabs as buttons</span></span>  
  
-   <span data-ttu-id="a9348-120">Ayarlama <xref:System.Windows.Forms.TabControl.Appearance%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.TabAppearance.Buttons> veya <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="a9348-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9348-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9348-121">See also</span></span>
- [<span data-ttu-id="a9348-122">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="a9348-122">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="a9348-123">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a9348-123">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="a9348-124">Nasıl yapılır: Sekme sayfasına denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="a9348-124">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="a9348-125">Nasıl yapılır: Sekme sayfalarını devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="a9348-125">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)
- [<span data-ttu-id="a9348-126">Nasıl yapılır: Windows Forms TabControl ile sekme ekleyip</span><span class="sxs-lookup"><span data-stu-id="a9348-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)

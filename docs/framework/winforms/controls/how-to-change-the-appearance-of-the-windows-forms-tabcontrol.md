---
title: "Nasıl yapılır: Windows Forms TabControl'nin Görünüşünü Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b244930f0837d3b1d548e0f7a8c77dd80e1ce039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="0e782-102">Nasıl yapılır: Windows Forms TabControl'nin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0e782-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="0e782-103">Özelliklerini kullanarak Windows Forms'ta sekmeler görünümünü değiştirebilirsiniz <xref:System.Windows.Forms.TabControl> ve <xref:System.Windows.Forms.TabPage> denetimi tek tek sekmelerinde oluşturan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0e782-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="0e782-104">Bu özellikleri ayarlayarak, görüntüleri sekmelerde görüntüleme, dikey yerine yatay sekmelerini görüntülemek, sekme, birden çok satır görüntüleme ve etkinleştirebilir veya sekmeleri program aracılığıyla devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="0e782-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="0e782-105">Simge bir sekme etiketi parçası görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="0e782-105">To display an icon on the label part of a tab</span></span>  
  
1.  <span data-ttu-id="0e782-106">Ekleme bir <xref:System.Windows.Forms.ImageList> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="0e782-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2.  <span data-ttu-id="0e782-107">Görüntüleri görüntü listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0e782-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="0e782-108">Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntüleri ekleme veya kaldırma](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="0e782-108">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3.  <span data-ttu-id="0e782-109">Ayarlama <xref:System.Windows.Forms.TabControl.ImageList%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.ImageList> denetim.</span><span class="sxs-lookup"><span data-stu-id="0e782-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4.  <span data-ttu-id="0e782-110">Ayarlama <xref:System.Windows.Forms.TabPage.ImageIndex%2A> özelliği <xref:System.Windows.Forms.TabPage> listesinde uygun görüntünün dizin.</span><span class="sxs-lookup"><span data-stu-id="0e782-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="0e782-111">Birden çok satır sekmelerinin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0e782-111">To create multiple rows of tabs</span></span>  
  
1.  <span data-ttu-id="0e782-112">Sekme sayfaları istediğiniz sayısı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0e782-112">Add the number of tab pages you want.</span></span>  
  
2.  <span data-ttu-id="0e782-113">Ayarlama <xref:System.Windows.Forms.TabControl.Multiline%2A> özelliği <xref:System.Windows.Forms.TabControl> için `true`.</span><span class="sxs-lookup"><span data-stu-id="0e782-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3.  <span data-ttu-id="0e782-114">Sekmeleri birden çok satır gösterilmezse ayarlamak <xref:System.Windows.Forms.Control.Width%2A> özelliği <xref:System.Windows.Forms.TabControl> sekmelerin dar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e782-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="0e782-115">Sekme denetimi yan tarafında düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="0e782-115">To arrange tabs on the side of the control</span></span>  
  
-   <span data-ttu-id="0e782-116">Ayarlama <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.TabAlignment.Left> veya <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="0e782-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="0e782-117">Program aracılığıyla etkinleştirmek veya bir sekmede tüm denetimleri devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="0e782-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1.  <span data-ttu-id="0e782-118">Ayarlama <xref:System.Windows.Forms.TabPage.Enabled%2A> özelliği <xref:System.Windows.Forms.TabPage> için `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="0e782-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="0e782-119">Düğme olarak sekmelerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="0e782-119">To display tabs as buttons</span></span>  
  
-   <span data-ttu-id="0e782-120">Ayarlama <xref:System.Windows.Forms.TabControl.Appearance%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.TabAppearance.Buttons> veya <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="0e782-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e782-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e782-121">See Also</span></span>  
 [<span data-ttu-id="0e782-122">TabControl denetimi</span><span class="sxs-lookup"><span data-stu-id="0e782-122">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="0e782-123">TabControl denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="0e782-123">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="0e782-124">Nasıl yapılır: sekme sayfasına denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="0e782-124">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="0e782-125">Nasıl yapılır: sekme sayfalarını devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="0e782-125">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="0e782-126">Nasıl yapılır: Windows Forms TabControl ile sekme ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="0e782-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)

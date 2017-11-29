---
title: TabControl Denetimi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TabControl control [Windows Forms]
- tab controls
- tab controls [Windows Forms], creating
- multipage dialog boxes
- dialog boxes [Windows Forms], creating multipage
- property pages [Windows Forms], creating
- tab dialog boxes
ms.assetid: 915091af-93ac-4d3d-8283-738dd2d21ea7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fdeb5011e5f44eb45d553045c2f89b97f9e4d100
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="tabcontrol-control-windows-forms"></a><span data-ttu-id="038d3-102">TabControl Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="038d3-102">TabControl Control (Windows Forms)</span></span>
<span data-ttu-id="038d3-103">Windows Forms `TabControl` etiketler, bir dosya dolabı klasörlerde kümesi ya da bir not defteri Bölücü gibi birden fazla sekme görüntüler.</span><span class="sxs-lookup"><span data-stu-id="038d3-103">The Windows Forms `TabControl` displays multiple tabs, like dividers in a notebook or labels in a set of folders in a filing cabinet.</span></span> <span data-ttu-id="038d3-104">Sekmeleri resimleri ve diğer denetimlerin içerebilir.</span><span class="sxs-lookup"><span data-stu-id="038d3-104">The tabs can contain pictures and other controls.</span></span> <span data-ttu-id="038d3-105">Kullanım `TabControl` özellik sayfaları oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="038d3-105">Use the `TabControl` to create property pages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="038d3-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="038d3-106">In This Section</span></span>  
 [<span data-ttu-id="038d3-107">TabControl denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="038d3-107">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="038d3-108">Bu denetimi nedir ve anahtar özellikleri ve özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="038d3-108">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="038d3-109">Nasıl yapılır: sekme sayfasına denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="038d3-109">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 <span data-ttu-id="038d3-110">Sekme sayfaları denetimlerini görüntüleme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="038d3-110">Gives directions for displaying controls on tab pages.</span></span>  
  
 [<span data-ttu-id="038d3-111">Nasıl yapılır: Windows Forms TabControl ile sekme ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="038d3-111">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="038d3-112">Sekmeler ekleme ve tasarımcı veya kod kaldırma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="038d3-112">Gives directions for adding and removing tabs in the designer or in code.</span></span>  
  
 [<span data-ttu-id="038d3-113">Nasıl yapılır: Windows Forms Tabcontrol'nin görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="038d3-113">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="038d3-114">Tek tek sekmeler görünümünü etkileyen özellikleri ayarlamak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="038d3-114">Gives directions for adjusting properties that affect the appearance of individual tabs.</span></span>  
  
 [<span data-ttu-id="038d3-115">Nasıl yapılır: sekme sayfalarını devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="038d3-115">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 <span data-ttu-id="038d3-116">Büyük olasılıkla kullanıcı kimlik bilgilerini temel alarak bir sekme sayfasına erişimi kısıtlamak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="038d3-116">Explains how to restrict access to a tab page, possibly based on user credentials.</span></span>  
  
 <span data-ttu-id="038d3-117">Ayrıca bkz. [nasıl yapılır: ekleme ve kaldırma sekmeleri Windows Formları TabControl kullanarak ile Tasarımcı](http://msdn.microsoft.com/library/ms233654\(v=vs.110\)), [nasıl yapılır: sekme sayfası kullanarak bir Tasarımcı denetim ekleme](http://msdn.microsoft.com/library/ms233668\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="038d3-117">Also see [How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer](http://msdn.microsoft.com/library/ms233654\(v=vs.110\)), [How to: Add a Control to a Tab Page Using the Designer](http://msdn.microsoft.com/library/ms233668\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="038d3-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="038d3-118">Reference</span></span>  
 <span data-ttu-id="038d3-119"><xref:System.Windows.Forms.TabControl>sınıfı</span><span class="sxs-lookup"><span data-stu-id="038d3-119"><xref:System.Windows.Forms.TabControl> class</span></span>  
 <span data-ttu-id="038d3-120">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="038d3-120">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="038d3-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="038d3-121">Related Sections</span></span>  
 [<span data-ttu-id="038d3-122">Windows Forms'ta iletişim kutuları</span><span class="sxs-lookup"><span data-stu-id="038d3-122">Dialog Boxes in Windows Forms</span></span>](../../../../docs/framework/winforms/dialog-boxes-in-windows-forms.md)  
 <span data-ttu-id="038d3-123">Görev listesi genellikle sekmelerini görüntülemek iletişim kutuları için sağlar.</span><span class="sxs-lookup"><span data-stu-id="038d3-123">Provides a list of tasks for dialog boxes, which often display tabs.</span></span>  
  
 [<span data-ttu-id="038d3-124">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="038d3-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="038d3-125">Windows Forms denetimleri, tam bir listesi ile bunların kullanılması hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="038d3-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>

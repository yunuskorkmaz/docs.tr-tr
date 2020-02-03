---
title: TabControl Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- TabControl
helpviewer_keywords:
- TabControl control [Windows Forms], about TabControl control
- tab pages [Windows Forms], about tab pages
- property pages [Windows Forms], Windows Forms
- Windows Forms dialog boxes [Windows Forms], tabs
ms.assetid: 2b4ea784-a39d-463c-81d8-af74ce068476
ms.openlocfilehash: 2668169488b4087673fbf2552650c23cda780642
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742833"
---
# <a name="tabcontrol-control-overview-windows-forms"></a><span data-ttu-id="23c3a-102">TabControl Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="23c3a-102">TabControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="23c3a-103">Windows Forms <xref:System.Windows.Forms.TabControl>, bir not defterindeki bölücüler veya bir dosyalama dolabında bir klasör kümesindeki Etiketler gibi birden çok sekme görüntüler.</span><span class="sxs-lookup"><span data-stu-id="23c3a-103">The Windows Forms <xref:System.Windows.Forms.TabControl> displays multiple tabs, like dividers in a notebook or labels in a set of folders in a filing cabinet.</span></span> <span data-ttu-id="23c3a-104">Sekmeler resimleri ve diğer denetimleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="23c3a-104">The tabs can contain pictures and other controls.</span></span> <span data-ttu-id="23c3a-105">Windows işletim sisteminde Denetim Masası ekran özellikleri gibi birçok yerde görünen birden çok sayfalı iletişim kutusu türünü oluşturmak için Tab denetimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23c3a-105">You can use the tab control to produce the kind of multiple-page dialog box that appears many places in the Windows operating system, such as the Control Panel Display Properties.</span></span> <span data-ttu-id="23c3a-106">Ayrıca <xref:System.Windows.Forms.TabControl>, ilgili özellikler grubunu ayarlamak için kullanılan özellik sayfaları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="23c3a-106">Additionally, the <xref:System.Windows.Forms.TabControl> can be used to create property pages, which are used to set a group of related properties.</span></span>  
  
## <a name="working-with-tabcontrol"></a><span data-ttu-id="23c3a-107">TabControl ile çalışma</span><span class="sxs-lookup"><span data-stu-id="23c3a-107">Working with TabControl</span></span>  
 <span data-ttu-id="23c3a-108"><xref:System.Windows.Forms.TabControl> en önemli özelliği, bireysel sekmeleri içeren <xref:System.Windows.Forms.TabControl.TabPages%2A>.</span><span class="sxs-lookup"><span data-stu-id="23c3a-108">The most important property of the <xref:System.Windows.Forms.TabControl> is <xref:System.Windows.Forms.TabControl.TabPages%2A>, which contains the individual tabs.</span></span> <span data-ttu-id="23c3a-109">Her tek sekme <xref:System.Windows.Forms.TabPage> nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="23c3a-109">Each individual tab is a <xref:System.Windows.Forms.TabPage> object.</span></span> <span data-ttu-id="23c3a-110">Bir sekmeye tıklandığında, bu <xref:System.Windows.Forms.TabPage> nesnesi için <xref:System.Windows.Forms.Control.Click> olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="23c3a-110">When a tab is clicked, it raises the <xref:System.Windows.Forms.Control.Click> event for that <xref:System.Windows.Forms.TabPage> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c3a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23c3a-111">See also</span></span>

- <xref:System.Windows.Forms.TabControl>
- [<span data-ttu-id="23c3a-112">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="23c3a-112">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="23c3a-113">Nasıl yapılır: Windows Forms TabControl’un Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="23c3a-113">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="23c3a-114">Nasıl yapılır: Sekme Sayfasına Denetim Ekleme</span><span class="sxs-lookup"><span data-stu-id="23c3a-114">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="23c3a-115">Nasıl yapılır: Windows Forms TabControl ile Sekme Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="23c3a-115">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="23c3a-116">Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="23c3a-116">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="23c3a-117">Windows Forms'ta İletişim Kutuları</span><span class="sxs-lookup"><span data-stu-id="23c3a-117">Dialog Boxes in Windows Forms</span></span>](../dialog-boxes-in-windows-forms.md)

---
title: "NotifyIcon Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c909537bd4c52a546faeb83c6e9291c4de76d76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="36686-102">NotifyIcon Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="36686-102">NotifyIcon Component Overview (Windows Forms)</span></span>
<span data-ttu-id="36686-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> bileşen arka planda çalışır ve bir kullanıcı gösterme işlemlerin çoğu zaman arabirim simgelerini görüntülemek için genellikle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="36686-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="36686-104">Bir örnek, bir görev durumu bildirim alanı simgesini tıklatarak erişilebilir bir virüsten koruma yazılımı olabilir.</span><span class="sxs-lookup"><span data-stu-id="36686-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>  
  
## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="36686-105">NotifyIcons temel özellikleri</span><span class="sxs-lookup"><span data-stu-id="36686-105">Key Properties of NotifyIcons</span></span>  
 <span data-ttu-id="36686-106">Her <xref:System.Windows.Forms.NotifyIcon> bileşen durum alanında tek bir simge görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36686-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="36686-107">Üç arka plan işlemleri ve her biri için bir simge görüntülemek istediğiniz varsa, üç eklemelisiniz <xref:System.Windows.Forms.NotifyIcon> forma bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="36686-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="36686-108">Anahtar özelliklerini <xref:System.Windows.Forms.NotifyIcon> bileşeni olan <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="36686-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="36686-109"><xref:System.Windows.Forms.NotifyIcon.Icon%2A> Özelliği durum alanında görüntülenen simgesi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="36686-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="36686-110">Görünmesi simge sırayla <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliği ayarlanmalıdır `true`.</span><span class="sxs-lookup"><span data-stu-id="36686-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>  
  
 <span data-ttu-id="36686-111">Kullanıyorsanız [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], büyük bir kitaplığı ile birlikte kullanabileceğiniz standart görüntülerinin erişimi <xref:System.Windows.Forms.NotifyIcon> denetim.</span><span class="sxs-lookup"><span data-stu-id="36686-111">If you are using [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you have access to a large library of standard images that you can use with the <xref:System.Windows.Forms.NotifyIcon> control.</span></span>  
  
## <a name="notifyicons-options"></a><span data-ttu-id="36686-112">NotifyIcons seçenekleri</span><span class="sxs-lookup"><span data-stu-id="36686-112">NotifyIcons Options</span></span>  
 <span data-ttu-id="36686-113">Balon ipuçları, kısayol menüleri ve araç ipuçları ile ilişkilendirebilirsiniz bir <xref:System.Windows.Forms.NotifyIcon> kullanıcı yardımcı olmak için.</span><span class="sxs-lookup"><span data-stu-id="36686-113">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>  
  
 <span data-ttu-id="36686-114">Balon ipuçlarını görüntüleyebilirsiniz bir <xref:System.Windows.Forms.NotifyIcon> çağırarak <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> yöntemi zaman aralığı belirtmek istiyorsanız balon ipucu'nu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="36686-114">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="36686-115">Metin, simge ve balon ucuyla başlığı da belirtebilirsiniz <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> ve <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="36686-115">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="36686-116"><xref:System.Windows.Forms.NotifyIcon>bileşenleri araç ipuçları ve kısayol menüleri ilişkili sahip.</span><span class="sxs-lookup"><span data-stu-id="36686-116"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="36686-117">Daha fazla bilgi için bkz: [ToolTip bileşenine genel bakış](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) ve [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="36686-117">For more information, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36686-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36686-118">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 [<span data-ttu-id="36686-119">NotifyIcon Bileşeni</span><span class="sxs-lookup"><span data-stu-id="36686-119">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)

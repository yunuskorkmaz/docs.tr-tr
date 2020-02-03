---
title: NotifyIcon Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 587bf514db853f1122ed16abc05a195985c5ce8d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742131"
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="ed725-102">NotifyIcon Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ed725-102">NotifyIcon Component Overview (Windows Forms)</span></span>

<span data-ttu-id="ed725-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> bileşeni genellikle arka planda çalışan işlemlere yönelik simgeler görüntülemek için kullanılır ve zaman içinde bir kullanıcı arabirimi göstermez.</span><span class="sxs-lookup"><span data-stu-id="ed725-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="ed725-104">Görev çubuğunun durum bildirimi alanındaki bir simgeye tıklanarak erişilebilen bir virüsten koruma programı örnek olarak yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="ed725-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>

## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="ed725-105">Notifysimgelerinden önemli özellikler</span><span class="sxs-lookup"><span data-stu-id="ed725-105">Key Properties of NotifyIcons</span></span>

<span data-ttu-id="ed725-106">Her <xref:System.Windows.Forms.NotifyIcon> bileşeni durum alanında tek bir simge görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ed725-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="ed725-107">Üç arka plan işlemleriniz varsa ve her biri için bir simge göstermek istiyorsanız, forma üç <xref:System.Windows.Forms.NotifyIcon> bileşeni eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed725-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="ed725-108"><xref:System.Windows.Forms.NotifyIcon> bileşenin temel özellikleri <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed725-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="ed725-109"><xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliği, durum alanında görüntülenen simgeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ed725-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="ed725-110">Simgenin görünmesi için <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğinin `true`olarak ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed725-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>

## <a name="notifyicons-options"></a><span data-ttu-id="ed725-111">Notifysimgeler seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ed725-111">NotifyIcons Options</span></span>

<span data-ttu-id="ed725-112">Kullanıcıya yardımcı olması için balon ipuçlarını, kısayol menülerini ve araç Ipuçlarını bir <xref:System.Windows.Forms.NotifyIcon> ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed725-112">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>

<span data-ttu-id="ed725-113">Balon ipucunun görüntülenmesini istediğiniz zaman aralığını belirten <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> yöntemini çağırarak bir <xref:System.Windows.Forms.NotifyIcon> balon ipuçlarını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed725-113">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="ed725-114">Balon ipucunun metin, simge ve başlığını sırasıyla <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> ve <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>ile de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed725-114">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="ed725-115"><xref:System.Windows.Forms.NotifyIcon> bileşenlerinde ayrıca ilişkili araç Ipuçları ve kısayol menüleri bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ed725-115"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="ed725-116">Daha fazla bilgi için bkz. [araç Ipucu bileşenine genel bakış](tooltip-component-overview-windows-forms.md) ve [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ed725-116">For more information, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed725-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed725-117">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- [<span data-ttu-id="ed725-118">NotifyIcon Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ed725-118">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)

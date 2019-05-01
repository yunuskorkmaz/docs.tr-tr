---
title: StatusBar Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
ms.openlocfilehash: 9ef6bc125a641538e7fd2da4c17c5f25dfc62709
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009662"
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="42b12-102">StatusBar Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="42b12-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="42b12-103"><xref:System.Windows.Forms.ToolStripStatusLabel> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.StatusBar> denetler; ancak, <xref:System.Windows.Forms.StatusBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="42b12-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="42b12-104">Windows Forms <xref:System.Windows.Forms.StatusBar> denetimi formlarında genellikle bir uygulama çeşitli durum bilgilerini görüntüleyebilir, bir penceresinin en altında görüntülenen bir alanı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42b12-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="42b12-105"><xref:System.Windows.Forms.StatusBar> denetimlerin durumu ya da bir işlemin çalıştığını gösteren simgeler animasyonda bir dizi belirtmek için simgeler görüntüleme durum çubuğu panellerinin bunlardaki olabilir; Örneğin, belgeyi Microsoft Word gösteren kaydediliyor.</span><span class="sxs-lookup"><span data-stu-id="42b12-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42b12-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="42b12-106">In This Section</span></span>  
 [<span data-ttu-id="42b12-107">StatusBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="42b12-107">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="42b12-108">Genel konseptlerini tanıtan <xref:System.Windows.Forms.StatusBar> form veya Denetim odağa sahip denetimi için ilgili bilgileri görmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="42b12-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="42b12-109">Nasıl yapılır: Bir StatusBar denetimine panel ekleme</span><span class="sxs-lookup"><span data-stu-id="42b12-109">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="42b12-110">Programlanabilir panellere ekleme işlemi açıklanmaktadır <xref:System.Windows.Forms.StatusBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="42b12-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="42b12-111">Nasıl yapılır: Windows Forms StatusBar denetiminde hangi panele tıklandığını belirleme</span><span class="sxs-lookup"><span data-stu-id="42b12-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="42b12-112">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.Control.Click> tetiklenen olayları <xref:System.Windows.Forms.StatusBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="42b12-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="42b12-113">Nasıl yapılır: Durum çubuğu panellerinin boyutunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="42b12-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="42b12-114">Genişliğini denetleyen ve çalışma zamanında durum çubuğu panellerinin davranışını yeniden boyutlandırma özelliklerini ayrıntılarını verir.</span><span class="sxs-lookup"><span data-stu-id="42b12-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="42b12-115">İzlenecek yol: Çalışma zamanında durum çubuğu bilgilerini güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="42b12-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="42b12-116">Durum çubuğu panellerinin verilerle program aracılığıyla denetlemek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="42b12-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="42b12-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="42b12-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="42b12-118">Sınıf ve onun üyeleri hakkında başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="42b12-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="42b12-119">Değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.StatusBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="42b12-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="42b12-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="42b12-120">Related Sections</span></span>  
 [<span data-ttu-id="42b12-121">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="42b12-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="42b12-122">Windows Forms denetimlerini, tam bir listesi, kullanımları hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="42b12-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>

---
title: SplitContainer Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: 504a2396902fecf2ac17c2db434fef68ff2ece45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009727"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="7529c-102">SplitContainer Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7529c-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="7529c-103">Windows Forms `SplitContainer` denetim düşünülebilir bileşik; taşınabilir bir çubukla ayırarak iki bölme.</span><span class="sxs-lookup"><span data-stu-id="7529c-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="7529c-104">Çubuğu üzerine fare işaretçisi olduğunda, işaretçi şekli çubuğu taşınabilir olduğunu göstermek için değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7529c-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7529c-105">İçinde **araç kutusu**, bu denetim değiştirir <xref:System.Windows.Forms.Splitter> Visual Studio'nun önceki sürümünde var olan denetim.</span><span class="sxs-lookup"><span data-stu-id="7529c-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="7529c-106">`SplitContainer` Denetimidir üzerinden çok tercih edilen <xref:System.Windows.Forms.Splitter> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7529c-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="7529c-107"><xref:System.Windows.Forms.Splitter> Sınıfı hala var olan uygulamalarla uyumluluk için .NET Framework dahil, ancak kullanmanızı önemle öneririz `SplitContainer` denetimi yeni projeler için.</span><span class="sxs-lookup"><span data-stu-id="7529c-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="7529c-108">`SplitContainer` Denetim karmaşık kullanıcı arabirimleri oluşturmanıza olanak sağlar; genellikle, hangi nesneler diğer panelinde gösterilir bir bölmede bir seçim belirler.</span><span class="sxs-lookup"><span data-stu-id="7529c-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="7529c-109">Bu düzenleme, görüntüleme ve gözatma bilgilerinin oldukça etkilidir.</span><span class="sxs-lookup"><span data-stu-id="7529c-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="7529c-110">İki panel sahip alanlarda toplam bilgileri sağlar ve çubuğuna ya da "ayırıcı," paneller yeniden boyutlandırmak kullanıcıların kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7529c-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7529c-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7529c-111">In This Section</span></span>  
 [<span data-ttu-id="7529c-112">SplitContainer Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7529c-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="7529c-113">Tanıtır `SplitContainer` denetlemek ve yaygın olarak kullanılan özellikleri, yöntemleri ve olayları açıklar.</span><span class="sxs-lookup"><span data-stu-id="7529c-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="7529c-114">Nasıl yapılır: Yeniden boyutlandırma ve konumlama davranışını bölünmüş pencerede tanımlama</span><span class="sxs-lookup"><span data-stu-id="7529c-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="7529c-115">Ayırıcının denetlemek nasıl açıklar `SplitContainer` denetimi.</span><span class="sxs-lookup"><span data-stu-id="7529c-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="7529c-116">Nasıl yapılır: Pencereyi yatay bölme</span><span class="sxs-lookup"><span data-stu-id="7529c-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="7529c-117">İçinde Bölümlendirici yönlendirmesini denetlemek nasıl açıklar `SplitContainer` denetimi.</span><span class="sxs-lookup"><span data-stu-id="7529c-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="7529c-118">Nasıl yapılır: Windows Forms ile çok bölmeli kullanıcı arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7529c-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="7529c-119">Microsoft Outlook içinde kullanılan benzer bir çok bölmesi kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7529c-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="7529c-120">Ayrıca bkz: [nasıl yapılır: Tasarımcı kullanarak pencereyi bölme](how-to-split-a-window-horizontally-using-the-designer.md), [nasıl yapılır: Bir Windows formunda Windows Gezgini stilinde bir arabirim oluşturma](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [nasıl yapılır: Tasarımcı kullanarak Windows Forms ile çok bölmeli kullanıcı arabirimi oluşturma](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="7529c-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7529c-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7529c-121">Reference</span></span>  
 <span data-ttu-id="7529c-122"><xref:System.Windows.Forms.SplitContainer> Sınıfı</span><span class="sxs-lookup"><span data-stu-id="7529c-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="7529c-123">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="7529c-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7529c-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7529c-124">Related Sections</span></span>  
 [<span data-ttu-id="7529c-125">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="7529c-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="7529c-126">Özellikle Windows Forms ile çalışmak üzere tasarlanmış denetimleri hakkındaki konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7529c-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="7529c-127">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="7529c-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="7529c-128">Windows Forms denetimlerini, tam bir listesi, kullanımları hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7529c-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>

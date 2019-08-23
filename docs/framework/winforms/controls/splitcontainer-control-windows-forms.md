---
title: SplitContainer Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: d860763e935c88619e3355661038757d00247dfd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963582"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="7d27f-102">SplitContainer Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7d27f-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="7d27f-103">Windows Forms `SplitContainer` denetimi bileşik olarak düşünülebilir; taşınabilir bir çubukla ayrılmış iki paneldir.</span><span class="sxs-lookup"><span data-stu-id="7d27f-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="7d27f-104">Fare işaretçisi çubuğun üzerindeyken, işaretçiyi çubuğun taşınabilir olduğunu göstermek için şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7d27f-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d27f-105">**Araç kutusunda**bu denetim, Visual Studio 'nun <xref:System.Windows.Forms.Splitter> önceki sürümünde bulunan denetimin yerini almıştır.</span><span class="sxs-lookup"><span data-stu-id="7d27f-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="7d27f-106">Denetim, denetimin <xref:System.Windows.Forms.Splitter> üzerinde çok tercih edilir. `SplitContainer`</span><span class="sxs-lookup"><span data-stu-id="7d27f-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="7d27f-107">Sınıfı, var olan uygulamalarla uyumluluk için .NET Framework dahil edilmiştir, ancak yeni projeler için `SplitContainer` denetimi kullanmanızı kesinlikle öneririz. <xref:System.Windows.Forms.Splitter></span><span class="sxs-lookup"><span data-stu-id="7d27f-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="7d27f-108">`SplitContainer` Denetim, karmaşık kullanıcı arabirimleri oluşturmanıza olanak sağlar; genellikle, bir panelde seçim diğer panelde hangi nesnelerin gösterileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="7d27f-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="7d27f-109">Bu düzenleme bilgileri görüntülemek ve göz atmak için oldukça etkilidir.</span><span class="sxs-lookup"><span data-stu-id="7d27f-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="7d27f-110">İki bölme olması, alanlarda bilgi toplamanıza olanak sağlar ve çubuk veya "ayırıcı", kullanıcıların panoları yeniden boyutlandırmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7d27f-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d27f-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7d27f-111">In This Section</span></span>  
 [<span data-ttu-id="7d27f-112">SplitContainer Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7d27f-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="7d27f-113">`SplitContainer` Denetimi tanıtır ve yaygın olarak kullanılan özellikleri, yöntemleri ve olayları açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d27f-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="7d27f-114">Nasıl yapılır: Bölünmüş pencerede yeniden boyutlandırma ve konumlandırma davranışını tanımlama</span><span class="sxs-lookup"><span data-stu-id="7d27f-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="7d27f-115">`SplitContainer` Denetimin içinde Bölümlendirici denetimini nasıl denetleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d27f-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="7d27f-116">Nasıl yapılır: Pencereyi yatay bölme</span><span class="sxs-lookup"><span data-stu-id="7d27f-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="7d27f-117">`SplitContainer` Denetim içinde Bölümlendirici yönünün nasıl kontrol edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d27f-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="7d27f-118">Nasıl yapılır: Windows Forms ile çok Bölbir Kullanıcı arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d27f-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="7d27f-119">Microsoft Outlook 'ta kullanılan bir çok bölgeli Kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d27f-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="7d27f-120">Ayrıca bkz [. nasıl yapılır: Tasarımcıyı](how-to-split-a-window-horizontally-using-the-designer.md)kullanarak bir pencereyi yatay bölme, [nasıl yapılır: Bir Windows formunda](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md)Windows Gezgini-stil arabirimi oluşturma, [nasıl yapılır: Tasarımcıyı](create-a-multipane-user-interface-with-wf-using-the-designer.md)kullanarak Windows Forms çoklu bölmeli Kullanıcı arabirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d27f-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7d27f-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7d27f-121">Reference</span></span>  
 <span data-ttu-id="7d27f-122"><xref:System.Windows.Forms.SplitContainer>sınıfı</span><span class="sxs-lookup"><span data-stu-id="7d27f-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="7d27f-123">Bu sınıfı açıklar ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="7d27f-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7d27f-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7d27f-124">Related Sections</span></span>  
 [<span data-ttu-id="7d27f-125">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="7d27f-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="7d27f-126">Windows Forms ile çalışmak için özel olarak tasarlanan denetimlerle ilgili konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d27f-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="7d27f-127">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="7d27f-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="7d27f-128">Windows Forms denetimlerinin tüm listesini, kullanımları hakkındaki bilgilerin bağlantılarıyla birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d27f-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>

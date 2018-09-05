---
title: SplitContainer Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: 63b1a4b9b2483d017a686819573f91744d8a565a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518813"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="d8d05-102">SplitContainer Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d8d05-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="d8d05-103">Windows Forms `SplitContainer` denetim düşünülebilir bileşik; taşınabilir bir çubukla ayırarak iki bölme.</span><span class="sxs-lookup"><span data-stu-id="d8d05-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="d8d05-104">Çubuğu üzerine fare işaretçisi olduğunda, işaretçi şekli çubuğu taşınabilir olduğunu göstermek için değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d8d05-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8d05-105">İçinde **araç kutusu**, bu denetim değiştirir <xref:System.Windows.Forms.Splitter> Visual Studio'nun önceki sürümünde var olan denetim.</span><span class="sxs-lookup"><span data-stu-id="d8d05-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="d8d05-106">`SplitContainer` Denetimidir üzerinden çok tercih edilen <xref:System.Windows.Forms.Splitter> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d8d05-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="d8d05-107"><xref:System.Windows.Forms.Splitter> Sınıfı hala var olan uygulamalarla uyumluluk için .NET Framework dahil, ancak kullanmanızı önemle öneririz `SplitContainer` denetimi yeni projeler için.</span><span class="sxs-lookup"><span data-stu-id="d8d05-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="d8d05-108">`SplitContainer` Denetim karmaşık kullanıcı arabirimleri oluşturmanıza olanak sağlar; genellikle, hangi nesneler diğer panelinde gösterilir bir bölmede bir seçim belirler.</span><span class="sxs-lookup"><span data-stu-id="d8d05-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="d8d05-109">Bu düzenleme, görüntüleme ve gözatma bilgilerinin oldukça etkilidir.</span><span class="sxs-lookup"><span data-stu-id="d8d05-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="d8d05-110">İki panel sahip alanlarda toplam bilgileri sağlar ve çubuğuna ya da "ayırıcı," paneller yeniden boyutlandırmak kullanıcıların kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d8d05-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8d05-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d8d05-111">In This Section</span></span>  
 [<span data-ttu-id="d8d05-112">SplitContainer Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d8d05-112">SplitContainer Control Overview</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="d8d05-113">Tanıtır `SplitContainer` denetlemek ve yaygın olarak kullanılan özellikleri, yöntemleri ve olayları açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8d05-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="d8d05-114">Nasıl yapılır: Bölünmüş Pencerede Yeniden Boyutlandırma ve Konumlama Davranışını Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d8d05-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="d8d05-115">Ayırıcının denetlemek nasıl açıklar `SplitContainer` denetimi.</span><span class="sxs-lookup"><span data-stu-id="d8d05-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="d8d05-116">Nasıl yapılır: Pencereyi Yatay Bölme</span><span class="sxs-lookup"><span data-stu-id="d8d05-116">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="d8d05-117">İçinde Bölümlendirici yönlendirmesini denetlemek nasıl açıklar `SplitContainer` denetimi.</span><span class="sxs-lookup"><span data-stu-id="d8d05-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="d8d05-118">Nasıl yapılır: Windows Forms ile Çok Bölmeli Kullanıcı Arabirimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d8d05-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="d8d05-119">Microsoft Outlook içinde kullanılan benzer bir çok bölmesi kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8d05-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="d8d05-120">Ayrıca bkz: [nasıl yapılır: pencereyi yatay olarak kullanarak bir tasarımcı bölünmüş](how-to-split-a-window-horizontally-using-the-designer.md), [nasıl yapılır: bir Windows formunda Windows Gezgini stilinde bir arabirim oluşturma](https://msdn.microsoft.com/library/zh2fe5a5\(v=vs.110\)), [nasıl yapılır: Multipane kullanıcı arabirimi ile oluşturma Tasarımcı kullanarak Windows Forms](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="d8d05-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](https://msdn.microsoft.com/library/zh2fe5a5\(v=vs.110\)), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d8d05-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d8d05-121">Reference</span></span>  
 <span data-ttu-id="d8d05-122"><xref:System.Windows.Forms.SplitContainer> Sınıfı</span><span class="sxs-lookup"><span data-stu-id="d8d05-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="d8d05-123">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="d8d05-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d8d05-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d8d05-124">Related Sections</span></span>  
 [<span data-ttu-id="d8d05-125">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="d8d05-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="d8d05-126">Özellikle Windows Forms ile çalışmak üzere tasarlanmış denetimleri hakkındaki konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8d05-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="d8d05-127">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="d8d05-127">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="d8d05-128">Windows Forms denetimlerini, tam bir listesi, kullanımları hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8d05-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>

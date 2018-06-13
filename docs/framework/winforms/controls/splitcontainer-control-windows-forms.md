---
title: SplitContainer Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: 42eccbf88db2a407c6dd40209ecd615f0c19eb7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539207"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="54987-102">SplitContainer Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="54987-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="54987-103">Windows Forms `SplitContainer` kontrol zorlayıcı bileşik olarak; iki bölme taşınabilir bir çubukla ayrılan değer.</span><span class="sxs-lookup"><span data-stu-id="54987-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="54987-104">Fare işaretçisini çubuğu üzerine olduğunda çubuğu taşınabilir olduğunu göstermek için Şekil işaretçi.</span><span class="sxs-lookup"><span data-stu-id="54987-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54987-105">İçinde **araç**, bu denetim değiştirir <xref:System.Windows.Forms.Splitter> Visual Studio'nun önceki sürümünde olduğu denetim.</span><span class="sxs-lookup"><span data-stu-id="54987-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="54987-106">`SplitContainer` Denetimidir üzerinden çok tercih edilen <xref:System.Windows.Forms.Splitter> denetim.</span><span class="sxs-lookup"><span data-stu-id="54987-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="54987-107"><xref:System.Windows.Forms.Splitter> Sınıf halen varolan uygulamalarla uyumluluk için .NET Framework dahil, ancak kullanmak için kesinlikle öneririz `SplitContainer` yeni projeler için denetim.</span><span class="sxs-lookup"><span data-stu-id="54987-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="54987-108">`SplitContainer` Denetim karmaşık kullanıcı arabirimleri oluşturmanıza olanak tanır; bu genellikle, bir panelinde seçimi hangi nesneleri diğer panelinde gösterileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="54987-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="54987-109">Bu düzenlemenin görüntüleme ve bilgi gözatma için çok etkili olur.</span><span class="sxs-lookup"><span data-stu-id="54987-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="54987-110">İki bölme sahip alanlarda toplama bilgilere izin, ve çubuğu ya da "bölme," paneller yeniden boyutlandırmak kullanıcılar için kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="54987-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54987-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="54987-111">In This Section</span></span>  
 [<span data-ttu-id="54987-112">SplitContainer Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="54987-112">SplitContainer Control Overview</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="54987-113">Tanıtır `SplitContainer` denetlemek ve yaygın olarak kullanılan özellikleri, yöntemleri ve olayları açıklar.</span><span class="sxs-lookup"><span data-stu-id="54987-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="54987-114">Nasıl yapılır: Bölünmüş Pencerede Yeniden Boyutlandırma ve Konumlama Davranışını Tanımlama</span><span class="sxs-lookup"><span data-stu-id="54987-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="54987-115">Bölümlendirici içinde denetlemek açıklar `SplitContainer` denetim.</span><span class="sxs-lookup"><span data-stu-id="54987-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="54987-116">Nasıl yapılır: Pencereyi Yatay Bölme</span><span class="sxs-lookup"><span data-stu-id="54987-116">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="54987-117">İçinde Bölümlendirici yönlendirmesini denetlemek açıklar `SplitContainer` denetim.</span><span class="sxs-lookup"><span data-stu-id="54987-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="54987-118">Nasıl yapılır: Windows Forms ile Çok Bölmeli Kullanıcı Arabirimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54987-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="54987-119">Microsoft Outlook içinde kullanılan benzer bir çok bölmesi kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54987-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="54987-120">Ayrıca bkz. [nasıl yapılır: pencereyi yatay olarak kullanarak bir tasarımcı bölme](http://msdn.microsoft.com/library/ms233667\(v=vs.110\)), [nasıl yapılır: bir Windows formunda Windows Gezgini stilinde bir arabirim oluşturma](http://msdn.microsoft.com/library/zh2fe5a5\(v=vs.110\)), [nasıl yapılır: ile çok bölmeli kullanıcı arabirimi oluşturma Tasarımcı kullanarak Windows Formları](http://msdn.microsoft.com/library/ms233661\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="54987-120">Also see [How to: Split a Window Horizontally Using the Designer](http://msdn.microsoft.com/library/ms233667\(v=vs.110\)), [How to: Create a Windows Explorer–Style Interface on a Windows Form](http://msdn.microsoft.com/library/zh2fe5a5\(v=vs.110\)), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](http://msdn.microsoft.com/library/ms233661\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="54987-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="54987-121">Reference</span></span>  
 <span data-ttu-id="54987-122"><xref:System.Windows.Forms.SplitContainer> sınıfı</span><span class="sxs-lookup"><span data-stu-id="54987-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="54987-123">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="54987-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="54987-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="54987-124">Related Sections</span></span>  
 [<span data-ttu-id="54987-125">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="54987-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="54987-126">Özellikle Windows Forms ile çalışmak üzere tasarlanmış denetimleriyle ilgili konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="54987-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="54987-127">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="54987-127">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="54987-128">Windows Forms denetimleri, tam bir listesi ile bunların kullanılması hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="54987-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>

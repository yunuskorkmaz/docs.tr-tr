---
title: "Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3186dcf3b1f56799709f1e1976a55288065352b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="87d7c-102">Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama</span><span class="sxs-lookup"><span data-stu-id="87d7c-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="87d7c-103">Yeni bir kapsayıcı denetiminin için formunuzda mevcut denetimleri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87d7c-103">You can assign controls that exist on your form to a new container control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87d7c-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="87d7c-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="87d7c-105">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="87d7c-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="87d7c-106">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="87d7c-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="87d7c-107">Mevcut denetimleri farklı bir üst öğeye yeniden atama</span><span class="sxs-lookup"><span data-stu-id="87d7c-107">To reassign existing controls to a different parent</span></span>  
  
1.  <span data-ttu-id="87d7c-108">Üç sürükleyin <xref:System.Windows.Forms.Button> gelen denetimleri **araç** forma.</span><span class="sxs-lookup"><span data-stu-id="87d7c-108">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>  
  
     <span data-ttu-id="87d7c-109">Diğer yakınında olmak getirin, ancak bunları hizalanmamış bırakın.</span><span class="sxs-lookup"><span data-stu-id="87d7c-109">Position them near to each other, but leave them unaligned.</span></span>  
  
2.  <span data-ttu-id="87d7c-110">İçinde **araç**, tıklatın <xref:System.Windows.Forms.FlowLayoutPanel> denetimi simgesi.</span><span class="sxs-lookup"><span data-stu-id="87d7c-110">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>  
  
     <span data-ttu-id="87d7c-111">Simge form üzerine sürükleyin değil.</span><span class="sxs-lookup"><span data-stu-id="87d7c-111">Do not drag the icon onto the form.</span></span>  
  
3.  <span data-ttu-id="87d7c-112">Fare işaretçisini üç yakın <xref:System.Windows.Forms.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="87d7c-112">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
     <span data-ttu-id="87d7c-113">Bir artı kıl ile işaretçi <xref:System.Windows.Forms.FlowLayoutPanel> bağlı denetimi simgesi.</span><span class="sxs-lookup"><span data-stu-id="87d7c-113">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>  
  
4.  <span data-ttu-id="87d7c-114">' A tıklayın ve fare düğmesini basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="87d7c-114">Click and hold the mouse button.</span></span>  
  
5.  <span data-ttu-id="87d7c-115">Özetini çizmek için fare işaretçisini sürükleyin <xref:System.Windows.Forms.FlowLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="87d7c-115">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="87d7c-116">Üç çevresinde anahat çizme <xref:System.Windows.Forms.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="87d7c-116">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
7.  <span data-ttu-id="87d7c-117">Fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="87d7c-117">Release the mouse button.</span></span>  
  
     <span data-ttu-id="87d7c-118">Üç <xref:System.Windows.Forms.Button> denetimleri içine şimdi eklenir <xref:System.Windows.Forms.FlowLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="87d7c-118">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d7c-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87d7c-119">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="87d7c-120">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="87d7c-120">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="87d7c-121">İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="87d7c-121">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="87d7c-122">İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="87d7c-122">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)

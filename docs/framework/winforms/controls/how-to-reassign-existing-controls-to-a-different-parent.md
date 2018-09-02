---
title: 'Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: 77246aaf2fdaa79ad986366e39ff98a9d0f5fb50
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420159"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="0937d-102">Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama</span><span class="sxs-lookup"><span data-stu-id="0937d-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="0937d-103">Formunuzdaki yeni bir kapsayıcı denetimi için mevcut denetimleri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0937d-103">You can assign controls that exist on your form to a new container control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0937d-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="0937d-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0937d-105">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="0937d-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0937d-106">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0937d-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="0937d-107">Mevcut denetimleri farklı bir üst öğeye yeniden atama</span><span class="sxs-lookup"><span data-stu-id="0937d-107">To reassign existing controls to a different parent</span></span>  
  
1.  <span data-ttu-id="0937d-108">Üç sürükleyin <xref:System.Windows.Forms.Button> denetimler **araç kutusu** forma.</span><span class="sxs-lookup"><span data-stu-id="0937d-108">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>  
  
     <span data-ttu-id="0937d-109">Birbirine yakın yerleştirin, ancak bunları hizalanmamış bırakın.</span><span class="sxs-lookup"><span data-stu-id="0937d-109">Position them near to each other, but leave them unaligned.</span></span>  
  
2.  <span data-ttu-id="0937d-110">İçinde **araç kutusu**, tıklayın <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesi.</span><span class="sxs-lookup"><span data-stu-id="0937d-110">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>  
  
     <span data-ttu-id="0937d-111">Simge, form üzerine sürükleyin değil.</span><span class="sxs-lookup"><span data-stu-id="0937d-111">Do not drag the icon onto the form.</span></span>  
  
3.  <span data-ttu-id="0937d-112">Fare işaretçisini üç yakın <xref:System.Windows.Forms.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="0937d-112">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
     <span data-ttu-id="0937d-113">Bir artı işareti ile işaretçi <xref:System.Windows.Forms.FlowLayoutPanel> bağlı denetim simgesi.</span><span class="sxs-lookup"><span data-stu-id="0937d-113">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>  
  
4.  <span data-ttu-id="0937d-114">' A tıklayın ve fare düğmesini basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="0937d-114">Click and hold the mouse button.</span></span>  
  
5.  <span data-ttu-id="0937d-115">Fare işaretçisi ana hat çizmek için sürükleyin <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="0937d-115">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="0937d-116">Üç çevresinde anahat çizmek <xref:System.Windows.Forms.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="0937d-116">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
7.  <span data-ttu-id="0937d-117">Fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="0937d-117">Release the mouse button.</span></span>  
  
     <span data-ttu-id="0937d-118">Üç <xref:System.Windows.Forms.Button> denetimleri içine eklenir artık <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="0937d-118">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0937d-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0937d-119">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="0937d-120">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="0937d-120">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="0937d-121">İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="0937d-121">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="0937d-122">İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="0937d-122">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)

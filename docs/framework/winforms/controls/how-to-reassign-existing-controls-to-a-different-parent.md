---
title: 'Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: a65b3c2b596a2d88ce4236aeadd86993bb268aa6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039781"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="7f7e9-102">Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama</span><span class="sxs-lookup"><span data-stu-id="7f7e9-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="7f7e9-103">Formunuzda bulunan denetimleri yeni bir kapsayıcı denetimine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-103">You can assign controls that exist on your form to a new container control.</span></span>

## <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="7f7e9-104">Varolan denetimleri farklı bir üst öğeye yeniden atamak için</span><span class="sxs-lookup"><span data-stu-id="7f7e9-104">To reassign existing controls to a different parent</span></span>

1. <span data-ttu-id="7f7e9-105"><xref:System.Windows.Forms.Button> **Araç kutusundan** üç denetimi form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-105">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>

     <span data-ttu-id="7f7e9-106">Bunları birbirlerine yakın bir konuma konumlandırın, ancak hizalanmamış olarak bırakın.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-106">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="7f7e9-107">**Araç kutusunda** <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-107">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>

     <span data-ttu-id="7f7e9-108">Simgeyi formun üzerine sürüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-108">Do not drag the icon onto the form.</span></span>

3. <span data-ttu-id="7f7e9-109">Fare işaretçisini üç <xref:System.Windows.Forms.Button> denetime yakın bir şekilde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-109">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

     <span data-ttu-id="7f7e9-110">İşaretçi, <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesinin eklendiği çapraz artı işaretine dönüşür.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-110">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="7f7e9-111">Fare düğmesine tıklayın ve basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-111">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="7f7e9-112"><xref:System.Windows.Forms.FlowLayoutPanel> Denetimin anahattını çizmek için fare işaretçisini sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-112">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="7f7e9-113">Ana hattı üç <xref:System.Windows.Forms.Button> denetimin çevresine çizin.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-113">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="7f7e9-114">Fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-114">Release the mouse button.</span></span>

     <span data-ttu-id="7f7e9-115">Üç <xref:System.Windows.Forms.Button> denetim artık <xref:System.Windows.Forms.FlowLayoutPanel> denetime eklenir.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-115">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f7e9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f7e9-116">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="7f7e9-117">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="7f7e9-117">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="7f7e9-118">İzlenecek yol: TableLayoutPanel kullanarak Windows Forms denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="7f7e9-118">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="7f7e9-119">İzlenecek yol: Anlık görüntü çizgilerini kullanarak Windows Forms denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="7f7e9-119">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)

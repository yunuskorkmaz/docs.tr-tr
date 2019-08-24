---
title: 'Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84e662e0bd2689115abe128c6442e4462eed3e18
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987040"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="71def-102">Nasıl yapılır: Varolan denetimleri farklı bir üst öğeye yeniden atama</span><span class="sxs-lookup"><span data-stu-id="71def-102">How to: Reassign existing controls to a different parent</span></span>

<span data-ttu-id="71def-103">Formunuzda bulunan denetimleri yeni bir kapsayıcı denetimine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71def-103">You can assign controls that exist on your form to a new container control.</span></span>

1. <span data-ttu-id="71def-104">Visual Studio 'da, <xref:System.Windows.Forms.Button> **araç kutusundan** üç denetimi form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="71def-104">In Visual Studio, drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span> <span data-ttu-id="71def-105">Bunları birbirlerine yakın bir konuma konumlandırın, ancak hizalanmamış olarak bırakın.</span><span class="sxs-lookup"><span data-stu-id="71def-105">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="71def-106">**Araç kutusunda** <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="71def-106">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span> <span data-ttu-id="71def-107">(Simgeyi formun üzerine sürüklemeyin.)</span><span class="sxs-lookup"><span data-stu-id="71def-107">(Do not drag the icon onto the form.)</span></span>

3. <span data-ttu-id="71def-108">Fare işaretçisini üç <xref:System.Windows.Forms.Button> denetime yakın bir şekilde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="71def-108">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

   <span data-ttu-id="71def-109">İşaretçi, <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesinin eklendiği çapraz artı işaretine dönüşür.</span><span class="sxs-lookup"><span data-stu-id="71def-109">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="71def-110">Fare düğmesine tıklayın ve basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="71def-110">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="71def-111"><xref:System.Windows.Forms.FlowLayoutPanel> Denetimin anahattını çizmek için fare işaretçisini sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="71def-111">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="71def-112">Ana hattı üç <xref:System.Windows.Forms.Button> denetimin çevresine çizin.</span><span class="sxs-lookup"><span data-stu-id="71def-112">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="71def-113">Fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="71def-113">Release the mouse button.</span></span>

   <span data-ttu-id="71def-114">Üç <xref:System.Windows.Forms.Button> denetim artık <xref:System.Windows.Forms.FlowLayoutPanel> denetime eklenir.</span><span class="sxs-lookup"><span data-stu-id="71def-114">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="71def-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71def-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="71def-116">İzlenecek yol: TableLayoutPanel kullanarak Windows Forms denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="71def-116">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="71def-117">İzlenecek yol: Anlık görüntü çizgilerini kullanarak Windows Forms denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="71def-117">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)

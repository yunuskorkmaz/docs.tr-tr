---
title: 'Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459201"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="975fe-102">Nasıl yapılır: mevcut denetimleri farklı bir üst öğeye yeniden atama</span><span class="sxs-lookup"><span data-stu-id="975fe-102">How to: Reassign existing controls to a different parent</span></span>

<span data-ttu-id="975fe-103">Formunuzda bulunan denetimleri yeni bir kapsayıcı denetimine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="975fe-103">You can assign controls that exist on your form to a new container control.</span></span>

1. <span data-ttu-id="975fe-104">Visual Studio 'da, **araç kutusundan** üç <xref:System.Windows.Forms.Button> denetimini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="975fe-104">In Visual Studio, drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span> <span data-ttu-id="975fe-105">Bunları birbirlerine yakın bir konuma konumlandırın, ancak hizalanmamış olarak bırakın.</span><span class="sxs-lookup"><span data-stu-id="975fe-105">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="975fe-106">**Araç kutusunda**<xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="975fe-106">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span> <span data-ttu-id="975fe-107">(Simgeyi formun üzerine sürüklemeyin.)</span><span class="sxs-lookup"><span data-stu-id="975fe-107">(Do not drag the icon onto the form.)</span></span>

3. <span data-ttu-id="975fe-108">Fare işaretçisini üç <xref:System.Windows.Forms.Button> denetimine yakın bir şekilde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="975fe-108">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

   <span data-ttu-id="975fe-109">İşaretçi, eklenen <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesiyle çapraz artı işaretine dönüşür.</span><span class="sxs-lookup"><span data-stu-id="975fe-109">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="975fe-110">Fare düğmesine tıklayın ve basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="975fe-110">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="975fe-111"><xref:System.Windows.Forms.FlowLayoutPanel> denetiminin anahattını çizmek için fare işaretçisini sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="975fe-111">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="975fe-112">Ana hattı üç <xref:System.Windows.Forms.Button> denetiminin çevresine çizin.</span><span class="sxs-lookup"><span data-stu-id="975fe-112">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="975fe-113">Fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="975fe-113">Release the mouse button.</span></span>

   <span data-ttu-id="975fe-114">Üç <xref:System.Windows.Forms.Button> denetimi artık <xref:System.Windows.Forms.FlowLayoutPanel> denetimine eklenir.</span><span class="sxs-lookup"><span data-stu-id="975fe-114">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="975fe-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="975fe-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="975fe-116">İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="975fe-116">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="975fe-117">İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="975fe-117">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)

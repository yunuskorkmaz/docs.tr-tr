---
title: GroupBox denetimi ile grup denetimleri
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: bb7476c410d2802b5d32cc9842a778f290765e32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736654"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="bcae8-102">Nasıl yapılır: Windows Formları GroupBox Denetimiyle Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="bcae8-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="bcae8-103">Windows Forms <xref:System.Windows.Forms.GroupBox> denetimleri diğer denetimleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcae8-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="bcae8-104">Denetimleri gruplamak için üç neden vardır:</span><span class="sxs-lookup"><span data-stu-id="bcae8-104">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="bcae8-105">Açık bir kullanıcı arabirimi için ilgili form öğelerinin görsel gruplandırmasını oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="bcae8-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="bcae8-106">Programlı gruplandırma oluşturmak için (örneğin, radyo düğmeleri).</span><span class="sxs-lookup"><span data-stu-id="bcae8-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="bcae8-107">Tasarım zamanında denetimleri bir birim olarak taşımak için.</span><span class="sxs-lookup"><span data-stu-id="bcae8-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="bcae8-108">Bir Grup denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bcae8-108">To create a group of controls</span></span>  
  
1. <span data-ttu-id="bcae8-109">Form üzerinde <xref:System.Windows.Forms.GroupBox> denetimi çizin.</span><span class="sxs-lookup"><span data-stu-id="bcae8-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="bcae8-110">Grup kutusuna, her bir grup kutusunun içine çizerek diğer denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bcae8-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="bcae8-111">Bir Grup kutusuna eklemek istediğiniz mevcut denetimleriniz varsa, tüm denetimleri seçebilir, pano 'ya kesebilir, <xref:System.Windows.Forms.GroupBox> denetimini seçebilir ve sonra bunları Grup kutusuna yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcae8-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="bcae8-112">Bunları Grup kutusuna da sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcae8-112">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="bcae8-113">Grup kutusunun <xref:System.Windows.Forms.GroupBox.Text%2A> özelliğini uygun bir başlık olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bcae8-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcae8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcae8-114">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="bcae8-115">GroupBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="bcae8-115">GroupBox Control</span></span>](groupbox-control-windows-forms.md)

---
title: GroupBox denetimi ile grup denetimleri
description: İlgili öğelerin görsel gruplandırmasını oluşturabilmeniz için Windows Forms GroupBox denetimiyle denetimleri gruplamayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: f84c495a18f4ae5e04367f024a1e2849f1ed59f9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618070"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="71e49-103">Nasıl yapılır: Windows Formları GroupBox Denetimiyle Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="71e49-103">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="71e49-104">Windows Forms <xref:System.Windows.Forms.GroupBox> denetimleri, diğer denetimleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71e49-104">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="71e49-105">Denetimleri gruplamak için üç neden vardır:</span><span class="sxs-lookup"><span data-stu-id="71e49-105">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="71e49-106">Açık bir kullanıcı arabirimi için ilgili form öğelerinin görsel gruplandırmasını oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="71e49-106">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="71e49-107">Programlı gruplandırma oluşturmak için (örneğin, radyo düğmeleri).</span><span class="sxs-lookup"><span data-stu-id="71e49-107">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="71e49-108">Tasarım zamanında denetimleri bir birim olarak taşımak için.</span><span class="sxs-lookup"><span data-stu-id="71e49-108">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="71e49-109">Bir Grup denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="71e49-109">To create a group of controls</span></span>  
  
1. <span data-ttu-id="71e49-110"><xref:System.Windows.Forms.GroupBox>Form üzerinde bir denetim çizin.</span><span class="sxs-lookup"><span data-stu-id="71e49-110">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="71e49-111">Grup kutusuna, her bir grup kutusunun içine çizerek diğer denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="71e49-111">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="71e49-112">Bir Grup kutusuna eklemek istediğiniz mevcut denetimleriniz varsa, tüm denetimleri seçebilir, panoya kesebilir, <xref:System.Windows.Forms.GroupBox> denetimi seçebilir ve sonra bunları Grup kutusuna yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71e49-112">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="71e49-113">Bunları Grup kutusuna da sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71e49-113">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="71e49-114"><xref:System.Windows.Forms.GroupBox.Text%2A>Grup kutusunun özelliğini uygun bir başlık olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="71e49-114">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e49-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71e49-115">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="71e49-116">GroupBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="71e49-116">GroupBox Control</span></span>](groupbox-control-windows-forms.md)

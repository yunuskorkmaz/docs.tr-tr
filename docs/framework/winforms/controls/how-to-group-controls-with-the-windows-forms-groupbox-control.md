---
title: 'Nasıl yapılır: Windows Forms GroupBox denetimiyle denetimleri gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 44f0116511165c021f8e3dc35fb14e5cfb6f619e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686926"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="9c98c-102">Nasıl yapılır: Windows Forms GroupBox denetimiyle denetimleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="9c98c-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="9c98c-103">Windows Forms <xref:System.Windows.Forms.GroupBox> denetimleri başka denetimler gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c98c-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="9c98c-104">Grup denetimleri için üç neden vardır:</span><span class="sxs-lookup"><span data-stu-id="9c98c-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="9c98c-105">Görsel gruplandırılmasını ilgili form öğeleri için açık kullanıcı arabirimi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9c98c-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="9c98c-106">Programlı gruplandırması (örneğin radyo düğmeleri) oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9c98c-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="9c98c-107">Denetimleri bir birim olarak tasarım zamanında taşımak için.</span><span class="sxs-lookup"><span data-stu-id="9c98c-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="9c98c-108">Denetimlerin bir grup oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9c98c-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="9c98c-109">Çizim bir <xref:System.Windows.Forms.GroupBox> form denetimi.</span><span class="sxs-lookup"><span data-stu-id="9c98c-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="9c98c-110">Her grup kutusunun içinde çizim grup kutusu diğer denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9c98c-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="9c98c-111">Bir grup kutusuna eklemek istediğiniz mevcut denetimleri varsa, tüm denetimler seçip onları seçin panoya Kes <xref:System.Windows.Forms.GroupBox> denetlemek ve ardından bunları Grup kutuya yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9c98c-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="9c98c-112">Ayrıca bunları grup kutusuna sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c98c-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="9c98c-113">Ayarlama <xref:System.Windows.Forms.GroupBox.Text%2A> grup kutusu için uygun bir açıklamalı alt yazı özelliği.</span><span class="sxs-lookup"><span data-stu-id="9c98c-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c98c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c98c-114">See also</span></span>
- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="9c98c-115">GroupBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="9c98c-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)

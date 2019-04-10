---
title: 'Nasıl yapılır: Windows Forms GroupBox Denetimiyle Denetimleri Gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: d2bad0020d18cd262bc2fe3489a00209308bd7b9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335881"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="0df78-102">Nasıl yapılır: Windows Forms GroupBox Denetimiyle Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="0df78-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="0df78-103">Windows Forms <xref:System.Windows.Forms.GroupBox> denetimleri başka denetimler gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0df78-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="0df78-104">Grup denetimleri için üç neden vardır:</span><span class="sxs-lookup"><span data-stu-id="0df78-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="0df78-105">Görsel gruplandırılmasını ilgili form öğeleri için açık kullanıcı arabirimi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="0df78-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="0df78-106">Programlı gruplandırması (örneğin radyo düğmeleri) oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="0df78-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="0df78-107">Denetimleri bir birim olarak tasarım zamanında taşımak için.</span><span class="sxs-lookup"><span data-stu-id="0df78-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="0df78-108">Denetimlerin bir grup oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0df78-108">To create a group of controls</span></span>  
  
1. <span data-ttu-id="0df78-109">Çizim bir <xref:System.Windows.Forms.GroupBox> form denetimi.</span><span class="sxs-lookup"><span data-stu-id="0df78-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="0df78-110">Her grup kutusunun içinde çizim grup kutusu diğer denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0df78-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="0df78-111">Bir grup kutusuna eklemek istediğiniz mevcut denetimleri varsa, tüm denetimler seçip onları seçin panoya Kes <xref:System.Windows.Forms.GroupBox> denetlemek ve ardından bunları Grup kutuya yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="0df78-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="0df78-112">Ayrıca bunları grup kutusuna sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0df78-112">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="0df78-113">Ayarlama <xref:System.Windows.Forms.GroupBox.Text%2A> grup kutusu için uygun bir açıklamalı alt yazı özelliği.</span><span class="sxs-lookup"><span data-stu-id="0df78-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df78-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0df78-114">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="0df78-115">GroupBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="0df78-115">GroupBox Control</span></span>](groupbox-control-windows-forms.md)

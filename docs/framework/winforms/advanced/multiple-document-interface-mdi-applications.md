---
title: "Çoklu Belge Arabirimi (MDI) Uygulamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74735afcb1d6be319ad5d497615a3b725a4d5574
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="164c4-102">Çoklu Belge Arabirimi (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="164c4-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="164c4-103">Birden çok belge arabirimi (MDI) uygulamaları, kendi penceresinde görüntülenen her belgeyle aynı anda birden çok belgeleri görüntülemek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="164c4-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="164c4-104">MDI uygulamaları genellikle windows veya belgeler arasında geçiş yapmak için alt menüler pencere Menü öğesiyle sahiptir.</span><span class="sxs-lookup"><span data-stu-id="164c4-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="164c4-105">Bazı Windows Forms MDI formları tek belge arabirimi (SDI) windows arasındaki davranış farklılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="164c4-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="164c4-106">`Opacity` Özelliği MDI alt formları görünümünü etkilemez.</span><span class="sxs-lookup"><span data-stu-id="164c4-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="164c4-107">Ayrıca, <xref:System.Windows.Forms.Form.CenterToParent%2A> yöntemi MDI alt formları davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="164c4-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="164c4-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="164c4-108">In This Section</span></span>  
 [<span data-ttu-id="164c4-109">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="164c4-109">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="164c4-110">MDI uygulama içinde birden çok belge için bir kapsayıcı oluşturma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="164c4-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="164c4-111">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="164c4-111">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="164c4-112">MDI üst formu içinde çalışan bir veya daha fazla windows oluşturma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="164c4-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="164c4-113">Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme</span><span class="sxs-lookup"><span data-stu-id="164c4-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="164c4-114">Odaklanmış alt pencere doğrulama için yönergeler sağlar (ve içeriğini panoya gönderme).</span><span class="sxs-lookup"><span data-stu-id="164c4-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="164c4-115">Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="164c4-115">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="164c4-116">Etkin alt pencere bilgileri taşıma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="164c4-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="164c4-117">Nasıl yapılır: MDI Alt Formlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="164c4-117">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="164c4-118">Döşeme, geçişli veya uygulamanın MDI alt pencereleri düzenleme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="164c4-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>

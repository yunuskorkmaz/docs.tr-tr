---
title: Çoklu Belge Arabirimi (MDI) Uygulamaları
description: Birden çok belgeli arabirim (MDI) uygulamalarının, her belge kendi penceresinde görüntülenen birden çok belgeyi aynı anda görüntülemenizi Windows Forms nasıl sağladığını öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0912a989ac1710d72c9db1cceb0e695f0ca85dee
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174659"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="04177-103">Çoklu Belge Arabirimi (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="04177-103">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="04177-104">Birden çok belge arabirimi (MDI) uygulamaları, her belge kendi penceresinde görüntülenirken, birden çok belgeyi aynı anda görüntülemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="04177-104">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="04177-105">MDI uygulamalarında, pencereler veya belgeler arasında geçiş yapmak için genellikle alt menüler içeren bir pencere menü öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="04177-105">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04177-106">Windows Forms 'daki MDI formları ve tek belge arabirimi (SDI) pencereleri arasında bazı davranış farklılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="04177-106">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="04177-107">`Opacity`ÖZELLIĞI MDI alt formlarının görünüşünü etkilemez.</span><span class="sxs-lookup"><span data-stu-id="04177-107">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="04177-108">Ayrıca, <xref:System.Windows.Forms.Form.CenterToParent%2A> YÖNTEMI MDI alt formlarının davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="04177-108">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04177-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="04177-109">In This Section</span></span>  
 [<span data-ttu-id="04177-110">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="04177-110">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="04177-111">Bir MDI uygulaması içindeki birden çok belge için kapsayıcı oluşturmaya yönelik yönergeler verir.</span><span class="sxs-lookup"><span data-stu-id="04177-111">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="04177-112">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="04177-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="04177-113">MDI üst formu içinde çalışan bir veya daha fazla pencere oluşturmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="04177-113">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="04177-114">Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme</span><span class="sxs-lookup"><span data-stu-id="04177-114">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="04177-115">Odağa sahip olan alt pencereyi doğrulamaya yönelik yönergeler verir (ve içeriğini panoya gönderir).</span><span class="sxs-lookup"><span data-stu-id="04177-115">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="04177-116">Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="04177-116">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="04177-117">Etkin alt pencereye bilgi aktarmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="04177-117">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="04177-118">Nasıl yapılır: MDI Alt Formlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="04177-118">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="04177-119">Bir MDI uygulamasının alt pencerelerini döşeme, basamaklı veya düzenleme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="04177-119">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>

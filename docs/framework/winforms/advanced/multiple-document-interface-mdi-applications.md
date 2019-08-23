---
title: Çoklu Belge Arabirimi (MDI) Uygulamaları
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 23e0275d5e6b081ec02d669a78e8695453360637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956553"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="8fc6d-102">Çoklu Belge Arabirimi (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="8fc6d-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="8fc6d-103">Birden çok belge arabirimi (MDI) uygulamaları, her belge kendi penceresinde görüntülenirken, birden çok belgeyi aynı anda görüntülemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="8fc6d-104">MDI uygulamalarında, pencereler veya belgeler arasında geçiş yapmak için genellikle alt menüler içeren bir pencere menü öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fc6d-105">Windows Forms 'daki MDI formları ve tek belge arabirimi (SDI) pencereleri arasında bazı davranış farklılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="8fc6d-106">`Opacity` Özelliği MDI alt formlarının görünüşünü etkilemez.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="8fc6d-107">Ayrıca, <xref:System.Windows.Forms.Form.CenterToParent%2A> yöntemi MDI alt formlarının davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fc6d-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8fc6d-108">In This Section</span></span>  
 [<span data-ttu-id="8fc6d-109">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fc6d-109">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="8fc6d-110">Bir MDI uygulaması içindeki birden çok belge için kapsayıcı oluşturmaya yönelik yönergeler verir.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="8fc6d-111">Nasıl yapılır: MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fc6d-111">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="8fc6d-112">MDI üst formu içinde çalışan bir veya daha fazla pencere oluşturmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="8fc6d-113">Nasıl yapılır: Etkin MDI alt öğesini belirleme</span><span class="sxs-lookup"><span data-stu-id="8fc6d-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="8fc6d-114">Odağa sahip olan alt pencereyi doğrulamaya yönelik yönergeler verir (ve içeriğini panoya gönderir).</span><span class="sxs-lookup"><span data-stu-id="8fc6d-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="8fc6d-115">Nasıl yapılır: Etkin MDI alt öğesine veri gönderme</span><span class="sxs-lookup"><span data-stu-id="8fc6d-115">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="8fc6d-116">Etkin alt pencereye bilgi aktarmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="8fc6d-117">Nasıl yapılır: MDI alt formlarını düzenleme</span><span class="sxs-lookup"><span data-stu-id="8fc6d-117">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="8fc6d-118">Bir MDI uygulamasının alt pencerelerini döşeme, basamaklı veya düzenleme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>

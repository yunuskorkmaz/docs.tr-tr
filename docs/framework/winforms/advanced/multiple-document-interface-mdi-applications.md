---
title: Çoklu Belge Arabirimi (MDI) Uygulamaları
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0ce7c66946d03d566b21473711cb6b3315885236
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717456"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="7b671-102">Çoklu Belge Arabirimi (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="7b671-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="7b671-103">Çok Belgeli Arabirim (MDI) uygulamaları aynı anda birden çok belge kendi penceresinde görüntülenen her bir belgeyi görüntülemek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="7b671-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="7b671-104">MDI uygulamaları, genellikle windows veya belgeler arasında geçiş yapmak için alt pencere Menü öğesiyle sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7b671-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b671-105">Bazı Windows Formları MDI formları ve windows tek Belgeli Arabirim (SDI) arasındaki davranış farklılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="7b671-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="7b671-106">`Opacity` Özelliği MDI alt formlarını görünümünü etkilemez.</span><span class="sxs-lookup"><span data-stu-id="7b671-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="7b671-107">Ayrıca, <xref:System.Windows.Forms.Form.CenterToParent%2A> yöntemi MDI alt formlarını davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="7b671-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b671-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7b671-108">In This Section</span></span>  
 [<span data-ttu-id="7b671-109">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b671-109">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="7b671-110">Bir MDI uygulaması içinde birden çok belge için bir kapsayıcı oluşturma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b671-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="7b671-111">Nasıl yapılır: MDI alt formları oluştur</span><span class="sxs-lookup"><span data-stu-id="7b671-111">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="7b671-112">MDI üst formu içinde çalışan bir veya daha fazla windows oluşturma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b671-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="7b671-113">Nasıl yapılır: Etkin MDI alt öğesini belirleme</span><span class="sxs-lookup"><span data-stu-id="7b671-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="7b671-114">Odağa sahip alt pencerenin doğrulamak için yönergeler sağlar (ve içeriği panoya gönderme).</span><span class="sxs-lookup"><span data-stu-id="7b671-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="7b671-115">Nasıl yapılır: Etkin MDI alt öğesine veri gönderme</span><span class="sxs-lookup"><span data-stu-id="7b671-115">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="7b671-116">Etkin alt penceresine bilgi taşıma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b671-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="7b671-117">Nasıl yapılır: MDI alt formlarını düzenleme</span><span class="sxs-lookup"><span data-stu-id="7b671-117">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="7b671-118">Döşeme, geçişli veya uygulamanın MDI alt pencereleri düzenleme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b671-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>

---
title: Çoklu Belge Arabirimi (MDI) Uygulamaları
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 3fa6f2517b52ecaaf4ad9db4f0de55908eac4c96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523974"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="2c49b-102">Çoklu Belge Arabirimi (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="2c49b-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="2c49b-103">Birden çok belge arabirimi (MDI) uygulamaları, kendi penceresinde görüntülenen her belgeyle aynı anda birden çok belgeleri görüntülemek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="2c49b-104">MDI uygulamaları genellikle windows veya belgeler arasında geçiş yapmak için alt menüler pencere Menü öğesiyle sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c49b-105">Bazı Windows Forms MDI formları tek belge arabirimi (SDI) windows arasındaki davranış farklılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="2c49b-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="2c49b-106">`Opacity` Özelliği MDI alt formları görünümünü etkilemez.</span><span class="sxs-lookup"><span data-stu-id="2c49b-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="2c49b-107">Ayrıca, <xref:System.Windows.Forms.Form.CenterToParent%2A> yöntemi MDI alt formları davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="2c49b-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c49b-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2c49b-108">In This Section</span></span>  
 [<span data-ttu-id="2c49b-109">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2c49b-109">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="2c49b-110">MDI uygulama içinde birden çok belge için bir kapsayıcı oluşturma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c49b-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="2c49b-111">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2c49b-111">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="2c49b-112">MDI üst formu içinde çalışan bir veya daha fazla windows oluşturma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c49b-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="2c49b-113">Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme</span><span class="sxs-lookup"><span data-stu-id="2c49b-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="2c49b-114">Odaklanmış alt pencere doğrulama için yönergeler sağlar (ve içeriğini panoya gönderme).</span><span class="sxs-lookup"><span data-stu-id="2c49b-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="2c49b-115">Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="2c49b-115">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="2c49b-116">Etkin alt pencere bilgileri taşıma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c49b-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="2c49b-117">Nasıl yapılır: MDI Alt Formlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="2c49b-117">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="2c49b-118">Döşeme, geçişli veya uygulamanın MDI alt pencereleri düzenleme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c49b-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>

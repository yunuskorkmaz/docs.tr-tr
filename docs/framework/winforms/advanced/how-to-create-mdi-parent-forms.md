---
title: "Nasıl yapılır: MDI Üst Formları Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f768e01981f75e5e322fd984e73ccf7b185c5e20
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="be026-102">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="be026-102">How to: Create MDI Parent Forms</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="be026-103">Bu konuda kullanan <xref:System.Windows.Forms.MainMenu> almıştır denetim <xref:System.Windows.Forms.MenuStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="be026-103">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="be026-104"><xref:System.Windows.Forms.MainMenu> Denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="be026-104">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span>  <span data-ttu-id="be026-105">Bir MDI oluşturma hakkında daha fazla bilgi için Form kullanarak üst bir <xref:System.Windows.Forms.MenuStrip>, bkz: [nasıl yapılır: MenuStrip ile MDI pencere listesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="be026-105">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>  
  
 <span data-ttu-id="be026-106">Bir Çoklu belge arabirimi (MDI) uygulaması MDI üst formu temelidir.</span><span class="sxs-lookup"><span data-stu-id="be026-106">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="be026-107">Bu kullanıcı ile MDI uygulama müşteriyle etkileşim alt Windows MDI alt pencereleri içeren formdur.</span><span class="sxs-lookup"><span data-stu-id="be026-107">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="be026-108">MDI üst formu oluşturma Windows Form Tasarımcısı hem program aracılığıyla kolaydır.</span><span class="sxs-lookup"><span data-stu-id="be026-108">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="be026-109">Tasarım zamanında MDI üst formu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="be026-109">To create an MDI parent form at design time</span></span>  
  
1.  <span data-ttu-id="be026-110">Bir Windows uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be026-110">Create a Windows Application project.</span></span>  
  
2.  <span data-ttu-id="be026-111">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğine **doğru**.</span><span class="sxs-lookup"><span data-stu-id="be026-111">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>  
  
     <span data-ttu-id="be026-112">Bu, formun alt windows için bir MDI kapsayıcı olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="be026-112">This designates the form as an MDI container for child windows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be026-113">Özellikleri ayarlama sırasında **özellikleri** penceresinde de ayarlayabilirsiniz `WindowState` özelliğine **Maximized**isterseniz, üst formu olduğunda MDI alt pencereleri işlemek kolay olduğundan ekranı.</span><span class="sxs-lookup"><span data-stu-id="be026-113">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="be026-114">Ayrıca, MDI üst formun kenarına sistem rengi (Windows Sistem Denetim Masası'nda kümesi) çeker, yerine arka plan rengi kullanılarak ayarlanan unutmayın <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="be026-114">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>  
  
3.  <span data-ttu-id="be026-115">Gelen **araç**, sürükleyin bir **MenuStrip** forma denetim.</span><span class="sxs-lookup"><span data-stu-id="be026-115">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="be026-116">Bir üst düzey menü öğesi oluşturma **metin** özelliğini **& Dosya** adlı alt menü öğeleriyle **& Yeni** ve **& Kapat**.</span><span class="sxs-lookup"><span data-stu-id="be026-116">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="be026-117">Ayrıca bir en üst düzey menü öğesi adlı oluşturmak **& penceresi**.</span><span class="sxs-lookup"><span data-stu-id="be026-117">Also create a top-level menu item called **&Window**.</span></span>  
  
     <span data-ttu-id="be026-118">İlk menü oluşturma ve çalışma zamanında menü öğelerini gizleme ve ikinci menüsü açık MDI alt pencereleri izlemek.</span><span class="sxs-lookup"><span data-stu-id="be026-118">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="be026-119">Bu noktada, MDI üst penceresine oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="be026-119">At this point, you have created an MDI parent window.</span></span>  
  
4.  <span data-ttu-id="be026-120">Tuşuna **F5** uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="be026-120">Press **F5** to run the application.</span></span> <span data-ttu-id="be026-121">MDI alt MDI üst form içinde çalışan windows oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: MDI alt formları oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="be026-121">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be026-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be026-122">See Also</span></span>  
 [<span data-ttu-id="be026-123">Birden çok belge arabirimi (MDI) uygulamaları</span><span class="sxs-lookup"><span data-stu-id="be026-123">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="be026-124">Nasıl yapılır: MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="be026-124">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="be026-125">Nasıl yapılır: etkin MDI alt öğesini belirleme</span><span class="sxs-lookup"><span data-stu-id="be026-125">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="be026-126">Nasıl yapılır: etkin MDI alt öğesine veri gönderme</span><span class="sxs-lookup"><span data-stu-id="be026-126">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="be026-127">Nasıl yapılır: MDI alt formlarını düzenleme</span><span class="sxs-lookup"><span data-stu-id="be026-127">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)

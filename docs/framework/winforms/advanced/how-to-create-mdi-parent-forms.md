---
title: 'Nasıl yapılır: MDI Üst Formları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d3ec2e16f06169790711c92c9d445ae93ee50c95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338663"
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="55a78-102">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="55a78-102">How to: Create MDI Parent Forms</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="55a78-103">Bu konuda kullanan <xref:System.Windows.Forms.MainMenu> almıştır denetimi <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="55a78-103">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="55a78-104"><xref:System.Windows.Forms.MainMenu> Denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="55a78-104">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span>  <span data-ttu-id="55a78-105">Bir MDI oluşturma hakkında daha fazla bilgi formu kullanarak üst bir <xref:System.Windows.Forms.MenuStrip>, bkz: [nasıl yapılır: MenuStrip ile MDI pencere listesi oluşturma](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="55a78-105">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>  
  
 <span data-ttu-id="55a78-106">Bir Çoklu belge arabirimi (MDI) uygulaması MDI üst formunun altyapıdır.</span><span class="sxs-lookup"><span data-stu-id="55a78-106">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="55a78-107">Bu gibi kullanıcı MDI uygulamayla etkileşimiyle alt pencereleri MDI alt pencereleri içeren biçimidir.</span><span class="sxs-lookup"><span data-stu-id="55a78-107">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="55a78-108">Bir MDI üst formu oluşturma Windows Form Tasarımcısı hem de program aracılığıyla kolaydır.</span><span class="sxs-lookup"><span data-stu-id="55a78-108">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="55a78-109">Tasarım zamanında MDI üst formu oluşturma</span><span class="sxs-lookup"><span data-stu-id="55a78-109">To create an MDI parent form at design time</span></span>  
  
1. <span data-ttu-id="55a78-110">Bir Windows uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55a78-110">Create a Windows Application project.</span></span>  
  
2. <span data-ttu-id="55a78-111">İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini **true**.</span><span class="sxs-lookup"><span data-stu-id="55a78-111">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>  
  
     <span data-ttu-id="55a78-112">Bu, form alt pencereler için bir MDI kapsayıcısı olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="55a78-112">This designates the form as an MDI container for child windows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="55a78-113">Özellikleri ayarlanırken **özellikleri** penceresinde de ayarlayabilirsiniz `WindowState` özelliğini **Maximized**isterseniz, üst formu olduğunda MDI alt pencereleri yönetmek kolay olduğu gibi ekranı.</span><span class="sxs-lookup"><span data-stu-id="55a78-113">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="55a78-114">Ayrıca, edge MDI üst formunun sistem rengi (Windows Sistem Denetim Masası'nda ayarlanan) seçer, arka plan rengi yerine kullanılarak ayarlanan unutmayın <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="55a78-114">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>  
  
3. <span data-ttu-id="55a78-115">Gelen **araç kutusu**, sürükleyin bir **MenuStrip** forma.</span><span class="sxs-lookup"><span data-stu-id="55a78-115">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="55a78-116">Üst düzey menü öğesiyle oluşturma **metin** özelliğini **& Dosya** adlı alt öğeleri ile **& Yeni** ve **& Kapat**.</span><span class="sxs-lookup"><span data-stu-id="55a78-116">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="55a78-117">Bir üst düzey menü öğesi adlı oluşturabilir **& Pencere**.</span><span class="sxs-lookup"><span data-stu-id="55a78-117">Also create a top-level menu item called **&Window**.</span></span>  
  
     <span data-ttu-id="55a78-118">İlk menüsü oluşturabilir ve çalışma zamanında menü öğelerini gizleme ve ikinci menüsünün açık MDI alt pencereleri izlemek.</span><span class="sxs-lookup"><span data-stu-id="55a78-118">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="55a78-119">Bu noktada, MDI üst penceresine oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="55a78-119">At this point, you have created an MDI parent window.</span></span>  
  
4. <span data-ttu-id="55a78-120">Tuşuna **F5** uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="55a78-120">Press **F5** to run the application.</span></span> <span data-ttu-id="55a78-121">MDI alt MDI üst formu içinde çalışan windows oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: MDI alt formları Oluştur](how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="55a78-121">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a78-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55a78-122">See also</span></span>

- [<span data-ttu-id="55a78-123">Çok Belgeli Arabirim (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="55a78-123">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="55a78-124">Nasıl yapılır: MDI alt formları oluştur</span><span class="sxs-lookup"><span data-stu-id="55a78-124">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="55a78-125">Nasıl yapılır: Etkin MDI alt öğesini belirleme</span><span class="sxs-lookup"><span data-stu-id="55a78-125">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="55a78-126">Nasıl yapılır: Etkin MDI alt öğesine veri gönderme</span><span class="sxs-lookup"><span data-stu-id="55a78-126">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="55a78-127">Nasıl yapılır: MDI alt formlarını düzenleme</span><span class="sxs-lookup"><span data-stu-id="55a78-127">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)

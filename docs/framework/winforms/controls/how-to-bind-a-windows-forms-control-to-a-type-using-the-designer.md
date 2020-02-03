---
title: Tasarımcıyı kullanarak bir türe denetim bağlama
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 2257489e123ceeea819ad3538952db51b726c7e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742023"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="738f2-102">Nasıl yapılır: Tasarımcı Kullanarak bir Windows Formları Denetimini bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="738f2-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>

<span data-ttu-id="738f2-103">Verilerle etkileşen denetimleri oluştururken, bazen bir denetimi bir nesne yerine bir türe bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="738f2-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="738f2-104">Genellikle bir denetimi tasarım zamanında bir türe bağlamanız gerekir, ancak veriler kullanılamayabilir, ancak yine de veri bağlama denetimlerinizi bir türün ortak arabiriminden verileri görüntülemesini istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="738f2-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="738f2-105">Aşağıdaki yordamlarda, bir türe bağlı yeni <xref:System.Windows.Forms.BindingSource> oluşturma ve ardından türün özelliklerinden birinin bir <xref:System.Windows.Forms.TextBox><xref:System.Windows.Forms.TextBox.Text%2A> özelliğine nasıl bağlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="738f2-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>

### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="738f2-106">BindingSource 'un bir türe bağlanması için</span><span class="sxs-lookup"><span data-stu-id="738f2-106">To bind the BindingSource to a type</span></span>

1. <span data-ttu-id="738f2-107">Windows Forms projesi oluşturun (**Dosya** > **Yeni** > **Proje** > **görsel C#**  veya **Visual Basic** > **Klasik Masaüstü** > Windows Forms **uygulaması**).</span><span class="sxs-lookup"><span data-stu-id="738f2-107">Create a Windows Forms project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="738f2-108">**Tasarım** görünümü ' nde, form üzerine bir <xref:System.Windows.Forms.BindingSource> bileşeni sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="738f2-108">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>

3. <span data-ttu-id="738f2-109">**Özellikler** penceresinde <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğinin okuna tıklayın.</span><span class="sxs-lookup"><span data-stu-id="738f2-109">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>

4. <span data-ttu-id="738f2-110">**DataSource Kullanıcı arabirimi türü düzenleyicisinde**, **proje veri kaynağı Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="738f2-110">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>

5. <span data-ttu-id="738f2-111">**Veri kaynağı türü seçin** sayfasında, **nesne** ' yi seçin ve **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="738f2-111">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>

6. <span data-ttu-id="738f2-112">Bağlanacak türü seçin:</span><span class="sxs-lookup"><span data-stu-id="738f2-112">Select the type to bind to:</span></span>

    - <span data-ttu-id="738f2-113">Bağlamak istediğiniz tür geçerli projede ise veya türü içeren derleme zaten başvuru olarak eklendiyse, istediğiniz türü bulmak için düğümleri genişletin ve ardından seçin.</span><span class="sxs-lookup"><span data-stu-id="738f2-113">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>

      <span data-ttu-id="738f2-114">\-veya-</span><span class="sxs-lookup"><span data-stu-id="738f2-114">\-or-</span></span>

    - <span data-ttu-id="738f2-115">Bağlamak istediğiniz tür diğer bir derlemede ise, şu anda başvuru listesinde değilse, **Başvuru Ekle**' ye tıklayın ve ardından **Projeler** sekmesine tıklayın. istediğiniz Iş nesnesini Içeren projeyi seçin ve **Tamam 'a**tıklayın.</span><span class="sxs-lookup"><span data-stu-id="738f2-115">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="738f2-116">Bu proje, derlemeler listesinde görünür, böylece istediğiniz türü bulmak için düğümleri genişletebilir ve ardından bunu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="738f2-116">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>

      > [!NOTE]
      > <span data-ttu-id="738f2-117">Bir Framework veya Microsoft derlemesinde bir türe bağlamak istiyorsanız, **Microsoft veya System ile başlayan derlemeleri Gizle** onay kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="738f2-117">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>

7. <span data-ttu-id="738f2-118">**İleri**'ye ve ardından **Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="738f2-118">Click **Next**, and then click **Finish**.</span></span>

### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="738f2-119">Denetimi BindingSource 'a bağlamak için</span><span class="sxs-lookup"><span data-stu-id="738f2-119">To bind the control to the BindingSource</span></span>

1. <span data-ttu-id="738f2-120">Forma <xref:System.Windows.Forms.TextBox> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="738f2-120">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>

2. <span data-ttu-id="738f2-121">**Özellikler** penceresinde **(DataBindings)** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="738f2-121">In the **Properties** window, expand the **(DataBindings)** node.</span></span>

3. <span data-ttu-id="738f2-122"><xref:System.Windows.Forms.TextBox.Text%2A> özelliğinin yanındaki oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="738f2-122">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

4. <span data-ttu-id="738f2-123">**DataSource Kullanıcı arabirimi türü düzenleyicisinde**, daha önce eklenen <xref:System.Windows.Forms.BindingSource> düğümünü genişletin ve <xref:System.Windows.Forms.TextBox><xref:System.Windows.Forms.TextBox.Text%2A> özelliğine bağlamak istediğiniz bağlı türün özelliğini seçin.</span><span class="sxs-lookup"><span data-stu-id="738f2-123">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="see-also"></a><span data-ttu-id="738f2-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="738f2-124">See also</span></span>

- [<span data-ttu-id="738f2-125">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="738f2-125">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="738f2-126">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="738f2-126">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
- [<span data-ttu-id="738f2-127">Visual Studio'da verilere denetimler bağlama</span><span class="sxs-lookup"><span data-stu-id="738f2-127">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

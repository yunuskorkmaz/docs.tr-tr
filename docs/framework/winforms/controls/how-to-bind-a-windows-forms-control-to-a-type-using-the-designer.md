---
title: 'Nasıl yapılır: Tasarımcı Kullanarak bir Windows Forms Denetimini bir Türe Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 5069d7d3b5ef4c5b05159dac521d32f5be8abdd1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046039"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="73c63-102">Nasıl yapılır: Tasarımcı Kullanarak bir Windows Forms Denetimini bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="73c63-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>

<span data-ttu-id="73c63-103">Verilerle etkileşen denetimleri oluştururken, bazen bir denetimi bir nesne yerine bir türe bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73c63-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="73c63-104">Genellikle bir denetimi tasarım zamanında bir türe bağlamanız gerekir, ancak veriler kullanılamayabilir, ancak yine de veri bağlama denetimlerinizi bir türün ortak arabiriminden verileri görüntülemesini istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="73c63-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="73c63-105">Aşağıdaki yordamlarda, bir türe bağlı yeni <xref:System.Windows.Forms.BindingSource> bir oluşturma ve ardından türün özelliklerinden <xref:System.Windows.Forms.TextBox.Text%2A> birinin bir <xref:System.Windows.Forms.TextBox>özelliğine nasıl bağlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73c63-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>

### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="73c63-106">BindingSource 'un bir türe bağlanması için</span><span class="sxs-lookup"><span data-stu-id="73c63-106">To bind the BindingSource to a type</span></span>

1. <span data-ttu-id="73c63-107">Windows Forms projesi oluşturma (**Dosya** > **Yeni** > **Proje** > **görseli C#**  veya **Visual Basic** **Klasik** Masaüstü >   >  **Windows Forms uygulama**).</span><span class="sxs-lookup"><span data-stu-id="73c63-107">Create a Windows Forms project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="73c63-108">**Tasarım** görünümü ' nde bir <xref:System.Windows.Forms.BindingSource> bileşeni formun üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="73c63-108">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>

3. <span data-ttu-id="73c63-109">**Özellikler** penceresinde, <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğin okuna tıklayın.</span><span class="sxs-lookup"><span data-stu-id="73c63-109">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>

4. <span data-ttu-id="73c63-110">**DataSource Kullanıcı arabirimi türü düzenleyicisinde**, **proje veri kaynağı Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="73c63-110">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>

5. <span data-ttu-id="73c63-111">**Veri kaynağı türü seçin** sayfasında, **nesne** ' yi seçin ve **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="73c63-111">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>

6. <span data-ttu-id="73c63-112">Bağlanacak türü seçin:</span><span class="sxs-lookup"><span data-stu-id="73c63-112">Select the type to bind to:</span></span>

    - <span data-ttu-id="73c63-113">Bağlamak istediğiniz tür geçerli projede ise veya türü içeren derleme zaten başvuru olarak eklendiyse, istediğiniz türü bulmak için düğümleri genişletin ve ardından seçin.</span><span class="sxs-lookup"><span data-stu-id="73c63-113">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>

      <span data-ttu-id="73c63-114">\-veya</span><span class="sxs-lookup"><span data-stu-id="73c63-114">\-or-</span></span>

    - <span data-ttu-id="73c63-115">Bağlamak istediğiniz tür başka bir derlemede ise, şu anda başvurular listesinde yer alıyorsa, **Başvuru Ekle**' ye tıklayın ve ardından **Projeler** sekmesine tıklayın. İstediğiniz iş nesnesini içeren projeyi seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="73c63-115">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="73c63-116">Bu proje, derlemeler listesinde görünür, böylece istediğiniz türü bulmak için düğümleri genişletebilir ve ardından bunu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73c63-116">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>

      > [!NOTE]
      > <span data-ttu-id="73c63-117">Bir Framework veya Microsoft derlemesinde bir türe bağlamak istiyorsanız, **Microsoft veya System ile başlayan derlemeleri Gizle** onay kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="73c63-117">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>

7. <span data-ttu-id="73c63-118">**İleri**'ye ve ardından **Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="73c63-118">Click **Next**, and then click **Finish**.</span></span>

### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="73c63-119">Denetimi BindingSource 'a bağlamak için</span><span class="sxs-lookup"><span data-stu-id="73c63-119">To bind the control to the BindingSource</span></span>

1. <span data-ttu-id="73c63-120">Forma bir <xref:System.Windows.Forms.TextBox> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="73c63-120">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>

2. <span data-ttu-id="73c63-121">**Özellikler** penceresinde **(DataBindings)** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="73c63-121">In the **Properties** window, expand the **(DataBindings)** node.</span></span>

3. <span data-ttu-id="73c63-122"><xref:System.Windows.Forms.TextBox.Text%2A> Özelliğin yanındaki oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="73c63-122">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

4. <span data-ttu-id="73c63-123">**DataSource Kullanıcı arabirimi türü düzenleyicisinde**, daha önce <xref:System.Windows.Forms.BindingSource> eklenen için düğümünü genişletin ve <xref:System.Windows.Forms.TextBox.Text%2A> özelliğine <xref:System.Windows.Forms.TextBox>bağlamak istediğiniz bağlı türün özelliğini seçin.</span><span class="sxs-lookup"><span data-stu-id="73c63-123">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="see-also"></a><span data-ttu-id="73c63-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73c63-124">See also</span></span>

- [<span data-ttu-id="73c63-125">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="73c63-125">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="73c63-126">Nasıl yapılır: Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="73c63-126">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
- [<span data-ttu-id="73c63-127">Visual Studio'da verilere denetimler bağlama</span><span class="sxs-lookup"><span data-stu-id="73c63-127">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

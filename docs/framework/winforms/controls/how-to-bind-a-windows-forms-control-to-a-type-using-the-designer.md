---
title: 'Nasıl yapılır: Tasarımcı Kullanarak bir Windows Forms Denetimini bir Türe Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: b298efb0494994659673f9bf9893b667f7eb0f8c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304220"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="7b9e5-102">Nasıl yapılır: Tasarımcı Kullanarak bir Windows Forms Denetimini bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="7b9e5-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>
<span data-ttu-id="7b9e5-103">Verilerle etkileşimde bulunmak denetimleri oluştururken, bazen bir nesne yerine bir tür bir denetimine bağlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="7b9e5-104">Genelde bir denetimi tasarım zamanında ne zaman veri kullanılamıyor olabilir, ancak yine de bir türün ortak arabirim verileri görüntülemek için verilere bağlı denetimler istediğiniz bir türe bağlama gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="7b9e5-105">Aşağıdaki yordamlar yeni bir oluşturma işlemini göstermektedir <xref:System.Windows.Forms.BindingSource> olan bir türü için sınır ve sonra nasıl bir türün özelliklerine bağlanacağını <xref:System.Windows.Forms.TextBox.Text%2A> özelliği bir <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="7b9e5-106">BindingSource bir türe bağlama için</span><span class="sxs-lookup"><span data-stu-id="7b9e5-106">To bind the BindingSource to a type</span></span>  
  
1. <span data-ttu-id="7b9e5-107">Bir Windows Forms projesi oluşturun (**dosya** > **yeni** > **proje** > **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).</span><span class="sxs-lookup"><span data-stu-id="7b9e5-107">Create a Windows Forms project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2. <span data-ttu-id="7b9e5-108">İçinde **tasarım** görüntülemek için sürükleyin bir <xref:System.Windows.Forms.BindingSource> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-108">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>  
  
3. <span data-ttu-id="7b9e5-109">İçinde **özellikleri** penceresinde için oka tıklayın <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-109">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>  
  
4. <span data-ttu-id="7b9e5-110">İçinde **DataSource UI türü düzenleyici**, tıklayın **proje veri kaynağı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-110">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>  
  
5. <span data-ttu-id="7b9e5-111">Üzerinde **bir veri kaynağı türü seçin** sayfasında **nesne** tıklatıp **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-111">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>  
  
6. <span data-ttu-id="7b9e5-112">Bağlanılacak türünü seçin:</span><span class="sxs-lookup"><span data-stu-id="7b9e5-112">Select the type to bind to:</span></span>  
  
    -   <span data-ttu-id="7b9e5-113">Bağlamak istediğiniz türü geçerli projede veya türü içeren derlemeye bir başvuru olarak zaten eklendi, istediğiniz türünü bulmak için düğümleri genişletin ve ardından bu seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-113">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>  
  
         <span data-ttu-id="7b9e5-114">-veya-</span><span class="sxs-lookup"><span data-stu-id="7b9e5-114">-or-</span></span>  
  
    -   <span data-ttu-id="7b9e5-115">Bağlamak istediğiniz türü olan başvuruları listesinde şu anda başka bir derlemede tıklarsanız **Başvuru Ekle**ve ardından **projeleri** sekmesi. ' A tıklayın ve istediğiniz iş nesnesi içeren projeyi seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-115">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="7b9e5-116">Bu proje, derleme, listede görünür türü bulmak için düğümleri genişletebilirsiniz. Bu nedenle, istediğiniz ve ardından bu seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-116">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="7b9e5-117">Framework ya da Microsoft derlemesi bir tür bağlamak istiyorsanız, Temizle **Gizle Microsoft veya sistem başlayan derlemeleri** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-117">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>  
  
7. <span data-ttu-id="7b9e5-118">**İleri**'ye ve ardından **Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-118">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="7b9e5-119">Denetimi için BindingSource bağlamak için</span><span class="sxs-lookup"><span data-stu-id="7b9e5-119">To bind the control to the BindingSource</span></span>  
  
1. <span data-ttu-id="7b9e5-120">Ekleme bir <xref:System.Windows.Forms.TextBox> form.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-120">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>  
  
2. <span data-ttu-id="7b9e5-121">İçinde **özellikleri** penceresini genişletin **(DataBindings)** düğümü.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-121">In the **Properties** window, expand the **(DataBindings)** node.</span></span>  
  
3. <span data-ttu-id="7b9e5-122">Yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-122">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
4. <span data-ttu-id="7b9e5-123">İçinde **DataSource UI türü düzenleyici**, düğümünü genişletin <xref:System.Windows.Forms.BindingSource> daha önce eklenmiş ve istediğiniz bağlamak için ilişkili tür özelliğine seçin <xref:System.Windows.Forms.TextBox.Text%2A> özelliği <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-123">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b9e5-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b9e5-124">See also</span></span>

- [<span data-ttu-id="7b9e5-125">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="7b9e5-125">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="7b9e5-126">Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="7b9e5-126">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
- [<span data-ttu-id="7b9e5-127">Visual Studio'da verilere denetimler bağlama</span><span class="sxs-lookup"><span data-stu-id="7b9e5-127">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

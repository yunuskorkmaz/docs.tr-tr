---
title: 'Nasıl yapılır: Tasarımcı Kullanarak bir Windows Formları Denetimini bir Türe Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: a58a528cd1a2246ddfdff7997b7c7cb0d8dcc6a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531059"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="a29ed-102">Nasıl yapılır: Tasarımcı Kullanarak bir Windows Formları Denetimini bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="a29ed-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>
<span data-ttu-id="a29ed-103">Verilerle etkileşimli denetimleri oluştururken, bazen bir nesne yerine bir tür bir denetimi bağlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="a29ed-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="a29ed-104">Genellikle bir denetim tasarım zamanında ne zaman veri kullanılamıyor olabilir, ancak hala bir türün ortak arabirimi verileri görüntülemek için veri bağlama denetimleri istediğiniz bir türe bağlama gerekir.</span><span class="sxs-lookup"><span data-stu-id="a29ed-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="a29ed-105">Aşağıdaki yordamlarda yeni bir oluşturma gösterilmektedir <xref:System.Windows.Forms.BindingSource> diğer bir deyişle bir tür için sınır ve ardından tür özelliklerinden biri nasıl bağlanacağı <xref:System.Windows.Forms.TextBox.Text%2A> özelliği bir <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="a29ed-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="a29ed-106">BindingSource bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="a29ed-106">To bind the BindingSource to a type</span></span>  
  
1.  <span data-ttu-id="a29ed-107">Bir Windows Forms projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a29ed-107">Create a Windows Forms project.</span></span>  
  
     <span data-ttu-id="a29ed-108">Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="a29ed-108">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="a29ed-109">İçinde **tasarım** görüntülemek için sürükleyin bir <xref:System.Windows.Forms.BindingSource> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="a29ed-109">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>  
  
3.  <span data-ttu-id="a29ed-110">İçinde **özellikleri** penceresinde oka tıklayın <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a29ed-110">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>  
  
4.  <span data-ttu-id="a29ed-111">İçinde **DataSource UI türü düzenleyici**, tıklatın **proje veri kaynağı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a29ed-111">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>  
  
5.  <span data-ttu-id="a29ed-112">Üzerinde **bir veri kaynağı türü seç** sayfasında, **nesne** tıklatıp **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a29ed-112">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>  
  
6.  <span data-ttu-id="a29ed-113">Bağlamak üzere türünü seçin:</span><span class="sxs-lookup"><span data-stu-id="a29ed-113">Select the type to bind to:</span></span>  
  
    -   <span data-ttu-id="a29ed-114">Bağlamak istediğiniz türü geçerli proje veya türünü içeren bütünleştirilmiş kodun bir başvuru olarak zaten eklendi istediğiniz türünü bulmak için düğümleri genişletin ve ardından seçin.</span><span class="sxs-lookup"><span data-stu-id="a29ed-114">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>  
  
         <span data-ttu-id="a29ed-115">-veya-</span><span class="sxs-lookup"><span data-stu-id="a29ed-115">-or-</span></span>  
  
    -   <span data-ttu-id="a29ed-116">Bağlamak istediğiniz türü olan başvuruları listesinde şu anda başka bir derlemede tıklatırsanız **Başvuru Ekle**ve ardından **projeleri** sekmesi. İstediğiniz iş nesnesini içeren projeyi seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="a29ed-116">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="a29ed-117">Bu proje derlemeler, listede görünür türü bulmak için düğümlerini genişletin şekilde, istediğiniz ve ardından seçin.</span><span class="sxs-lookup"><span data-stu-id="a29ed-117">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a29ed-118">Bir türe framework ya da Microsoft derleme bağlamak istiyorsanız, temizleyin **Gizle Microsoft veya sistem başlayan derlemeleri** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="a29ed-118">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>  
  
7.  <span data-ttu-id="a29ed-119">**İleri**'ye ve ardından **Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a29ed-119">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="a29ed-120">BindingSource denetimi bağlamak için</span><span class="sxs-lookup"><span data-stu-id="a29ed-120">To bind the control to the BindingSource</span></span>  
  
1.  <span data-ttu-id="a29ed-121">Ekleme bir <xref:System.Windows.Forms.TextBox> form.</span><span class="sxs-lookup"><span data-stu-id="a29ed-121">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>  
  
2.  <span data-ttu-id="a29ed-122">İçinde **özellikleri** penceresinde genişletin **(veri bağlamaları)** düğümü.</span><span class="sxs-lookup"><span data-stu-id="a29ed-122">In the **Properties** window, expand the **(DataBindings)** node.</span></span>  
  
3.  <span data-ttu-id="a29ed-123">Yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a29ed-123">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
4.  <span data-ttu-id="a29ed-124">İçinde **DataSource UI türü düzenleyici**, düğümünü genişletin <xref:System.Windows.Forms.BindingSource> daha önce eklediğiniz ve bağlamak istediğiniz ilişkili tür özelliğine seçin <xref:System.Windows.Forms.TextBox.Text%2A> özelliği <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="a29ed-124">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29ed-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a29ed-125">See Also</span></span>  
 [<span data-ttu-id="a29ed-126">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="a29ed-126">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="a29ed-127">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="a29ed-127">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [<span data-ttu-id="a29ed-128">Visual Studio'da verilere denetimler bağlama</span><span class="sxs-lookup"><span data-stu-id="a29ed-128">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

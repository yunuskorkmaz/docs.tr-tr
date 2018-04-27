---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a1d4a6abd35642bc1e73ea52195ba740833baad
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="e2fff-102">Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="e2fff-102">How to: Bind Data to the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e2fff-103"><xref:System.Windows.Forms.DataGridView> Denetimi, çeşitli veri kaynakları için bağlı olacağı şekilde standart Windows Forms veri bağlama modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="e2fff-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to a variety of data sources.</span></span> <span data-ttu-id="e2fff-104">Çoğu durumda, ancak siz bağlanacağı bir <xref:System.Windows.Forms.BindingSource> veri kaynağıyla etkileşim ayrıntılarını yönetecek bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e2fff-104">In most circumstances, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component which will manage the details of interacting with the data source.</span></span> <span data-ttu-id="e2fff-105"><xref:System.Windows.Forms.BindingSource> Bileşeni herhangi bir Windows Forms veri kaynağını temsil edebilir ve seçme veya değiştirirken, verilerin konumu büyük esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2fff-105">The <xref:System.Windows.Forms.BindingSource> component can represent any Windows Forms data source and gives you great flexibility when choosing or modifying the location of your data.</span></span> <span data-ttu-id="e2fff-106">Tarafından desteklenen veri kaynakları hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e2fff-106">For more information about the data sources supported by the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="e2fff-107">Visual Studio'da bu görev için kapsamlı destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="e2fff-107">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="e2fff-108">Ayrıca bkz. [nasıl yapılır: Windows Forms DataGridView denetimi kullanarak Tasarımcı veri bağlama](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e2fff-108">Also see [How to: Bind Data to the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="e2fff-109">Yordam</span><span class="sxs-lookup"><span data-stu-id="e2fff-109">Procedure</span></span>  
  
#### <a name="to-connect-a-datagridview-control-to-data"></a><span data-ttu-id="e2fff-110">DataGridView denetimine veri bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="e2fff-110">To connect a DataGridView control to data</span></span>  
  
1.  <span data-ttu-id="e2fff-111">Bir veritabanından veri alma ayrıntılarını işlemek için koruma yöntemi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2fff-111">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="e2fff-112">Aşağıdaki kod örneği uygulayan bir `GetData` başlatır yöntemi bir <xref:System.Data.SqlClient.SqlDataAdapter> bileşen ve doldurmak için kullandığı bir <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="e2fff-112">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="e2fff-113"><xref:System.Data.DataTable> Sonra bağlı <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e2fff-113">The <xref:System.Data.DataTable> is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="e2fff-114">Ayarladığınızdan emin olun `connectionString` değişken veritabanınız için uygun olan bir değer.</span><span class="sxs-lookup"><span data-stu-id="e2fff-114">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="e2fff-115">Northwind SQL Server örnek veritabanı yüklenmiş bir sunucuya erişimi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2fff-115">You will need access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  <span data-ttu-id="e2fff-116">Formun içinde <xref:System.Windows.Forms.Form.Load> olay işleyicisi, BIND <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource> bileşeni ve çağrı `GetData` veritabanından veri almak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="e2fff-116">In your form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="e2fff-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2fff-117">Example</span></span>  
 <span data-ttu-id="e2fff-118">Aşağıdaki tam kod örnek veritabanındaki verileri yeniden yüklemeyi ve değişiklikleri veritabanına göndermek için düğmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2fff-118">The following complete code example provides buttons for reloading data from the database and submitting changes to the database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e2fff-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e2fff-119">Compiling the Code</span></span>  
 <span data-ttu-id="e2fff-120">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e2fff-120">This example requires:</span></span>  
  
-   <span data-ttu-id="e2fff-121">Sistem, System.Windows.Forms, System.Data ve System.XML derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e2fff-121">References to the System, System.Windows.Forms, System.Data, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="e2fff-122">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e2fff-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e2fff-123">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="e2fff-123">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="e2fff-124">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e2fff-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e2fff-125">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e2fff-125">.NET Framework Security</span></span>  
 <span data-ttu-id="e2fff-126">Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="e2fff-126">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="e2fff-127">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="e2fff-127">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="e2fff-128">Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="e2fff-128">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fff-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2fff-129">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="e2fff-130">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e2fff-130">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e2fff-131">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="e2fff-131">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)

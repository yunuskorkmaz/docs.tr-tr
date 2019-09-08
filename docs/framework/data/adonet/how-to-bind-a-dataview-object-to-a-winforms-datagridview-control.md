---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimine DataView Nesnesi Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 3a3089073cdc5afb4ee51caca9114b401c740b45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795008"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="e26ca-102">Nasıl yapılır: Windows Forms DataGridView Denetimine DataView Nesnesi Bağlama</span><span class="sxs-lookup"><span data-stu-id="e26ca-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e26ca-103">Denetim <xref:System.Windows.Forms.DataGridView> , verileri tablolu biçimde görüntülemenin güçlü ve esnek bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="e26ca-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="e26ca-104">Denetim standart Windows Forms veri bağlama modelini destekler, bu nedenle diğer birçok veri kaynağına <xref:System.Data.DataView> bağlanır. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="e26ca-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="e26ca-105">Ancak çoğu durumda, veri kaynağıyla etkileşim ayrıntılarını yönetecek bir <xref:System.Windows.Forms.BindingSource> bileşene bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e26ca-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="e26ca-106"><xref:System.Windows.Forms.DataGridView> Denetim hakkında daha fazla bilgi için bkz. [DataGridView denetimine genel bakış](../../winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e26ca-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="e26ca-107">Bir DataGridView denetimini bir DataView 'a bağlamak için</span><span class="sxs-lookup"><span data-stu-id="e26ca-107">To connect a DataGridView control to a DataView</span></span>  
  
1. <span data-ttu-id="e26ca-108">Veritabanından veri alma ayrıntılarını işlemek için bir yöntem uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e26ca-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="e26ca-109">Aşağıdaki kod örneği, bir `GetData` <xref:System.Data.SqlClient.SqlDataAdapter> bileşeni Başlatan bir yöntemi uygular ve onu doldurması için <xref:System.Data.DataSet>kullanır.</span><span class="sxs-lookup"><span data-stu-id="e26ca-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e26ca-110">Değişkeni, `connectionString` veritabanınız için uygun bir değere ayarladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e26ca-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="e26ca-111">AdventureWorks SQL Server örnek veritabanının yüklü olduğu bir sunucuya erişmeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="e26ca-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. <span data-ttu-id="e26ca-112">Formunuzun olay işleyicisinde, <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.BindingSource> bileşene bağlayın ve verileri veritabanından almak için `GetData` yöntemini çağırın. <xref:System.Windows.Forms.Form.Load></span><span class="sxs-lookup"><span data-stu-id="e26ca-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="e26ca-113">, <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource> Kişi <xref:System.Data.DataTable> üzerinde LINQ to DataSet bir sorgudan oluşturulur ve ardından bileşene bağlanır.</span><span class="sxs-lookup"><span data-stu-id="e26ca-113">The <xref:System.Data.DataView> is created from a LINQ to DataSet query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="e26ca-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e26ca-114">See also</span></span>

- [<span data-ttu-id="e26ca-115">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e26ca-115">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)

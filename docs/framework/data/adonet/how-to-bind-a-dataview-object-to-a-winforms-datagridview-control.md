---
title: 'Nasıl yapılır: bir DataView nesnesi bir Windows Forms DataGridView denetimine bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 98b3afcded257bc11dc3bca7d9a9310dc1a7cc89
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765028"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="3412f-102">Nasıl yapılır: bir DataView nesnesi bir Windows Forms DataGridView denetimine bağlama</span><span class="sxs-lookup"><span data-stu-id="3412f-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3412f-103"><xref:System.Windows.Forms.DataGridView> Denetimi verileri tablo biçiminde görüntülemek için güçlü ve esnek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3412f-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="3412f-104"><xref:System.Windows.Forms.DataGridView> Denetim bağlı olacağı şekilde standart Windows Forms veri bağlama modelini destekleyen <xref:System.Data.DataView> ve çeşitli diğer veri kaynakları.</span><span class="sxs-lookup"><span data-stu-id="3412f-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="3412f-105">Çoğu durumda, ancak siz bağlanacağı bir <xref:System.Windows.Forms.BindingSource> veri kaynağıyla etkileşim ayrıntılarını yönetecek bileşeni.</span><span class="sxs-lookup"><span data-stu-id="3412f-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="3412f-106">Hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3412f-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="3412f-107">DataGridView denetimi için DataView bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="3412f-107">To connect a DataGridView control to a DataView</span></span>  
  
1.  <span data-ttu-id="3412f-108">Bir veritabanından veri alma ayrıntılarını işlemek için koruma yöntemi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3412f-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="3412f-109">Aşağıdaki kod örneği uygulayan bir `GetData` başlatır yöntemi bir <xref:System.Data.SqlClient.SqlDataAdapter> bileşen ve doldurmak için kullandığı bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="3412f-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3412f-110">Ayarladığınızdan emin olun `connectionString` değişken veritabanınız için uygun olan bir değer.</span><span class="sxs-lookup"><span data-stu-id="3412f-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="3412f-111">AdventureWorks SQL Server örnek veritabanı yüklü bir sunucuya erişimi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3412f-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2.  <span data-ttu-id="3412f-112">İçinde <xref:System.Windows.Forms.Form.Load> olay işleyicisi formunuz bağlama <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource> bileşeni ve çağrı `GetData` veritabanından veri almak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="3412f-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="3412f-113"><xref:System.Data.DataView> Oluşturulur bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu kişi üzerinden <xref:System.Data.DataTable> ve ardından bağlı <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="3412f-113">The <xref:System.Data.DataView> is created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="3412f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3412f-114">See Also</span></span>  
 [<span data-ttu-id="3412f-115">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="3412f-115">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)

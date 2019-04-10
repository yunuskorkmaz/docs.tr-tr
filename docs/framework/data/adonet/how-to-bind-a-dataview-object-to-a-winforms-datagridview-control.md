---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimine DataView Nesnesi Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 7a567aa60e226803435b9b2b7b806097e9b47f76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230349"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="0f83e-102">Nasıl yapılır: Windows Forms DataGridView Denetimine DataView Nesnesi Bağlama</span><span class="sxs-lookup"><span data-stu-id="0f83e-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0f83e-103"><xref:System.Windows.Forms.DataGridView> Denetimi verileri tablo biçiminde görüntülemek için güçlü ve esnek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f83e-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="0f83e-104"><xref:System.Windows.Forms.DataGridView> Denetim bağlı olacağı şekilde standart Windows Forms veri bağlama modelini destekleyen <xref:System.Data.DataView> ve çeşitli diğer veri kaynakları.</span><span class="sxs-lookup"><span data-stu-id="0f83e-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="0f83e-105">Çoğu durumda, ancak siz bağlanacağı bir <xref:System.Windows.Forms.BindingSource> veri kaynağıyla etkileşim ayrıntılarını yönetecek bileşeni.</span><span class="sxs-lookup"><span data-stu-id="0f83e-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="0f83e-106">Hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0f83e-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="0f83e-107">DataGridView denetimine DataView nesnesine bağlamak için</span><span class="sxs-lookup"><span data-stu-id="0f83e-107">To connect a DataGridView control to a DataView</span></span>  
  
1.  <span data-ttu-id="0f83e-108">Bir veritabanından veri alma ayrıntılarını işlemek için bir yöntem uygulayın.</span><span class="sxs-lookup"><span data-stu-id="0f83e-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="0f83e-109">Aşağıdaki kod örneğinde uygular bir `GetData` başlatan yöntem bir <xref:System.Data.SqlClient.SqlDataAdapter> bileşeni ve doldurmak için kullandığı bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0f83e-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="0f83e-110">Ayarladığınızdan emin olun `connectionString` değişken veritabanınız için uygun olan bir değer.</span><span class="sxs-lookup"><span data-stu-id="0f83e-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="0f83e-111">Yüklü SQL Server AdventureWorks örnek veritabanı ile bir sunucu için erişim gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f83e-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2.  <span data-ttu-id="0f83e-112">İçinde <xref:System.Windows.Forms.Form.Load> olay işleyicisi formunuza bağlama <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource> bileşen ve çağrıya `GetData` veritabanından veri almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0f83e-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="0f83e-113"><xref:System.Data.DataView> İçinden oluşturulan bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kişi üzerindeki sorgu <xref:System.Data.DataTable> ve ardından bağlı <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="0f83e-113">The <xref:System.Data.DataView> is created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="0f83e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f83e-114">See also</span></span>

- [<span data-ttu-id="0f83e-115">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0f83e-115">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)

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
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimine DataView Nesnesi Bağlama
Denetim <xref:System.Windows.Forms.DataGridView> , verileri tablolu biçimde görüntülemenin güçlü ve esnek bir yolunu sağlar. Denetim standart Windows Forms veri bağlama modelini destekler, bu nedenle diğer birçok veri kaynağına <xref:System.Data.DataView> bağlanır. <xref:System.Windows.Forms.DataGridView> Ancak çoğu durumda, veri kaynağıyla etkileşim ayrıntılarını yönetecek bir <xref:System.Windows.Forms.BindingSource> bileşene bağlayabilirsiniz.  
  
 <xref:System.Windows.Forms.DataGridView> Denetim hakkında daha fazla bilgi için bkz. [DataGridView denetimine genel bakış](../../winforms/controls/datagridview-control-overview-windows-forms.md).  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a>Bir DataGridView denetimini bir DataView 'a bağlamak için  
  
1. Veritabanından veri alma ayrıntılarını işlemek için bir yöntem uygulayın. Aşağıdaki kod örneği, bir `GetData` <xref:System.Data.SqlClient.SqlDataAdapter> bileşeni Başlatan bir yöntemi uygular ve onu doldurması için <xref:System.Data.DataSet>kullanır. Değişkeni, `connectionString` veritabanınız için uygun bir değere ayarladığınızdan emin olun. AdventureWorks SQL Server örnek veritabanının yüklü olduğu bir sunucuya erişmeniz gerekecektir.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. Formunuzun olay işleyicisinde, <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.BindingSource> bileşene bağlayın ve verileri veritabanından almak için `GetData` yöntemini çağırın. <xref:System.Windows.Forms.Form.Load> , <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource> Kişi <xref:System.Data.DataTable> üzerinde LINQ to DataSet bir sorgudan oluşturulur ve ardından bileşene bağlanır.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)

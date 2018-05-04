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
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a>Nasıl yapılır: bir DataView nesnesi bir Windows Forms DataGridView denetimine bağlama
<xref:System.Windows.Forms.DataGridView> Denetimi verileri tablo biçiminde görüntülemek için güçlü ve esnek bir yol sağlar. <xref:System.Windows.Forms.DataGridView> Denetim bağlı olacağı şekilde standart Windows Forms veri bağlama modelini destekleyen <xref:System.Data.DataView> ve çeşitli diğer veri kaynakları. Çoğu durumda, ancak siz bağlanacağı bir <xref:System.Windows.Forms.BindingSource> veri kaynağıyla etkileşim ayrıntılarını yönetecek bileşeni.  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a>DataGridView denetimi için DataView bağlanmak için  
  
1.  Bir veritabanından veri alma ayrıntılarını işlemek için koruma yöntemi uygulayabilirsiniz. Aşağıdaki kod örneği uygulayan bir `GetData` başlatır yöntemi bir <xref:System.Data.SqlClient.SqlDataAdapter> bileşen ve doldurmak için kullandığı bir <xref:System.Data.DataSet>. Ayarladığınızdan emin olun `connectionString` değişken veritabanınız için uygun olan bir değer. AdventureWorks SQL Server örnek veritabanı yüklü bir sunucuya erişimi gerekir.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2.  İçinde <xref:System.Windows.Forms.Form.Load> olay işleyicisi formunuz bağlama <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource> bileşeni ve çağrı `GetData` veritabanından veri almak için yöntem. <xref:System.Data.DataView> Oluşturulur bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu kişi üzerinden <xref:System.Data.DataTable> ve ardından bağlı <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)

---
title: 'Nasıl yapılır: Windows Forms DataGridView denetimine DataView nesnesi bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: e2e8cad453311035332e5a397667835f047184b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548371"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetimine DataView nesnesi bağlama
<xref:System.Windows.Forms.DataGridView> Denetimi verileri tablo biçiminde görüntülemek için güçlü ve esnek bir yol sağlar. <xref:System.Windows.Forms.DataGridView> Denetim bağlı olacağı şekilde standart Windows Forms veri bağlama modelini destekleyen <xref:System.Data.DataView> ve çeşitli diğer veri kaynakları. Çoğu durumda, ancak siz bağlanacağı bir <xref:System.Windows.Forms.BindingSource> veri kaynağıyla etkileşim ayrıntılarını yönetecek bileşeni.  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a>DataGridView denetimine DataView nesnesine bağlamak için  
  
1.  Bir veritabanından veri alma ayrıntılarını işlemek için bir yöntem uygulayın. Aşağıdaki kod örneğinde uygular bir `GetData` başlatan yöntem bir <xref:System.Data.SqlClient.SqlDataAdapter> bileşeni ve doldurmak için kullandığı bir <xref:System.Data.DataSet>. Ayarladığınızdan emin olun `connectionString` değişken veritabanınız için uygun olan bir değer. Yüklü SQL Server AdventureWorks örnek veritabanı ile bir sunucu için erişim gerekir.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2.  İçinde <xref:System.Windows.Forms.Form.Load> olay işleyicisi formunuza bağlama <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource> bileşen ve çağrıya `GetData` veritabanından veri almak için yöntemi. <xref:System.Data.DataView> İçinden oluşturulan bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kişi üzerindeki sorgu <xref:System.Data.DataTable> ve ardından bağlı <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)

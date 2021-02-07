---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: DataView nesnesini Windows Forms DataGridView denetimine bağlama'
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimine DataView Nesnesi Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 59bc1a0f6b7b2b0d6da4fa6d88e06922d95c9f46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723913"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimine DataView Nesnesi Bağlama

<xref:System.Windows.Forms.DataGridView>Denetim, verileri tablolu biçimde görüntülemenin güçlü ve esnek bir yolunu sağlar. <xref:System.Windows.Forms.DataGridView>Denetim standart Windows Forms veri bağlama modelini destekler, bu nedenle <xref:System.Data.DataView> diğer birçok veri kaynağına bağlanır. Ancak çoğu durumda, <xref:System.Windows.Forms.BindingSource> veri kaynağıyla etkileşim ayrıntılarını yönetecek bir bileşene bağlayabilirsiniz.  
  
 Denetim hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> bkz. [DataGridView denetimine genel bakış](/dotnet/desktop/winforms/controls/datagridview-control-overview-windows-forms).  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a>Bir DataGridView denetimini bir DataView 'a bağlamak için  
  
1. Veritabanından veri alma ayrıntılarını işlemek için bir yöntem uygulayın. Aşağıdaki kod örneği, bir `GetData` bileşeni Başlatan bir yöntemi uygular <xref:System.Data.SqlClient.SqlDataAdapter> ve onu doldurması için kullanır <xref:System.Data.DataSet> . `connectionString`Değişkeni, veritabanınız için uygun bir değere ayarladığınızdan emin olun. AdventureWorks SQL Server örnek veritabanının yüklü olduğu bir sunucuya erişmeniz gerekecektir.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. <xref:System.Windows.Forms.Form.Load>Formunuzun olay işleyicisinde, <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.BindingSource> bileşene bağlayın ve `GetData` verileri veritabanından almak için yöntemini çağırın. , <xref:System.Data.DataView> Kişi üzerinde LINQ to DataSet bir sorgudan oluşturulur <xref:System.Data.DataTable> ve ardından <xref:System.Windows.Forms.BindingSource> bileşene bağlanır.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)

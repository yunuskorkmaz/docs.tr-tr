---
title: 'Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama'
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e147109a64687177f201ad1e312fab56ea61d604
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160076"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama

<xref:System.Windows.Forms.DataGridView> Denetimi, çeşitli veri kaynakları için bağlayabilirsiniz için standart Windows Forms veri bağlama modelini destekler. Genellikle, adlarınıza bir <xref:System.Windows.Forms.BindingSource> , veri kaynağı ile etkileşimi yönetir. <xref:System.Windows.Forms.BindingSource> Seçerek ya da veri konumu değiştirirken büyük esneklik sağlayan bir Windows Forms veri kaynağı olabilir. Veri kaynakları hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> destekler, bkz [DataGridView denetimine genel bakış](datagridview-control-overview-windows-forms.md).  

Visual Studio DataGridView denetimine veri bağlama için kapsamlı destek sunar. Daha fazla bilgi için [nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetimine veri bağlama](bind-data-to-the-datagrid-using-the-designer.md).  

DataGridView denetimine veri bağlama için:

1. Veri alma ayrıntılarını işlemek için bir yöntem uygulayın. Aşağıdaki kod örneğinde uygular bir `GetData` başlatan yöntem bir <xref:System.Data.SqlClient.SqlDataAdapter>ve doldurmak için kullandığı bir <xref:System.Data.DataTable>. Ardından bağlar <xref:System.Data.DataTable> için <xref:System.Windows.Forms.BindingSource>. 

2. Formun <xref:System.Windows.Forms.Form.Load> olay işleyicisi, bağlama <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource>ve çağrı `GetData` verileri almak için yöntemi.  

## <a name="example"></a>Örnek

Bu tam kod örneği, bir Windows forma DataGridView denetiminde doldurmak için bir veritabanından verileri alır. Form verileri yeniden yüklemek ve veritabanına değişiklikleri gönderme düğmeleri de vardır.  

Bu örnek gerektirir: 

- Bir SQL Server Northwind örnek veritabanına erişim. Northwind örnek veritabanını yükleme hakkında daha fazla bilgi için bkz. [örnek veritabanları ADO.NET için kod örneklerine](../../data/adonet/sql/linq/downloading-sample-databases.md). 

- Sistem, System.Windows.Forms, System.Data ve System.Xml derlemesine ilişkin başvurular.  

Derleme ve bu örneği çalıştırmak için kodun içine yapıştırın *Form1* kod dosyasına yeni bir Windows Forms projesi. Binanın öğrenmek için C# veya bkz. Visual Basic komut satırı [csc.exe ile komut satırı derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Doldurma `connectionString` örnekte SQL Server Northwind örnek veritabanı bağlantınız için değerleri değişken. Windows kimlik doğrulama, tümleşik güvenlik olarak da bilinir, bağlantı dizesinde parola depolamak daha veritabanına bağlanmak için daha güvenli bir yoludur. Bağlantı güvenliği hakkında daha fazla bilgi için bkz: [bağlantı bilgilerini korumak](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView denetiminde veri görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md)

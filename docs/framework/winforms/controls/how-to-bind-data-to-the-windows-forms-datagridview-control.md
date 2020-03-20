---
title: Verileri DataGridView Denetimine bağlama
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182270"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Verileri Windows Forms DataGridView denetimine bağlama

Denetim <xref:System.Windows.Forms.DataGridView> standart Windows Forms veri bağlama modelini destekler, böylece çeşitli veri kaynaklarına bağlanabilir. Genellikle, veri kaynağı <xref:System.Windows.Forms.BindingSource> ile etkileşimi yöneten bir bağbağlanırsınız. Verilerinizin <xref:System.Windows.Forms.BindingSource> konumunu seçerken veya değiştirirken size büyük esneklik sağlayan herhangi bir Windows Forms veri kaynağı olabilir. Denetimin <xref:System.Windows.Forms.DataGridView> desteklediği veri kaynakları hakkında daha fazla bilgi için [DataGridView denetimine genel bakış'a](datagridview-control-overview-windows-forms.md)bakın.  

Visual Studio, DataGridView denetimine bağlanan veriler için kapsamlı bir desteğe sahiptir. Daha fazla bilgi için [bkz: Verileri Tasarımcıyı kullanarak Windows Forms DataGridView denetimine bağla.](bind-data-to-the-datagrid-using-the-designer.md)  

DataGridView denetimini verilere bağlamak için:

1. Verileri alma ayrıntılarını işlemek için bir yöntem uygulayın. Aşağıdaki kod örneği, `GetData` a <xref:System.Data.SqlClient.SqlDataAdapter>' yı başlýlayan bir yöntem <xref:System.Data.DataTable>uygular ve bir . Daha sonra <xref:System.Data.DataTable> bağlar <xref:System.Windows.Forms.BindingSource>.

2. Formun olay <xref:System.Windows.Forms.Form.Load> <xref:System.Windows.Forms.DataGridView> işleyicisinde, denetimi <xref:System.Windows.Forms.BindingSource>,' ye bağla `GetData` ve verileri almak için yöntemi çağırın.  

## <a name="example"></a>Örnek

Bu tam kod örneği, Bir DataGridView denetimini Windows formunda doldurmak için veritabanından veri alır. Formda ayrıca verileri yeniden yüklemek ve veritabanına değişiklik göndermek için düğmeler de vardır.  

Bu örnek şunları gerektirir:

- Northwind SQL Server örnek veritabanına erişim. Northwind örnek veritabanını yükleme hakkında daha fazla bilgi için [ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md)bkz.

- Sistem, System.Windows.Forms, System.Data ve System.Xml derlemelerine yapılan atıflar.  

Bu örneği oluşturmak ve çalıştırmak için, kodu yeni bir Windows Forms projesinde *Form1* kod dosyasına yapıştırın. C# veya Visual Basic komut satırından bina hakkında bilgi için [csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [Build komut satırına](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)sahip Komut satırı binasına bakın.  
  
Örnekteki `connectionString` değişkeni Northwind SQL Server örnek veritabanı bağlantınızın değerleriyle doldurun. Tümleşik güvenlik olarak da adlandırılan Windows Kimlik Doğrulama, veritabanına bağlanmanın bağlantı dizesinde parola depolamaktan daha güvenli bir yoldur. Bağlantı güvenliği hakkında daha fazla bilgi için [bkz.](../../data/adonet/protecting-connection-information.md)  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Verileri Windows Forms DataGridView denetiminde görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md)

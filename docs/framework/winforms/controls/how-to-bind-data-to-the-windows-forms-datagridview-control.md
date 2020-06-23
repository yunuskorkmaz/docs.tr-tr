---
title: Verileri DataGridView denetimine bağlama
ms.date: 02/08/2019
description: DataGridView denetiminin çeşitli veri kaynaklarına bağlanabilmesi için standart Windows Forms veri bağlama modelini nasıl desteklediğini öğrenin.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904422"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama

<xref:System.Windows.Forms.DataGridView>Denetim standart Windows Forms veri bağlama modelini destekler, bu nedenle çeşitli veri kaynaklarına bağlanabilir. Genellikle, <xref:System.Windows.Forms.BindingSource> veri kaynağıyla etkileşimi yöneten bir öğesine bağlarsınız. , <xref:System.Windows.Forms.BindingSource> Verilerinizin konumunu seçerken veya değiştirirken harika bir esneklik sağlayan herhangi bir Windows Forms veri kaynağı olabilir. Denetimin desteklediği veri kaynakları hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> bkz. [DataGridView denetimine genel bakış](datagridview-control-overview-windows-forms.md).  

Visual Studio, DataGridView denetimine veri bağlama için kapsamlı destek içerir. Daha fazla bilgi için bkz. [nasıl yapılır: Tasarımcıyı kullanarak verileri Windows Forms DataGridView denetimine bağlama](bind-data-to-the-datagrid-using-the-designer.md).  

Bir DataGridView denetimini verilere bağlamak için:

1. Verileri alma ayrıntılarını işlemek için bir yöntem uygulayın. Aşağıdaki kod örneği `GetData` , öğesini Başlatan bir yöntemi uygular <xref:System.Data.SqlClient.SqlDataAdapter> ve bunu doldurmak için kullanır <xref:System.Data.DataTable> . Daha sonra öğesini <xref:System.Data.DataTable> öğesine bağlar <xref:System.Windows.Forms.BindingSource> .

2. Formun <xref:System.Windows.Forms.Form.Load> olay işleyicisinde, <xref:System.Windows.Forms.DataGridView> denetimini öğesine bağlayın <xref:System.Windows.Forms.BindingSource> ve `GetData` verileri almak için yöntemini çağırın.  

## <a name="example"></a>Örnek

Bu kod örneği, bir Windows formundaki DataGridView denetimini doldurmak için bir veritabanından veri alır. Formun Ayrıca verileri yeniden yükleme ve değişiklikleri veritabanına gönderme düğmeleri de vardır.  

Bu örnek şunları gerektirir:

- Northwind SQL Server örnek veritabanına erişim. Northwind örnek veritabanını yükleme hakkında daha fazla bilgi için bkz. [ADO.net Code örnekleri için örnek veritabanları edinme](../../data/adonet/sql/linq/downloading-sample-databases.md).

- Sisteme, System. Windows. Forms, System. Data ve System.Xml derlemelerine başvurular.  

Bu örneği derlemek ve çalıştırmak için, kodu yeni bir Windows Forms projesindeki *Form1* kod dosyasına yapıştırın. C# veya Visual Basic komut satırından oluşturma hakkında bilgi için, bkz. [komut satırı oluşturma csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
`connectionString`Örnekteki değişkeni Northwind SQL Server örnek veritabanı bağlantınızın değerleriyle doldurun. Tümleşik güvenlik olarak da bilinen Windows kimlik doğrulaması, veritabanına bağlanmak için bağlantı dizesinde parola depolamadan daha güvenli bir yoldur. Bağlantı güvenliği hakkında daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView denetiminde verileri görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md)

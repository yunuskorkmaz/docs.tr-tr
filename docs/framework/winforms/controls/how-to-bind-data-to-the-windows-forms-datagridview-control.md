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
ms.openlocfilehash: bdba8af04cd9473b17d1a28f07ead7cd5bf43698
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139089"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama

<xref:System.Windows.Forms.DataGridView> denetimi standart Windows Forms veri bağlama modelini destekler, bu nedenle çeşitli veri kaynaklarına bağlanabilir. Genellikle, veri kaynağıyla etkileşimi yöneten bir <xref:System.Windows.Forms.BindingSource> bağlarsınız. <xref:System.Windows.Forms.BindingSource>, verilerinizin konumunu seçerken veya değiştirirken size büyük bir esneklik sağlayan herhangi bir Windows Forms veri kaynağı olabilir. <xref:System.Windows.Forms.DataGridView> denetiminin desteklediği veri kaynakları hakkında daha fazla bilgi için bkz. [DataGridView denetimine genel bakış](datagridview-control-overview-windows-forms.md).  

Visual Studio, DataGridView denetimine veri bağlama için kapsamlı destek içerir. Daha fazla bilgi için bkz. [nasıl yapılır: Tasarımcıyı kullanarak verileri Windows Forms DataGridView denetimine bağlama](bind-data-to-the-datagrid-using-the-designer.md).  

Bir DataGridView denetimini verilere bağlamak için:

1. Verileri alma ayrıntılarını işlemek için bir yöntem uygulayın. Aşağıdaki kod örneği, bir <xref:System.Data.SqlClient.SqlDataAdapter>Başlatan bir `GetData` yöntemi uygular ve <xref:System.Data.DataTable>doldurmak için onu kullanır. Ardından <xref:System.Data.DataTable> <xref:System.Windows.Forms.BindingSource>bağlar. 

2. Formun <xref:System.Windows.Forms.Form.Load> olay işleyicisinde, <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource>bağlayın ve verileri almak için `GetData` yöntemini çağırın.  

## <a name="example"></a>Örnek

Bu kod örneği, bir Windows formundaki DataGridView denetimini doldurmak için bir veritabanından veri alır. Formun Ayrıca verileri yeniden yükleme ve değişiklikleri veritabanına gönderme düğmeleri de vardır.  

Bu örnek şunları gerektirir: 

- Northwind SQL Server örnek veritabanına erişim. Northwind örnek veritabanını yükleme hakkında daha fazla bilgi için bkz. [ADO.net Code örnekleri için örnek veritabanları edinme](../../data/adonet/sql/linq/downloading-sample-databases.md). 

- Sisteme, System. Windows. Forms, System. Data ve System. xml derlemelerine başvurular.  

Bu örneği derlemek ve çalıştırmak için, kodu yeni bir Windows Forms projesindeki *Form1* kod dosyasına yapıştırın. C# Veya Visual Basic komut satırından oluşturma hakkında bilgi için, bkz. [CSC. exe ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Örnekteki `connectionString` değişkenini Northwind SQL Server örnek veritabanı bağlantınızın değerleriyle doldurun. Tümleşik güvenlik olarak da bilinen Windows kimlik doğrulaması, veritabanına bağlanmak için bağlantı dizesinde parola depolamadan daha güvenli bir yoldur. Bağlantı güvenliği hakkında daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView denetiminde verileri görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md)

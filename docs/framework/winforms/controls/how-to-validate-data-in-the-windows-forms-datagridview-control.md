---
title: DataGridView Denetimindeki verileri doğrulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 5fd881829f87fa1dec135d936f22996f196b0594
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728314"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Doğrulama
Aşağıdaki kod örneği, bir kullanıcı tarafından <xref:System.Windows.Forms.DataGridView> denetimine girilen verilerin nasıl doğrulandığını gösterir. Bu örnekte, <xref:System.Windows.Forms.DataGridView> Northwind örnek veritabanının `Customers` tablosundaki satırlarla doldurulur. Kullanıcı `CompanyName` sütununda bir hücreyi düzenlediğinde, boş olmadığını denetleyerek değeri geçerlilik için test edilir. <xref:System.Windows.Forms.DataGridView.CellValidating> olayının olay işleyicisi değerin boş bir dize olduğunu belirlerse, <xref:System.Windows.Forms.DataGridView> boş olmayan bir dize girilene kadar kullanıcının hücreden çıkılmasını önler.  
  
 Bu kod örneği hakkında ayrıntılı bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView Denetimindeki verileri doğrulama](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Windows. Forms ve System. XML derlemelerine başvuru.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)

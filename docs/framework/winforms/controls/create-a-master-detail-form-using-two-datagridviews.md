---
title: Iki DataGridView denetimi kullanarak ana ayrıntı formu oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: d317f4e592790c9b48b539b1601814569e14529f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737325"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Nasıl Yapılır: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma
Aşağıdaki kod örneği, iki <xref:System.Windows.Forms.BindingSource> bileşeni ile bağlantılı iki <xref:System.Windows.Forms.DataGridView> denetimini kullanarak bir ana/ayrıntı formu oluşturur. Veri kaynağı Northwind SQL Server örnek veritabanından `Customers` ve `Orders` tabloları içeren bir <xref:System.Data.DataSet> <xref:System.Data.DataRelation> sütunu ile ilişkili bir `CustomerID`.  
  
 Bir <xref:System.Windows.Forms.BindingSource>, veri kümesindeki üst `Customers` tabloya bağlanır. Bu veriler ana <xref:System.Windows.Forms.DataGridView> denetiminde görüntülenir. Diğer <xref:System.Windows.Forms.BindingSource> ilk veri bağlayıcısına bağlanır. İkinci <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.DataMember%2A> özelliği <xref:System.Data.DataRelation> adına ayarlanır. Bu, ilişkili ayrıntı <xref:System.Windows.Forms.DataGridView> denetiminin ana <xref:System.Windows.Forms.DataGridView> denetimindeki geçerli satıra karşılık gelen alt `Orders` tablosunun satırlarını görüntülemesine neden olur.  
  
 Bu kod örneği hakkında ayrıntılı bir açıklama için bkz. [Izlenecek yol: iki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma](creating-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
 Sisteme, System. Data, System. Windows. Forms ve System. XML derlemelerine başvuru.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [İzlenecek yol: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma](creating-a-master-detail-form-using-two-datagridviews.md)
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)

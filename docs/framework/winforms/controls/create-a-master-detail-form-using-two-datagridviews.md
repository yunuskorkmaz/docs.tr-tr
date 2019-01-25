---
title: 'Nasıl yapılır: İki Windows Forms DataGridView denetimi kullanarak ana öğe-ayrıntı formu oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: 4d6ea3d22919d8407d881e60993f9fe920d446d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640747"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Nasıl yapılır: İki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma
Aşağıdaki kod örneği iki kullanarak ana/ayrıntı formu oluşturur <xref:System.Windows.Forms.DataGridView> denetimleri bağlı iki <xref:System.Windows.Forms.BindingSource> bileşenleri. Veri kaynağı bir <xref:System.Data.DataSet> içeren `Customers` ve `Orders` ile birlikte SQL Server Northwind örnek veritabanındaki tablolar bir <xref:System.Data.DataRelation> aracılığıyla iki ilişkili `CustomerID` sütun.  
  
 Bir <xref:System.Windows.Forms.BindingSource> üst öğeye bağlı `Customers` tabloda veri kümesi. Ana veritabanında bu verilerin görüntülenme <xref:System.Windows.Forms.DataGridView> denetimi. Diğer <xref:System.Windows.Forms.BindingSource> ilk veri bağlayıcıya bağlıdır. <xref:System.Windows.Forms.BindingSource.DataMember%2A> İkinci özelliği <xref:System.Windows.Forms.BindingSource> ayarlanır <xref:System.Data.DataRelation> adı. Bu ilişkilendirilmiş ayrıntısı neden <xref:System.Windows.Forms.DataGridView> alt satırları görüntülemek için Denetim `Orders` ana geçerli satırda karşılık gelen tablo <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 Bu kod örneği tam bir açıklaması için bkz. [izlenecek yol: İki Windows kullanarak ana/ayrıntı formu oluşturma Forms DataGridView denetimlerine](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
 Sistem, System.Data, System.Windows.Forms ve System.XML derlemesine ilişkin başvurular.  
  
-   Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için [bağlantı bilgilerini koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [İzlenecek yol: İki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)

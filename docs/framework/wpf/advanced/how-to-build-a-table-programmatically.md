---
title: 'Nasıl yapılır: Program Aracılığıyla Tablo Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 315154b37218c0a6845f0a46149fc056780ee650
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172633"
---
# <a name="how-to-build-a-table-programmatically"></a>Nasıl yapılır: Program Aracılığıyla Tablo Oluşturma
Aşağıdaki örnekler program aracılığıyla nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Documents.Table> ve içerikle doldurur. Tablosunun beş satır paylaştırıldı (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> bulunan nesneleri bir <xref:System.Windows.Documents.Table.RowGroups%2A> nesnesi) ve altı sütunları (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> nesneleri). Satırları tablonun tamamını ve tabloda veri sütunlarının açıklamak için bir üst bilgi satırı özet bilgileri içeren bir alt bilgi satırı başlık yönelik bir başlık satırı da dahil olmak üzere farklı sunu amacıyla kullanılır.  "Title", "header" ve "alt" satırları kavramı tabloya devralınan değildir; Bunlar, yalnızca satır farklı özelliklere sahip olur. Tablo hücreleri metinlerin, resimlerin veya her türlü diğer oluşan gerçek içeriği içeren [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğesi.  
  
## <a name="example"></a>Örnek  
 İlk olarak, bir <xref:System.Windows.Documents.FlowDocument> oluşturulan konağa <xref:System.Windows.Documents.Table>ve yeni bir <xref:System.Windows.Documents.Table> oluşturulur ve içeriği için eklenen <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>Örnek  
 Ardından, altı <xref:System.Windows.Documents.TableColumn> nesnelerinin oluşturulduğu ve tablonun eklenen <xref:System.Windows.Documents.Table.Columns%2A> bazı biçimlendirme uygulanmış olan koleksiyonu.  
  
> [!NOTE]
>  Unutmayın tablo <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonun kullandığı standart sıfır tabanlı dizin.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>Örnek  
 Ardından, bir başlık satırı oluşturulur ve bazı biçimlendirme uygulanmış tablosuna eklenir.  Tablodaki tüm altı sütunu kapsayan tek bir hücre içermesi için başlık satırı gerçekleşir.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>Örnek  
 Ardından, bir üst bilgi satırı oluşturulur ve tabloya eklenen ve üst bilgi satırı hücrelerde oluşturulur ve içeriği ile doldurulur.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>Örnek  
 Ardından, veriler için bir satır oluşturulur ve tabloya eklenen ve bu satırı hücrelerde oluşturulur ve içerikle doldurulur.  Bu satırı oluşturma üst bilgi satırı biraz farklı biçimlendirme uygulanmış oluşturmak için benzer.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>Örnek  
 Son olarak, bir alt bilgi satırı oluşturulan, eklenen biçimlendirilmiş ve.  Başlık satırı gibi tüm altı sütun kapsayan tek bir hücre alt bilgi içerir.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tabloya Genel Bakış](table-overview.md)

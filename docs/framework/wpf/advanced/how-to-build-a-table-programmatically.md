---
title: "Nasıl yapılır: Program Aracılığıyla Tablo Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ef961bb219f201cf5fe32a5b2bbdf70ef45e73b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-build-a-table-programmatically"></a>Nasıl yapılır: Program Aracılığıyla Tablo Oluşturma
Program aracılığıyla oluşturma Aşağıdaki örnekler bir <xref:System.Windows.Documents.Table> ve içeriği ile doldurabilirsiniz. Tablosunun içeriğini beş satıra paylaştırıldı (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> içinde yer alan nesneler bir <xref:System.Windows.Documents.Table.RowGroups%2A> nesnesi) ve altı sütunlar (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> nesneleri). Satırları tüm tablo, tablodaki veri sütunlarını açıklamak için bir başlık satırı ve Özet bilgiler ile altbilgi satırı başlık yönelik bir başlık satırı dahil olmak üzere, farklı sunu amaçlarıyla kullanılır.  "Title", "üstbilgi" ve "Altbilgi" satır kavramı tabloya devralınmış değildir; Bunlar yalnızca satır farklı özelliklere sahip olan. Tablo hücrelerini içeren metin, görüntüler veya neredeyse tüm diğer oluşan gerçek içeriği [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğesi.  
  
## <a name="example"></a>Örnek  
 İlk olarak, bir <xref:System.Windows.Documents.FlowDocument> oluşturulan ana bilgisayara <xref:System.Windows.Documents.Table>ve yeni bir <xref:System.Windows.Documents.Table> oluşturulur ve içeriğini eklenir <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>Örnek  
 Ardından, altı <xref:System.Windows.Documents.TableColumn> nesneleri oluşturulur ve tablonun eklenen <xref:System.Windows.Documents.Table.Columns%2A> bazı uygulanan biçimlendirme içeren koleksiyon.  
  
> [!NOTE]
>  Unutmayın tablonun <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonu kullanan standart sıfır tabanlı dizin.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>Örnek  
 Ardından, bir başlık satırı oluşturulur ve bazı biçimlendirme uygulanmış tablosuna eklenir.  Tablodaki tüm altı sütunu kapsayan tek bir hücre içermesi için başlık satırı olur.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>Örnek  
 Ardından, bir başlık satırı oluşturulur ve tabloya eklenir ve üstbilgi satırındaki hücreler oluşturulur ve içerik ile doldurulur.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>Örnek  
 Ardından, veriler için bir satır oluşturulur ve tabloya eklenir ve bu satırda hücreler oluşturulur ve içerik ile doldurulur.  Bu satırı oluşturmak uygulanan biraz farklı biçimlendirme ile üstbilgi satırını oluşturmakla benzerdir.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>Örnek  
 Son olarak, bir altbilgi satırı oluşturulan, eklenen biçimlendirilmiş ve.  Başlık satırı gibi altbilgi tablodaki tüm altı sütunu kapsayan tek bir hücre içerir.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tablo genel bakış](../../../../docs/framework/wpf/advanced/table-overview.md)

---
title: 'Nasıl yapılır: XAML ile Tablo Tanımlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 7398af6fddae56238e1af3ee4e726420c01ab7ea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376942"
---
# <a name="how-to-define-a-table-with-xaml"></a>Nasıl yapılır: XAML ile Tablo Tanımlama
Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Documents.Table> kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Örnek tabloda dört sütun vardır (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> öğeleri) ve birkaç satır (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> öğeleri) verileri de içeren başlık, başlığı ve alt bilgi.  Satır içinde içerilmeli bir <xref:System.Windows.Documents.TableRowGroup> öğesi.  Tablodaki her satır bir veya daha fazla hücre oluşur (tarafından temsil edilen <xref:System.Windows.Documents.TableCell> öğeleri).  İçerik tablo hücresi içinde bulunan, içinde bir <xref:System.Windows.Documents.Block> öğesi; bu durumda <xref:System.Windows.Documents.Paragraph> öğeleri kullanılır.  Tabloda ayrıca bir köprü barındıran (tarafından temsil edilen <xref:System.Windows.Documents.Hyperlink> öğesi) altbilgi satırında.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 Aşağıdaki şekil, bu örnekte, tanımlanan tablo nasıl işlediğini gösterir.  
  
 ![İşlenen tablo. ](./media/tableeg.png "TableEG")

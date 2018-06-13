---
title: 'Nasıl yapılır: XAML ile Tablo Tanımlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 2a35a27567d962fc125cb3c408ccab95afa222af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543107"
---
# <a name="how-to-define-a-table-with-xaml"></a>Nasıl yapılır: XAML ile Tablo Tanımlama
Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Documents.Table> kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Örnek tablo dört sütun vardır (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> öğeleri) ve birkaç satır (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> öğeleri) verileri de içeren başlık, üstbilgi ve altbilgi bilgileri.  Satır içerdiği, içinde bir <xref:System.Windows.Documents.TableRowGroup> öğesi.  Tablodaki her satırda bir veya birden çok hücreden oluşur (tarafından temsil edilen <xref:System.Windows.Documents.TableCell> öğeleri).  İçeriği bir tablo hücresi içinde bulunan, içinde bir <xref:System.Windows.Documents.Block> öğesi; bu durumda <xref:System.Windows.Documents.Paragraph> öğeleri kullanılır.  Tablo bir köprü de barındıran (tarafından temsil edilen <xref:System.Windows.Documents.Hyperlink> öğesi) altbilgi satırında.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 Bu örnekte, tanımlı tablo nasıl işlediğini aşağıdaki şekilde gösterilmiştir.  
  
 ![İşlenmiş tablo. ] (../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")

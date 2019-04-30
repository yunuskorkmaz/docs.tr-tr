---
title: 'Nasıl yapılır: XAML ile Tablo Tanımlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 011f612527f0c9e89ec05643edbb95b2d908488c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776588"
---
# <a name="how-to-define-a-table-with-xaml"></a>Nasıl yapılır: XAML ile Tablo Tanımlama
Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Documents.Table> kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Örnek tabloda dört sütun vardır (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> öğeleri) ve birkaç satır (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> öğeleri) verileri de içeren başlık, başlığı ve alt bilgi.  Satır içinde içerilmeli bir <xref:System.Windows.Documents.TableRowGroup> öğesi.  Tablodaki her satır bir veya daha fazla hücre oluşur (tarafından temsil edilen <xref:System.Windows.Documents.TableCell> öğeleri).  İçerik tablo hücresi içinde bulunan, içinde bir <xref:System.Windows.Documents.Block> öğesi; bu durumda <xref:System.Windows.Documents.Paragraph> öğeleri kullanılır.  Tabloda ayrıca bir köprü barındıran (tarafından temsil edilen <xref:System.Windows.Documents.Hyperlink> öğesi) altbilgi satırında.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 Bu örnekte, tanımlanan tablo nasıl işlediğini aşağıdaki şekilde gösterilmiştir:  
  
 ![XAML ile tanımlanan bir tablonun ekran görüntüsü.](./media/how-to-define-a-table-with-xaml/planetary-information-xaml-table.png)

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
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="f5037-102">Nasıl yapılır: XAML ile Tablo Tanımlama</span><span class="sxs-lookup"><span data-stu-id="f5037-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="f5037-103">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Documents.Table> kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f5037-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="f5037-104">Örnek tablo dört sütun vardır (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> öğeleri) ve birkaç satır (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> öğeleri) verileri de içeren başlık, üstbilgi ve altbilgi bilgileri.</span><span class="sxs-lookup"><span data-stu-id="f5037-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="f5037-105">Satır içerdiği, içinde bir <xref:System.Windows.Documents.TableRowGroup> öğesi.</span><span class="sxs-lookup"><span data-stu-id="f5037-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="f5037-106">Tablodaki her satırda bir veya birden çok hücreden oluşur (tarafından temsil edilen <xref:System.Windows.Documents.TableCell> öğeleri).</span><span class="sxs-lookup"><span data-stu-id="f5037-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="f5037-107">İçeriği bir tablo hücresi içinde bulunan, içinde bir <xref:System.Windows.Documents.Block> öğesi; bu durumda <xref:System.Windows.Documents.Paragraph> öğeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5037-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="f5037-108">Tablo bir köprü de barındıran (tarafından temsil edilen <xref:System.Windows.Documents.Hyperlink> öğesi) altbilgi satırında.</span><span class="sxs-lookup"><span data-stu-id="f5037-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5037-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5037-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="f5037-110">Bu örnekte, tanımlı tablo nasıl işlediğini aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f5037-110">The following figure shows how the table defined in this example renders.</span></span>  
  
 <span data-ttu-id="f5037-111">![İşlenmiş tablo. ] (../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span><span class="sxs-lookup"><span data-stu-id="f5037-111">![Rendered table.](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span></span>

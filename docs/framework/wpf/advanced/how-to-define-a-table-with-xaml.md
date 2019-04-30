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
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="4bb70-102">Nasıl yapılır: XAML ile Tablo Tanımlama</span><span class="sxs-lookup"><span data-stu-id="4bb70-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="4bb70-103">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Documents.Table> kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4bb70-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="4bb70-104">Örnek tabloda dört sütun vardır (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> öğeleri) ve birkaç satır (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> öğeleri) verileri de içeren başlık, başlığı ve alt bilgi.</span><span class="sxs-lookup"><span data-stu-id="4bb70-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="4bb70-105">Satır içinde içerilmeli bir <xref:System.Windows.Documents.TableRowGroup> öğesi.</span><span class="sxs-lookup"><span data-stu-id="4bb70-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="4bb70-106">Tablodaki her satır bir veya daha fazla hücre oluşur (tarafından temsil edilen <xref:System.Windows.Documents.TableCell> öğeleri).</span><span class="sxs-lookup"><span data-stu-id="4bb70-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="4bb70-107">İçerik tablo hücresi içinde bulunan, içinde bir <xref:System.Windows.Documents.Block> öğesi; bu durumda <xref:System.Windows.Documents.Paragraph> öğeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4bb70-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="4bb70-108">Tabloda ayrıca bir köprü barındıran (tarafından temsil edilen <xref:System.Windows.Documents.Hyperlink> öğesi) altbilgi satırında.</span><span class="sxs-lookup"><span data-stu-id="4bb70-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bb70-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bb70-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="4bb70-110">Bu örnekte, tanımlanan tablo nasıl işlediğini aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4bb70-110">The following figure shows how the table defined in this example renders:</span></span>  
  
 ![XAML ile tanımlanan bir tablonun ekran görüntüsü.](./media/how-to-define-a-table-with-xaml/planetary-information-xaml-table.png)

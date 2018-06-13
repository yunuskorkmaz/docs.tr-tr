---
title: 'Nasıl yapılır: Karmaşık Kılavuz Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: 49bf9781d56b93fd4529f3c9b62deb171e69155f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553601"
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="f4d35-102">Nasıl yapılır: Karmaşık Kılavuz Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f4d35-102">How to: Create a Complex Grid</span></span>
<span data-ttu-id="f4d35-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.Grid> aylık takvim gibi görünen bir düzen oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f4d35-103">This example shows how to use a <xref:System.Windows.Controls.Grid> to create layout that looks like a monthly calendar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4d35-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4d35-104">Example</span></span>  
 <span data-ttu-id="f4d35-105">Aşağıdaki örnek kullanarak sekiz sıra ve sekiz sütun tanımlar <xref:System.Windows.Controls.RowDefinition> ve <xref:System.Windows.Controls.ColumnDefinition> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="f4d35-105">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="f4d35-106">Kullandığı <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> ile birlikte ekli özelliklerini, <xref:System.Windows.Shapes.Rectangle> çeşitli sütunları ve satırları arka dolgu öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f4d35-106">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="f4d35-107">Bu tasarım, birden fazla öğe her hücresinde olabileceğinden bir <xref:System.Windows.Controls.Grid>, ilkesine birbirinden <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Documents.Table>.</span><span class="sxs-lookup"><span data-stu-id="f4d35-107">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>  
  
 <span data-ttu-id="f4d35-108">Örnek dikey gradyanlar kullanır <xref:System.Windows.Shapes.Shape.Fill%2A> görsel sunumu ve takvimin okunabilirliğini artırmak için satırlar ve sütunlar.</span><span class="sxs-lookup"><span data-stu-id="f4d35-108">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows in order to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="f4d35-109">Biçimlendirilmiş <xref:System.Windows.Controls.TextBlock> öğeleri tarih ve haftanın günleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f4d35-109">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="f4d35-110"><xref:System.Windows.Controls.TextBlock> öğeleri kesinlikle yerleştirilir kendi hücrelerde kullanarak <xref:System.Windows.FrameworkElement.Margin%2A> özelliği ve uygulama için stil içinde tanımlanan hizalama özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="f4d35-110"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f4d35-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4d35-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [<span data-ttu-id="f4d35-112">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f4d35-112">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="f4d35-113">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f4d35-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="f4d35-114">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f4d35-114">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)

---
title: Karmaşık kılavuz oluşturma
description: Aylık takvim gibi görünen bir düzen oluşturmak için bir kılavuz denetimi kullanma hakkında bir örnek.
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: e2356113457e8c9a6737132e9779e49c05a23d77
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199987"
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="e211c-103">Karmaşık kılavuz oluşturma</span><span class="sxs-lookup"><span data-stu-id="e211c-103">How to create a complex Grid</span></span>

<span data-ttu-id="e211c-104">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Controls.Grid> aylık takvim gibi görünen bir düzen oluşturmak için denetimi.</span><span class="sxs-lookup"><span data-stu-id="e211c-104">This example shows how to use a <xref:System.Windows.Controls.Grid> control to create a layout that looks like a monthly calendar.</span></span>

## <a name="example"></a><span data-ttu-id="e211c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e211c-105">Example</span></span>

<span data-ttu-id="e211c-106">Aşağıdaki örnek sekiz satırları ve sütunları sekiz kullanarak tanımlar <xref:System.Windows.Controls.RowDefinition> ve <xref:System.Windows.Controls.ColumnDefinition> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e211c-106">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="e211c-107">Kullandığı <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> ile birlikte iliştirilmiş özellikler, <xref:System.Windows.Shapes.Rectangle> çeşitli sütunları ve satırları arka plan dolgu öğeleri.</span><span class="sxs-lookup"><span data-stu-id="e211c-107">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="e211c-108">Bu tasarım, her bir hücresinde birden fazla öğe var olabileceğinden bir <xref:System.Windows.Controls.Grid>, ilkeye birbirinden <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Documents.Table>.</span><span class="sxs-lookup"><span data-stu-id="e211c-108">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>

<span data-ttu-id="e211c-109">Dikey gradyanlar örnekte <xref:System.Windows.Shapes.Shape.Fill%2A> görsel sunumunu ve Takvim okunabilirliğini geliştirmek için satırlar ve sütunlar.</span><span class="sxs-lookup"><span data-stu-id="e211c-109">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="e211c-110">Biçimlendirilmiş <xref:System.Windows.Controls.TextBlock> öğeleri tarih ve haftanın günlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e211c-110">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="e211c-111"><xref:System.Windows.Controls.TextBlock> öğeleri kesinlikle yerleştirilir hücreleri içinde kullanarak <xref:System.Windows.FrameworkElement.Margin%2A> özelliği ve uygulama için bir stil içinde tanımlanan alignment özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e211c-111"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>

[!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

<span data-ttu-id="e211c-112">Aşağıdaki görüntüde, sonuç olarak oluşan denetimi, özelleştirilebilir bir takvim gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e211c-112">The following image shows the resulting control, a customizable calendar:</span></span>

![Sonuç olarak oluşan denetimi, ekran görüntüsü](./media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a><span data-ttu-id="e211c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e211c-114">See also</span></span>

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [<span data-ttu-id="e211c-115">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e211c-115">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="e211c-116">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e211c-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="e211c-117">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e211c-117">Table Overview</span></span>](../advanced/table-overview.md)
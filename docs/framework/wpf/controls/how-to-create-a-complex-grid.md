---
title: Karmaşık kılavuz oluşturma
description: Aylık takvim gibi görünen bir düzen oluşturmak için bir kılavuz denetimi kullanma hakkında bir örnek.
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: dd17dfeea85e2b404f7a284f93faceec63145b1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911007"
---
# <a name="how-to-create-a-complex-grid"></a>Karmaşık kılavuz oluşturma

Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Controls.Grid> aylık takvim gibi görünen bir düzen oluşturmak için denetimi.

## <a name="example"></a>Örnek

Aşağıdaki örnek sekiz satırları ve sütunları sekiz kullanarak tanımlar <xref:System.Windows.Controls.RowDefinition> ve <xref:System.Windows.Controls.ColumnDefinition> sınıfları. Kullandığı <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> ile birlikte iliştirilmiş özellikler, <xref:System.Windows.Shapes.Rectangle> çeşitli sütunları ve satırları arka plan dolgu öğeleri. Bu tasarım, her bir hücresinde birden fazla öğe var olabileceğinden bir <xref:System.Windows.Controls.Grid>, ilkeye birbirinden <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Documents.Table>.

Dikey gradyanlar örnekte <xref:System.Windows.Shapes.Shape.Fill%2A> görsel sunumunu ve Takvim okunabilirliğini geliştirmek için satırlar ve sütunlar. Biçimlendirilmiş <xref:System.Windows.Controls.TextBlock> öğeleri tarih ve haftanın günlerini temsil eder. <xref:System.Windows.Controls.TextBlock> öğeleri kesinlikle yerleştirilir hücreleri içinde kullanarak <xref:System.Windows.FrameworkElement.Margin%2A> özelliği ve uygulama için bir stil içinde tanımlanan alignment özellikleri.

[!code-xaml[GridComplex#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

Aşağıdaki görüntüde, sonuç olarak oluşan denetimi, özelleştirilebilir bir takvim gösterilmektedir:

![Sonuç olarak oluşan denetimi, ekran görüntüsü](././media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Panellere Genel Bakış](panels-overview.md)
- [Tabloya Genel Bakış](../advanced/table-overview.md)
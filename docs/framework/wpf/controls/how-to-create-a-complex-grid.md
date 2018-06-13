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
# <a name="how-to-create-a-complex-grid"></a>Nasıl yapılır: Karmaşık Kılavuz Oluşturma
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.Grid> aylık takvim gibi görünen bir düzen oluşturmak için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanarak sekiz sıra ve sekiz sütun tanımlar <xref:System.Windows.Controls.RowDefinition> ve <xref:System.Windows.Controls.ColumnDefinition> sınıfları. Kullandığı <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> ile birlikte ekli özelliklerini, <xref:System.Windows.Shapes.Rectangle> çeşitli sütunları ve satırları arka dolgu öğeleri. Bu tasarım, birden fazla öğe her hücresinde olabileceğinden bir <xref:System.Windows.Controls.Grid>, ilkesine birbirinden <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Documents.Table>.  
  
 Örnek dikey gradyanlar kullanır <xref:System.Windows.Shapes.Shape.Fill%2A> görsel sunumu ve takvimin okunabilirliğini artırmak için satırlar ve sütunlar. Biçimlendirilmiş <xref:System.Windows.Controls.TextBlock> öğeleri tarih ve haftanın günleri temsil eder. <xref:System.Windows.Controls.TextBlock> öğeleri kesinlikle yerleştirilir kendi hücrelerde kullanarak <xref:System.Windows.FrameworkElement.Margin%2A> özelliği ve uygulama için stil içinde tanımlanan hizalama özelliklerini.  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Tabloya Genel Bakış](../../../../docs/framework/wpf/advanced/table-overview.md)

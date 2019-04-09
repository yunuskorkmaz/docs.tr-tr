---
title: 'Nasıl yapılır: ColumnDefinitionsCollections ve RowDefinitionsCollections Kullanarak Sütunları ve Satırları İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
ms.openlocfilehash: f316cced076223edba1d39c9cfb21b9a504b9eee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147738"
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a>Nasıl yapılır: ColumnDefinitionsCollections ve RowDefinitionsCollections Kullanarak Sütunları ve Satırları İşleme
Bu örnek yöntemleri kullanmayı gösterir <xref:System.Windows.Controls.ColumnDefinitionCollection> ve <xref:System.Windows.Controls.RowDefinitionCollection> ekleme, temizlenmesi veya satır veya sütun içeriğini sayım gibi eylemleri gerçekleştirmek için sınıflar. Örneğin, <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, veya <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> dahil olan öğeler bir <xref:System.Windows.Controls.ColumnDefinition> veya <xref:System.Windows.Controls.RowDefinition>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Grid> öğesi ile bir <xref:System.Windows.FrameworkElement.Name%2A> , `grid1`. <xref:System.Windows.Controls.Grid> İçeren bir <xref:System.Windows.Controls.StackPanel> tutan <xref:System.Windows.Controls.Button> öğeleri, her denetlenen farklı bir koleksiyon yöntemi tarafından. Tıkladığınızda bir <xref:System.Windows.Controls.Button>, arka plan kod dosyasında bir yöntem çağrısının etkinleştirir.  
  
 [!code-xaml[ColumnDefinitionsGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 Bu örnek, bir dizi her karşılık gelen özel yöntem tanımlar. bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayında [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya. Sütun ve satır sayısını değiştirebilirsiniz <xref:System.Windows.Controls.Grid> çeşitli yollarla içeren ekleme veya satırları ve sütunları; kaldırılıyor ve sayım satırları ve sütunları toplam sayısı. Önlemek için <xref:System.ArgumentOutOfRangeException> ve <xref:System.ArgumentException> özel durumları, hata denetimi işlevlerini kullanabilirsiniz, <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> yöntemi sağlar.  
  
 [!code-csharp[ColumnDefinitionsGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.ColumnDefinitionCollection>
- <xref:System.Windows.Controls.RowDefinitionCollection>

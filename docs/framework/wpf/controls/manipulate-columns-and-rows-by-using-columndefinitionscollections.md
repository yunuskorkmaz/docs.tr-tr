---
title: "Nasıl yapılır: ColumnDefinitionsCollections ve RowDefinitionsCollections Kullanarak Sütunları ve Satırları İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ba9566e9688984cc881a94e39b065fdadb4cc11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a>Nasıl yapılır: ColumnDefinitionsCollections ve RowDefinitionsCollections Kullanarak Sütunları ve Satırları İşleme
Bu örnek yöntemleri kullanmayı gösterir <xref:System.Windows.Controls.ColumnDefinitionCollection> ve <xref:System.Windows.Controls.RowDefinitionCollection> ekleme, temizleme veya satır veya sütun içeriğini sayma gibi eylemleri gerçekleştirmek için sınıflar. Örneğin, <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, veya <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> içinde yer alan öğeleri bir <xref:System.Windows.Controls.ColumnDefinition> veya <xref:System.Windows.Controls.RowDefinition>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Grid> öğesi ile bir <xref:System.Windows.FrameworkElement.Name%2A> , `grid1`. <xref:System.Windows.Controls.Grid> İçeren bir <xref:System.Windows.Controls.StackPanel> tutan <xref:System.Windows.Controls.Button> öğeleri, her denetlenen farklı koleksiyon metodu tarafından. ' A tıkladığınızda bir <xref:System.Windows.Controls.Button>, arka plan kod dosyasına bir yöntem çağrısı etkinleştirir.  
  
 [!code-xaml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 Bu örnek özel yöntemler, her karşılık gelen bir dizi tanımlayan bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayında [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya. Sütun ve satır sayısını değiştirebilirsiniz <xref:System.Windows.Controls.Grid> çeşitli yollarla da içeren ekleme veya satırları ve sütunları; kaldırma ve sayım satırları ve sütunları toplam sayısı. Önlemek için <xref:System.ArgumentOutOfRangeException> ve <xref:System.ArgumentException> özel durumlar, hata denetleme işlevini kullanabilirsiniz, <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> yöntemi sağlar.  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.ColumnDefinitionCollection>  
 <xref:System.Windows.Controls.RowDefinitionCollection>

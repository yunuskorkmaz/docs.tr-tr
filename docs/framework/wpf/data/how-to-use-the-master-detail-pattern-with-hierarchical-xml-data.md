---
title: 'Nasıl yapılır: Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 2b1ed34fe363f44a3a9eb80dc56d721868329717
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378112"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Nasıl yapılır: Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma
Bu örnek ile ana öğe-ayrıntı senaryonun nasıl uygulanacağını gösterir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] içinde açıklanan örneğin veri sürümünü [hiyerarşik veriler ile ana öğe-ayrıntı desenini kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Bu örnekte, veri dosyasındandır `League.xml`. Not nasıl üçüncü <xref:System.Windows.Controls.ListBox> denetim ikinci seçim değişiklikleri izleyen <xref:System.Windows.Controls.ListBox> bağlayarak kendi <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliği.  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.HierarchicalDataTemplate>
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)

---
title: 'Nasıl yapılır: Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 4beb2377fa9740e5103df0a82cfda9bd5f6f4769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550082"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Nasıl yapılır: Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma
Bu örnek ile ana öğe-ayrıntı senaryonun nasıl uygulanacağını gösterir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] içinde açıklanan örneğin veri sürümünü [hiyerarşik veriler ile ana öğe-ayrıntı desenini kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Bu örnekte, veri dosyasındandır `League.xml`. Not nasıl üçüncü <xref:System.Windows.Controls.ListBox> denetim ikinci seçim değişiklikleri izleyen <xref:System.Windows.Controls.ListBox> bağlayarak kendi <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliği.  
  
 [!code-xaml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.HierarchicalDataTemplate>
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

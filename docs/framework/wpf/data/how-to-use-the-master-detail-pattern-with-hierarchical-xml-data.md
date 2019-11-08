---
title: 'Nasıl yapılır: Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 0fe42d57fcaf4acee09340fdb3f5df73d7291566
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733417"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Nasıl yapılır: Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma
Bu örnek, XML verileriyle master-detail senaryosunun nasıl uygulanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, [hiyerarşik verilerle ana ayrıntı modelini kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)bölümünde AÇıKLANAN örnek xml veri sürümüdür. Bu örnekte, veriler dosya `League.xml`. Üçüncü <xref:System.Windows.Controls.ListBox> denetiminin <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliğine bağlayarak ikinci <xref:System.Windows.Controls.ListBox> seçim değişikliklerini nasıl izlediğini aklınızda edin.  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.HierarchicalDataTemplate>
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)

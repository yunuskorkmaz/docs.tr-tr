---
title: 'Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 2e7d9ceed3ab8385f07d87ecdb92c0a99d410b40
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459085"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma
Bu örnek, ana ayrıntı senaryosunun nasıl uygulanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `LeagueList` bir `Leagues`koleksiyonudur. Her `League` bir `Name` ve bir `Divisions`koleksiyonu vardır ve her bir `Division` bir ad ve bir `Teams`koleksiyonu vardır. Her `Team` bir takım adına sahiptir.  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Aşağıda, örneğin bir ekran görüntüsü verilmiştir. `Divisions` <xref:System.Windows.Controls.ListBox>, `Leagues` <xref:System.Windows.Controls.ListBox> seçimleri otomatik olarak izler ve ilgili verileri görüntüler. `Teams` <xref:System.Windows.Controls.ListBox> diğer iki <xref:System.Windows.Controls.ListBox> denetimlerindeki seçimleri izler.  
  
 ![Ana&#45;ayrıntı senaryosu örneği gösteren ekran görüntüsü.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 Bu örnekte dikkat etmeniz gereken iki şey şunlardır:  
  
1. Üç <xref:System.Windows.Controls.ListBox> denetimi aynı kaynağa bağlanır. <xref:System.Windows.Controls.ListBox> görüntülenmesini istediğiniz veri düzeyini belirtmek için bağlamanın <xref:System.Windows.Data.Binding.Path%2A> özelliğini ayarlarsınız.  
  
2. <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini, izlemekte olduğunuz seçimin <xref:System.Windows.Controls.ListBox> denetimlerinde `true` olarak ayarlamanız gerekir. Bu özelliğin ayarlanması, seçilen öğenin her zaman <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>olarak ayarlanmasını sağlar. Alternatif olarak, <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Data.CollectionViewSource>verileri alırsa, seçim ve para birimini otomatik olarak eşitler.  
  
 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileri kullanırken teknik biraz farklıdır. Bir örnek için bkz. [HIYERARŞIK XML verileriyle Master-Detail modelini kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.HierarchicalDataTemplate>
- [Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](data-templating-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)

---
title: 'Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 46733b462861bdac3381cdacb8f2fbe0536d12eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556802"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma
Bu örnek ana-ayrıntı senaryosunun nasıl uygulanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `LeagueList` koleksiyonudur `Leagues`. Her `League` sahip bir `Name` ve koleksiyonu `Divisions`ve her `Division` bir ad ve bir koleksiyonu vardır `Teams`. Her `Team` bir takım adı vardır.  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Örneğin bir ekran görüntüsü verilmiştir. `Divisions` <xref:System.Windows.Controls.ListBox> Otomatik olarak seçimleri izleyen `Leagues` <xref:System.Windows.Controls.ListBox> ve karşılık gelen verileri görüntüleyebilirsiniz. `Teams` <xref:System.Windows.Controls.ListBox> Diğer iki seçimleri izler <xref:System.Windows.Controls.ListBox> kontrol eder.  
  
 ![Ana&#45;ayrıntı örneği](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 Bu örnekte fark için iki şey vardır:  
  
1.  Üç <xref:System.Windows.Controls.ListBox> denetimleri aynı kaynağa bağlanır. Ayarladığınız <xref:System.Windows.Data.Binding.Path%2A> hangi düzeyde verileri istediğiniz belirtmek için bağlama özelliğini <xref:System.Windows.Controls.ListBox> görüntülemek için.  
  
2.  Ayarlamalısınız <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğine `true` üzerinde <xref:System.Windows.Controls.ListBox> denetimlerinin izlediğiniz seçim. Bu özelliği ayarlamak sağlar Seçili öğe olarak her zaman ayarlanır <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatif olarak, varsa <xref:System.Windows.Controls.ListBox> verilerinden alır bir <xref:System.Windows.Data.CollectionViewSource>, seçimi ve para birimi otomatik olarak eşitler.  
  
 Kullanırken teknik biraz farklıdır [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri. Bir örnek için bkz: [hiyerarşik XML veriler ile ana-ayrıntı desenini kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Veri Şablonu Oluşturmaya Genel Bakış](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

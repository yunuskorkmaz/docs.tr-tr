---
title: 'Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 36eded28085aec3aaea1a2351ae3babc6ad6c700
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689646"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma
Bu örnek, ana öğe-ayrıntı senaryonun nasıl uygulanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `LeagueList` koleksiyonudur `Leagues`. Her `League` sahip bir `Name` ve koleksiyonu `Divisions`ve her `Division` bir ad ve bir koleksiyonu `Teams`. Her `Team` bir takım adı vardır.  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Örneğin bir ekran görüntüsü aşağıda verilmiştir. `Divisions` <xref:System.Windows.Controls.ListBox> Seçimleri otomatik olarak izler `Leagues` <xref:System.Windows.Controls.ListBox> ve karşılık gelen verileri görüntüleyin. `Teams` <xref:System.Windows.Controls.ListBox> İzler ve diğer iki seçimleri <xref:System.Windows.Controls.ListBox> kontrol eder.  
  
 ![Ana&#45;ayrıntı örneği](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 Bu örnekte fark etmeye iki şey vardır:  
  
1.  Üç <xref:System.Windows.Controls.ListBox> denetimleri aynı kaynağına bağlayın. Ayarladığınız <xref:System.Windows.Data.Binding.Path%2A> hangi veri düzeyini istediğinizi belirtmek için bağlama özelliğini <xref:System.Windows.Controls.ListBox> görüntülenecek.  
  
2.  Ayarlamalısınız <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini `true` üzerinde <xref:System.Windows.Controls.ListBox> denetimlerinin izlediğiniz seçimi. Bu özelliğin ayarlanması sağlar Seçili öğe olarak her zaman ayarlandığından <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatif olarak, <xref:System.Windows.Controls.ListBox> öğesinden veri alır bir <xref:System.Windows.Data.CollectionViewSource>, seçim ve para birimi otomatik olarak eşitler.  
  
 Kullanırken tekniği biraz daha farklı olmasına [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri. Bir örnek için bkz. [hiyerarşik XML verileri ile ana öğe-ayrıntı desenini kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.HierarchicalDataTemplate>
- [Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

---
title: 'Performansı iyileştirme: Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 156d248921499aa78c3638e45af113c5698bdacd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668021"
---
# <a name="optimizing-performance-data-binding"></a>Performansı iyileştirme: Veri Bağlama
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama sunmak ve verilerle etkileşimde bulunmak üzere uygulamalar için basit ve tutarlı bir yol sağlar. Çeşitli veri kaynaklarından biçiminde veriye, öğeler bağlanabilir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri ve [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Bu konu, veri bağlama performans önerileri sağlar.  
  

  
<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Veri bağlama başvuruları nasıl çözümlenir  
 Veri bağlama performans sorunlarını ele almadan önce keşfetmek için faydalı olduğu nasıl [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama altyapısı nesne başvuru bağlamasının giderir.  
  
 Kaynağı bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama herhangi olabilir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesne. Özellikler, alt özellik veya dizin oluşturucular, adlarınıza bağlayabileceğiniz bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesne. Bağlama başvurularının ya da Microsoft .NET Framework yansıma kullanarak çözümlenir veya <xref:System.ComponentModel.ICustomTypeDescriptor>. Bağlama için nesne başvurularını çözümlemek için üç yöntem şunlardır.  
  
 Yansıma kullanarak ilk yöntem içerir. Bu durumda, <xref:System.Reflection.PropertyInfo> nesne özelliğin özniteliklerini bulmak için kullanılır ve özellik meta verilerine erişim sağlar. Kullanırken <xref:System.ComponentModel.ICustomTypeDescriptor> arabirimi, veri bağlama altyapısı bu arabirim özellik değerlerine erişmek için kullanır. <xref:System.ComponentModel.ICustomTypeDescriptor> Arabirimidir burada nesnesinin yok statik bir özellikler kümesini durumlarda özellikle yararlıdır.  
  
 Özellik değişikliği bildirimleri uygulayarak ya da sağlanabilir <xref:System.ComponentModel.INotifyPropertyChanged> ilişkili değişiklik bildirimleri kullanarak veya arabirim <xref:System.ComponentModel.TypeDescriptor>. Ancak, özellik değişikliği bildirimlerini uygulamak için tercih edilen bir strateji kullanmaktır <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Kaynak nesne ise bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesne ve kaynak özelliği bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama altyapısı olan ilk almak için kaynak nesnesindeki yansıma kullanmak <xref:System.ComponentModel.TypeDescriptor>ve ardından sorgu bir <xref:System.ComponentModel.PropertyDescriptor>. Bu yansıma işlemlerin sırasını büyük olasılıkla bir performans açısından çok zaman alır.  
  
 Nesne başvuruları çözümlemek için ikinci yöntem içerir bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] uygulayan kaynak nesne <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi ve bir kaynak özelliği bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği. Bu durumda, veri bağlama altyapısı doğrudan kaynak türüne yansıma kullanır ve gerekli özelliği alır. Bu yine de en iyi yöntem değildir, ancak ilk yöntem kümesi gereksinimlerinde çalışırken daha az maliyetlidir.  
  
 Nesne başvurularını çözümlemek için üçüncü bir yöntem olan bir kaynak nesne içeren bir <xref:System.Windows.DependencyObject> ve bir kaynak özelliği bir <xref:System.Windows.DependencyProperty>. Bu durumda, yansıma kullanmak veri bağlama altyapısı gerekmez. Bunun yerine özellik altyapısı ve veri bağlama altyapısı birlikte özellik başvurusu bağımsız olarak çözümler. Bu, veri bağlama için kullanılan nesne başvurularını çözümlemek için en iyi yöntemdir.  
  
 Aşağıdaki tabloda veri bağlama hızına karşılaştırır <xref:System.Windows.Controls.TextBlock.Text%2A> bin özelliği <xref:System.Windows.Controls.TextBlock> öğeleri bu üç yöntemi kullanarak.  
  
|**Bir TextBlock Text özelliğine bağlama**|**Bağlama süresi (ms)**|**İşleme zamanı--bağlama (ms) içerir**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Bir özelliğine bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesnesi|115|314|  
|Bir özelliğine bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] uygulayan nesne <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|İçin bir <xref:System.Windows.DependencyProperty> , bir <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Büyük boyutlu CLR nesnelere bağlama  
 Verileri tek bir bağladığınızda önemli performans etkisi olan [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özellikleri binlerce nesne. Tek bir nesnede birden çok bölerek Bu etkiyi en aza indirebilirsiniz [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri ile daha az özellik. Tablo Bağlama ve veri bağlama için tek bir işleme sürelerini büyük gösterir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] birden çok daha küçük nesneleri ve nesne.  
  
|**Veri bağlama 1000 TextBlock nesneleri**|**Bağlama süresi (ms)**|**İşleme zamanı--bağlama (ms) içerir**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|İçin bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 1000 özelliklere sahip nesne|950|1200|  
|1000 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] bir özelliği olan nesneler|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Bir ItemsSource bağlama  
 Sahip olduğunuz bir senaryo düşünün bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> görüntülemek istediğiniz çalışanların bir listesini tutan nesne bir <xref:System.Windows.Controls.ListBox>. Bu iki nesne arasındaki ilişkiyi oluşturmak için çalışan listenize bağlamak <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox>. Ancak, yeni bir çalışan, gruba katılıyor olduğunu varsayalım. Bu yeni bir kişiye bağımlı eklemek için düşündüğünüzden <xref:System.Windows.Controls.ListBox> değerleri yalnızca bu kişinin çalışan listenize eklediğinizde ve veri bağlama altyapısı tarafından otomatik olarak tanınması için bu değişikliğin. Bu varsayım yanlış olur; çünkü değişiklik içinde yansıtılmaz <xref:System.Windows.Controls.ListBox> otomatik olarak. Bunun nedeni, [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> nesne olmayan otomatik olarak Yükselt bir koleksiyon değişti olayı. Ürününü <xref:System.Windows.Controls.ListBox> değişiklikleri almak için çalışanların listesi yeniden oluşturun ve yeniden bağlamanız gerekir <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox>. Bu çözüm çalışırken, bir büyük performans etkisi tanıtır. Her zaman, yeniden atama <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , <xref:System.Windows.Controls.ListBox> yeni bir nesne <xref:System.Windows.Controls.ListBox> ilk olarak önceki öğelerinden hemen oluşturur ve tüm listeyi yeniden oluşturur. Performans etkisi, büyütülür, <xref:System.Windows.Controls.ListBox> karmaşık bir <xref:System.Windows.DataTemplate>.  
  
 Bu sorun için çok etkili bir çözüm çalışan listesini olmaktır bir <xref:System.Collections.ObjectModel.ObservableCollection%601>. Bir <xref:System.Collections.ObjectModel.ObservableCollection%601> nesnesi başlatan bir değişiklik bildirimi veri bağlama altyapısı alabilir. Olay ekler veya kaldırır bir <xref:System.Windows.Controls.ItemsControl> listesinin tümünü yeniden oluşturmak zorunda kalmadan.  
  
 Aşağıdaki tabloda bir güncelleştirme süresini gösterir <xref:System.Windows.Controls.ListBox> (devre dışı kullanıcı Arabirimi sanallaştırma ile) bir öğe eklendiğinde. İlk satır numarasında geçen süreyi temsil eder, [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> nesne bağlı <xref:System.Windows.Controls.ListBox> öğenin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. İkinci satır numarasında geçen süreyi temsil eder, bir <xref:System.Collections.ObjectModel.ObservableCollection%601> bağlı <xref:System.Windows.Controls.ListBox> öğenin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Not önemli zaman tasarrufu kullanarak <xref:System.Collections.ObjectModel.ObservableCollection%601> veri bağlama stratejisi.  
  
|**Veri ItemsSource bağlama**|**Güncelleştirme 1 için süresi (ms) öğesi**|  
|--------------------------------------|---------------------------------------|  
|İçin bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> nesnesi|1656|  
|İçin bir <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>IList değil IEnumerable ItemsControl için bağlama  
 Bağlama arasında seçim yapma varsa bir <xref:System.Collections.Generic.IList%601> veya <xref:System.Collections.IEnumerable> için bir <xref:System.Windows.Controls.ItemsControl> nesne öğesini <xref:System.Collections.Generic.IList%601> nesne. Bağlama <xref:System.Collections.IEnumerable> için bir <xref:System.Windows.Controls.ItemsControl> zorlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir sarmalayıcı oluşturmak için <xref:System.Collections.Generic.IList%601> nesnesidir performansınızı ikinci bir nesnesinin gereksiz yükü tarafından etkilenen anlamına gelir.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>CLR nesnelerini yalnızca XML veri bağlama için yapın.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlama için verir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] içerik; ancak, veri bağlama [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] içeriktir veri bağlama daha yavaş [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri. Dönüştürme işlemini [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] tek amacı, veri bağlama için ise XML veri nesnesi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)
- [Donanımdan Yararlanma](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)
- [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
- [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Nesne Davranışı](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)
- [Uygulama Kaynakları](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
- [Diğer Performans Önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
- [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [İzlenecek yol: Bir WPF uygulamasında uygulama verilerini önbelleğe alma](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)

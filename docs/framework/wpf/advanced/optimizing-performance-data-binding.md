---
title: 'Performansı İyileştirme: Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: da870e9459ee2cbe0384c146546c378fb7247f03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-data-binding"></a>Performansı İyileştirme: Veri Bağlama
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama sunmak ve veri ile etkileşim kurmak üzere uygulamalar için basit ve tutarlı bir yol sağlar. Çeşitli veri kaynakları biçiminde veriye, öğeler bağlanabilir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri ve [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Bu konu, veri bağlama performans önerileri sağlar.  
  

  
<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Veri bağlama başvuruları nasıl çözümleneceğini  
 Veri bağlama başarım sorunlarını ele önce keşfetmek faydalı olacaktır nasıl [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama altyapısı bağlama için nesne başvuruları giderir.  
  
 Kaynağı bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama herhangi olabilir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesnesi. Özellikler, alt özellikleri veya dizin oluşturucular, bağlayabileceğiniz bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesnesi. Bağlama başvuruları ya da Microsoft .NET Framework yansıma kullanarak çözümlenir veya bir <xref:System.ComponentModel.ICustomTypeDescriptor>. Bağlama için nesne başvurularını çözmek için üç yöntem şunlardır.  
  
 Yansıma kullanarak ilk yöntemi içerir. Bu durumda, <xref:System.Reflection.PropertyInfo> nesnesi özelliğin özniteliklerini bulmak için kullanılır ve özellik meta verilerine erişim sağlar. Kullanırken <xref:System.ComponentModel.ICustomTypeDescriptor> arabirimi, veri bağlama altyapısı bu arabirimi özellik değerlerine erişmek için kullanır. <xref:System.ComponentModel.ICustomTypeDescriptor> Arabirimidir burada nesnesinin yok statik bir özellikler kümesi durumlarda özellikle yararlıdır.  
  
 Özellik değişikliği bildirimlerini uygulayarak ya da sağlanabilir <xref:System.ComponentModel.INotifyPropertyChanged> ilişkili değişikliği bildirimlerini kullanarak veya arabirim <xref:System.ComponentModel.TypeDescriptor>. Ancak, özellik değişikliği bildirimlerini uygulamak için tercih edilen strateji kullanmaktır <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Kaynak nesnesi ise bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesne ve kaynak özelliği olan bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama altyapısı sahip ilk yansıma kaynak nesne üzerinde almak için kullanılacak <xref:System.ComponentModel.TypeDescriptor>ve ardından sorgu bir <xref:System.ComponentModel.PropertyDescriptor>. Bu dizisi yansıma işlemleri, büyük olasılıkla bir performans açısından çok zaman alır.  
  
 Nesne başvuruları çözmek için ikinci yöntem içerir bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] uygulayan kaynak nesnesi <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi ve olan bir kaynak özelliği bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği. Bu durumda, veri bağlama altyapısı yansıma doğrudan kaynak türü üzerinde kullanır ve gerekli özelliği alır. Bu hala en iyi yöntem değildir, ancak ilk yöntem kümesi gereksinimlerinde çalışma daha düşük maliyetlidir.  
  
 Nesne başvuruları çözmek için üçüncü yöntemi olan bir kaynak nesne içerir bir <xref:System.Windows.DependencyObject> ve olan bir kaynak özelliği bir <xref:System.Windows.DependencyProperty>. Bu durumda, veri bağlama altyapısı yansıma kullanması gerekmez. Bunun yerine, özellik altyapısı ve veri bağlama altyapısı birlikte özelliği başvurusunu bağımsız olarak çözümleyin. Bu, veri bağlama için kullanılan nesne başvuruları çözmek için en iyi yöntemdir.  
  
 Aşağıdaki tabloda veri bağlama hızına karşılaştırır <xref:System.Windows.Controls.TextBlock.Text%2A> bin özelliğinin <xref:System.Windows.Controls.TextBlock> bu üç yöntemi kullanarak öğeleri.  
  
|**Bir TextBlock metin özelliğini bağlama**|**Bağlama süresi (ms)**|**İşleme zamanı--bağlama (ms) içerir**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Bir özelliği için bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesnesi|115|314|  
|Bir özelliği için bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] uygulayan nesne <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|İçin bir <xref:System.Windows.DependencyProperty> , bir <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Büyük CLR nesnelere bağlama  
 Verileri tek bir bağladığınızda önemli performans etkisi olan [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özellikleri binlerce nesne. Birden çok tek bir nesnede bölerek Bu etkiyi en aza indirebilirsiniz [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] daha az özellik nesneleriyle. Veri bağlama için tek bir işleme zamanlarını ve bağlama tablo büyük gösterir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] birden çok daha küçük nesnelerine karşı nesnesi.  
  
|**Veri bağlama 1000 TextBlock nesneleri**|**Bağlama süresi (ms)**|**İşleme zamanı--bağlama (ms) içerir**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|İçin bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 1000 özellikleriyle nesnesi|950|1200|  
|1000 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] bir özelliği olan nesneleri|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Bir ItemsSource bağlama  
 Sahip olduğunuz bir senaryo düşünün bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> görüntülemek istediğiniz çalışanların bir listesini tutar nesnesi bir <xref:System.Windows.Controls.ListBox>. Bu iki nesne arasındaki ilişkiyi oluşturmak için çalışan listenize bağlamak <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox>. Ancak, grubunuza katılacak yeni bir çalışan olduğunu varsayalım. Bu yeni bir kişiye bağımlı eklemek için düşünebilirsiniz <xref:System.Windows.Controls.ListBox> değerleri, sadece bu kişinin çalışan listenize ekleyin ve bu değişikliğin veri bağlama altyapısı tarafından otomatik olarak tanınmıyor. Bu varsayım yanlış olur; çünkü değişiklik içinde yansıtılmaz <xref:System.Windows.Controls.ListBox> otomatik olarak. Bunun nedeni, [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> nesnesi değil otomatik olarak Yükselt koleksiyonu değiştirildi olay. Alabilmek için <xref:System.Windows.Controls.ListBox> değişiklikleri almak için çalışanların listesini oluşturun ve yeniden eklemektir olurdu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox>. Bu çözüm çalışırken, çok büyük performans etkisi tanıtır. Bağladığınız her sefer <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , <xref:System.Windows.Controls.ListBox> yeni bir nesne <xref:System.Windows.Controls.ListBox> ilk olarak önceki öğelerinden hemen oluşturur ve tüm listeyi yeniden oluşturur. Performans etkisi, büyütülmüş, <xref:System.Windows.Controls.ListBox> karmaşık bir <xref:System.Windows.DataTemplate>.  
  
 Bu sorun için çok etkili bir çözüm çalışan listesini yapmaktır bir <xref:System.Collections.ObjectModel.ObservableCollection%601>. Bir <xref:System.Collections.ObjectModel.ObservableCollection%601> nesne veri bağlama altyapısı alabileceği bir değişiklik bildirimi başlatır. Olay ekler veya kaldırır bir <xref:System.Windows.Controls.ItemsControl> listenin tamamını yeniden oluşturmak zorunda kalmadan.  
  
 Aşağıdaki tabloda güncelleştirme süresini gösterir <xref:System.Windows.Controls.ListBox> (ile UI sanallaştırma devre dışı) bir öğe eklendiğinde. İlk satır numarasında geçen süreyi temsil eder, [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> nesnesi bağlı <xref:System.Windows.Controls.ListBox> öğenin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. İkinci satır numarasında geçen süreyi temsil eder, bir <xref:System.Collections.ObjectModel.ObservableCollection%601> bağlı <xref:System.Windows.Controls.ListBox> öğenin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Önemli zaman tasarrufu kullanarak Not <xref:System.Collections.ObjectModel.ObservableCollection%601> veri bağlama stratejisini.  
  
|**Veri ItemsSource bağlama**|**Saat 1 için güncelleştirme öğesi (ms)**|  
|--------------------------------------|---------------------------------------|  
|İçin bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> nesnesi|1656|  
|İçin bir <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>IList ItemsControl değil IEnumerable bağlama  
 Bağlama arasında seçim yapmanız gerekirse bir <xref:System.Collections.Generic.IList%601> veya bir <xref:System.Collections.IEnumerable> için bir <xref:System.Windows.Controls.ItemsControl> nesne, seçin <xref:System.Collections.Generic.IList%601> nesnesi. Bağlama <xref:System.Collections.IEnumerable> için bir <xref:System.Windows.Controls.ItemsControl> zorlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir sarmalayıcı oluşturmak için <xref:System.Collections.Generic.IList%601> performansınızı ikinci nesnenin gereksiz ek yükü tarafından etkilenen anlamına gelir nesnesi.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Veri bağlama için CLR nesnelerini yalnızca XML yapın.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlama için verir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] içerik; ancak, veri bağlamayı [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] içeriktir veri bağlama daha yavaş [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri. Dönüştürme işlemini [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] tek amacı veri bağlama ise XML veri nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Uygulama Performansını Planlama](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Donanımdan Yararlanma](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Nesne Davranışı](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Uygulama Kaynakları](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Diğer Performans Önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)

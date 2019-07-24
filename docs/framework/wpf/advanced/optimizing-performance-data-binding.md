---
title: 'Performansı İyileştirme: Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 25c0906e9f23948476732b10b2c5fb10fe4eb55f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401455"
---
# <a name="optimizing-performance-data-binding"></a>Performansı İyileştirme: Veri Bağlama
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]veri bağlama, uygulamaların sunmak ve verilerle etkileşim kurmak için basit ve tutarlı bir yol sağlar. Öğeler, CLR nesneleri [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]biçimindeki çeşitli veri kaynaklarından verilere bağlanabilir.  
  
 Bu konu veri bağlama performans önerileri sağlar.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Veri bağlama başvurularının çözümlenmesi  
 Veri bağlama performans sorunlarını tartışmadan önce, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama altyapısının bağlama için nesne başvurularını nasıl çözümlediği araştırılamaz.  
  
 Veri bağlamasının kaynağı herhangi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bir CLR nesnesi olabilir. Bir CLR nesnesinin özelliklerine, alt özelliklerine veya dizin oluşturucularının bağlama yapabilirsiniz. Bağlama başvuruları Microsoft .NET Framework Reflection veya bir <xref:System.ComponentModel.ICustomTypeDescriptor>kullanılarak çözümlenir. Bağlama için nesne başvurularını çözümlemek için üç yöntem aşağıda verilmiştir.  
  
 İlk yöntem, yansıma kullanımını içerir. Bu durumda, <xref:System.Reflection.PropertyInfo> nesne özelliğin özniteliklerini saptamak için kullanılır ve özellik meta verilerine erişim sağlar. <xref:System.ComponentModel.ICustomTypeDescriptor> Arabirimi kullanılırken, veri bağlama altyapısı özellik değerlerine erişmek için bu arabirimi kullanır. <xref:System.ComponentModel.ICustomTypeDescriptor> Arabirim, özellikle nesnenin statik bir özellik kümesine sahip olmadığı durumlarda faydalıdır.  
  
 Özellik değişikliği bildirimleri, <xref:System.ComponentModel.INotifyPropertyChanged> <xref:System.ComponentModel.TypeDescriptor>arabirimini uygulayarak veya ile ilişkili değişiklik bildirimleri kullanılarak gerçekleştirilebilir. Ancak, özellik değişikliği bildirimlerinin uygulanması için tercih edilen strateji kullanılır <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Kaynak nesne bir CLR nesnesi ise ve kaynak özelliği bir CLR özelliği ise, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama altyapısının öncelikle kaynak nesnesinde <xref:System.ComponentModel.TypeDescriptor>yansıma kullanması gerekir ve ardından bir <xref:System.ComponentModel.PropertyDescriptor>için sorgu alır. Bu yansıma işlemi sırası, performans açısından çok zaman alabilir.  
  
 Nesne başvurularını çözümlemek için ikinci yöntem, <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulayan bir clr kaynak nesnesi ve CLR özelliği olan bir kaynak özelliği içerir. Bu durumda, veri bağlama altyapısı doğrudan kaynak türünde yansıma kullanır ve gerekli özelliği alır. Bu, en iyi yöntem olmaya devam eder, ancak çalışma kümesi gereksinimlerinde ilk yöntemden daha az ücret alınacaktır.  
  
 Nesne başvurularını çözmenin üçüncü yöntemi bir olan kaynak nesnesi <xref:System.Windows.DependencyObject> ve bir olan kaynak özelliği <xref:System.Windows.DependencyProperty>içerir. Bu durumda, veri bağlama altyapısının yansıma kullanması gerekmez. Bunun yerine, özellik altyapısı ve veri bağlama altyapısı birlikte Özellik başvurusunu bağımsız olarak çözümler. Bu, veri bağlama için kullanılan nesne başvurularını çözümlemek için en iyi yöntemdir.  
  
 Aşağıdaki tabloda, bu üç yöntemi kullanarak 1000 <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock> öğelerinin özelliği ile veri bağlama hızı karşılaştırılır.  
  
|**TextBlock öğesinin Text özelliğini bağlama**|**Bağlama süresi (MS)**|**İşleme süresi--bağlama dahildir (MS)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Bir CLR nesnesinin özelliğine|115|314|  
|Uygulayan bir CLR nesnesinin özelliğine<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|' A bir <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyProperty>|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Büyük CLR nesnelerine bağlama  
 Binlerce özellik içeren tek bir CLR nesnesine veri bağladığınızda önemli bir performans etkisi vardır. Bu etkiyi, tek nesneyi birden çok CLR nesnesine daha az özelliklerle bölerek bu etkiyi en aza indirebilir. Tablo, tek bir büyük CLR nesnesine ve birden çok daha küçük nesneye veri bağlamanın bağlama ve işleme sürelerini gösterir.  
  
|**Veri bağlama 1000 TextBlock nesneleri**|**Bağlama süresi (MS)**|**İşleme süresi--bağlama dahildir (MS)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|1000 özelliklerine sahip bir CLR nesnesine|950|1200|  
|Tek bir özellikle 1000 CLR nesnesine|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Itembir kaynağa bağlama  
 İçinde görüntülenmesini <xref:System.Collections.Generic.List%601> <xref:System.Windows.Controls.ListBox>istediğiniz çalışanların listesini tutan bir CLR nesnesine sahip olduğunuz bir senaryoyu düşünün. Bu iki nesne arasında bir yazışmalar oluşturmak için, çalışan listenizi <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox>öğesinin özelliğine bağlarsınız. Ancak, grubunuza katılan yeni bir çalışana sahip olduğunuzu varsayalım. Bu yeni kişiyi ilişkili <xref:System.Windows.Controls.ListBox> değerlerinizle eklemek için, bu kişiyi yalnızca çalışan listenize eklemenizi ve bu değişikliğin veri bağlama altyapısı tarafından otomatik olarak tanınmasını beklemeniz gerektiğini düşünebilirsiniz. Bu varsayım yanlış olduğunu kanıtlayacaktı; Bu durumda değişiklik <xref:System.Windows.Controls.ListBox> otomatik olarak yansıtılmaz. Bunun nedeni, clr <xref:System.Collections.Generic.List%601> nesnesinin bir koleksiyon değişti olayını otomatik olarak oluşturmaz. Değişiklikleri almak <xref:System.Windows.Controls.ListBox> için, çalışanların listesini yeniden oluşturmanız ve ' nin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox>özelliğine yeniden iliştirmeye ihtiyacınız vardır. Bu çözüm çalışırken çok büyük bir performans etkisi ortaya koymaktadır. ' Yi yeni <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> birnesneye<xref:System.Windows.Controls.ListBox> her atadığınızda, ilkiöncekiöğeleriniyerineatarvetümlistesiniyenidenoluşturur.<xref:System.Windows.Controls.ListBox> Daha karmaşık <xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate>bir eşleme yaptıysanız performans etkisi büyütülür.  
  
 Bu soruna yönelik çok verimli bir çözüm, çalışan listenizi bir <xref:System.Collections.ObjectModel.ObservableCollection%601>hale getirir. Bir <xref:System.Collections.ObjectModel.ObservableCollection%601> nesne, veri bağlama altyapısının alabileceği bir değişiklik bildirimi oluşturur. Olay, tüm listeyi yeniden oluşturmak gerekmeden bir <xref:System.Windows.Controls.ItemsControl> öğeyi öğesinden ekler veya kaldırır.  
  
 Aşağıdaki tabloda, <xref:System.Windows.Controls.ListBox> bir öğe eklendiğinde (UI Sanallaştırması kapatılmış) öğesini güncelleştirmek için gereken süre gösterilmektedir. İlk satırdaki sayı, clr <xref:System.Collections.Generic.List%601> nesnesi <xref:System.Windows.Controls.ListBox> öğenin öğesine <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>bağlandığında geçen süreyi temsil eder. İkinci satırdaki sayı, bir <xref:System.Collections.ObjectModel.ObservableCollection%601> <xref:System.Windows.Controls.ListBox> öğe öğesine <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>bağlandığında geçen süreyi temsil eder. <xref:System.Collections.ObjectModel.ObservableCollection%601> Veri bağlama stratejisini kullanarak önemli zaman tasarruflarını aklınızda edin.  
  
|**ItemSource verileri bağlama**|**1 öğe için güncelleştirme zamanı (MS)**|  
|--------------------------------------|---------------------------------------|  
|Bir clr <xref:System.Collections.Generic.List%601> nesnesine|1656|  
|Bir<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>IList 'i ıtem' öğesine bağlama IEnumerable denetimi  
 Bir <xref:System.Collections.Generic.IList%601> veya<xref:System.Windows.Controls.ItemsControl> bir nesnesine bağlama arasında bir seçeneğiniz varsa <xref:System.Collections.Generic.IList%601> nesneyi seçin. <xref:System.Collections.IEnumerable> Bir <xref:System.Collections.IEnumerable> <xref:System.Windows.Controls.ItemsControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sarmalayıcı nesnesioluşturmakiçinbirzorlamaylabağlama,budaPerformanslarınızınikincibirnesneningereksizekyükündenetkilenmesidir.<xref:System.Collections.Generic.IList%601>  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Yalnızca veri bağlama için CLR nesnelerini XML 'e dönüştürmeyin.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] içeriğe veri bağlamayı sağlar; ancak [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] içeriğe veri bağlama, clr nesnelerine veri bağlamaktan daha yavaştır. Tek amaç veri bağlama için ise, CLR nesne verilerini XML 'e dönüştürmeyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](planning-for-application-performance.md)
- [Donanımdan Yararlanma](optimizing-performance-taking-advantage-of-hardware.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [2B Grafikleri ve Görüntüleme](optimizing-performance-2d-graphics-and-imaging.md)
- [Nesne Davranışı](optimizing-performance-object-behavior.md)
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Metin](optimizing-performance-text.md)
- [Diğer Performans Önerileri](optimizing-performance-other-recommendations.md)
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [İzlenecek yol: WPF uygulamasında uygulama verilerini önbelleğe alma](walkthrough-caching-application-data-in-a-wpf-application.md)

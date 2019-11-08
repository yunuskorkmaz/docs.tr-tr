---
title: 'Performansı İyileştirme: Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 9b302be3ed9f01ccd27470063f49966dc7d74708
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740801"
---
# <a name="optimizing-performance-data-binding"></a>Performansı İyileştirme: Veri Bağlama
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama, uygulamaların verileri sunmak ve verilerle etkileşim kurmak için basit ve tutarlı bir yol sağlar. Öğeler, CLR nesneleri ve XML biçiminde çeşitli veri kaynaklarından verilere bağlanabilir.  
  
 Bu konu veri bağlama performans önerileri sağlar.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Veri bağlama başvurularının çözümlenmesi  
 Veri bağlama performans sorunlarını tartışmadan önce, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama altyapısının bağlama için nesne başvurularını nasıl çözümlediği araştırılamaz.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlamasının kaynağı herhangi bir CLR nesnesi olabilir. Bir CLR nesnesinin özelliklerine, alt özelliklerine veya dizin oluşturucularının bağlama yapabilirsiniz. Bağlama başvuruları Microsoft .NET Framework Reflection veya bir <xref:System.ComponentModel.ICustomTypeDescriptor>kullanılarak çözümlenir. Bağlama için nesne başvurularını çözümlemek için üç yöntem aşağıda verilmiştir.  
  
 İlk yöntem, yansıma kullanımını içerir. Bu durumda, <xref:System.Reflection.PropertyInfo> nesnesi özelliğin özniteliklerini saptamak için kullanılır ve özellik meta verilerine erişim sağlar. <xref:System.ComponentModel.ICustomTypeDescriptor> arabirimini kullanırken, veri bağlama altyapısı özellik değerlerine erişmek için bu arabirimi kullanır. <xref:System.ComponentModel.ICustomTypeDescriptor> arabirimi, özellikle nesnenin statik bir özellik kümesine sahip olmadığı durumlarda faydalıdır.  
  
 Özellik değişikliği bildirimleri <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulayarak ya da <xref:System.ComponentModel.TypeDescriptor>ilişkili değişiklik bildirimleri kullanılarak gerçekleştirilebilir. Ancak, özellik değişikliği bildirimleri uygulamak için tercih edilen strateji <xref:System.ComponentModel.INotifyPropertyChanged>kullanmaktır.  
  
 Kaynak nesne bir CLR nesnesi ise ve kaynak özelliği bir CLR özelliği ise, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama altyapısının öncelikle <xref:System.ComponentModel.TypeDescriptor>almak için kaynak nesnede yansıma kullanması ve ardından bir <xref:System.ComponentModel.PropertyDescriptor>sorgulaması gerekir. Bu yansıma işlemi sırası, performans açısından çok zaman alabilir.  
  
 Nesne başvurularını çözümlemek için ikinci yöntem <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulayan bir CLR kaynak nesnesi ve CLR özelliği olan bir kaynak özelliği içerir. Bu durumda, veri bağlama altyapısı doğrudan kaynak türünde yansıma kullanır ve gerekli özelliği alır. Bu, en iyi yöntem olmaya devam eder, ancak çalışma kümesi gereksinimlerinde ilk yöntemden daha az ücret alınacaktır.  
  
 Nesne başvurularını çözmenin üçüncü yöntemi, bir <xref:System.Windows.DependencyObject> ve bir <xref:System.Windows.DependencyProperty>kaynak özelliği olan bir kaynak nesnesi içerir. Bu durumda, veri bağlama altyapısının yansıma kullanması gerekmez. Bunun yerine, özellik altyapısı ve veri bağlama altyapısı birlikte Özellik başvurusunu bağımsız olarak çözümler. Bu, veri bağlama için kullanılan nesne başvurularını çözümlemek için en iyi yöntemdir.  
  
 Aşağıdaki tabloda, bu üç yöntemi kullanarak 1000 <xref:System.Windows.Controls.TextBlock> öğesi <xref:System.Windows.Controls.TextBlock.Text%2A> özelliğini bağlama verilerinin hızı karşılaştırılır.  
  
|**TextBlock öğesinin Text özelliğini bağlama**|**Bağlama süresi (MS)**|**İşleme süresi--bağlama dahildir (MS)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Bir CLR nesnesinin özelliğine|115|314|  
|<xref:System.ComponentModel.INotifyPropertyChanged> uygulayan bir CLR nesnesinin özelliğine|115|305|  
|Bir <xref:System.Windows.DependencyObject><xref:System.Windows.DependencyProperty>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Büyük CLR nesnelerine bağlama  
 Binlerce özellik içeren tek bir CLR nesnesine veri bağladığınızda önemli bir performans etkisi vardır. Bu etkiyi, tek nesneyi birden çok CLR nesnesine daha az özelliklerle bölerek bu etkiyi en aza indirebilir. Tablo, tek bir büyük CLR nesnesine ve birden çok daha küçük nesneye veri bağlamanın bağlama ve işleme sürelerini gösterir.  
  
|**Veri bağlama 1000 TextBlock nesneleri**|**Bağlama süresi (MS)**|**İşleme süresi--bağlama dahildir (MS)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|1000 özelliklerine sahip bir CLR nesnesine|950|1200|  
|Tek bir özellikle 1000 CLR nesnesine|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Itembir kaynağa bağlama  
 Bir <xref:System.Windows.Controls.ListBox>göstermek istediğiniz çalışanların listesini tutan bir CLR <xref:System.Collections.Generic.List%601> nesnesine sahip olduğunuz bir senaryoyu düşünün. Bu iki nesne arasında bir yazışmalar oluşturmak için, çalışan listenizi <xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğine bağlarsınız. Ancak, grubunuza katılan yeni bir çalışana sahip olduğunuzu varsayalım. Bu yeni kişiyi bağlantılı <xref:System.Windows.Controls.ListBox> değerlerinizle eklemek için, bu kişiyi yalnızca çalışan listenize eklemeniz ve bu değişikliğin veri bağlama altyapısı tarafından otomatik olarak tanınmasını beklemeniz gerekir. Bu varsayım yanlış olduğunu kanıtlayacaktı; Gerçekte, değişiklik <xref:System.Windows.Controls.ListBox> otomatik olarak yansıtılmaz. Bunun nedeni, CLR <xref:System.Collections.Generic.List%601> nesnesinin koleksiyon tarafından değiştirilen bir olayı otomatik olarak oluşturmaz. Değişiklikleri <xref:System.Windows.Controls.ListBox> almak için, çalışanların listesini yeniden oluşturmanız ve <xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğine yeniden iliştirmeye ihtiyacınız vardır. Bu çözüm çalışırken çok büyük bir performans etkisi ortaya koymaktadır. <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> yeni bir nesneye her atadığınızda, <xref:System.Windows.Controls.ListBox> önce önceki öğelerini atar ve tüm listesini yeniden oluşturur. <xref:System.Windows.Controls.ListBox> karmaşık bir <xref:System.Windows.DataTemplate>eşleniyorsa performans etkisi büyütülür.  
  
 Bu soruna yönelik çok verimli bir çözüm, çalışan listenizi bir <xref:System.Collections.ObjectModel.ObservableCollection%601>hale maktır. <xref:System.Collections.ObjectModel.ObservableCollection%601> nesnesi, veri bağlama altyapısının alabileceği bir değişiklik bildirimi oluşturur. Olay, tüm listeyi yeniden oluşturma gerekmeden bir <xref:System.Windows.Controls.ItemsControl> öğe ekler veya kaldırır.  
  
 Aşağıdaki tabloda, bir öğe eklendiğinde <xref:System.Windows.Controls.ListBox> güncelleştirmek için gereken süre gösterilmektedir (UI Sanallaştırması kapatılmış şekilde). İlk satırdaki sayı, CLR <xref:System.Collections.Generic.List%601> nesnesi <xref:System.Windows.Controls.ListBox> öğenin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>bağlandığında geçen süreyi temsil eder. İkinci satırdaki sayı, bir <xref:System.Collections.ObjectModel.ObservableCollection%601> <xref:System.Windows.Controls.ListBox> öğenin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>bağlandığında geçen süreyi temsil eder. <xref:System.Collections.ObjectModel.ObservableCollection%601> veri bağlama stratejisini kullanarak önemli ölçüde tasarruf edin.  
  
|**ItemSource verileri bağlama**|**1 öğe için güncelleştirme zamanı (MS)**|  
|--------------------------------------|---------------------------------------|  
|Bir CLR <xref:System.Collections.Generic.List%601> nesnesine|1656|  
|<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>IList 'i ıtem' öğesine bağlama IEnumerable denetimi  
 Bir <xref:System.Collections.Generic.IList%601> bağlama veya bir <xref:System.Collections.IEnumerable> <xref:System.Windows.Controls.ItemsControl> nesnesine bağlama arasında seçim yaptıysanız, <xref:System.Collections.Generic.IList%601> nesnesini seçin. <xref:System.Collections.IEnumerable> bir <xref:System.Windows.Controls.ItemsControl> bağlama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir sarmalayıcı <xref:System.Collections.Generic.IList%601> nesnesi oluşturmaya zorlar, bu da Performanslarınızın ikinci bir nesnenin gereksiz ek yükünden etkilenmesidir.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Yalnızca veri bağlama için CLR nesnelerini XML 'e dönüştürmeyin.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], XML içeriğine veri bağlama olanağı sağlar; Ancak, XML içeriğine veri bağlama, CLR nesnelerine veri bağlamaktan daha yavaştır. Tek amaç veri bağlama için ise, CLR nesne verilerini XML 'e dönüştürmeyin.  
  
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
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma](walkthrough-caching-application-data-in-a-wpf-application.md)

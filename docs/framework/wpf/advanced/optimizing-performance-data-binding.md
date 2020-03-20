---
title: 'Performansı İyileştirme: Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 3128f453378f9d74f867b571e30f2be4e8add8a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186753"
---
# <a name="optimizing-performance-data-binding"></a>Performansı İyileştirme: Veri Bağlama
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]veri bağlama, uygulamaların veri sunması ve verilerle etkileşimde bulunması için basit ve tutarlı bir yol sağlar. Öğeler CLR nesneleri ve XML şeklinde çeşitli veri kaynaklarından gelen verilere bağlanabilir.  
  
 Bu konu veri bağlama performans önerileri sağlar.  

<a name="HowDataBindingReferencesAreResolved"></a>
## <a name="how-data-binding-references-are-resolved"></a>Veri Bağlama Başvuruları Nasıl Çözülür?  
 Veri bağlama performans sorunlarını tartışmadan önce, veri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bağlama altyapısının bağlayıcı için nesne başvurularını nasıl çözdüğünü keşfetmeye değer.  
  
 Veri bağlamanın [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kaynağı herhangi bir CLR nesnesi olabilir. ClR nesnesinin özelliklerine, alt özelliklerine veya dizin leyicilerine bağlanabilirsiniz. Bağlayıcı başvurular Microsoft .NET Framework yansıması veya bir <xref:System.ComponentModel.ICustomTypeDescriptor>. Burada bağlama için nesne başvuruları çözmek için üç yöntem vardır.  
  
 İlk yöntem yansıma yı içerir. Bu durumda, <xref:System.Reflection.PropertyInfo> nesne özelliğin özniteliklerini keşfetmek için kullanılır ve özellik meta verilerine erişim sağlar. <xref:System.ComponentModel.ICustomTypeDescriptor> Arabirimi kullanırken, veri bağlama altyapısı özellik değerlerine erişmek için bu arabirimi kullanır. Arabirim, <xref:System.ComponentModel.ICustomTypeDescriptor> özellikle nesnenin statik bir özellik kümesine sahip olmadığı durumlarda kullanışlıdır.  
  
 Özellik değişikliği <xref:System.ComponentModel.INotifyPropertyChanged> bildirimleri, arabirimi uygulayarak veya 'ile <xref:System.ComponentModel.TypeDescriptor>ilişkili değişiklik bildirimleri kullanılarak sağlanabilir. Ancak, özellik değişikliği bildirimleri uygulamak için tercih <xref:System.ComponentModel.INotifyPropertyChanged>edilen strateji kullanmaktır.  
  
 Kaynak nesne bir CLR nesnesi ve kaynak özelliği bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] CLR özelliği ise, veri bağlama altyapısı <xref:System.ComponentModel.TypeDescriptor>almak için önce <xref:System.ComponentModel.PropertyDescriptor>kaynak nesne üzerinde yansıması kullanmak zorunda , ve sonra bir . Bu yansıma işlemleri dizisi, performans açısından potansiyel olarak çok zaman alır.  
  
 Nesne başvurularını çözmek için ikinci yöntem, arabirimi uygulayan <xref:System.ComponentModel.INotifyPropertyChanged> bir CLR kaynak nesnesi ve CLR özelliği olan bir kaynak özelliği içerir. Bu durumda, veri bağlama motoru doğrudan kaynak türüne yansıma kullanır ve gerekli özelliği alır. Bu hala en iyi yöntem değildir, ancak çalışma kümesi gereksinimleri ilk yöntemdaha az maliyetli olacaktır.  
  
 Nesne başvurularını çözmek için üçüncü yöntem, a <xref:System.Windows.DependencyObject> ve kaynak <xref:System.Windows.DependencyProperty>özelliği olan bir kaynak nesne içerir. Bu durumda, veri bağlama motorunun yansıma kullanması gerekmez. Bunun yerine, özellik altyapısı ve veri bağlama altyapısı birlikte özellik başvuruçözür. Bu, veri bağlama için kullanılan nesne başvurularını çözmek için en uygun yöntemdir.  
  
 Aşağıdaki tabloda, bu üç yöntemi <xref:System.Windows.Controls.TextBlock.Text%2A> kullanarak bin <xref:System.Windows.Controls.TextBlock> öğenin özelliğini bağlayan veri hızı karşılaştırılmaktadır.  
  
|**TextBlock'un Metin özelliğini bağlama**|**Bağlama süresi (ms)**|**Render süresi -- bağlama (ms) içerir**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|CLR nesnesinin özelliğine|115|314|  
|Uygulayan bir CLR nesnesinin özelliğine<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Bir. <xref:System.Windows.DependencyProperty> <xref:System.Windows.DependencyObject>|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>
## <a name="binding-to-large-clr-objects"></a>Büyük CLR Nesnelerine Bağlanma  
 Binlerce özelliği olan tek bir CLR nesnesine veri bağlanınca önemli bir performans etkisi vardır. Tek bir nesneyi daha az özelliklere sahip birden çok CLR nesnesine bölerek bu etkiyi en aza indirebilirsiniz. Tablo, birden çok küçük nesneye karşı tek bir büyük CLR nesnesine veri bağlama için bağlama ve işleme sürelerini gösterir.  
  
|**Veri bağlama 1000 TextBlock nesneleri**|**Bağlama süresi (ms)**|**Render süresi -- bağlama (ms) içerir**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|1000 özellisi olan bir CLR nesnesine|950|1200|  
|Tek bir özelliğe sahip 1000 CLR nesnesine|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>
## <a name="binding-to-an-itemssource"></a>Bir ItemsSource'a bağlanma  
 Bir <xref:System.Windows.Controls.ListBox>'de görüntülemek istediğiniz çalışanların <xref:System.Collections.Generic.List%601> listesini tutan bir CLR nesnesine sahip olduğunuz bir senaryo düşünün. Bu iki nesne arasında bir yazışma oluşturmak için, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> çalışan listenizi <xref:System.Windows.Controls.ListBox>. Ancak, grubunuza katılan yeni bir çalışanınız olduğunu varsayalım. Bu yeni kişiyi bağlı <xref:System.Windows.Controls.ListBox> değerlerinize eklemek için bu kişiyi çalışan listenize ekleyeceğiniz ve bu değişikliğin veri bağlama motoru tarafından otomatik olarak tanınmasını bekleyeceğinizi düşünebilirsiniz. Bu varsayım yanlış olur; aslında, değişiklik <xref:System.Windows.Controls.ListBox> otomatik olarak yansıtılmayacaktır. Bunun nedeni, CLR <xref:System.Collections.Generic.List%601> nesnesinin otomatik olarak değiştirilen bir olayı yükseltmemesidir. Değişiklikleri almak <xref:System.Windows.Controls.ListBox> için, çalışan listenizi yeniden oluşturmanız ve 'nin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğine yeniden iliştirmeniz <xref:System.Windows.Controls.ListBox>gerekir. Bu çözüm çalışırken, büyük bir performans etkisi sunar. Yeni bir nesneye yeniden atadığınızda, <xref:System.Windows.Controls.ListBox> ilk ibare önceki öğelerini atar ve tüm listesini yeniden oluşturur. <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Bir karmaşık <xref:System.Windows.DataTemplate>la eşlemleriniz <xref:System.Windows.Controls.ListBox> varsa performans etkisi büyütülmüşolur.  
  
 Bu soruna çok etkili bir çözüm çalışan <xref:System.Collections.ObjectModel.ObservableCollection%601>listenizi bir . Nesne, <xref:System.Collections.ObjectModel.ObservableCollection%601> veri bağlama altyapısının alabileceği bir değişiklik bildirimi yükseltir. Olay, tüm listeyi yeniden <xref:System.Windows.Controls.ItemsControl> oluşturmaya gerek kalmadan bir öğeyi ekler veya kaldırır.  
  
 Aşağıdaki tablo, bir öğe eklendiğinde <xref:System.Windows.Controls.ListBox> (Kullanıcı Arabirimi sanallaştırması kapalıyken) güncelleştirmenin gereken süreyi gösterir. İlk satırdaki sayı, CLR <xref:System.Collections.Generic.List%601> nesnesinin <xref:System.Windows.Controls.ListBox> öğenin . <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> İkinci satırdaki sayı, bir <xref:System.Collections.ObjectModel.ObservableCollection%601> <xref:System.Windows.Controls.ListBox> öğenin . <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Veri bağlama stratejisini <xref:System.Collections.ObjectModel.ObservableCollection%601> kullanarak önemli zaman tasarrufuna dikkat edin.  
  
|**ItemsSource'u veri bağlama**|**1 öğe (ms) için güncelleştirme süresi**|  
|--------------------------------------|---------------------------------------|  
|CLR <xref:System.Collections.Generic.List%601> nesnesine|1656|  
|Bir<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Öğeleri Bağlama IListKontrol Ayrılmaz  
 Bir <xref:System.Collections.IEnumerable> <xref:System.Windows.Controls.ItemsControl> nesneye bağlama <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IList%601> arasında bir seçeneğiniz varsa, nesneyi seçin. Bir <xref:System.Collections.IEnumerable> <xref:System.Windows.Controls.ItemsControl> sarmalayıcı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Collections.Generic.IList%601> nesnesi oluşturmak için bir kuvvete bağlama, bu da performansınızın ikinci bir nesnenin gereksiz yükünden etkilendiği anlamına gelir.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>CLR nesnelerini Yalnızca Veri Bağlama için XML'e dönüştürmeyin.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XML içeriğine veri bağlamanızı sağlar; ancak, XML içeriğine veri bağlama CLR nesneleri için veri bağlama daha yavaştır. Tek amaç veri bağlamaysa CLR nesne verilerini XML'e dönüştürmeyin.  
  
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
- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma](walkthrough-caching-application-data-in-a-wpf-application.md)

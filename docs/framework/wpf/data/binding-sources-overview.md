---
title: Kaynakların Bağlanmasına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: 4b7a5681840bf70eaebc824ff3d0dbeef3d1d799
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169101"
---
# <a name="binding-sources-overview"></a>Kaynakların Bağlanmasına Genel Bakış
Veri bağlamada bağlama kaynak nesnesi, verileri aldığınız nesneye başvurur. Bu konuda, bağlama kaynağı olarak kullanabileceğiniz nesne türleri ele alınmaktadır.  

<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>Bağlama kaynak türleri  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]veri bağlama, aşağıdaki bağlama kaynak türlerini destekler:  
  
|Bağlama kaynağı|Açıklama|  
|--------------------|-----------------|  
|ortak dil çalışma zamanı (CLR) nesneleri|Ortak özellikler, alt özellikler ve tüm ortak dil çalışma zamanı (CLR) nesnesinin dizin oluşturucularının bağlayabilirsiniz. Bağlama altyapısı, özelliklerin değerlerini almak için CLR Reflection kullanır. Alternatif olarak, uygulayan <xref:System.ComponentModel.ICustomTypeDescriptor> veya <xref:System.ComponentModel.TypeDescriptionProvider> içeren nesneler, bağlama altyapısı ile de çalışır.<br /><br /> Bağlama kaynağı olarak kullanılabilecek bir sınıfın nasıl uygulanacağı hakkında daha fazla bilgi için, bu konunun ilerleyen kısımlarında yer alan [bağlama kaynağı için bir sınıf uygulama](#classes) bölümüne bakın.|  
|dinamik nesneler|<xref:System.Dynamic.IDynamicMetaObjectProvider> Arabirim uygulayan bir nesnenin kullanılabilir özelliklerine ve dizin oluşturucularının bağlama yapabilirsiniz. Kodda üyeye erişebilmek için bağlayabilirsiniz. Örneğin, dinamik bir nesne koddaki bir üyeye aracılığıyla `someObjet.AProperty`erişmenizi sağlar, bağlama `AProperty`yolunu ayarlayarak buna bağlanabilirsiniz.|  
|ADO.NET nesneleri|Gibi ADO.NET nesnelerine <xref:System.Data.DataTable>bağlayabilirsiniz. ADO.net <xref:System.Data.DataView> , bağlama altyapısının <xref:System.ComponentModel.IBindingList> dinlediği değişiklik bildirimleri sağlayan arabirimini uygular.|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]nesneyi|<xref:System.Xml.XmlNode>, `XPath` Veya<xref:System.Xml.XmlDocument>' de sorguları bağlanabilir ve üzerinde sorgu çalıştırabilirsiniz. <xref:System.Xml.XmlElement> Biçimlendirme içindeki bağlama kaynağı olan [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilere erişmenin kolay bir yolu bir <xref:System.Windows.Data.XmlDataProvider> nesne kullanmaktır. Daha fazla bilgi için bkz. [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Ayrıca, bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>' a bağlanabilir veya LINQ to XML kullanarak bu türlerin nesnelerinde çalıştırılan sorguların sonuçlarına bağlayabilirsiniz. Biçimlendirme içindeki bağlama kaynağı olan XML verilerine erişmek için LINQ to XML kullanmanın kolay bir yolu bir <xref:System.Windows.Data.ObjectDataProvider> nesne kullanmaktır. Daha fazla bilgi için bkz. [XML sorgu sonuçları Için XDocument, XElement veya LINQ 'A bağlama](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|  
|<xref:System.Windows.DependencyObject>nesneyi|Herhangi <xref:System.Windows.DependencyObject>birinin bağımlılık özelliklerine bağlanabilirsiniz. Bir örnek için bkz. [Iki denetimin özelliklerini bağlama](how-to-bind-the-properties-of-two-controls.md).|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>Bağlama kaynağı için bir sınıf uygulama  
 Kendi bağlama kaynaklarınızı oluşturabilirsiniz. Bu bölümde, bağlama kaynağı olarak kullanılacak bir sınıf uyguladığınızda bilmeniz gereken noktalar açıklanmaktadır.  
  
### <a name="providing-change-notifications"></a>Değişiklik bildirimleri sağlama  
 Ya <xref:System.Windows.Data.BindingMode.OneWay> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] da bağlamayı kullanıyorsanız (bağlama kaynak özellikleri dinamik olarak değiştiğinde güncelleştirilmesini istiyorsanız), uygun bir özellik değiştirildi bildirim mekanizması uygulamanız gerekir. <xref:System.Windows.Data.BindingMode.TwoWay> Önerilen mekanizma, clr veya dinamik sınıfın <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulaması içindir. Daha fazla bilgi için bkz. [özellik değişiklik bildirimini uygulama](how-to-implement-property-change-notification.md).  
  
 Gerçekleştirmeyen <xref:System.ComponentModel.INotifyPropertyChanged>bir CLR nesnesi oluşturursanız, bir bağlamada kullanılan verilerin güncel kalmasını sağlamak için kendi bildirim sisteminizi düzenlemeniz gerekir. Değişiklik bildirimlerini istediğiniz her bir özelliğin `PropertyChanged` modelini destekleyerek değişiklik bildirimleri sağlayabilirsiniz. Bu kalıbı desteklemek için her bir özellik için *PropertyName*Changed olayını tanımlarsınız; burada *PropertyName* özelliğin adıdır. Olay, özellik her değiştiğinde tetiklenir.  
  
 Bağlama kaynağınız bu bildirim mekanizmalarından birini uygularsa, hedef güncelleştirmeler otomatik olarak gerçekleşir. Herhangi bir nedenden dolayı bağlama kaynağınız uygun özellik değiştirme bildirimlerini sağlamıyorsa, hedef özelliği açıkça güncelleştirmek için <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> yöntemini kullanma seçeneğiniz vardır.  
  
### <a name="other-characteristics"></a>Diğer özellikler  
 Aşağıdaki listede dikkat edilecek diğer önemli noktaları verilmiştir:  
  
- İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nesnesini oluşturmak istiyorsanız, sınıfının parametresiz bir oluşturucusu olmalıdır. Gibi bazı .NET dillerde C#parametresiz Oluşturucu sizin için oluşturulmuş olabilir.  
  
- Bağlama için bağlama kaynak özellikleri olarak kullandığınız özellikler, sınıfınızın ortak özellikleri olmalıdır. Açıkça tanımlanan arabirim özelliklerine bağlama amaçları için erişilemez, ya da hiçbir temel uygulamasına sahip olmayan korumalı, özel, iç veya sanal özellikler olabilir.  
  
- Ortak alanlara bağlayamazsınız.  
  
- Sınıfınıza göre belirtilen özelliğin türü, bağlamaya geçirilen türdür. Ancak, son olarak bağlama tarafından kullanılan tür bağlama kaynak özelliği değil, bağlama hedefi özelliğinin türüne bağlıdır. Türünde bir fark varsa, özel özelliğinin ilk olarak bağlamaya nasıl geçtiğini işlemek için bir dönüştürücü yazmak isteyebilirsiniz. Daha fazla bilgi için bkz. <xref:System.Windows.Data.IValueConverter>.  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>Tüm nesneleri bağlama kaynağı olarak kullanma  
 Tüm nesneyi bağlama kaynağı olarak kullanabilirsiniz. Veya özelliğini kullanarak bir bağlama kaynağı belirtebilir ve ardından boş bir bağlama bildirimi sağlayabilirsiniz: `{Binding}`. <xref:System.Windows.Data.Binding.Source%2A> <xref:System.Windows.FrameworkElement.DataContext%2A> Bunun yararlı olduğu senaryolar, tür String olan nesnelere bağlamayı, ilgilendiğiniz birden fazla özelliğe sahip nesnelere bağlamayı veya koleksiyon nesnelerine bağlamayı içerir. Tüm koleksiyon nesnesine bağlama örneği için bkz. [hiyerarşik verilerle ana ayrıntı modelini kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Verilerin, bağlantılı hedef özelliği için anlamlı olması için özel mantık uygulamanız gerekebileceğini unutmayın. Özel mantık özel bir dönüştürücü biçiminde olabilir (varsayılan tür dönüştürmesi yoksa) veya bir <xref:System.Windows.DataTemplate>. Dönüştürücüler hakkında daha fazla bilgi için [veri bağlamaya genel bakış](data-binding-overview.md)' ın veri dönüştürme bölümüne bakın. Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](data-templating-overview.md).  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>Koleksiyon nesnelerini bağlama kaynağı olarak kullanma  
 Genellikle, bağlama kaynağı olarak kullanmak istediğiniz nesne bir özel nesneler koleksiyonudur. Her nesne, yinelenen bir bağlamanın bir örneğinin kaynağı olarak görev yapar. Örneğin, uygulamanızın, kaç tane siparişin `CustomerOrders` mevcut olduğunu ve her `CustomerOrder` birinde yer alan verileri öğrenmek için koleksiyon üzerinde yineleme yapan nesnelerden oluşan bir koleksiyonunuz olabilir.  
  
 <xref:System.Collections.IEnumerable> Arabirimini uygulayan herhangi bir koleksiyonun üzerinde listeleme yapabilirsiniz. Bununla birlikte, koleksiyondaki ekleme veya silme işlemlerinin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] otomatik olarak güncelleştirilmesini sağlamak için dinamik bağlamaları ayarlamak için koleksiyonun <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimini uygulaması gerekir. Bu arabirim, temeldeki koleksiyon değiştiğinde oluşturulması gereken bir olay gösterir.  
  
 Sınıfı, <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi kullanıma sunan bir veri koleksiyonunun yerleşik bir uygulamasıdır. <xref:System.Collections.ObjectModel.ObservableCollection%601> Koleksiyon içindeki bireysel veri nesneleri, önceki bölümlerde açıklanan gereksinimleri karşılamalıdır. Bir örnek için bkz. [oluşturma ve bir ObservableCollection bağlama](how-to-create-and-bind-to-an-observablecollection.md). Kendi koleksiyonunuzu uygulamadan önce, <xref:System.Collections.ObjectModel.ObservableCollection%601> , ve <xref:System.ComponentModel.BindingList%601>gibi var olan koleksiyon sınıflarından <xref:System.Collections.Generic.List%601> <xref:System.Collections.ObjectModel.Collection%601>birini ya da birçok başka konuda kullanmayı düşünün.  
  
 WPF hiçbir şekilde doğrudan bir koleksiyona bağlanmaz. Bir koleksiyonu bağlama kaynağı olarak belirtirseniz, WPF aslında koleksiyonun varsayılan görünümüne bağlanır. Varsayılan görünümler hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](data-binding-overview.md).  
  
 Gelişmiş bir senaryonuz varsa ve kendi koleksiyonunuzu uygulamak istiyorsanız, <xref:System.Collections.IList> arabirimini kullanmayı göz önünde bulundurun. <xref:System.Collections.IList>, dizin tarafından tek tek erişilebilen, performansı iyileştirebilecek, genel olmayan nesnelerin bir koleksiyonunu sağlar.  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>Veri bağlamada izin gereksinimleri  
 Veri bağlama sırasında uygulamanın güven düzeyini göz önünde bulundurmanız gerekir. Aşağıdaki tabloda, hangi özellik türlerinin tam güvende ya da kısmi güvende yürütülen bir uygulamada bağlanacağı özetlenmektedir:  
  
|Özellik türü<br /><br /> (tüm erişim değiştiricileri)|Dinamik nesne özelliği|Dinamik nesne özelliği|CLR özelliği|CLR özelliği|Dependency özelliği|Dependency özelliği|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**Güven düzeyi**|**Tam güven**|**Kısmi güven**|**Tam güven**|**Kısmi güven**|**Tam güven**|**Kısmi güven**|  
|Genel sınıf|Evet|Evet|Evet|Evet|Evet|Evet|  
|Genel olmayan sınıf|Evet|Hayır|Evet|Hayır|Evet|Evet|  
  
 Bu tabloda, veri bağlamasındaki izin gereksinimleriyle ilgili aşağıdaki önemli noktaları açıklanmaktadır:  
  
- CLR özellikleri için, bağlama altyapısı yansıma kullanarak bağlama kaynağı özelliğine erişebilmiş olduğu sürece veri bağlama işe yarar. Aksi halde bağlama altyapısı, özelliğin bulunamadığını ve geri dönüş değerini ya da varsa varsayılan değeri kullanacağını belirten bir uyarı verir.  
  
- Derleme zamanında veya çalışma zamanında tanımlanan dinamik nesnelerdeki özelliklere bağlanabilirsiniz.  
  
- Bağımlılık özelliklerine her zaman bağlanabilirsiniz.  
  
 Bağlama için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] izin gereksinimi benzerdir. Kısmi güven korumalı alanında, <xref:System.Windows.Data.XmlDataProvider> belirtilen verilere erişim izni olmadığında başarısız olur.  
  
 Anonim türe sahip nesneler iç. Anonim türlerin özelliklerine yalnızca tam güvende çalışırken bağlayabilirsiniz. Anonim türler hakkında daha fazla bilgi için bkz. [anonim türlerC# (Programlama Kılavuzu)](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) veya [anonim türler (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).  
  
 Kısmi güven güvenliği hakkında daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.ObjectDataProvider>
- <xref:System.Windows.Data.XmlDataProvider>
- [Bağlama Kaynağı Belirtme](how-to-specify-the-binding-source.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [LINQ to XML ile WPF Verilerini Bağlamaya Genel Bakış](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)

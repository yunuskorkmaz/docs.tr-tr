---
title: Kaynakların Bağlanmasına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: bd397bfad26863e302b0f69c3aa57155f0d62b79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="binding-sources-overview"></a>Kaynakların Bağlanmasına Genel Bakış
Veri bağlama bağlama kaynak nesnesi verileri elde ettiğiniz nesneye başvurur. Bu konu bağlama kaynağı olarak kullanabileceğiniz nesne türlerini açıklar.  
  
  
  
<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>Bağlama kaynak türleri  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama aşağıdaki bağlama kaynak türlerini destekler:  
  
|Kaynak bağlama|Açıklama|  
|--------------------|-----------------|  
|[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] Nesneleri|Herhangi bir dizin oluşturucular yanı sıra ortak özellikler, alt özellikleri bağlayabilirsiniz [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nesnesi. Bağlama altyapısı kullanır [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliklerinin değerlerini almak için yansıma. Alternatif olarak, uygulayan nesneler <xref:System.ComponentModel.ICustomTypeDescriptor> veya kayıtlı <xref:System.ComponentModel.TypeDescriptionProvider> bağlama altyapısı ile de çalışır.<br /><br /> Bağlama kaynağı olarak görev bir sınıf uygulama hakkında daha fazla bilgi için bkz: [bağlama kaynağı için bir sınıf uygulama](#classes) bu konuda daha sonra.|  
|dinamik nesneler|Kullanılabilir özellikler ve dizin oluşturucular uygulayan nesnenin bağlayabilirsiniz <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimi. Kodda üyeye erişebiliyorsanız, onu bağlayabilirsiniz. Örneğin, bir dinamik Nesne bir üye kodu aracılığıyla erişmenizi sağlayan `someObjet.AProperty`, onu bağlama yolu ayarlayarak bağlayabilirsiniz `AProperty`.|  
|[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] Nesneleri|Bağlayabileceğiniz [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] gibi nesneleri <xref:System.Data.DataTable>. [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] <xref:System.Data.DataView> Uygulayan <xref:System.ComponentModel.IBindingList> bağlama altyapısı dinler değişim bildirimlerini sağlayan arabirim.|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] Nesneleri|Bağlayabilir ve çalıştırabilirsiniz `XPath` üzerinde sorgular bir <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlDocument>, veya <xref:System.Xml.XmlElement>. Erişmek için kolay bir yol [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] biçimlendirmede bağlama kaynağı veri kullanmaktır bir <xref:System.Windows.Data.XmlDataProvider> nesnesi. Daha fazla bilgi için bkz: [XML verileri kullanarak bir XMLDataProvider ve XPath sorguları bağlamak](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Ayrıca bağlayabileceğiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>, veya bağı LINQ-XML kullanarak bu tür nesneler üzerinde çalışan sorgu sonuçları. LINQ-XML biçimlendirmede bağlama kaynağı XML verilere erişmek için kullanılacak kolay bir yol kullanmaktır bir <xref:System.Windows.Data.ObjectDataProvider> nesnesi. Daha fazla bilgi için bkz: [XDocument, XElement veya LINQ XML sorgu sonuçları için bağlamak](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|  
|<xref:System.Windows.DependencyObject> Nesneleri|İçin bağımlılık özellikleri herhangi bağlayabilirsiniz <xref:System.Windows.DependencyObject>. Bir örnek için bkz: [özellikleri, iki denetimler bağlama](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>Bağlama kaynağı için bir sınıf uygulama  
 Kendi bağlama kaynaklarınızı oluşturabilirsiniz. Bu bölümde bağlama kaynağı olarak hizmet verecek bir sınıf uygulama durumunda bilmeniz gerekenler açıklanmaktadır.  
  
### <a name="providing-change-notifications"></a>Değişiklik bildirimleri sağlama  
 Ya da kullanıyorsanız, <xref:System.Windows.Data.BindingMode.OneWay> veya <xref:System.Windows.Data.BindingMode.TwoWay> bağlama (içermesini istediğinizden, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bağlama kaynağı özellikleri dinamik olarak değiştiğinde güncelleştirmek için), uygun özellik değiştirildi bildirim mekanizması uygulamalıdır. İçin önerilen mekanizmasıdır [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] uygulamak için dinamik sınıf veya <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Daha fazla bilgi için bkz: [uygulama özellik değişikliği bildirimi](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
 Oluşturursanız, bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] uygulamayan nesne <xref:System.ComponentModel.INotifyPropertyChanged>, kendi bildirim sistemi bağlamada kullanılan verinin güncel olduğundan emin olmak düzenlemeniz gerekir. Değişiklik bildirimleri destekleyerek sağlayabilirsiniz `PropertyChanged` değişiklik bildirimleri için istediğiniz her bir özellik için desen. Bu desenin desteklenmesi için tanımladığınız bir *PropertyName*değiştirilen olay her bir özellik için burada *PropertyName* özelliği adıdır. Özellik değişiklikleri her zaman olayı oluşturun.  
  
 Bağlama kaynağınız bu bildirim mekanizmaları uygularsa, hedef güncelleştirmeleri otomatik olarak gerçekleşir. Bağlama kaynağınız uygun özellik sağlamaz herhangi bir nedenle bildirimleri değiştirdiyseniz kullanma seçeneğini sahip <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> hedef özelliğini açıkça güncelleştirmek için yöntem.  
  
### <a name="other-characteristics"></a>Diğer özellikleri  
 Aşağıdaki listede dikkat edilecek diğer önemli noktaları sağlar:  
  
-   Nesne oluşturmak istiyorsanız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], sınıfın varsayılan bir oluşturucu olması gerekir. Bazı [!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)] gibi C# ' ta, dilleri varsayılan oluşturucu oluşturulabilir sizin için.  
  
-   Bağlama için bir bağlama kaynak özellikleri sınıfınızın ortak özellikleri olmalıdır gibi özellikleri, kullanın. Açıkça tanımlanmış arabirimi özellikleri bağlama amacıyla erişilemez veya temel uygulaması olmayan korumalı, özel, iç veya sanal özelliklerini kullanabilirsiniz.  
  
-   Genel alanlar bağlanamaz.  
  
-   Sınıfınızda bildirilen özellik türü bağlamaya geçirilen türüdür. Ancak, sonuçta bağlama tarafından kullanılan tür bağlama hedef özelliği türüne bağlıdır bağlama kaynak özelliği değil. Türü bir fark ise özel özelliği için bağlama başlangıçta nasıl geçtiğini işlemek için bir dönüştürücü yazmak isteyebilirsiniz. Daha fazla bilgi için bkz. <xref:System.Windows.Data.IValueConverter>.  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>Tüm nesneleri bağlama kaynağı olarak kullanma  
 Nesnenin tamamı bağlama kaynağı olarak kullanabilirsiniz. Kullanarak bir bağlama kaynağı belirtebilirsiniz <xref:System.Windows.Data.Binding.Source%2A> veya <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği, boş bir bağlama bildirimi girin: `{Binding}`. Bu faydalı olduğu senaryolar ilgilendiğiniz birden fazla özelliğe sahip nesnelere bağlama veya koleksiyon nesnelere bağlama bağlama türü dize olan nesneleri içerir. Tüm koleksiyon nesneyi bağlamanın bir örnek için bkz [hiyerarşik veriler ile ana-ayrıntı desenini kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Veri bağlama hedef özelliğinizi anlamlı olmasını sağlamak özel mantığını uygulamak gerekebileceğini unutmayın. (Varsayılan tür dönüşümü yoksa) özel mantık özel bir dönüştürücü biçiminde olabilir veya bir <xref:System.Windows.DataTemplate>. Veri dönüştürme bölümünü dönüştürücüler hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md). Veri şablonları hakkında daha fazla bilgi için bkz: [veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>Koleksiyon nesnelerini bağlama kaynağı olarak kullanma  
 Genellikle, bağlama kaynağı olarak kullanmak istediğiniz nesne özel nesneleri koleksiyonudur. Her nesne yinelenen bağlamanın bir örnek için kaynak olarak görev yapar. Örneğin, sahip olabileceğiniz bir `CustomerOrders` oluşan koleksiyon `CustomerOrder` nesneleri, burada, uygulamanızın tekrarlanan kaç siparişleri mevcut belirlemek için koleksiyon ve her bulunan veriler üzerinde.  
  
 Uygulayan herhangi bir koleksiyonu listeleme <xref:System.Collections.IEnumerable> arabirimi. Ancak, dinamik bağlamaları eklemeleri ya da silme işlemleri koleksiyondaki güncelleştirecek şekilde ayarlamak için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] toplama otomatik olarak uygulamalıdır <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi. Bu arabirim temel alınan koleksiyon her değiştiğinde oluşturulması gereken olayı sunar.  
  
 <xref:System.Collections.ObjectModel.ObservableCollection%601> Sınıftır kullanıma sunan bir veri toplama yerleşik bir uygulaması <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi. Koleksiyonun içindeki tek tek veri nesneleri, önceki bölümlerde açıklanan gereksinimleri karşılaması gerekir. Bir örnek için bkz: [oluşturup bağladığı ObservableCollection](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md). Kendi koleksiyonunuzu uygulamadan önce kullanmayı <xref:System.Collections.ObjectModel.ObservableCollection%601> veya gibi mevcut koleksiyonu birini sınıfları <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, ve <xref:System.ComponentModel.BindingList%601>, diğer birçok arasında.  
  
 WPF doğrudan bir koleksiyona hiçbir zaman bağlanmaz. Bağlama kaynağı olarak bir koleksiyonu belirtirseniz, WPF koleksiyonunun varsayılan görünümüne fiilen bağlar. Varsayılan görünümler hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Gelişmiş bir senaryo varsa ve kendi koleksiyonunuzu uygulamak isterseniz, kullanmayı <xref:System.Collections.IList> arabirimi. <xref:System.Collections.IList> performansı artırabilir dizini tarafından erişilebilecek nesnelerin genel olmayan koleksiyonu sağlar.  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>Veri bağlama içindeki izin gereksinimleri  
 Veri bağlama, uygulama güven düzeyini göz önüne aldığınızda, gerekir. Aşağıdaki tabloda türleri tam güven veya kısmi güven yürütüyor uygulamaya bağlanabilir hangi özelliği özetlenmiştir:  
  
|Özellik türü<br /><br /> (tüm erişim değiştiricileri)|Dinamik Nesne özelliği|Dinamik Nesne özelliği|CLR özelliği|CLR özelliği|Bağımlılık özelliği|Bağımlılık özelliği|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**Güven düzeyi**|**Tam güven**|**Kısmi güven**|**Tam güven**|**Kısmi güven**|**Tam güven**|**Kısmi güven**|  
|Genel sınıf|Evet|Evet|Evet|Evet|Evet|Evet|  
|Ortak olmayan sınıfı|Evet|Hayır|Evet|Hayır|Evet|Evet|  
  
 Bu tablo veri bağlamada izin gereksinimleri hakkında aşağıdaki önemli noktaları açıklanmaktadır:  
  
-   İçin [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özellikleri, veri bağlama çalışır bağlama altyapısı yansıma kullanarak bağlama kaynağı özelliğine mümkün olduğu sürece. Aksi takdirde, bağlama altyapısı özelliği bulunamıyor bir uyarı verir ve kullanılabilir durumdaysa geri dönüş veya varsayılan değerini kullanır.  
  
-   Derleme veya çalışma süresini tanımlanan dinamik nesneler özelliklere bağlayabilirsiniz.  
  
-   Bağımlılık özellikleri her zaman bağlayabilirsiniz.  
  
 İzni gereksinimini [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] bağlama benzerdir. Kısmi güven korumalı alanı içinde <xref:System.Windows.Data.XmlDataProvider> belirtilen verilere erişim izni olmadığında başarısız olur.  
  
 Anonim bir tür iç nesneleridir. Anonim türler özelliklerine yalnızca tam güvende çalışırken bağlayabilirsiniz. Anonim türler hakkında daha fazla bilgi için bkz: [anonim türler (C# programlama Kılavuzu)](~/docs/csharp/programming-guide/classes-and-structs/anonymous-types.md) veya [anonim türler (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).  
  
 Kısmi güven güvenlik hakkında daha fazla bilgi için bkz: [WPF kısmi güven güvenlik](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.ObjectDataProvider>  
 <xref:System.Windows.Data.XmlDataProvider>  
 [Bağlama Kaynağı Belirtme](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [LINQ to XML ile WPF Verilerini Bağlamaya Genel Bakış](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)

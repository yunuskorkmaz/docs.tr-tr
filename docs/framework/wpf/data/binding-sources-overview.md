---
title: Kaynakların Bağlanmasına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: 72ef84cb53c6eff1fc2fb9459b40e780869243a1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145931"
---
# <a name="binding-sources-overview"></a>Kaynakların Bağlanmasına Genel Bakış
Veri bağlamasında, bağlama kaynak nesne verilerden elde nesneye başvurur. Bu konu bağlama kaynağı olarak kullanabileceğiniz nesne türlerini açıklar.  

<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>Bağlama kaynağı türleri  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama, aşağıdaki bağlama kaynak türlerini destekler:  
  
|Bağlama kaynağı|Açıklama|  
|--------------------|-----------------|  
|[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] Nesneleri|Herhangi bir dizin oluşturucular yanı sıra ortak özellikler, alt özellikleri bağlayabilirsiniz [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nesne. Bağlama altyapısı kullanır [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] yansıma özelliklerinin değerlerini almak için. Alternatif olarak, uygulayan nesneler <xref:System.ComponentModel.ICustomTypeDescriptor> veya kayıtlı bir <xref:System.ComponentModel.TypeDescriptionProvider> bağlama altyapısı ile de çalışır.<br /><br /> Bağlama kaynağı olarak hizmet verebilen bir sınıfın nasıl uygulanacağı hakkında daha fazla bilgi için bkz. [bağlama kaynağı için bir sınıf uygulama](#classes) bu konuda.|  
|dinamik nesneler|Kullanılabilir özellikler ve dizin oluşturucular uygulayan nesnenin bağlayabilirsiniz <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimi. Üye kodu erişebiliyorsa, onu bağlayabilirsiniz. Örneğin, bir dinamik Nesne üyesi aracılığıyla kod içinde erişmenizi sağlayan `someObjet.AProperty`, onu bağlama yolu ayarlayarak bağlayabilirsiniz `AProperty`.|  
|[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] Nesneleri|Adlarınıza bağlayabileceğiniz [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] gibi nesneleri <xref:System.Data.DataTable>. [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] <xref:System.Data.DataView> Uygulayan <xref:System.ComponentModel.IBindingList> bağlama altyapısı için bekleyen değişiklik bildirimleri sağlayan arabirim.|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] Nesneleri|Bağlamak ve çalıştırmak `XPath` üzerinde sorgular bir <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlDocument>, veya <xref:System.Xml.XmlElement>. Erişim için kullanışlı bir yol [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] biçimlendirmede bağlama kaynağı veriler, kullanılacak bir <xref:System.Windows.Data.XmlDataProvider> nesne. Daha fazla bilgi için [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Ayrıca adlarınıza bağlayabileceğiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>, ya da LINQ to XML kullanarak bu tür nesneler üzerinde çalıştırılan sorguların sonuçlarını bağlayabilirsiniz. Bağlama kaynağı biçimlendirme içinde XML verilere erişmek, LINQ to XML kullanmak için kullanışlı bir yol kullanmaktır bir <xref:System.Windows.Data.ObjectDataProvider> nesne. Daha fazla bilgi için [XML sorgu sonuçları için XDocument, XElement veya LINQ'ya bağlama](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|  
|<xref:System.Windows.DependencyObject> Nesneleri|Bağımlılık özelliklerine herhangi bağlayabilirsiniz <xref:System.Windows.DependencyObject>. Bir örnek için bkz. [özellikleri, iki denetim bağlama](how-to-bind-the-properties-of-two-controls.md).|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>Bağlama kaynağı için bir sınıf uygulama  
 Kendi kaynakları bağlama oluşturabilirsiniz. Bu bölümde, bağlama kaynağı olarak görev yapacak bir sınıf uygulama, bilmeniz gereken şeyleri ele alınmaktadır.  
  
### <a name="providing-change-notifications"></a>Değişiklik bildirimleri oluşturma  
 Ya da kullanıyorsanız <xref:System.Windows.Data.BindingMode.OneWay> veya <xref:System.Windows.Data.BindingMode.TwoWay> bağlama (içermesini istediğinizden, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bağlama kaynağı özellikleri dinamik olarak değiştirdiğinizde güncelleştirmek için), uygun özellik değiştirildi bildirim mekanizması uygulamanız gerekir. İçin önerilen mekanizmadır [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] veya dinamik bir sınıf uygulamak için <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Daha fazla bilgi için [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md).  
  
 Oluşturursanız, bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] uygulamıyor nesne <xref:System.ComponentModel.INotifyPropertyChanged>, bir bağlamada kullanılan verilerin güncel olduğundan emin olmak kendi bildirim sistemi düzenlemeniz gerekir. Değişiklik bildirimleri destekleyerek sağlayabilirsiniz `PropertyChanged` bildirimleri için değiştirmek istediğiniz her bir özellik için bir desen. Bu desenin desteklenmesi için tanımladığınız bir *PropertyName*değiştirilen olay her bir özellik için burada *PropertyName* özelliğin adıdır. Size özelliği her değiştiğinde olayı oluşturun.  
  
 Bağlama kaynağınızı bu bildirim mekanizması uygularsa, hedef güncelleştirmeleri otomatik olarak gerçekleşir. Bağlama kaynak uygun özellik sağlamaz herhangi bir nedenle bildirimleri değiştirdiyseniz kullanma seçeneğini sahip <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> hedef özelliği açıkça güncelleştirmek için yöntemi.  
  
### <a name="other-characteristics"></a>Diğer özellikler  
 Dikkat edilecek diğer önemli noktaları listelenmektedir:  
  
-   Nesneyi oluşturmak istiyorsanız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], sınıfın bir varsayılan oluşturucuya sahip olmalıdır. Bazı [!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)] diller gibi C#, varsayılan oluşturucu sizin için oluşturulmuş olabilir.  
  
-   Özellikleri bağlama kaynak özellikleri bir bağlama için kendi sınıfınızı genel özelliklerini olması gerektiği kullanırsınız. Açıkça tanımlanmış arabirimi özellikleri, bağlama amacıyla erişilemiyor ya da temel uygulaması olmayan korumalı, özel, iç veya sanal özelliklerine erişebilirsiniz.  
  
-   Genel alanlar için bağlanamıyor.  
  
-   Sınıfınız içinde bildirilen özellik türünü bağlamaya geçirilen türüdür. Ancak, sonuçta bağlama tarafından kullanılan tür bağlama hedefi özelliği türüne bağlıdır bağlama kaynak özelliği değil. Türü bir fark varsa, özel özelliğinizi bağlamaya başlangıçta nasıl geçtiğini işlemek üzere bir dönüştürücü yazmak isteyebilirsiniz. Daha fazla bilgi için bkz. <xref:System.Windows.Data.IValueConverter>.  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>Tüm nesneleri bağlama kaynağı kullanma  
 Bir nesnenin tamamını bağlama kaynağı olarak kullanabilirsiniz. Kullanarak bir bağlama kaynağı belirtebilirsiniz <xref:System.Windows.Data.Binding.Source%2A> veya <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği ve ardından boş bir bağlama bildirimi sağlayın: `{Binding}`. Bu faydalı olduğu senaryolar ilgilendiğiniz birden fazla özelliğe sahip nesneleri bağlama veya koleksiyon nesnelere bağlama bağlama dize türünde nesneler içerir. Tüm koleksiyon nesne bağlama örneği için bkz [hiyerarşik veriler ile ana öğe-ayrıntı desenini kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Böylece veriler, ilişkili hedef özelliği için anlamlı olan özel mantığı uygulamak gerekebileceğini unutmayın. (Varsayılan tür dönüştürmesi mevcut değilse) özel mantığı özel bir dönüştürücü biçiminde olabilir veya <xref:System.Windows.DataTemplate>. Veri dönüştürme bölümünü dönüştürücüler hakkında daha fazla bilgi için bkz. [Data Binding Overview](data-binding-overview.md). Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](data-templating-overview.md).  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>Bağlama kaynağı koleksiyon nesnelerini kullanma  
 Genellikle, bağlama kaynağı kullanmak istediğiniz nesne bir özel nesneler topluluğudur. Her nesne bir örneğini yinelenen bir bağlama için kaynak görevi görür. Örneğin, sahip olabileceğiniz bir `CustomerOrders` oluşan bir koleksiyon `CustomerOrder` nesneleri, uygulamanızın nerede yinelenir koleksiyonu kaç siparişleri var olup olmadığını belirleyin ve her yer alan veriler üzerinde.  
  
 Uygulayan herhangi bir koleksiyonu numaralandırabilirsiniz <xref:System.Collections.IEnumerable> arabirimi. Ancak, dinamik bağlamaları eklemeler ve silmeleri koleksiyondaki güncelleştirecek şekilde ayarlamak için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] koleksiyonu otomatik olarak, uygulamalıdır <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi. Bu arabirim, altta yatan seçki değiştiğinde oluşturulması gereken bir olayı kullanıma sunar.  
  
 <xref:System.Collections.ObjectModel.ObservableCollection%601> Sınıfı, bir yerleşik uygulama kullanıma sunan bir veri toplama <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi. Koleksiyon içindeki tek veri nesneleri, önceki bölümde açıklanan gereksinimleri karşılaması gerekir. Bir örnek için bkz. [oluşturup bağladığı ObservableCollection](how-to-create-and-bind-to-an-observablecollection.md). Kendi koleksiyon uygulamadan önce kullanmayı <xref:System.Collections.ObjectModel.ObservableCollection%601> veya gibi bir mevcut koleksiyon sınıfları <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, ve <xref:System.ComponentModel.BindingList%601>, birçok diğerlerinin yanı sıra.  
  
 WPF hiçbir zaman doğrudan bir derlemeye bağlar. Bağlama kaynağı olarak bir koleksiyonu belirtirseniz, WPF gerçekten koleksiyonunun varsayılan görünümünü olarak bağlar. Varsayılan görünümleri hakkında daha fazla bilgi için bkz: [Data Binding Overview](data-binding-overview.md).  
  
 Gelişmiş bir senaryo varsa ve kendi koleksiyon uygulamak istediğiniz kullanmayı <xref:System.Collections.IList> arabirimi. <xref:System.Collections.IList> tek tek performansını iyileştirebilir dizin tarafından erişilebilen nesneleri genel olmayan koleksiyonu sağlar.  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>Veri bağlamaya izin gereksinimleri  
 Ne zaman veri bağlama, uygulamanın güven düzeyini düşünmelisiniz. Aşağıdaki tabloda, hangi özellik türleri tam güven veya kısmi güven yürüten bir uygulama bağlanabilir özetlenmektedir:  
  
|Özellik türü<br /><br /> (tüm erişim değiştiricileri)|Dinamik Nesne özelliği|Dinamik Nesne özelliği|CLR özelliği|CLR özelliği|Bağımlılık özelliği|Bağımlılık özelliği|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**Güven düzeyi**|**Tam güven**|**Kısmi güven**|**Tam güven**|**Kısmi güven**|**Tam güven**|**Kısmi güven**|  
|Genel sınıf|Evet|Evet|Evet|Evet|Evet|Evet|  
|Genel olmayan sınıfı|Evet|Hayır|Evet|Hayır|Evet|Evet|  
  
 Bu tablo, veri bağlama izni gereksinimleri hakkında aşağıdaki önemli noktaları açıklar:  
  
-   İçin [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özellikleri, veri bağlama çalışır bağlama altyapısı yansıma kullanarak bağlama kaynak özelliğine erişmek mümkün olduğu sürece. Aksi takdirde, bağlama altyapısı özelliği bulunamayan bir uyarı verir ve varsa, geri dönüş veya varsayılan değeri kullanır.  
  
-   Derleme zamanı veya çalışma zamanı tanımlanan dinamik nesnelerdeki özelliklerin bağlayabilirsiniz.  
  
-   Bağımlılık özellikleri için her zaman bağlayabilirsiniz.  
  
 İzni gereksinimini [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] bağlama benzerdir. Kısmi güven korumalı alanı içinde <xref:System.Windows.Data.XmlDataProvider> başarısız olduğunda, belirtilen veri erişim izni yok.  
  
 Anonim bir tür ile iç nesneleridir. Yalnızca tam güvende çalıştırıldığında, anonim türler özelliklerine bağlayabilirsiniz. Anonim türler hakkında daha fazla bilgi için bkz. [anonim türler (C# Programlama Kılavuzu)](~/docs/csharp/programming-guide/classes-and-structs/anonymous-types.md) veya [anonim türleri (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).  
  
 Kısmi güven güvenliği hakkında daha fazla bilgi için bkz. [WPF kısmi güven güvenliği](../wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.ObjectDataProvider>
- <xref:System.Windows.Data.XmlDataProvider>
- [Bağlama Kaynağı Belirtme](how-to-specify-the-binding-source.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [LINQ to XML ile WPF Verilerini Bağlamaya Genel Bakış](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)

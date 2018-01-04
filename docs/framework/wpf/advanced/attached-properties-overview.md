---
title: "Ekli Özelliklere Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d1d0eb55e75cd450d55b69aadca9c60e157eb09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="attached-properties-overview"></a>Ekli Özelliklere Genel Bakış
Ekli özellik XAML tarafından tanımlanan bir kavramdır. Ekli özellik, herhangi bir nesne ayarlanamaz genel özellik türü olarak kullanılmak üzere tasarlanmıştır. İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], ekli özellikler genellikle geleneksel özelliği "sarmalayıcı" olmayan bir bağımlılık özelliğinin özel biçimi tanımlanmış.  
  
   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu bağımlılık özellikleri varolan bağımlılık özelliklerinin tüketicisi açısından anladığınızı varsayar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Bu konudaki örnekleri izlemek için ayrıca XAML anlamak ve nasıl yazıldığını bilmeniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
<a name="attached_properties_usage"></a>   
## <a name="why-use-attached-properties"></a>Ekli özellikler neden kullanılır?  
 Ekli özellik bir amacı farklı alt öğeleri gerçekte bir üst öğesi tanımlanmış bir özellik için benzersiz değerler belirtmek izin vermektir. Bu senaryo, belirli bir uygulama nasıl içinde sunulacak oldukları üst öğenin alt bildirmesidir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Bir örnektir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> özelliği. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Özelliği içinde bulunan öğeler üzerinde ayarlamak için tasarlandığından iliştirilmiş bir özellik olarak oluşturulan bir <xref:System.Windows.Controls.DockPanel>, yerine <xref:System.Windows.Controls.DockPanel> kendisi. <xref:System.Windows.Controls.DockPanel> Sınıfı tanımlayan statik <xref:System.Windows.DependencyProperty> adlı alanı <xref:System.Windows.Controls.DockPanel.DockProperty>ve ardından sağlar <xref:System.Windows.Controls.DockPanel.GetDock%2A> ve <xref:System.Windows.Controls.DockPanel.SetDock%2A> ekli özellik için ortak erişimci olarak yöntemler.  
  
<a name="attached_properties_xaml"></a>   
## <a name="attached-properties-in-xaml"></a>XAML'de ekli özellikler  
 XAML'de, ekli özellikler sözdizimini kullanarak ayarladığınız *AttachedPropertyProvider*. *PropertyName*  
  
 Aşağıdaki nasıl ayarlanacağını gösteren bir örnektir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> XAML'de:  
  
 [!code-xaml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]  
  
 Kullanım statik özelliğe biraz benzer olduğunu unutmayın; her zaman türü başvuru <xref:System.Windows.Controls.DockPanel> sahip olan ve ekli özellik kaydeder adıyla belirtilen herhangi bir örneğine başvuran yerine.  
  
 Ayrıca, XAML'de iliştirilmiş bir özellik biçimlendirmede ayarladığınız bir öznitelik olduğundan, yalnızca ayarlama işlemi herhangi bir ilgisi yoktur. Stillerdeki tetikleyiciler gibi değerleri karşılaştırmak için dolaylı bazı mekanizmalar olmasına rağmen bir özelliği XAML'de doğrudan alınamıyor (Ayrıntılar için bkz [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md)).  
  
### <a name="attached-property-implementation-in-wpf"></a>WPF uygulamasında ekli özellik  
 İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]mevcut ekli özellikler çoğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] UI sunuya ilgili türleri, bağımlılık özellikleri olarak uygulanır. Ekli özellikler bağımlılık özellikleri ise bir XAML kavramı olan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kavram. Çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli özellikler bağımlılık özellikleri, bağımlılık özelliği kavramlarını özellik meta verileri gibi destekler ve bu özellik meta verisinden varsayılan değerler.  
  
<a name="howused"></a>   
## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Ekli özellikler sorumlu türü tarafından kullanılan nasıl  
 Ekli özellikler herhangi bir nesne ayarlanamaz olmasına rağmen otomatik olarak özelliğinin ayarlanması somut bir sonuç oluşturur veya değer herhangi bir zamanda başka bir nesne tarafından kullanılacak anlamına gelmez. Genellikle, çok çeşitli olası sınıf hiyerarşileri veya mantıksal ilişkiler gelen nesnelerin iliştirilmiş özelliği tanımlayan türü, her rapor ortak bilgileri böylece ekli özellikler yöneliktir. Ekli özelliğe genellikle tanımlayan tür Bu modeller birini aşağıdaki gibidir:  
  
-   Ekli özelliğe tanımlayan tür ekli özellik değerlerini ayarlar öğelerin üst öğesi olabilir şekilde tasarlanmıştır. Türü sonra bazı nesne ağaç yapısı karşı İç mantık aracılığıyla alt nesneleri tekrarlanan, değerlerini alır ve bu değerleri bazı şekilde davranır.  
  
-   Ekli özelliğe tanımlayan tür alt öğesi olarak çeşitli olası üst öğeler ve içerik modelleri için kullanılır.  
  
-   Ekli özelliğe tanımlayan tür bir hizmet temsil eder. Diğer türleri ekli özellik değerlerini ayarlayın. Ardından, özellik set öğesi hizmet bağlamında değerlendirildiğinde ekli özellik değerlerini hizmet sınıfı İç mantık elde edilir.  
  
### <a name="an-example-of-a-parent-defined-attached-property"></a>Bir üst tanımlı ekli özellik örneği  
 Tipik senaryo nerede [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli bir tanımlar özelliği olduğunda bir üst öğesi bir alt öğe koleksiyonunu destekler ve ayrıca bir davranış uygulayan burada davranışı tek tek her alt öğe için raporlandığı.  
  
 <xref:System.Windows.Controls.DockPanel>tanımlar <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> özelliği, eklenmiş ve <xref:System.Windows.Controls.DockPanel> işleme mantığı bir parçası olarak sınıf düzeyi koduna sahip (özellikle <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> ve <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). A <xref:System.Windows.Controls.DockPanel> örneği herhangi ve anlık alt öğeleri için bir değer ayarlamış olup olmadığını görmek için her zaman denetleyecek <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Öyleyse, bu değerleri bu belirli alt öğeye uygulanan işleme mantığı için giriş haline gelir. İç içe geçmiş <xref:System.Windows.Controls.DockPanel> örnekleri kendi hemen alt öğe koleksiyonları kabul eder, ancak bu davranışı uygulamasına özeldir nasıl <xref:System.Windows.Controls.DockPanel> işlemleri <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> değerleri. Teorik olarak en yakın üst ötesinde öğeleri etkileyen özellikleri ekli mümkündür. Varsa <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ekli özelliğe sahip olmayan bir öğe üzerinde ayarlanmış <xref:System.Windows.Controls.DockPanel> , hiçbir hata veya özel durum sırasında yapması üst öğesi oluşturulur. Bu yalnızca bir genel özellik değerini ayarlamak, ancak geçerli olduğu anlamına gelir <xref:System.Windows.Controls.DockPanel> bilgileri kullanabilecek üst.  
  
<a name="attached_properties_code"></a>   
## <a name="attached-properties-in-code"></a>Kodda ekli özellikler  
 Özelliklerinde bağlı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] normal olmayan [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] kolay alma/ayarlama erişimi için "sarmalayıcı" yöntemleri. Ekli özelliğe olmadığından budur mutlaka parçası [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ad alanı için örnekler özelliğinin ayarlandığı. Ancak, bir XAML işlemci XAML ayrıştırıldığında bu değerleri ayarlayın kurabilmesi gerekir. Etkili ekli özellik kullanımı desteklemek için ekli özelliğe sahip türü ayrılmış erişimci yöntemleri biçiminde uygulamalıdır `Get` *PropertyName* ve `Set` *PropertyName*. Bu ayrılmış erişimci yöntemleri almak veya kodda iliştirilmiş özelliği ayarlamak de yararlıdır. Kod açısından bakıldığında, bir ekli özellik erişimcisi yerine yöntem erişimcisi sahip bir yedekleme alanını benzer ve alan yedekleme'nün herhangi bir nesne yerine özellikle tanımlanması gerek bulunabilir özelliğidir.  
  
 Aşağıdaki örnek, iliştirilmiş bir özellik kodda nasıl ayarlayabileceğiniz gösterir. Bu örnekte, `myCheckBox` örneği <xref:System.Windows.Controls.CheckBox> sınıfı.  
  
 [!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
 [!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]  
  
 XAML benzer durumda ise `myCheckBox` zaten bir alt öğesi eklenmemişse `myDockPanel` tarafından üçüncü satır kod dördüncü satırlık bir kod bir özel durum oluşturmaz, ancak özellik değeri ile etkileşime olmayan bir <xref:System.Windows.Controls.DockPanel> üst ve bu nedenle hiçbir şey yapmayabilir. Yalnızca bir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> değerinin varlığıyla birleştirilmiş bir alt öğesi üzerinde ayarlanmış bir <xref:System.Windows.Controls.DockPanel> üst öğesi işlenmiş uygulamada etkili bir davranışa neden olur. (Bu durumda, ekli özellik ayarlayın, sonra ağaca iliştirebilirsiniz. Veya ağaca iliştirebilirsiniz sonra ekli özelliğini ayarlayın. Her iki eylemin sırası aynı sonucu sağlar.)  
  
<a name="attached_properties_metadata"></a>   
## <a name="attached-property-metadata"></a>Ekli özellik meta verileri  
 Özelliği kaydederken <xref:System.Windows.FrameworkPropertyMetadata> özelliği işleme, ölçüm ve benzeri etkileyip özelliğinin özelliklerini belirtmek için ayarlayın. Bağlı bir özellik için meta veriler bir bağımlılık özelliği genellikle farklı değildir. Ekli özellik meta verileri geçersiz kılmada varsayılan bir değer belirtirseniz, değeri geçersiz kılma sınıfının örnekleri örtülü iliştirilmiş özelliğin varsayılan değeri olur. Bazı sorgular ile iliştirilmiş bir özellik değeri için işlem, varsayılan değer özellikle bildirilen `Get` yöntemi erişimcisi bu özellik için burada belirttiğiniz meta verileri ve değeri için sınıfının bir örneği belirtme ekli özellik ayarlanmamış Aksi takdirde.  
  
 Bir özelliğin özellik değeri devralmayı etkinleştirmek istiyorsanız, bağlı olmayan bağımlılık özellikleri yerine ekli özellikler kullanmanız gerekir. Ayrıntılar için bkz [özellik değeri devralma](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
<a name="custom"></a>   
## <a name="custom-attached-properties"></a>Özel ekli özellikler  
  
<a name="create_attached_properties"></a>   
### <a name="when-to-create-an-attached-property"></a>Ekli özellik oluşturma zamanı  
 Özellik ayarlama tanımlayan sınıf dışındaki sınıflar için mekanizması sağlamak için bir neden olduğunda iliştirilmiş bir özellik oluşturabilirsiniz. Bunun en yaygın senaryo düzeni ' dir. Varolan Düzen özelliklerine örnekleri <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>, ve <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>. Buradaki etkin senaryo olan düzeni denetleme alt öğesi olarak mevcut öğeleri öğeleri tek tek düzen gereksinimlerini kendi düzen üst öğeler için express için her bir özellik değeri üst bağlı tanımladığı ayarlar özellik.  
  
 Ekli özellik kullanmaya yönelik başka bir senaryo, bir hizmet, sınıfı temsil eder ve hizmeti daha şeffaf bir şekilde tümleştirmek için sınıflar istediğinizde.  
  
 Başka bir senaryo almaktır [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] desteği, gibi **özellikleri** penceresi düzenleme. Daha fazla bilgi için bkz: [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Özellik değeri devralmayı kullanmak istiyorsanız, önce belirtildiği gibi iliştirilmiş bir özellik olarak kaydetmelisiniz.  
  
<a name="how_do_i_create_attached_properties"></a>   
### <a name="how-to-create-an-attached-property"></a>Ekli özellik oluşturma  
 Sınıfınıza diğer türlerde kullanmak için kesinlikle ekli özellik tanımlama ardından sınıf türetin yok <xref:System.Windows.DependencyObject>. Ancak öğesinden türetilen gerek <xref:System.Windows.DependencyObject> bütün izlerseniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli özelliğine sahip bir modelin bağımlılık özelliği de.  
  
 Bildirerek, ekli özellik bağımlılık özelliği olarak tanımlayan bir `public` `static` `readonly` türü alan <xref:System.Windows.DependencyProperty>. Dönüş değerini kullanarak bu alan tanımlayan <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi. Alan adı dizesine eklenerek ekli özellik adıyla eşleşmelidir `Property`, kurulan izlemek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tanımlayıcı adlandırma desenini temsil ettikleri özelliklere karşı alanları. Ekli özellik sağlayıcısı ayrıca statik sağlamalısınız `Get` *PropertyName* ve `Set` *PropertyName* ekli özellik erişimciler olarak yöntemlerini; bu işlem yapmak için başarısız ekli özellik erişememe özellik sistemindeki neden.  
  
> [!NOTE]
>  Eklenen özelliğin get erişimcisine atlarsanız, özellikte veri bağlama tasarım araçlarına gibi çalışmaz [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ve Expression Blend.  
  
#### <a name="the-get-accessor"></a>Get erişimcisi  
 İmza için `Get` *PropertyName* erişimci olması gerekir:  
  
 `public static object Get`*PropertyName* `(object` `target`  `)`  
  
-   `target` Nesnesi, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> yöntemi türleri parametre olarak <xref:System.Windows.UIElement>, çünkü iliştirilmiş özelliği yalnızca ayarlanmış olmayı amaçlar <xref:System.Windows.UIElement> örnekleri.  
  
-   Dönüş değeri, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.GetDock%2A> yöntemi olarak türleri <xref:System.Windows.Controls.Dock>, değer yalnızca o numaralandırması için ayarlanabilir.  
  
#### <a name="the-set-accessor"></a>Set erişimcisi  
 İmza için `Set` *PropertyName* erişimci olması gerekir:  
  
 `public static void Set`*PropertyName* `(object` `target` `, object` `value`    `)`  
  
-   `target` Nesnesi, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemi olarak türleri <xref:System.Windows.UIElement>, çünkü iliştirilmiş özelliği yalnızca ayarlanmış olmayı amaçlar <xref:System.Windows.UIElement> örnekleri.  
  
-   `value` Nesnesi, uygulamanızda daha belirli bir tür olarak belirtilebilir. Örneğin, <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemi olarak türleri <xref:System.Windows.Controls.Dock>, değer yalnızca o numaralandırması için ayarlanabilir. Bu yöntem için değerinin, ekli özellik biçimlendirmede ekli özellik kullanımı karşılaştığında XAML yükleyicisinden gelen giriş olduğunu unutmayın. Bu giriş, biçimlendirmede XAML öznitelik değeri olarak belirtilen değerdir. Bu nedenle olmalıdır tür dönüştürme, değer serileştirici veya kullanın, türü için işaretleme uzantısı desteği sağlayacak şekilde uygun türe (, sonuçta bir dize olan) öznitelik değerinden oluşturulabilir.  
  
 Aşağıdaki örnek, bağımlılık özelliği kaydını gösterir (kullanarak <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi), yanı sıra `Get` *PropertyName* ve `Set` *PropertyName* erişimciler . Örnekte, ekli özellik addır `IsBubbleSource`. Bu nedenle, erişimciler adlandırılmalıdır `GetIsBubbleSource` ve `SetIsBubbleSource`.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
#### <a name="attached-property-attributes"></a>Ekli özellik öznitelikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]birkaç tanımlar [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] yansıma işlemleri ve yansıma ve özellik bilgilerini tasarımcıları gibi tipik kullanıcılarının ekli özellikler hakkında bilgi sağlamayı amaçlar. Ekli özellikler sınırsız kapsam türü olduğundan, tasarımcıları XAML kullanan belirli teknoloji uygulamasında tanımlanan tüm iliştirilmiş özelliklerin genel listesiyle kullanıcıları zorlamayı önlemek için bir yönteme ihtiyacınız vardır. [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] , [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ekli özellikler burada ekli özelliğe görüntülenmesi gerekip Özellikler penceresinde durumları kapsamak için kullanılabilir tanımlar. Bu öznitelikler, kendi özel ekli özellikler için uygulamayı düşünebilirsiniz. Amaç ve sözdizimi [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] uygun başvuru sayfalarında açıklanır:  
  
-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>  
  
<a name="more"></a>   
## <a name="learning-more-about-attached-properties"></a>Ekli özellikler hakkında daha fazla öğrenme  
  
-   Ekli özellik oluşturma hakkında daha fazla bilgi için bkz: [iliştirilmiş özellik](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md).  
  
-   Daha gelişmiş bağımlılık özellikleri için kullanım senaryoları ve ekli özellikler için bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
-   Ayrıca bir özelliği eklenen bir özellik olarak ve bir bağımlılık özelliği olarak kaydedebilirsiniz, ancak hala "sarmalayıcı" uygulamalarını kullanıma sunar. Bu durumda, özelliği bu öğede ya da ayarlayabilirsiniz veya XAML aracılığıyla herhangi bir öğe üzerinde özellik sözdizimi bağlı. Standart ve iliştirilmiş kullanımlar için uygun bir senaryoyla özelliğin örneği <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.DependencyProperty>  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Ekli Özelliği Kaydetme](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)

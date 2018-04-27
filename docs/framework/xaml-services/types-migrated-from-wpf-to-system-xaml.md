---
title: WPF'den System.Xaml'e Geçirilen Türler
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
caps.latest.revision: 14
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4d4bc0b21770e5ac0c138c140334198d30a740a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>WPF'den System.Xaml'e Geçirilen Türler
İçinde [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] ve [!INCLUDE[net_v30_long](../../../includes/net-v30-long-md.md)], her iki [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ve Windows Workflow Foundation dahil XAML dil uygulama. WPF XAML uygulamasını genişletilebilirlik sağlanan genel türleri çoğunu WindowsBase, PresentationCore ve PresentationFramework derlemelerde vardı. Benzer şekilde, Windows Workflow Foundation XAML için genişletilebilirlik sağlanan genel türleri System.Workflow.ComponentModel derlemede vardı. İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], bazı XAML ilgili türleri System.Xaml derlemeye geçirilir. Bir ortak XAML dil Hizmetleri .NET Framework uygulamasını ilk olarak belirli bir framework'ün XAML uygulama tarafından tanımlanan ancak artık genel parçası olan birçok XAML genişletilebilirlik senaryoları mümkün kılar [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] XAML dil desteği. Bu konu, geçişle ilgili sorunlar açıklanır ve geçirilir türleri listelenmektedir.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Derlemeler ve ad alanları  
 İçinde [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ve [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], WPF XAML desteklemek için uygulanan türleri genellikle söz <xref:System.Windows.Markup> ad alanı. Bu tür çoğunu WindowsBase derlemede yoktu.  
  
 İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], yeni bir <xref:System.Xaml> ad alanı ve yeni bir System.Xaml derleme. WPF XAML için ilk olarak uygulanan türlerinin çoğunu şimdi genişletilebilirlik noktaları veya hizmetleri için XAML herhangi bir uygulaması olarak sağlanır. Daha fazla genel senaryolar için kullanılabilir hale getirme bir parçası olarak, türü kendi özgün WPF derlemesinden System.Xaml derlemeye iletilen türleridir. Bu, XAML genişletilebilirlik senaryolara (WPF ve Windows Workflow Foundation gibi) diğer çerçeveler derlemelerinin eklemek zorunda kalmadan olanak sağlar.  
  
 Geçirilen türlerinde türlerinin çoğu kalır <xref:System.Windows.Markup> ad alanı. Kısmen dosya başına temelinde mevcut uygulamalarında CLR ad alanı eşlemeleri çiğnemekten önlemek için bu. Sonuç olarak, <xref:System.Windows.Markup> ad alanında [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (System.Xaml derlemesinden) genel XAML dil desteği türlerinin bir karışımını içerir ve WPF XAML uygulama (WindowsBase ve diğer WPF derlemelerini) belirli türleri. System.xaml'e geçirilen, ancak daha önceden bir WPF derlemede varolan herhangi bir türü sürüm WPF derleme 4 tür iletme desteğine sahip.  
  
### <a name="workflow-xaml-support-types"></a>İş akışı XAML destek türleri  
 Windows Workflow Foundation de XAML destek türleri sağlanır ve çoğu durumda bu eşdeğer bir WPF aynı kısa adlarını kaldı. Windows Workflow Foundation XAML destek türlerinin bir listesi verilmiştir:  
  
-   <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Bu destek türleri hala mevcut için Windows Workflow Foundation derlemelerde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve özel Windows Workflow Foundation uygulamalar için hala kullanılabilir; Bununla birlikte, bunlar uygulamalar veya kullanmayın çerçeveleri tarafından başvurulması değil Windows Workflow Foundation.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 İçinde [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ve [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> WPF WindowsBase derlemede için sınıf. Windows Workflow Foundation için paralel bir sınıf <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, System.Workflow.ComponentModel derlemesindeki var. İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> sınıfı System.Xaml derlemeye geçirilir. İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> yalnızca belirli çerçevesinde yapı olanlar için .NET Framework XAML hizmetleri kullanan XAML genişletilebilirlik senaryosu için tasarlanmıştır. Mümkün olduğunda, belirli çerçeveleri veya Framework'te kullanıcı kodu aynı zamanda oluşturup <xref:System.Windows.Markup.MarkupExtension> XAML uzantısı için sınıf.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>MarkupExtension destekleme hizmeti sınıfları  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ve [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] WPF için kullanılabilen çeşitli Hizmetleri sağlanan için <xref:System.Windows.Markup.MarkupExtension> Implementers ve <xref:System.ComponentModel.TypeConverter> XAML'de türü/özellik kullanımı desteklemek için uygulamaları. Bu hizmetler şunlardır:  
  
-   <xref:System.Windows.Markup.IProvideValueTarget>  
  
-   <xref:System.Windows.Markup.IUriContext>  
  
-   <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  Başka bir hizmet [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] biçimlendirme uzantıları ilgili olduğu <xref:System.Windows.Markup.IReceiveMarkupExtension> arabirimi. <xref:System.Windows.Markup.IReceiveMarkupExtension> geçirilmedi ve işaretlenmiş `[Obsolete]` için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Daha önce kullanılan senaryoları <xref:System.Windows.Markup.IReceiveMarkupExtension> kullanmalısınız <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> geri aramalar öznitelikli. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> Ayrıca işaretlenmiş `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>XAML dil özellikleri  
 Daha önce birkaç XAML dil özellikleri ve WPF bileşenlerini PresentationFramework derlemede vardı. Bunlar olarak uygulanan bir <xref:System.Windows.Markup.MarkupExtension> biçimlendirme uzantısı kullanımları XAML biçimlendirme içinde kullanıma sunmak için bir alt kümesi. İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], WPF derlemeleri içermez projeleri bu XAML dil düzeyi özellikleri kullanabilmesi için bu System.Xaml derlemede mevcut. WPF için aynı bu uygulamaları kullanan [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] uygulamalar. Bu konu başlığı altında listelenen diğer durumlarda ile destekleyen türler devam mevcut <xref:System.Windows.Markup> ad önceki başvuruları çiğnemekten kaçının.  
  
 Aşağıdaki tabloda System.Xaml içinde tanımlanan XAML özellik desteği sınıflarının bir listesini içerir.  
  
|XAML dil özelliği|Kullanım|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 System.Xaml belirli destek sınıfları olmayabilir rağmen XAML dili için dil özellikleri artık işlemek için genel mantığı System.Xaml ve uygulanan XAML okuyucuları ve XAML yazıcıları içinde yer alıyor. Örneğin, `x:TypeArguments` XAML okuyucuları ve System.Xaml uygulamalarından; XAML yazarları tarafından işlenen bir özniteliktir, XAML düğüm akış içinde belirtilen, varsayılan (CLR tabanlı) XAML şema içeriği sahiptir, bir XAML tür sistemi gösterimi ve benzeri. Sonuç olarak, başvuru tüm XAML dil düzeyi özellikleri için şekline belgesidir [XAML Hizmetleri](../../../docs/framework/xaml-services/index.md) ve o genel alanı olarak ayarla WPF belgelerinin bir parçası olmak yerine .NET Framework belgeleri kümesinin bir alt konu, [Gelişmiş (Windows Presentation Foundation)](../../../docs/framework/wpf/advanced/index.md) (hala 3.5 belgelerine kümelerinde olduğu gibi).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer ve destekleyen sınıfları  
 <xref:System.Windows.Markup.ValueSerializer> Sınıfı, özellikle, burada serileştirme gerektirebilir birden fazla modları veya düğümde çıktıda XAML serileştirme durumlarda bir dize türü dönüşümünü destekler. İçinde [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ve [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], <xref:System.Windows.Markup.ValueSerializer> WPF WindowsBase derlemede dışındaydı. İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.ValueSerializer> sınıfı System.Xaml içinde olduğundan ve hiçbir XAML genişletilebilirlik senaryosu için değil, WPF yapı yöneliktir. <xref:System.Windows.Markup.IValueSerializerContext> (bir destek hizmeti) ve <xref:System.Windows.Markup.DateTimeValueSerializer> (belirli bir alt sınıfı) System.xaml'e ayrıca geçirilir.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>XAML ilgili öznitelikleri  
 WPF XAML hareketli XAML davranışlarını belirtmek için CLR Türleri uygulanabilir birkaç öznitelik dahil. WPF derlemelerde varolan öznitelikleri listesi aşağıdadır [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ve [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]. Bu öznitelikler System.XAML'ye geçirilir [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
-   <xref:System.Windows.Markup.AmbientAttribute>  
  
-   <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
-   <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
-   <xref:System.Windows.Markup.DependsOnAttribute>  
  
-   <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
-   <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
-   <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
-   <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
-   <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
-   <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
-   <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>Çeşitli sınıfları  
 <xref:System.Windows.Markup.IComponentConnector> Arabirimi ayrıntıların WindowsBase içinde [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ve [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], ancak System.Xaml içinde bulunmaktadır [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. <xref:System.Windows.Markup.IComponentConnector> Öncelikle, destek ve XAML işaretleme derleyicileri tooling için tasarlanmıştır.  
  
 <xref:System.Windows.Markup.INameScope> Arabirimi ayrıntıların WindowsBase içinde [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ve [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], ancak System.Xaml içinde bulunmaktadır [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. <xref:System.Windows.Markup.INameScope> XAML isim alanı için temel işlemleri tanımlar.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>System.Xaml ve WPF de mevcut paylaşılan adlarıyla XAML ile ilgili sınıflar  
 WPF derlemeler ve System.Xaml derlemede aşağıdaki sınıflar mevcut [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 WPF uygulaması bulunan <xref:System.Windows.Markup> ad alanı ve PresentationFramework derleme. System.Xaml uygulaması bulunan <xref:System.Xaml> ad alanı. WPF türleri kullanıyorsanız veya WPF türlerinden türetme, WPF uygulamalarında genellikle kullanması gereken <xref:System.Windows.Markup.XamlReader> ve <xref:System.Windows.Markup.XamlWriter> System.Xaml uygulamaları yerine. Açıklamalar, daha fazla bilgi için bkz: <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 WPF derlemeler ve System.Xaml başvuruları dahil olmak üzere ve ayrıca kullanıyorsanız `include` deyimleri her ikisi için de <xref:System.Windows.Markup> ve <xref:System.Xaml> ad alanlarını, türleri çözümlemek amacıyla bu API çağrıları tam olarak nitelemek gerekebilir karışıklık.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML Hizmetleri](../../../docs/framework/xaml-services/index.md)

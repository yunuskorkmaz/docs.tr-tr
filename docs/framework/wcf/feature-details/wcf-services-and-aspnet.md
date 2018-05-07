---
title: WCF Hizmetleri ve ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 6cfd4f8a5dc2a7835cba409a37b09166e49e8df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-services-and-aspnet"></a>WCF Hizmetleri ve ASP.NET
Bu konuda barındırma Windows Communication Foundation (WCF) hizmetlerini yan yana ASP.NET ve ASP.NET uyumluluk modunda barındırma ile anlatılmaktadır.  
  
## <a name="hosting-wcf-side-by-side-with-aspnet"></a>WCF yan yana ASP.NET ile barındırma  
 Internet Information Services (IIS) barındırılan WCF hizmetleri ile bulunabilir. ASPX sayfaları ve ASMX Web Hizmetleri içinde bir tek, ortak uygulama etki alanı. ASP.NET AppDomain yönetimi ve WCF ve ASP.NET HTTP çalışma zamanı için dinamik derleme gibi ortak altyapı hizmetleri sağlar. Yan yana varsayılan yapılandırmadır WCF için ASP.NET ile.  
  
 ![WCF hizmetleri ve ASP .NET: durumu paylaşımı](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 ASP.NET HTTP çalışma zamanı ASP.NET isteklerini işler ancak ASP.NET içerik olduğundan bu hizmetler aynı AppDomain içinde barındırılan olsa bile WCF hizmetleri için hedefleyen istekleri işleme katılmıyor. Bunun yerine, WCF hizmet modeli WCF hizmetlerine gönderilen iletiler durdurur ve WCF aktarım/kanal yığınından yönlendirir.  
  
 Yan yana modeli sonuçlarını aşağıdaki gibidir:  
  
-   ASP.NET ve WCF hizmetlerini AppDomain durumu paylaşabilirsiniz. İki çerçeveleri aynı AppDomain'e olabildiğinden WCF AppDomain durumu da (statik değişkenler, olaylar vb. dahil) ASP.NET ile paylaşabilirsiniz.  
  
-   WCF hizmetleri sürekli bağımsız barındırma ortamı ve taşıma olarak davranır. ASP.NET HTTP çalışma zamanı barındırma ortamı ve HTTP iletişimi IIS/ASP.NET bilerek birleştirilmiştir. Buna karşılık, WCF barındırma ortamları arasında tutarlı olarak davranacak şekilde tasarlanmıştır (WCF davranır tutarlı bir şekilde her ikisi içinde ve dışında IIS) ve aktarım arasında (bir hizmet barındırılan IIS 7.0 ve üzeri, kullanıma sunar, tüm uç noktalar arasında tutarlı bir davranışı vardır olsa bile Bu uç bazıları HTTP dışındaki protokollerin kullanın).  
  
-   AppDomain içinde ASP.NET içeriği ancak WCF HTTP çalışma zamanı tarafından uygulanan özellikler uygulayın. ASP.NET uygulama platformu HTTP özgü özelliklerinin çoğu, ASP.NET içeriği içeren bir AppDomain içinde barındırılan WCF hizmetlerine uygulanmaz. Bu özelliklerin örnekler aşağıdakileri içerir:  
  
    -   HttpContext: <xref:System.Web.HttpContext.Current%2A> her zaman `null` bir WCF hizmeti içinde erişildiğinde. Kullanım <!--zz <xref:System.ServiceModel.OperationContext.Current.RequestContext>--> `RequestContext` yerine.  
  
    -   Dosya tabanlı bir yetkilendirme: WCF güvenlik modeli, bir hizmet isteğine yetki verilip verilmediğini karar verirken hizmet .svc dosyaya uygulanan Erişim Denetim listesi için (ACL) izin vermez.  
  
    -   URL yetkilendirmesi: yapılandırma temelli benzer şekilde, WCF güvenlik modeli System.Web içinde ait belirtilen herhangi bir URL tabanlı yetkilendirme kuralını için uymaz \<yetkilendirme > yapılandırma öğesi. Bir hizmet ASP tarafından güvenli hale getirilmiş bir URL alanında bulunuyorsa bu ayarlar için WCF istekleri göz ardı edilir. NET'in URL yetkilendirme kuralları.  
  
    -   HTTP genişletilebilirlik: WCF barındırma altyapı karşılar WCF ne zaman istekleri <xref:System.Web.HttpApplication.PostAuthenticateRequest> olay tetiklenir ve işleme ASP.NET HTTP ardışık düzene döndürmüyor. Ardışık Düzen sonraki aşamalarında isteklerin kesilmesi için kodlanmış modülleri WCF isteklerin kesilmesi değil.  
  
    -   ASP.NET kimliğe bürünme: kimlik, IIS'nin işlediği gibi ASP.NET kimliğe bürünme System.Web'ın kullanarak etkinleştirmek için ayarlanmış olsa bile, varsayılan olarak, WCF çalıştığı her zaman ister. \<kimliğine bürünemediğinden = "true" / > yapılandırma seçeneği.  
  
 Bu kısıtlamalar yalnızca IIS uygulamada barındırılan WCF hizmetleri için geçerlidir. ASP.NET içeriği davranışını WCF varlığını tarafından etkilenmez.  
  
 Geleneksel olarak HTTP ardışık düzen tarafından sağlanan işlevselliği gerektiren WCF uygulamalar, ana bilgisayar olan ve bağımsız aktarım WCF eşdeğerleri kullanmayı düşünmeniz gerekir:  
  
-   <xref:System.ServiceModel.OperationContext> yerine <xref:System.Web.HttpContext>.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ASP yerine. NET'in dosya/URL yetkilendirmesi.  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> veya HTTP modülleri yerine özel katmanlı kanalları.  
  
-   Kimliğe bürünme WCF System.Web kimliğe bürünme yerine kullanılarak her bir işlemin.  
  
 Alternatif olarak, hizmetlerinizi WCF'ın ASP.NET uyumluluk modunda çalışan düşünebilirsiniz.  
  
## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>WCF hizmetleri ASP.NET uyumluluk modunda barındırma  
 WCF modeli barındırma ortamları ve aktarımlar arasında tutarlı olarak davranacak şekilde tasarlanmış olsa da, da genellikle, bir uygulama bu oranda esneklik gerektirmez senaryo vardır. WCF'ın ASP.NET uyumluluk modu ana bilgisayar IIS dışında veya HTTP dışındaki protokoller üzerinden iletişim kurmak için yeteneği gerektirmez, ancak, tüm ASP.NET Web uygulaması platformu özelliklerini kullanan senaryolar için uygundur.  
  
 Burada WCF barındırma altyapı WCF iletileri durdurur ve HTTP ardışık düzen dışı yönlendirir, varsayılan yan yana yapılandırma farklı olarak, ASP.NET uyumluluk modunda çalışan WCF hizmetleri tam olarak ASP.NET HTTP isteği çevriminin katılın. Uyumluluk modunda WCF hizmetleri HTTP ardışık düzen üzerinden kullanan bir <xref:System.Web.IHttpHandler> uygulaması, ASPX sayfaları ve ASMX Web Hizmetleri işlenme biçimini isteklerine benzer. Sonuç olarak, WCF göre aşağıdaki ASP.NET özellikleri için ASMX aynı şekilde davranır:  
  
-   <xref:System.Web.HttpContext>: ASP.NET uyumluluk modunda çalışan WCF hizmetleri erişebilir <xref:System.Web.HttpContext.Current%2A> ve ilişkili durumu.  
  
-   Dosya tabanlı bir yetkilendirme: WCF hizmetleri ASP.NET uyumluluk modunda çalışan olabilir güvenli dosya sistemi erişim denetim listeleri (ACL'ler) hizmetin .svc dosyasına ekleyerek.  
  
-   Yapılandırılabilir URL yetkilendirmesi: ASP. WCF hizmetini ASP.NET uyumluluk modunda çalışırken NET'in URL yetkilendirme kuralları için WCF istekleri uygulanır.  
  
-   <xref:System.Web.HttpModuleCollection> Genişletilebilirlik: ASP.NET uyumluluk modunda çalışan için WCF hizmetleri katılmak tam olarak ASP.NET HTTP isteği çevriminin, HTTP ardışık düzeninde yapılandırılmış herhangi bir HTTP modülü WCF isteklerinde önce ve sonra hizmet başlatma çalışabilir.  
  
-   ASP.NET kimliğe bürünme: ASP.NET geçerli kimliğini kullanarak çalıştırmak WCF hizmetleri, ASP.NET kimliğe bürünme uygulama için etkinleştirilmişse, IIS işlem kimliği farklı iş parçacığı Kimliğine bürünülen. ASP.NET kimliğe bürünme ve WCF kimliğe bürünme özelliğini her ikisi de belirli bir hizmet işlemi için etkinse hizmet uygulaması sonuçta WCF elde edilen kimliğini kullanarak çalıştırır.  
  
 WCF'ın ASP.NET uyumluluk modu (uygulamanın Web.config dosyasında bulunur) aşağıdaki yapılandırma ile uygulama düzeyinde etkinleştirilir:  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 Bu değer varsayılan olarak "`true`" belirtilmezse. Bu değeri ayarlamak "`false`" uygulamasında çalışan tüm WCF hizmetleri ASP.NET uyumluluk modunda çalışmaz gösterir.  
  
 ASP.NET uyumluluğu modunu temelde WCF varsayılandan farklı istek işleme semantiği gösterdiğinden, hangi ASP.NET için bir uygulama içinde çalıştırdıkları olsun bireysel hizmet uygulamaları denetleme olanağı vardır Uyumluluk modu etkinleştirildi. Hizmetleri kullanma <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.NET uyumluluk modu desteği olup olmadığını belirtmek için. Bu öznitelik için varsayılan değer <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.  
  
 `[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]`  
  
 `public class CalculatorService : ICalculatorSession`  
  
 `{//Implement calculator service methods.}`  
  
 Aşağıdaki tabloda, uygulama genelinde uyumluluk modu ayarı tek tek hizmetin ile destek düzeyi belirtilen etkileşim nasıl gösterilmektedir:  
  
|Uygulama çapında uyumluluk modu ayarı|[AspNetCompatibilityRequirementsMode]<br /><br /> Ayar|Gözlemlenen sonucu|  
|--------------------------------------------------|---------------------------------------------------------|---------------------|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Hizmeti başarılı bir şekilde etkinleştirir.|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Hizmeti başarılı bir şekilde etkinleştirir.|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Hizmet bir ileti alındığında bir etkinleştirme hatası oluşur.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Hizmet bir ileti alındığında bir etkinleştirme hatası oluşur.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Hizmeti başarılı bir şekilde etkinleştirir.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Hizmeti başarılı bir şekilde etkinleştirir.|  
  
> [!NOTE]
>  IIS 7.0 ve WAS WCF hizmetleri HTTP dışındaki protokoller üzerinden iletişim kurmasına izin verir. Ancak, ASP.NET uyumluluk modu etkin uygulamalarda çalışan WCF hizmetleri HTTP olmayan uç noktalarını kullanıma sunmak için izin verilmez. Hizmeti, ilk ileti aldığında bu tür bir yapılandırma bir etkinleştirme özel durum oluşturur.  
  
 WCF hizmetleri için ASP.NET uyumluluğu modunu etkinleştirme hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> ve [ASP.NET uyumluluğu](../../../../docs/framework/wcf/samples/aspnet-compatibility.md) örnek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)

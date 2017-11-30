---
title: WCF Hizmetleri ve ASP.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c86ab6996b85e679fc5c15d85e86d25eaa8b1844
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-services-and-aspnet"></a>WCF Hizmetleri ve ASP.NET
Bu konuda ele alınmıştır barındırma [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yana birimi ASP.NET ve ASP.NET uyumluluk modunda barındırma hizmetleri.  
  
## <a name="hosting-wcf-side-by-side-with-aspnet"></a>WCF yan yana ASP.NET ile barındırma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Internet Information Services (IIS) barındırılan hizmetleri ile bulunabilir. ASPX sayfaları ve ASMX Web Hizmetleri içinde bir tek, ortak uygulama etki alanı. ASP.NET, AppDomain yönetimi ve her ikisi için de dinamik derleme gibi ortak altyapı hizmetleri sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve ASP.NET HTTP çalışma zamanı. İçin varsayılan yapılandırmayı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yan yana olan ASP.NET ile.  
  
 ![WCF hizmetleri ve ASP .NET: durumu paylaşımı](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 ASP.NET HTTP çalışma zamanı ASP.NET isteklerini işler ancak için hedeflenen istekleri işleme katılmayan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri rağmen ASP.NET içerik olduğundan bu hizmetler aynı AppDomain içinde barındırılır. Bunun yerine, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet modeli karşılar gönderilen iletileri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri ve bunları aracılığıyla yönlendiren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aktarım/kanal yığını.  
  
 Yan yana modeli sonuçlarını aşağıdaki gibidir:  
  
-   ASP.NET ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri AppDomain durumu paylaşabilir. İki çerçeveleri aynı AppDomain içinde bulunabilir olduğundan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AppDomain durumu (statik değişkenler, olaylar vb. dahil) ASP.NET ile de paylaşabilir.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Hizmetleri sürekli bağımsız barındırma ortamı ve taşıma olarak davranır. ASP.NET HTTP çalışma zamanı barındırma ortamı ve HTTP iletişimi IIS/ASP.NET bilerek birleştirilmiştir. Buna karşılık, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] barındırma ortamları arasında tutarlı olarak davranmak için tasarlanmıştır ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] her ikisi de sürekli olarak davranır içinde ve dışında IIS) ve (bir hizmet barındırılan IIS 7.0 ve üzeri olan tutarlı davranış tüm arasında taşıma Bu uç bazıları HTTP dışındaki protokollerin kullansanız bile uç noktaları, gösterir).  
  
-   AppDomain içinde HTTP çalışma zamanı tarafından uygulanan özellikleri ASP.NET içeriğe değil uygulamamayı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. ASP.NET uygulama platformu HTTP özgü özelliklerinin çoğu için geçerli değildir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET içeriği içeren bir AppDomain içinde barındırılan hizmetler. Bu özelliklerin örnekler aşağıdakileri içerir:  
  
    -   HttpContext: <xref:System.Web.HttpContext.Current%2A> her zaman `null` içinden erişildiğinde bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet. Kullanım <!--zz <xref:System.ServiceModel.OperationContext.Current.RequestContext>--> `RequestContext` yerine.  
  
    -   Dosya tabanlı bir yetkilendirme: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik modeli, bir hizmet isteğine yetki verilip verilmediğini karar verirken hizmet .svc dosyaya uygulanan Erişim Denetim listesi için (ACL) izin vermez.  
  
    -   URL yetkilendirmesi: yapılandırma temelli benzer şekilde, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik modeli System.Web içinde ait belirtilen herhangi bir URL tabanlı yetkilendirme kuralını için uygun değil \<yetkilendirme > yapılandırma öğesi. Bu ayarlar için göz ardı edilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir ASP tarafından güvenli hale getirilmiş bir URL alanında bulunduğunu, ister. NET'in URL yetkilendirme kuralları.  
  
    -   HTTP genişletilebilirlik: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı durdurur barındırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne zaman istekleri <xref:System.Web.HttpApplication.PostAuthenticateRequest> olay tetiklenir ve işleme ASP.NET HTTP ardışık düzene döndürmüyor. Ardışık Düzen sonraki aşamalarında isteklerin kesilmesi için kodlanmış modülleri değil müdahale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istekleri.  
  
    -   ASP.NET kimliğe bürünme: varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kimlik, IIS'nin işlediği gibi ASP.NET kimliğe bürünme System.Web'ın kullanarak etkinleştirmek için ayarlanmış olsa bile, her zaman çalışır istediğinde \<kimliğine bürünemediğinden = "true" / > yapılandırma seçeneği.  
  
 Bu kısıtlamalar yalnızca [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS uygulamada barındırılan hizmetleri. ASP.NET içeriği davranışını varlığını tarafından etkilenmez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Geleneksel olarak HTTP ardışık düzen tarafından sağlanan işlevselliği gerektiren uygulamalar kullanarak düşünmelisiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konak olan ve bağımsız aktarım eşdeğerleri:  
  
-   <xref:System.ServiceModel.OperationContext>yerine <xref:System.Web.HttpContext>.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>ASP yerine. NET'in dosya/URL yetkilendirmesi.  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector>veya HTTP modülleri yerine özel katmanlı kanalları.  
  
-   Her işlem kullanmak için kimliğe bürünme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System.Web kimliğe bürünme yerine.  
  
 Alternatif olarak, hizmetlerinizi çalışır durumda düşünebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s ASP.NET uyumluluk modunda.  
  
## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>WCF hizmetleri ASP.NET uyumluluk modunda barındırma  
 Ancak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modeli barındırma ortamları ve aktarımlar arasında tutarlı olarak davranacak şekilde tasarlanmıştır, çoğunlukla olduğu bir uygulama gerektirmez bu oranda esneklik senaryolar vardır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ın ASP.NET uyumluluk modu özelliği IIS dışında barındırmak için veya HTTP dışındaki protokoller üzerinden iletişim kurmak için gerekli olmadığı, ancak tüm ASP.NET Web uygulaması platformu özelliklerini kullanan senaryolar için uygun.  
  
 Varsayılan yan yana yapılandırmanın aksine nerede [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı durdurur barındırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletileri ve HTTP ardışık düzen dışı yönlendiren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET uyumluluk modunda çalışan hizmetler katılmak tam olarak ASP.NET HTTP isteği ömrü. Uyumluluk modunda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmetlerini kullanmak HTTP kanalı yoluyla bir <xref:System.Web.IHttpHandler> uygulaması, ASPX sayfaları ve ASMX Web Hizmetleri işlenme biçimini isteklerine benzer. Sonuç olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] için ASMX göre aşağıdaki ASP.NET özellikleri aynı şekilde davranır:  
  
-   <xref:System.Web.HttpContext>: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET uyumluluk modunda çalışan hizmetler erişebilir <xref:System.Web.HttpContext.Current%2A> ve ilişkili durumu.  
  
-   Dosya tabanlı bir yetkilendirme: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET uyumluluk modunda çalışan hizmetler güvenli dosya sistemi erişim denetim listeleri (ACL'ler) hizmetin .svc dosyasına ekleyerek.  
  
-   Yapılandırılabilir URL yetkilendirmesi: ASP. NET'in URL yetkilendirme kuralları için zorlanmaz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne zaman istekleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet, ASP.NET uyumluluk modunda çalışıyor.  
  
-   <xref:System.Web.HttpModuleCollection>Genişletilebilirlik: çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET uyumluluk modunda çalışan hizmetler katılmak tam olarak ASP.NET HTTP isteği çevriminin, HTTP ardışık düzeninde yapılandırılmış herhangi bir HTTP modülü üzerinde çalışacağı olanağına sahip [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] öncesinde ve sonrasında istekleri Hizmet başlatma.  
  
-   ASP.NET kimliğe bürünme: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET geçerli kimliğini kullanarak çalışan hizmetleri, ASP.NET kimliğe bürünme uygulama için etkinleştirilmişse, IIS işlem kimliği farklı iş parçacığı Kimliğine bürünülen. ASP.NET kimliğe bürünme ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kimliğe bürünme hem de etkin belirli bir hizmet işlemi için hizmet uygulaması, sonuçta elde kimliğini kullanarak çalıştırılır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ın (uygulamanın Web.config dosyasında bulunur) aşağıdaki yapılandırma ile uygulama düzeyinde ASP.NET uyumluluk modu etkin:  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 Bu değer varsayılan olarak "`true`" belirtilmezse. Bu değeri ayarlamak "`false`" bildiren tüm [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamada çalışan hizmetler, ASP.NET uyumluluk modunda çalışmaz.  
  
 ASP.NET uyumluluğu modunu temelde farklı olduğundan istek işleme semantiği gösterdiğinden [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] varsayılan, bireysel hizmet uygulamaları sahip bir uygulama içinde hangi ASP çalıştırdıkları olup olmadığını denetleme olanağı. NET uyumluluk modu etkinleştirildi. Hizmetleri kullanma <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.NET uyumluluk modu desteği olup olmadığını belirtmek için. Bu öznitelik için varsayılan değer <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.  
  
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
>  IIS 7.0 ve WAS izin veren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP dışındaki protokoller üzerinden iletişim kurmak için hizmetleri. Ancak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET uyumluluk modu etkin uygulamalarda çalışan hizmetler, HTTP olmayan uç noktalarını kullanıma sunar izin verilmez. Hizmeti, ilk ileti aldığında bu tür bir yapılandırma bir etkinleştirme özel durum oluşturur.  
  
 ASP.NET uyumluluğu modunu etkinleştirme hakkında daha fazla bilgi için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri, bkz: <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> ve [ASP.NET uyumluluğu](../../../../docs/framework/wcf/samples/aspnet-compatibility.md) örnek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)

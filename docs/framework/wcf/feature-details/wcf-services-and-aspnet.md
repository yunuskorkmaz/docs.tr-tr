---
title: WCF hizmetleri ve ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: ef772a360ea53c2b5f177ed88ad14c4a1e1277ef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637542"
---
# <a name="wcf-services-and-aspnet"></a>WCF hizmetleri ve ASP.NET

Bu konuda, barındırma Windows Communication Foundation (WCF) Hizmetleri yan yana ASP.NET ve ASP.NET uyumluluk modunda bunları barındırma anlatılmaktadır.

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>WCF yan yana ASP.NET ile barındırma

Internet Information Services (IIS) barındırılan WCF hizmetleri ile yer alabilir. ASPX sayfaları ve tek, ortak bir uygulama etki içinde ASMX Web Hizmetleri. ASP.NET uygulama etki alanı yönetimi ve hem WCF ve ASP.NET HTTP çalışma zamanı için dinamik derleme gibi genel altyapı hizmetleri sağlar. WCF için varsayılan yapılandırma yan yana ASP.NET ile.

![WCF hizmetleri ve ASP .NET gösteren ekran görüntüsü: durum paylaşımı.](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

ASP.NET HTTP çalışma zamanı ASP.NET istek işleme ancak rağmen ASP.NET içerik olduğu gibi bu hizmetler aynı AppDomain içinde barındırılan WCF hizmetleri için hedefleyen isteklerin işlenmesini içinde yer almaz. Bunun yerine, WCF hizmet modeli, WCF hizmetlerine gönderilen iletiler gelmeyecek durdurur ve bunları WCF aktarma kanala yığınından yönlendirir.

Yan yana modeli sonuçları aşağıdaki gibidir:

- ASP.NET ve WCF hizmetlerini AppDomain durumu paylaşabilirsiniz. İki çerçeveleri aynı AppDomain içinde olabildiğinden WCF (statik değişkenler, olayları vb. dahil) ile ASP.NET AppDomain durumu da paylaşabilirsiniz.

- WCF hizmetleri tutarlı olarak bağımsız barındırma ortamı ve aktarım olarak davranır. ASP.NET HTTP çalışma zamanı barındırma ortamı ve HTTP iletişimi IIS/ASP.NET kasıtlı olarak birleştirilmiştir. Buna karşılık, WCF barındırma ortamları arasında tutarlı olarak davranacak şekilde tasarlanmıştır (WCF davranışını tutarlı bir şekilde hem içindeki ve dışındaki IIS) ve aktarım arasında (barındırılan IIS 7.0 ve üzeri bir hizmet kullanıma sunduğu, tüm uç noktalar genelinde tutarlı bir davranış sahip olsa bile Bu uç noktalara bazıları HTTP dışındaki protokollerin kullanın).

- Bir AppDomain içinde ASP.NET içeriği, ancak WCF HTTP çalışma zamanı tarafından uygulanan özellikleri geçerlidir. HTTP özel ASP.NET uygulama platformu özelliklerinin çoğu, ASP.NET içeriği içeren bir AppDomain içinde barındırılan WCF hizmetlerine uygulanmaz. Bu özelliklerin örnekler aşağıdakileri içerir:

    - HttpContext: <xref:System.Web.HttpContext.Current%2A> her zaman `null` bir WCF hizmetinde erişildiğinde. Bunun yerine <xref:System.ServiceModel.Channels.RequestContext> kullanın.

    - Dosya tabanlı yetkilendirme: WCF güvenlik modeli, bir hizmet isteğinin yetkilendirilip yetkilendirilmediğini verirken hizmet .svc dosyaya uygulanan erişim için Denetim listesi (ACL) izin vermez.

    - Yapılandırma temelli URL yetkilendirmesi: Benzer şekilde, WCF güvenlik modeli System.Web kullanıcının belirtilen tüm URL tabanlı yetkilendirme kuralları kalmıyor \<yetkilendirme > yapılandırma öğesi. Bir hizmet tarafından ASP güvenli bir URL alanında bulunuyorsa WCF istekleri için bu ayarları göz ardı edilir. NET URL yetkilendirme kuralları.

    - HttpModule genişletilebilirlik: WCF barındırma altyapısını WCF karşılar ne zaman istekleri <xref:System.Web.HttpApplication.PostAuthenticateRequest> olay tetiklenir ve ASP.NET HTTP işlem hattına işleme döndürmez. İşlem hattının sonraki aşamalarda isteklerin kesilmesi için kodlanmış modülleri WCF istekleri kesmenize değil.

    - ASP.NET kimliğe bürünme: Kimlik, IIS'nin işlediği gibi ASP.NET kimliğe bürünme System.Web'ın kullanarak etkinleştirmek için ayarlanmış olsa bile varsayılan olarak, WCF çalışmaları her zaman ister. \<Kimliğe bürün = "true" / > yapılandırma seçeneği.

Bu kısıtlama, uygulama IIS barındırılan WCF hizmetleri için uygulanır. ASP.NET içeriği davranışını varlığını WCF tarafından etkilenmez.

Geleneksel olarak HTTP ardışık düzen tarafından sağlanan işlevselliği gerektiren WCF uygulamalar, konak ve bağımsız aktarım WCF eşdeğerleri kullanmayı düşünmelisiniz:

- <xref:System.ServiceModel.OperationContext> yerine <xref:System.Web.HttpContext>.

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ASP yerine. NET dosya/URL yetkilendirme.

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> veya özel kanallar HTTP modülleri yerine katmanlı.

- System.Web kimliğe bürünme yerine WCF kullanarak her bir işlem için kimliğe bürünme.

Alternatif olarak, hizmetlerinizi WCF'ın ASP.NET uyumluluk modunda çalışan düşünebilirsiniz.

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>ASP.NET uyumluluk modunda WCF hizmetlerini barındırma

WCF modeli barındırma ortamları ve taşımalar arasında tutarlı olarak davranacak şekilde tasarlanmış olsa da genellikle burada bir uygulama bu ölçüde esneklik gerektirmeyen senaryolar vardır. WCF'ın ASP.NET uyumluluk modunun konak IIS dışında veya HTTP dışındaki protokoller üzerinden iletişim kurmak için yeteneği gerektirmez, ancak tüm ASP.NET Web uygulaması platformu özelliklerini kullanan senaryolar için uygundur.

Burada WCF barındırma altyapısını, WCF iletileri durdurur ve bunları HTTP ardışık düzen dışında yönlendirir, varsayılan yan yana yapılandırmada ASP.NET uyumluluk modunda çalışan WCF hizmetleri HTTP ASP.NET isteği yaşam döngüsünde tam olarak katılın. Uyumluluk modunda, WCF hizmetleri HTTP ardışık düzen üzerinden kullanın. bir <xref:System.Web.IHttpHandler> uygulama, ASPX sayfaları ve ASMX Web Hizmetleri işlenme biçimini isteklerine benzer. Sonuç olarak, WCF ile ilgili aşağıdaki ASP.NET özellikleri için ASMX aynı şekilde davranır:

- <xref:System.Web.HttpContext>: ASP.NET uyumluluk modunda çalışan WCF hizmetleri erişim <xref:System.Web.HttpContext.Current%2A> ve ilişkili durumu.

- Dosya tabanlı yetkilendirme: WCF hizmetleri ASP.NET uyumluluk modunda çalışan dosya sistemi erişim denetim listeleri (ACL) hizmetin .svc dosyasına ekleyerek güvenli olabilir.

- URL yetkilendirmesi yapılandırılabilir: ASP. WCF hizmetini ASP.NET uyumluluk modunda çalışırken NET'in URL yetkilendirme kuralları için WCF istekleri uygulanır.

- <xref:System.Web.HttpModuleCollection> Genişletilebilirlik: ASP.NET uyumluluk modunda çalışan WCF hizmetleri HTTP ASP.NET isteği yaşam döngüsünde tam olarak katılmak için HTTP işlem hattı, yapılandırılmış herhangi bir HTTP modülü WCF isteklerinde önce ve sonra hizmet başlatma çalışabilir.

- ASP.NET kimliğe bürünme: WCF hizmetleri ASP.NET geçerli kimliğini kullanarak çalışan ASP.NET kimliğe bürünme uygulama için etkinleştirilmişse, IIS işlem kimliği farklı olabilecek iş parçacığı, hesabın kimliğine büründü. ASP.NET kimliğe bürünme ve WCF kimliğe bürünme hem de bir hizmet işlemi için etkinleştirilip etkinleştirilmediğini hizmet uygulaması WCF alınan kimlik kullanarak nihai olarak çalışır.

WCF'ın ASP.NET uyumluluk modunun (uygulamanın Web.config dosyasında bulunur) aşağıdaki yapılandırma yoluyla uygulama düzeyinde etkinleştirilir:

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

Bu değeri varsayılan olarak "`true`" belirtilmezse. Bu değeri ayarlamak "`false`" uygulama içinde çalışan tüm WCF hizmetleri ASP.NET uyumluluk modunda çalışmayacaktır gösterir.

ASP.NET uyumluluk modunun tamamen WCF varsayılandan farklı istek işleme semantikler gösterdiğinden, hangi ASP.NET için bir uygulama içinde çalıştıkları olup olmadığını bireysel hizmet uygulamaları denetleme olanağı vardır Uyumluluk modu etkinleştirildi. Hizmetleri kullanma <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.NET uyumluluk modunun destek belirtmek için. Bu öznitelik için varsayılan değer <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

Aşağıdaki tabloda, uygulama genelinde uyumluluk modu ayarının bireysel hizmet ile destek düzeyini belirtilen etkileşim nasıl gösterilmektedir:

|Birçok farklı uygulama uyumluluk modu ayarı|[AspNetCompatibilityRequirementsMode]<br /><br /> Ayar|Gözlemlenen sonucu|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Hizmet başarıyla etkinleştirir.|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Hizmet başarıyla etkinleştirir.|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Hizmetin bir ileti aldığında, bir etkinleştirme hatası oluşur.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Hizmetin bir ileti aldığında, bir etkinleştirme hatası oluşur.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Hizmet başarıyla etkinleştirir.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Hizmet başarıyla etkinleştirir.|

> [!NOTE]
> IIS 7.0 ve WAS'ta WCF hizmetleri HTTP dışındaki protokoller üzerinden iletişim kurmasına izin verir. Ancak, ASP.NET uyumluluk modunun etkin uygulamalarda çalışan WCF hizmetleri HTTP olmayan uç noktalarını kullanıma sunmak için izin verilmez. Hizmeti, ilk ileti aldığında, bu tür bir yapılandırma etkinleştirme özel durum oluşturur.

WCF hizmetleri için ASP.NET uyumluluk modunun etkinleştirme hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> ve [ASP.NET Uyumluluk](../samples/aspnet-compatibility.md) örnek.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))

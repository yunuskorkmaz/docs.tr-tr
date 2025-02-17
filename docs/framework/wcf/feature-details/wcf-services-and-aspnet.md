---
title: WCF Hizmetleri ve ASP.NET
description: WCF hizmetlerini ASP.NET ile yan yana barındırma ve ASP.NET uyumluluk modunda barındırma hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 765a509f94a0a934cdbbf0212cfc1d4053d29f9c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553323"
---
# <a name="wcf-services-and-aspnet"></a>WCF Hizmetleri ve ASP.NET

Bu konuda, ASP.NET ile yan yana Windows Communication Foundation (WCF) hizmetlerinin barındırılması ve ASP.NET uyumluluk modunda barındırılması ele alınmaktadır.

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>ASP.NET ile WCF yan yana barındırma

Internet Information Services (IIS) içinde barındırılan WCF Hizmetleri ile bulunabilir. Tek, ortak bir uygulama etki alanının içindeki ASPX sayfaları ve ASMX Web Hizmetleri. ASP.NET, hem WCF hem de ASP.NET HTTP çalışma zamanı için AppDomain yönetimi ve dinamik derleme gibi ortak altyapı hizmetleri sağlar. WCF için varsayılan yapılandırma, ASP.NET ile yan yana olur.

![WCF hizmetlerini gösteren ekran görüntüsü ve ASP .NET: paylaşım durumu.](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

ASP.NET HTTP Runtime, ASP.NET isteklerini işler, ancak bu hizmetler ASP.NET içeriğiyle aynı AppDomain 'de barındırıldığında bile, WCF Hizmetleri için hedeflenen isteklerin işlenmesine katılmaz. Bunun yerine, WCF hizmeti modeli WCF hizmetlerine yönelik iletileri keser ve bunları WCF taşıma/kanal yığını aracılığıyla yönlendirir.

Yan yana modelin sonuçları aşağıdaki gibidir:

- ASP.NET ve WCF Hizmetleri AppDomain durumunu paylaşabilir. İki çerçeve aynı AppDomain içinde bulunabilir, çünkü WCF Ayrıca AppDomain durumunu ASP.NET ile paylaşabilir (statik değişkenler, olaylar vb. dahil).

- WCF Hizmetleri, barındırma ortamından ve aktarımından bağımsız olarak tutarlı bir şekilde davranır. ASP.NET HTTP çalışma zamanı, IIS/ASP. NET barındırma ortamına ve HTTP iletişimine kasıtlı olarak bağlanmış. Buna karşılık, WCF, barındırma ortamlarında tutarlı bir şekilde davranması için tasarlanmıştır (WCF hem IIS 'nin içinde hem de dışında bir şekilde davranır) ve taşıma (IIS 7,0 ' de barındırılan bir hizmet ve daha yeni bir deyişle, bu uç noktaların HTTP dışındaki protokolleri kullanıyor olsa bile)

- Bir AppDomain içinde, HTTP çalışma zamanı tarafından uygulanan özellikler ASP.NET içerik için geçerlidir ancak WCF 'ye uygulanmaz. ASP.NET uygulama platformunun HTTP 'e özgü birçok özelliği, ASP.NET içeriği içeren bir AppDomain içinde barındırılan WCF Hizmetleri için uygulanmaz. Bu özelliklere örnek olarak şunlar verilebilir:

  - HttpContext: <xref:System.Web.HttpContext.Current%2A> her zaman `null` bir WCF hizmeti içinden erişildiği zaman. Bunun yerine <xref:System.ServiceModel.Channels.RequestContext> kullanın.

  - Dosya tabanlı yetkilendirme: WCF güvenlik modeli, bir hizmet isteğinin yetkilendirilip yetkilendirilmeyeceğine karar verirken hizmetin. svc dosyasına uygulanan erişim denetim listesi 'ne (ACL) izin vermez.

  - Yapılandırma tabanlı URL yetkilendirmesi: benzer şekilde, WCF güvenlik modeli System. Web 'in yapılandırma öğesinde belirtilen herhangi bir URL tabanlı yetkilendirme kuralına bağlı değildir \<authorization> . Bu ayarlar, bir hizmetin ASP tarafından güvenliği sağlanmış bir URL alanında yer alıyorsa WCF istekleri için yoksayılır. NET 'in URL Yetkilendirme kuralları.

  - HttpModule genişletilebilirliği: WCF barındırma altyapısı, olay harekete çıktığında WCF isteklerini karşılar <xref:System.Web.HttpApplication.PostAuthenticateRequest> ve ASP.NET HTTP işlem hattına işlem döndürmez. İşlem hattının sonraki aşamalarında istekleri ele almak için kodlanmış modüller WCF isteklerini ele vermez.

  - ASP.NET Kimliğe bürünme: varsayılan olarak, ASP.NET System. Web 'in yapılandırma seçeneği kullanılarak kimliğe bürünme özelliğini etkinleştirmek üzere ayarlanmış olsa bile, WCF istekleri her zaman IIS işlem kimliği olarak çalışır \<identity impersonate="true" /> .

Bu kısıtlamalar yalnızca IIS uygulamasında barındırılan WCF Hizmetleri için geçerlidir. ASP.NET içeriğinin davranışı WCF 'nin varlığından etkilenmez.

HTTP işlem hattı tarafından geleneksel işlevselliği gerektiren WCF uygulamaları, ana bilgisayar ve aktarımdan bağımsız olan WCF eşdeğerlerini kullanmayı göz önünde bulundurmalıdır:

- <xref:System.ServiceModel.OperationContext> yerine <xref:System.Web.HttpContext> .

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> yerine ASP. NET 'in dosya/URL yetkilendirmesi.

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> veya HTTP modülleri yerine özel katmanlı kanallar.

- System. Web kimliğe bürünme yerine WCF kullanarak her işlem için kimliğe bürünme.

Alternatif olarak, hizmetlerinizi WCF 'nin ASP.NET uyumluluk modunda çalıştırmayı düşünebilirsiniz.

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>WCF hizmetlerini ASP.NET uyumluluk modunda barındırma

WCF modeli, barındırma ortamları ve aktarımları arasında tutarlı bir şekilde davranması için tasarlansa da, genellikle bir uygulamanın bu düzeyde esneklik gerektirmemesine neden olan senaryolar vardır. WCF 'nin ASP.NET uyumluluk modu, IIS dışında bir şekilde barındırmanıza veya HTTP dışındaki protokoller üzerinden iletişim kurmaya gerek olmayan, ancak ASP.NET Web uygulaması platformunun tüm özelliklerini kullanan senaryolar için uygundur.

WCF barındırma altyapısının WCF iletilerini aldığı ve HTTP ardışık düzeninde yönlendirdiğini varsayılan yan yana yapılandırmanın aksine, ASP.NET uyumluluk modunda çalışan WCF Hizmetleri, ASP.NET HTTP istek yaşam döngüsüne tam olarak katılır. Uyumluluk modunda, WCF Hizmetleri, <xref:System.Web.IHttpHandler> aspx sayfaları ve asmx Web hizmetleri isteklerinin işlenme yöntemine benzer şekilde bir uygulama aracılığıyla HTTP işlem hattını kullanır. Sonuç olarak, WCF aşağıdaki ASP.NET özelliklerine göre de ASMX ile aynı şekilde davranır:

- <xref:System.Web.HttpContext>: ASP.NET uyumluluk modunda çalışan WCF Hizmetleri, <xref:System.Web.HttpContext.Current%2A> ve ilişkili durumuna erişebilir.

- Dosya tabanlı yetkilendirme: ASP.NET uyumluluk modunda çalışan WCF Hizmetleri, hizmet. svc dosyasına dosya sistemi erişim denetim listeleri (ACL 'Ler) eklenerek güvenli olabilir.

- Yapılandırılabilir URL yetkilendirmesi: ASP. WCF hizmeti ASP.NET uyumluluk modunda çalışırken, ağ URL 'SI yetkilendirme kuralları WCF istekleri için zorlanır.

- <xref:System.Web.HttpModuleCollection> genişletilebilirlik: ASP.NET uyumluluk modunda çalışan WCF Hizmetleri, ASP.NET HTTP istek yaşam döngüsüne tam olarak katıldığından, HTTP işlem hattında yapılandırılan HTTP modülleri, hizmet çağrısından önce ve sonra hem WCF istekleri üzerinde işleyebilir.

- ASP.NET Kimliğe bürünme: WCF Hizmetleri, uygulama için ASP.NET Kimliğe bürünme etkinleştirilmişse, IIS işlem kimliğinden farklı olabilecek ASP.NET Kimliğine bürünülen iş parçacığının geçerli kimliğini kullanarak çalışır. ASP.NET Kimliğe bürünme ve WCF kimliğe bürünme her ikisi de belirli bir hizmet işlemi için etkinleştirildiyse, hizmet uygulamasının sonunda WCF 'den elde edilen kimlik kullanılarak çalışır.

WCF 'nin ASP.NET uyumluluk modu, uygulama düzeyinde aşağıdaki yapılandırma (uygulamanın Web.config dosyasında bulunur) aracılığıyla etkinleştirilir:

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

Bu değer belirtilmemişse varsayılan değerdir `false` . Değeri, `false` uygulamada çalışan tüm WCF hizmetlerinin ASP.NET uyumluluk modunda çalıştırılmayacağını gösterir.

ASP.NET uyumluluk modu, WCF varsayılanlarından temelde farklı olan istek işleme semantiğini gösterdiği için, tek tek hizmet uygulamaları, ASP.NET uyumluluk modunun etkinleştirildiği bir uygulamanın içinde çalıştırılıp çalıştırılmadığını denetleyebilir. Hizmetler, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.NET uyumluluk modunu destekleyip desteklemediğini göstermek için öğesini kullanabilir. <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>, bu öznitelik için varsayılan değerdir.

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

Aşağıdaki tabloda, uygulama genelinde uyumluluk modu ayarının, tek tek hizmetin belirtilen destek düzeyiyle nasıl etkileşimde bulunduğu gösterilmektedir:

|Uygulama genelinde uyumluluk modu ayarı|[AspNetCompatibilityRequirementsMode]<br /><br /> Ayar|Gözlemlenen sonuç|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Hizmet başarıyla etkinleştirilir.|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Hizmet başarıyla etkinleştirilir.|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Hizmet bir ileti aldığında bir etkinleştirme hatası oluşur.|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Hizmet bir ileti aldığında bir etkinleştirme hatası oluşur.|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Hizmet başarıyla etkinleştirilir.|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Hizmet başarıyla etkinleştirilir.|

> [!NOTE]
> IIS 7,0 ve, WCF hizmetlerinin HTTP dışındaki protokoller üzerinden iletişim kurmasına izin verir. Ancak, ASP.NET uyumluluk modu etkinleştirilmiş uygulamalarda çalışan WCF Hizmetleri, HTTP olmayan uç noktaları kullanıma sunmasına izin verilmez. Bu tür bir yapılandırma, hizmet ilk iletisini aldığında bir etkinleştirme özel durumu oluşturur.

WCF Hizmetleri için ASP.NET uyumluluk modunu etkinleştirme hakkında daha fazla bilgi için, bkz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> . ve [ASP.NET uyumluluk](../samples/aspnet-compatibility.md) örneği.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))

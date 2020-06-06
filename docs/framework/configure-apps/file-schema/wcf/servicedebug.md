---
title: <serviceDebug>
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 4eb79cc91ef489501c4c8bb6311f240d855ed053
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399628"
---
# \<serviceDebug>
Bir Windows Communication Foundation (WCF) hizmeti için hata ayıklama ve yardım bilgileri özelliklerini belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDebug>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceDebug httpHelpPageBinding="String"
              httpHelpPageBindingConfiguration="String"
              httpHelpPageEnabled="Boolean"
              httpHelpPageUrl="Uri"
              httpsHelpPageBinding="String"
              httpsHelpPageBindingConfiguration="String"
              httpsHelpPageEnabled="Boolean"
              httpsHelpPageUrl="Uri"
              includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|httpHelpPageBinding|Hizmet yardım sayfasına erişmek için HTTP kullanılırken kullanılacak bağlama türünü belirten bir dize değeri.<br /><br /> Yalnızca destekleyen iç bağlama öğeleri olan bağlamalar <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> .|  
|httpHelpPageBindingConfiguration|`httpHelpPageBinding`Bu bağlamanın ek yapılandırma bilgilerine başvuran özniteliğinde belirtilen bağlama adını belirten bir dize. Bölümünde aynı ad tanımlanmalıdır `<bindings>` .|  
|httpHelpPageEnabled|WCF 'nin öznitelik tarafından belirtilen adreste bir HTML Yardım sayfası yayımlalayıp yayımlamayacağını denetleyen Boolean bir değer `httpHelpPageUrl` . Varsayılan değer: `true`.<br /><br /> HTML `false` tarayıcılarına görünür BIR HTML Yardım sayfası yayımını devre dışı bırakmak için, bu özelliği olarak ayarlayabilirsiniz.<br /><br /> HTML yardım sayfasının öznitelik tarafından denetlenen konumda yayımlanmasını sağlamak için `httpHelpPageUrl` , bu özniteliği olarak ayarlamanız gerekir `true` . Ayrıca, aşağıdaki koşullardan biri de sağlanmalıdır:<br /><br /> - `httpHelpPageUrl` Öznitelik, http protokol düzenini destekleyen mutlak bir adrestir.<br />-HTTP protokol düzenini destekleyen hizmet için bir temel adres vardır.<br /><br /> HTTP protokol düzenini desteklemeyen mutlak bir adres özniteliğe atanmamışsa bir özel durum oluşsa da `httpHelpPageUrl` , önceki ölçütlerden hiçbirinin karşılanmadığı başka hiçbir senaryo hiçbir özel durum değildir ve HTML Yardım sayfası içermez.|  
|'Nin HttpHelpPageUrl|Uç nokta bir HTML tarayıcısı kullanılarak görüntülendiğinde kullanıcının gördüğü özel HTML Yardım dosyasının göreli veya mutlak HTTP tabanlı URL 'sini belirten bir URI.<br /><br /> Bu özniteliği bir HTTP/Get isteğinden döndürülen özel bir HTML Yardım dosyasının kullanımını etkinleştirmek için kullanabilirsiniz. Örneğin, bir HTML tarayıcısı. HTML Yardım dosyasının konumu aşağıdaki şekilde çözümlenir.<br /><br /> 1. bu özniteliğin değeri göreli bir adres ise, HTML Yardım dosyasının konumu, HTTP isteklerini destekleyen hizmet temel adresinin değeridir ve bu özellik değeridir.<br />2. bu özniteliğin değeri mutlak bir adres ise ve HTTP isteklerini destekliyorsa, HTML Yardım dosyasının konumu bu özelliğin değeridir.<br />3. bu özniteliğin değeri mutlak olup HTTP isteklerini desteklemiyorsa, bir özel durum oluşturulur.<br /><br /> Bu öznitelik yalnızca özniteliği olduğunda geçerlidir `httpHelpPageEnabled` `true` .|  
|httpsHelpPageBinding|Hizmet yardım sayfasına erişmek için HTTPS kullanılırken kullanılacak bağlama türünü belirten bir dize değeri.<br /><br /> Yalnızca destekleyen iç bağlama öğeleri olan bağlamalar <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> .|  
|httpsHelpPageBindingConfiguration|`httpsHelpPageBinding`Bu bağlamanın ek yapılandırma bilgilerine başvuran özniteliğinde belirtilen bağlama adını belirten bir dize. Bölümünde aynı ad tanımlanmalıdır `<bindings>` .|  
|httpsHelpPageEnabled|WCF 'nin öznitelik tarafından belirtilen adreste bir HTML Yardım sayfası yayımlalayıp yayımlamayacağını denetleyen Boolean bir değer `httpsHelpPageUrl` . Varsayılan değer: `true`.<br /><br /> HTML `false` tarayıcılarına görünür BIR HTML Yardım sayfası yayımını devre dışı bırakmak için, bu özelliği olarak ayarlayabilirsiniz.<br /><br /> HTML yardım sayfasının öznitelik tarafından denetlenen konumda yayımlanmasını sağlamak için `httpsHelpPageUrl` , bu özniteliği olarak ayarlamanız gerekir `true` . Ayrıca, aşağıdaki koşullardan biri de sağlanmalıdır:<br /><br /> - `httpsHelpPageUrl` Öznitelik, HTTPS protokol düzenini destekleyen mutlak bir adrestir.<br />-HTTPS protokol düzenini destekleyen hizmet için bir temel adres vardır.<br /><br /> HTTPS protokol düzenini desteklemeyen mutlak bir adres özniteliğe atanmamışsa bir özel durum oluşsa da `httpsHelpPageUrl` , önceki ölçütlerden hiçbirinin karşılanmadığı başka hiçbir senaryo hiçbir özel durum değildir ve HTML Yardım sayfası içermez.|  
|'Nin HttpsHelpPageUrl|Uç nokta bir HTML tarayıcısı kullanılarak görüntülendiğinde kullanıcının gördüğü özel HTML Yardım dosyasının göreli veya mutlak HTTPS tabanlı URL 'sini belirten bir URI.<br /><br /> Bu özniteliği bir HTTPS/Get isteğinden döndürülen özel bir HTML Yardım dosyasının kullanımını etkinleştirmek için kullanabilirsiniz. Örneğin, bir HTML tarayıcısı. HTML Yardım dosyasının konumu aşağıdaki şekilde çözümlenir:<br /><br /> -Bu özelliğin değeri göreli bir adres ise, HTML Yardım dosyasının konumu, HTTPS isteklerini destekleyen hizmet temel adresinin değeridir ve bu özellik değeridir.<br />-Bu özelliğin değeri mutlak bir adres ise ve HTTPS isteklerini destekliyorsa, HTML Yardım dosyasının konumu bu özelliğin değeridir.<br />-Bu özelliğin değeri mutlak ise ancak HTTPS isteklerini desteklemiyorsa, bir özel durum oluşturulur.<br /><br /> Bu öznitelik yalnızca özniteliği olduğunda geçerlidir `httpHelpPageEnabled` `true` .|  
|IncludeExceptionDetailInFaults|Yönetilen özel durum bilgilerinin, hata ayıklama amacıyla istemciye döndürülen SOAP hatalarının ayrıntısına eklenip eklenmeyeceğini belirten bir değer. Varsayılan değer: `false`.<br /><br /> Bu özniteliği olarak ayarlarsanız `true` , hata ayıklama amacıyla istemciye yönetilen özel durum bilgileri akışını ve Web tarayıcılarında hizmete göz atan KULLANıCıLARıN HTML bilgi dosyalarının yayımlanmasını sağlayabilirsiniz. **Dikkat:**  Yönetilen özel durum bilgilerini istemcilere döndürmek bir güvenlik riski oluşturabilir. Bunun nedeni, özel durum ayrıntılarının yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulamasıyla ilgili bilgileri kullanıma sunmasıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `includeExceptionDetailInFaults`İçin ayarı `true` , özel durum kullanılarak bildirilmemiş olsa bile, hizmetin uygulama kodu tarafından oluşturulan herhangi bir özel durumu döndürmesini sağlar <xref:System.ServiceModel.FaultContractAttribute> . Bu ayar, sunucunun beklenmeyen bir özel durum oluşturan durumlarda hata ayıklaması yaparken faydalıdır. Bu özniteliği kullanarak, bilinmeyen özel durumun serileştirilmiş formu döndürülür ve özel durumun daha fazla ayrıntılarını inceleyebilirsiniz.  
  
> [!CAUTION]
> Yönetilen özel durum bilgilerini istemcilere döndürmek, özel durum ayrıntıları yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulamasıyla ilgili bilgileri kullanıma sunduğundan güvenlik riski oluşturabilir. Söz konusu güvenlik sorunları nedeniyle, yalnızca denetimli hata ayıklama senaryolarında bunu yapmanız önemle önerilir. Uygulamanızı dağıttığınızda olarak ayarlamanız gerekir `includeExceptionDetailInFaults` `false` .  
  
 Yönetilen özel durumla ilgili güvenlik sorunları hakkında daha fazla bilgi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md). Kod örneği için bkz. [hizmet hata ayıklama davranışı](../../../wcf/samples/service-debug-behavior.md).  
  
 Ayrıca `httpsHelpPageEnabled` `httpsHelpPageUrl` , yardım sayfasını etkinleştirip etkinleştirebilir veya devre dışı bırakabilirsiniz. Her hizmet, isteğe bağlı olarak hizmetle ilgili WSDL 'yi almak için uç nokta dahil olmak üzere hizmet hakkındaki bilgileri içeren bir yardım sayfası sunabilir. Bu, ayarına göre etkinleştirilebilir `httpHelpPageEnabled` `true` . Bu, yardım sayfasının, hizmetin temel adresine yönelik bir GET isteğine döndürülmesini sağlar. Özniteliği ayarlayarak bu adresi değiştirebilirsiniz `httpHelpPageUrl` . Ayrıca, HTTP yerine HTTPS kullanarak bunu güvenli hale getirebilirsiniz.  
  
 İsteğe bağlı `httpHelpPageBinding` ve `httpHelpPageBinding` öznitelikleri, hizmet Web sayfasına erişmek için kullanılan bağlamaları yapılandırmanızı sağlar. Bunlar belirtilmemişse, `HttpTransportBindingElement` hizmet yardım sayfası erişimi için uygun olan varsayılan bağlamalar (http ve söz konusu olduğunda, `HttpsTransportBindingElement` https durumunda) kullanılır. Bu öznitelikleri yerleşik WCF bağlamaları ile kullanamazsınız. Yalnızca XREF: System. ServiceModel. Channels. IReplyChannel destekleyen desteklenecektir> destekleyen iç bağlama öğelerine sahip bağlamalar desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceDebugElement>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Özel Durum ve Hataları İşleme](../../../wcf/extending/handling-exceptions-and-faults.md)
- [Hizmet Hata Ayıklama Davranışı](../../../wcf/samples/service-debug-behavior.md)

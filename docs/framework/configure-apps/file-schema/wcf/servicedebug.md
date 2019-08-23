---
title: <serviceDebug>
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: cbeb0d254bf6716296f34020ea8796885e0f368a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936263"
---
# <a name="servicedebug"></a>\<serviceDebug >
Bir Windows Communication Foundation (WCF) hizmeti için hata ayıklama ve yardım bilgileri özelliklerini belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
\<serviceDebug >  
  
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
|httpHelpPageBinding|Hizmet yardım sayfasına erişmek için HTTP kullanılırken kullanılacak bağlama türünü belirten bir dize değeri.<br /><br /> Yalnızca destekleyen <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> iç bağlama öğeleri olan bağlamalar desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpHelpPageBindingConfiguration|Bu bağlamanın ek yapılandırma bilgilerine başvuran `httpHelpPageBinding` özniteliğinde belirtilen bağlama adını belirten bir dize. `<bindings>` Bölümünde aynı ad tanımlanmalıdır.|  
|httpHelpPageEnabled|WCF 'nin `httpHelpPageUrl` öznitelik tarafından belirtilen adreste bir HTML Yardım sayfası yayımlalayıp yayımlamayacağını denetleyen Boolean bir değer. Varsayılan, `true` değeridir.<br /><br /> HTML tarayıcılarına görünür bir HTML `false` yardım sayfası yayımını devre dışı bırakmak için, bu özelliği olarak ayarlayabilirsiniz.<br /><br /> HTML yardım sayfasının `httpHelpPageUrl` öznitelik tarafından denetlenen konumda yayımlanmasını sağlamak için, bu özniteliği olarak `true`ayarlamanız gerekir. Ayrıca, aşağıdaki koşullardan biri de sağlanmalıdır:<br /><br /> `httpHelpPageUrl` -Öznitelik, http protokol düzenini destekleyen mutlak bir adrestir.<br />-HTTP protokol düzenini destekleyen hizmet için bir temel adres vardır.<br /><br /> HTTP protokol düzenini desteklemeyen mutlak bir adres `httpHelpPageUrl` özniteliğe atanmamışsa bir özel durum oluşsa da, önceki ölçütlerden hiçbirinin karşılanmadığı başka hiçbir senaryo hiçbir özel durum değildir ve HTML Yardım sayfası içermez.|  
|'Nin HttpHelpPageUrl|Uç nokta bir HTML tarayıcısı kullanılarak görüntülendiğinde kullanıcının gördüğü özel HTML Yardım dosyasının göreli veya mutlak HTTP tabanlı URL 'sini belirten bir URI.<br /><br /> Bu özniteliği bir HTTP/Get isteğinden döndürülen özel bir HTML Yardım dosyasının kullanımını etkinleştirmek için kullanabilirsiniz. Örneğin, bir HTML tarayıcısı. HTML Yardım dosyasının konumu aşağıdaki şekilde çözümlenir.<br /><br /> 1.  Bu özniteliğin değeri göreli bir adres ise, HTML Yardım dosyasının konumu, HTTP isteklerini destekleyen hizmet temel adresinin değeridir ve bu özellik değeridir.<br />2.  Bu özniteliğin değeri mutlak bir adres ise ve HTTP isteklerini destekliyorsa, HTML Yardım dosyasının konumu bu özelliğin değeridir.<br />3.  Bu özniteliğin değeri mutlak ise ancak HTTP isteklerini desteklemiyorsa, bir özel durum oluşturulur.<br /><br /> Bu öznitelik yalnızca `httpHelpPageEnabled` `true`özniteliği olduğunda geçerlidir.|  
|httpsHelpPageBinding|Hizmet yardım sayfasına erişmek için HTTPS kullanılırken kullanılacak bağlama türünü belirten bir dize değeri.<br /><br /> Yalnızca destekleyen <xref:System.ServiceModel.Channels.IReplyChannel> iç bağlama öğeleri olan bağlamalar desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpsHelpPageBindingConfiguration|Bu bağlamanın ek yapılandırma bilgilerine başvuran `httpsHelpPageBinding` özniteliğinde belirtilen bağlama adını belirten bir dize. `<bindings>` Bölümünde aynı ad tanımlanmalıdır.|  
|httpsHelpPageEnabled|WCF 'nin `httpsHelpPageUrl` öznitelik tarafından belirtilen adreste bir HTML Yardım sayfası yayımlalayıp yayımlamayacağını denetleyen Boolean bir değer. Varsayılan, `true` değeridir.<br /><br /> HTML tarayıcılarına görünür bir HTML `false` yardım sayfası yayımını devre dışı bırakmak için, bu özelliği olarak ayarlayabilirsiniz.<br /><br /> HTML yardım sayfasının `httpsHelpPageUrl` öznitelik tarafından denetlenen konumda yayımlanmasını sağlamak için, bu özniteliği olarak `true`ayarlamanız gerekir. Ayrıca, aşağıdaki koşullardan biri de sağlanmalıdır:<br /><br /> `httpsHelpPageUrl` -Öznitelik, HTTPS protokol düzenini destekleyen mutlak bir adrestir.<br />-HTTPS protokol düzenini destekleyen hizmet için bir temel adres vardır.<br /><br /> HTTPS protokol düzenini desteklemeyen mutlak bir adres `httpsHelpPageUrl` özniteliğe atanmamışsa bir özel durum oluşsa da, önceki ölçütlerden hiçbirinin karşılanmadığı başka hiçbir senaryo hiçbir özel durum değildir ve HTML Yardım sayfası içermez.|  
|'Nin HttpsHelpPageUrl|Uç nokta bir HTML tarayıcısı kullanılarak görüntülendiğinde kullanıcının gördüğü özel HTML Yardım dosyasının göreli veya mutlak HTTPS tabanlı URL 'sini belirten bir URI.<br /><br /> Bu özniteliği bir HTTPS/Get isteğinden döndürülen özel bir HTML Yardım dosyasının kullanımını etkinleştirmek için kullanabilirsiniz. Örneğin, bir HTML tarayıcısı. HTML Yardım dosyasının konumu aşağıdaki şekilde çözümlenir:<br /><br /> -Bu özelliğin değeri göreli bir adres ise, HTML Yardım dosyasının konumu, HTTPS isteklerini destekleyen hizmet temel adresinin değeridir ve bu özellik değeridir.<br />-Bu özelliğin değeri mutlak bir adres ise ve HTTPS isteklerini destekliyorsa, HTML Yardım dosyasının konumu bu özelliğin değeridir.<br />-Bu özelliğin değeri mutlak ise ancak HTTPS isteklerini desteklemiyorsa, bir özel durum oluşturulur.<br /><br /> Bu öznitelik yalnızca `httpHelpPageEnabled` `true`özniteliği olduğunda geçerlidir.|  
|IncludeExceptionDetailInFaults|Yönetilen özel durum bilgilerinin, hata ayıklama amacıyla istemciye döndürülen SOAP hatalarının ayrıntısına eklenip eklenmeyeceğini belirten bir değer. Varsayılan, `false` değeridir.<br /><br /> Bu özniteliği olarak `true`ayarlarsanız, hata ayıklama amacıyla istemciye yönetilen özel durum bilgileri akışını ve Web tarayıcılarında hizmete göz atan kullanıcıların HTML bilgi dosyalarının yayımlanmasını sağlayabilirsiniz. **Dikkatli**  Yönetilen özel durum bilgilerini istemcilere döndürmek bir güvenlik riski oluşturabilir. Bunun nedeni, özel durum ayrıntılarının yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulamasıyla ilgili bilgileri kullanıma sunmasıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İçin `includeExceptionDetailInFaults` ayarı`true` ,<xref:System.ServiceModel.FaultContractAttribute>özel durum kullanılarak bildirilmemiş olsa bile, hizmetin uygulama kodu tarafından oluşturulan herhangi bir özel durumu döndürmesini sağlar. Bu ayar, sunucunun beklenmeyen bir özel durum oluşturan durumlarda hata ayıklaması yaparken faydalıdır. Bu özniteliği kullanarak, bilinmeyen özel durumun serileştirilmiş formu döndürülür ve özel durumun daha fazla ayrıntılarını inceleyebilirsiniz.  
  
> [!CAUTION]
>  Yönetilen özel durum bilgilerini istemcilere döndürmek, özel durum ayrıntıları yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulamasıyla ilgili bilgileri kullanıma sunduğundan güvenlik riski oluşturabilir. Söz konusu güvenlik sorunları nedeniyle, yalnızca denetimli hata ayıklama senaryolarında bunu yapmanız önemle önerilir. Uygulamanızı dağıttığınızda olarak `includeExceptionDetailInFaults` `false` ayarlamanız gerekir.  
  
 Yönetilen özel durumla ilgili güvenlik sorunları hakkında daha fazla bilgi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md). Kod örneği için bkz. [hizmet hata ayıklama davranışı](../../../wcf/samples/service-debug-behavior.md).  
  
 `httpsHelpPageEnabled` Ayrıca`httpsHelpPageUrl` , yardım sayfasını etkinleştirip etkinleştirebilir veya devre dışı bırakabilirsiniz. Her hizmet, isteğe bağlı olarak hizmetle ilgili WSDL 'yi almak için uç nokta dahil olmak üzere hizmet hakkındaki bilgileri içeren bir yardım sayfası sunabilir. Bu, ayarına `httpHelpPageEnabled` `true`göre etkinleştirilebilir. Bu, yardım sayfasının, hizmetin temel adresine yönelik bir GET isteğine döndürülmesini sağlar. `httpHelpPageUrl` Özniteliği ayarlayarak bu adresi değiştirebilirsiniz. Ayrıca, HTTP yerine HTTPS kullanarak bunu güvenli hale getirebilirsiniz.  
  
 İsteğe bağlı `httpHelpPageBinding` ve `httpHelpPageBinding` öznitelikleri, hizmet Web sayfasına erişmek için kullanılan bağlamaları yapılandırmanızı sağlar. Bunlar belirtilmemişse, hizmet yardım sayfası erişimi için uygun olan`HttpTransportBindingElement`varsayılan bağlamalar (http ve `HttpsTransportBindingElement`söz konusu olduğunda, https durumunda) kullanılır. Bu öznitelikleri yerleşik WCF bağlamaları ile kullanamazsınız. Yalnızca XREF: System. ServiceModel. Channels. IReplyChannel destekleyen desteklenecektir > destekleyen iç bağlama öğelerine sahip bağlamalar desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceDebugElement>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Özel Durum ve Hataları İşleme](../../../wcf/extending/handling-exceptions-and-faults.md)
- [Hizmet Hata Ayıklama Davranışı](../../../wcf/samples/service-debug-behavior.md)

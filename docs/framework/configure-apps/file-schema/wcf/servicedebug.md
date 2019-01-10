---
title: '&lt;serviceDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: e4f929e5c847c1f8db3a3ab5a8e72ec198c7d223
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145815"
---
# <a name="ltservicedebuggt"></a>&lt;serviceDebug&gt;
Bir Windows Communication Foundation (WCF) hizmeti için hata ayıklama ve Yardım bilgileri özelliklerini belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
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
|httpHelpPageBinding|Hizmet yardım sayfasına erişmek için HTTP yararlanıldığında kullanılacak bağlama türünü belirten bir dize değeri.<br /><br /> Destekleyen iç bağlama öğeleri içeren bağlamaları yalnızca <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpHelpPageBindingConfiguration|İçinde belirtilmiş bağlama adını belirten bir dize `httpHelpPageBinding` bu bağlamanın ek yapılandırma bilgilerinie başvuran öznitelik. Aynı ada tanımlanmalıdır `<bindings>` bölümü.|  
|HttpHelpPageEnabled|WCF tarafından belirtilen adresten bir HTML Yardım sayfası yayımlar olup olmadığını denetleyen bir Boole değeri `httpHelpPageUrl` özniteliği. Varsayılan, `true` değeridir.<br /><br /> Bu özelliği ayarlamak `false` tarayıcılara HTML görünür bir HTML Yardım sayfası yayınlarını devre dışı bırakmak için.<br /><br /> HTML Yardımı emin olmak için sayfası tarafından denetlenen konumunda yayımlanır `httpHelpPageUrl` özniteliği bu öznitelik ayarlamalısınız `true`. Ayrıca, aşağıdaki koşullardan biri de karşılanmalıdır:<br /><br /> - `httpHelpPageUrl` Özniteliktir HTTP protokolü düzenini destekleyen bir mutlak bir adres.<br />-Bir HTTP protokol şeması destekleyen hizmeti temel adresi yok.<br /><br /> HTTP protokolü düzeni desteklemeyen bir mutlak bir adres atanırsa, bir özel durum oluşturulur ancak `httpHelpPageUrl` özniteliği, hiçbir özel durum ve hiçbir HTML Yardım sayfası met sonuçları hangi hiçbiri yukarıdaki ölçütlere içinde olan herhangi bir senaryo.|  
|HttpHelpPageUrl|Göreli veya mutlak HTTP tabanlı URL'yi özel HTML belirten bir URI, uç nokta HTML tarayıcı kullanarak görüntülendiğinde kullanıcının gördüğü dosya yardımcı olur.<br /><br /> Bu öznitelik, bir HTTP/Get isteğinden, örneğin, bir HTML tarayıcısından dönen özel HTML Yardım dosyasının kullanımını etkinleştirmek için kullanabilirsiniz. HTML Yardım dosyasının konumu gibi çözümlenir.<br /><br /> 1.  Bu özniteliğin değeri, göreli bir adres ise, HTML Yardım dosyasının konumunu HTTP isteklerini destekleyen hizmeti temel adresi değeri yanı sıra, bu özellik değeri ' dir.<br />2.  Bu özniteliğin değeri mutlak bir adres ve HTTP isteklerini destekler, HTML Yardım dosyasının konumu bu özellik değeridir.<br />3.  Bu özniteliğin değeri mutlak ancak HTTP isteklerini desteklemez, bir özel durum oluşturulur.<br /><br /> Bu özniteliği yalnızca geçerli olduğunda, `httpHelpPageEnabled` özniteliği `true`.|  
|httpsHelpPageBinding|Hizmet yardım sayfasına erişmek için HTTPS yararlanıldığında kullanılacak bağlama türünü belirten bir dize değeri.<br /><br /> Destekleyen iç bağlama öğeleri içeren bağlamaları yalnızca <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpsHelpPageBindingConfiguration|İçinde belirtilmiş bağlama adını belirten bir dize `httpsHelpPageBinding` bu bağlamanın ek yapılandırma bilgilerinie başvuran öznitelik. Aynı ada tanımlanmalıdır `<bindings>` bölümü.|  
|HttpsHelpPageEnabled|WCF tarafından belirtilen adresten bir HTML Yardım sayfası yayımlar olup olmadığını denetleyen bir Boole değeri `httpsHelpPageUrl` özniteliği. Varsayılan, `true` değeridir.<br /><br /> Bu özelliği ayarlamak `false` tarayıcılara HTML görünür bir HTML Yardım sayfası yayınlarını devre dışı bırakmak için.<br /><br /> HTML Yardımı emin olmak için sayfası tarafından denetlenen konumunda yayımlanır `httpsHelpPageUrl` özniteliği bu öznitelik ayarlamalısınız `true`. Ayrıca, aşağıdaki koşullardan biri de karşılanmalıdır:<br /><br /> - `httpsHelpPageUrl` Özniteliktir HTTPS protokolü düzenini destekleyen bir mutlak bir adres.<br />-Temel adres için HTTPS protokolü düzenini destekleyen hizmet yok.<br /><br /> HTTPS protokolü şeması desteklemeyen bir mutlak bir adres atanırsa, bir özel durum oluşturulur ancak `httpsHelpPageUrl` özniteliği, hiçbir özel durum ve hiçbir HTML Yardım sayfası met sonuçları hangi hiçbiri yukarıdaki ölçütlere içinde olan herhangi bir senaryo.|  
|HttpsHelpPageUrl|Göreli veya mutlak HTTPS tabanlı URL özel HTML belirten bir URI, uç nokta HTML tarayıcı kullanarak görüntülendiğinde kullanıcının gördüğü dosya yardımcı olur.<br /><br /> Bu öznitelik, bir HTTPS/Get isteğinden, örneğin, bir HTML tarayıcısından dönen özel HTML Yardım dosyasının kullanımını etkinleştirmek için kullanabilirsiniz. HTML Yardım dosyasının konumu gibi çözümlenir:<br /><br /> -Bu özelliğin değeri göreli adres HTML Yardım dosyasının konumunu HTTPS isteklerini destekler hizmeti temel adresi değeri yanı sıra, bu özelliği değer ise.<br />-Bu özelliğin değeri mutlak bir adres ve HTTPS isteklerini destekler, HTML Yardım dosyasının konumu bu özellik değeridir.<br />-Bu özelliğin değeri mutlak olduğundan, ancak HTTPS isteklerini desteklemez, bir özel durum oluşturulur.<br /><br /> Bu özniteliği yalnızca geçerli olduğunda, `httpHelpPageEnabled` özniteliği `true`.|  
|IncludeExceptionDetailInFaults|Hata ayıklama amacıyla istemciye dönen SOAP hatalarının ayrıntılarındaki yönetilen özel durum bilgilerinin dahil edilip edilmeyeceğini belirten bir değeri. Varsayılan, `false` değeridir.<br /><br /> Bu öznitelik ayarlanırsa verilen `true`, yayının kullanıcılar Web tarayıcıları hizmetinde gezinme için HTML bilgi dosyaların yanı sıra hata ayıklama amacıyla istemciye yönetilen özel durum bilgilerinin akışını etkinleştirebilirsiniz. **Dikkat:**  İstemcilere döndüren yönetilen özel durum bilgilerini bir güvenlik riski olabilir. Özel durum ayrıntıları yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulaması hakkında bilgi açığa olmasıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayarı `includeExceptionDetailInFaults` için `true` kullanarak özel durum bildirilmedi bile uygulama kodu tarafından oluşturulan tüm özel durum geri dönmek hizmet verir <xref:System.ServiceModel.FaultContractAttribute>. Bu ayar, sunucu beklenmeyen bir özel durum burada atma durumlarda hata ayıklama sırasında yararlıdır. Bu özniteliği kullanarak, bir seri hala getirilmiş biçimini Bilinmeyen özel durum döndürülür ve daha fazla özel durum ayrıntıları inceleyebilirsiniz.  
  
> [!CAUTION]
>  Özel durum ayrıntıları yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulaması hakkında bilgi açığa istemcilere döndüren yönetilen özel durum bilgilerini bir güvenlik riski olabilir. İlgili güvenlik sorunları nedeniyle yalnızca denetimli hata ayıklama senaryolarında yapmanız önemle tavsiye edilir. Ayarlamalısınız `includeExceptionDetailInFaults` için `false` uygulamanızı dağıtırken.  
  
 Yönetilen özel durum için ilgili güvenlik sorunları hakkında daha fazla ayrıntı için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Bir kod örneği için bkz. [hizmet hata ayıklama davranışı](../../../../../docs/framework/wcf/samples/service-debug-behavior.md).  
  
 Ayrıca `httpsHelpPageEnabled` ve `httpsHelpPageUrl` etkinleştirme veya devre dışı Yardım sayfası. Her bir hizmet, isteğe bağlı olarak hizmet için WSDL almak için uç nokta gibi hizmet hakkındaki bilgileri içeren bir Yardım sayfası kullanıma sunabilirsiniz. Bu ayarlayarak etkinleştirilebilir `httpHelpPageEnabled` için `true`. Bu hizmetin taban adresi için bir GET isteği için döndürülecek yardım sayfasına sağlar. Bu adresi ayarlayarak değiştirebilirsiniz `httpHelpPageUrl` özniteliği. Ayrıca, bu HTTP yerine HTTPS kullanarak güvenli hale getirebilirsiniz.  
  
 İsteğe bağlı `httpHelpPageBinding` ve `httpHelpPageBinding` öznitelikleri izin, hizmet web sayfasına erişmek için kullanılan bağlamaları yapılandırmak. Bunlar belirtilmezse, varsayılan bağlamaları (`HttpTransportBindingElement`, HTTP söz konusu olduğunda ve `HttpsTransportBindingElement`, HTTPS söz konusu olduğunda) uygun şekilde hizmet yardım sayfasına erişim için kullanılır. Bu öznitelikler yerleşik WCF bağlamaları ile kullanamazsınız dikkat edin. Xref:System.ServiceModel.Channels.IReplyChannel destekleyen iç bağlama öğeleri içeren bağlamaları yalnızca > desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceDebugElement>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>  
 [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Özel Durum ve Hataları İşleme](../../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Hizmet Hata Ayıklama Davranışı](../../../../../docs/framework/wcf/samples/service-debug-behavior.md)

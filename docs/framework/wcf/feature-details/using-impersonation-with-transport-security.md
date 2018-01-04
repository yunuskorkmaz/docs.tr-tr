---
title: "Taşıma Güvenliği ile Kimliğe Bürünme Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
caps.latest.revision: "12"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 57b40493d0e9bcbbaaf1366c74ff116343f6ee96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-impersonation-with-transport-security"></a>Taşıma Güvenliği ile Kimliğe Bürünme Kullanma
*Kimliğe bürünme* bir sunucu uygulaması istemci kimliği üzerinde gerçekleştirilecek özelliğidir. Kimliğe bürünme kaynaklarına erişimi doğrularken kullanmak üzere hizmetlerin yaygındır. Bir hizmet hesabı kullanarak sunucu uygulaması çalışır, ancak server istemci bağlantısı kabul ettiğinde, böylece erişim denetimlerini istemcinin kimlik bilgileri kullanılarak gerçekleştirilir, istemci temsil eder. Taşıma güvenliği bir hem de bu kimlik bilgilerini kullanarak güvenli hale getirmek ve kimlik bilgilerini geçirme mekanizmadır. Bu konu, taşıma güveliği kullanarak açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kimliğe bürünme özelliği ile. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ileti güvenliği kullanarak kimliğe bürünme bkz [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Beş kimliğe bürünme düzeyi  
 Aktarım güvenliği kullanır kimliğe bürünme, beş düzeyde aşağıdaki tabloda açıklandığı gibi.  
  
|Kimliğe bürünme düzeyi|Açıklama|  
|-------------------------|-----------------|  
|Yok.|Sunucu uygulaması istemci kimliğine bürünmek denemez.|  
|Anonim|Sunucu uygulaması istemci kimlik bilgilerine yönelik erişim denetimleri gerçekleştirebilirsiniz, ancak istemcinin kimliği hakkında hiçbir bilgi almaz. Bu kimliğe bürünme düzeyini, yalnızca adlandırılmış kanallar gibi makine üzerindeki iletişim için anlamlıdır. Kullanarak `Anonymous` ile uzak bağlantı tanımla kimliğe bürünme düzeyini yükseltir.|  
|Tanımlayın|Sunucu uygulaması istemci kimliğini bilir ve erişimi doğrulaması istemcinin kimlik bilgilerine karşı gerçekleştirebilirsiniz, ancak istemci alınamıyor. Tanımlamak SSPI kimlik bilgileri ile kullanılan varsayılan kimliğe bürünme düzeyi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sürece farklı kimliğe bürünme düzeyi belirteç sağlayıcı sağlar.|  
|Impersonate|Sunucu uygulaması, erişim denetimleri yapmak yanı sıra istemci olarak server makinesinde kaynaklara erişebilir. Sunucu uygulaması Kimliğine bürünülen belirteci ağ kimlik bilgilerine sahip olmadığından istemcinin kimliğini kullanarak uzak makinelerde kaynaklarına erişemiyor|  
|Temsilci|Aynı özelliklerine sahip yanı sıra `Impersonate`, temsilci kimliğe bürünme düzeyini ayrıca istemcinin kimliğini kullanarak uzak makinelerde ve başka uygulamalar için kimlik geçirmek için kaynaklara erişmek için sunucu uygulaması sağlar.<br /><br /> **Önemli** sunucusu etki alanı hesabı işaretlenmelidir bu ek özellikleri kullanmak için etki alanı denetleyicisinde temsilci olarak güvenilir. Bu kimliğe bürünme düzeyi, gizli olarak işaretlenmiş istemci etki alanı hesaplarıyla kullanılamaz.|  
  
 İle taşıma güvenliği en yaygın olarak kullanılan düzeyleri `Identify` ve `Impersonate`. Düzeyleri `None` ve `Anonymous` genel kullanım için tavsiye edilmez ve birçok taşımaları bu düzeyleri ile kimlik doğrulaması kullanmayı desteklemez. `Delegate` Düzeyi dikkatli kullanılması gereken güçlü bir özelliktir. Yalnızca güvenilir sunucu uygulamalarını kimlik bilgileri temsilcisi izni verilmesi gerekir.  
  
 Kimliğe bürünme sırasında kullanılarak `Impersonate` veya `Delegate` düzeyleri gerektiren sunucu uygulamayı `SeImpersonatePrivilege` ayrıcalık. Bir hizmet SID ile (ağ hizmeti, yerel hizmet veya yerel sistem) Administrators grubundaki bir hesabı veya bir hesap üzerinde çalışıyorsa bir uygulama bu ayrıcalık varsayılan olarak sahiptir. Kimliğe bürünme, istemci ve sunucu, karşılıklı kimlik doğrulaması gerektirmez. Kimliğe bürünme, NTLM gibi destek bazı kimlik doğrulama şemasını ile karşılıklı kimlik doğrulaması kullanılamaz.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Kimliğe bürünme aktarım özgü sorunları  
 Bir taşıma seçimi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kimliğe bürünme için olası seçeneklerini etkiler. Bu bölümde, standart HTTP etkileyen sorunları açıklar ve kanal aktarımlarda adlı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Özel taşımaları kimliğe bürünme için destek kendi kısıtlamaları vardır.  
  
### <a name="named-pipe-transport"></a>Adlandırılmış kanal taşıma  
 Aşağıdaki öğeler ile adlandırılmış kanal taşıma kullanılır:  
  
-   Adlandırılmış kanal taşıma yalnızca yerel makinede kullanıma yöneliktir. Adlandırılmış kanal taşıma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] makineler arası bağlantılar açıkça izin vermez.  
  
-   Adlandırılmış Kanallar ile kullanılamaz `Impersonate` veya `Delegate` kimliğe bürünme düzeyi. Adlandırılmış kanal Bu kimliğe bürünme düzeyleri makine üzerinde garantisi zorunlu kılamaz.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Adlandırılmış Kanallar, bkz: [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
### <a name="http-transport"></a>HTTP taşıma  
 HTTP taşıması kullanan bağlamaları (<xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.BasicHttpBinding>) birden fazla kimlik doğrulama şemasını açıklandığı gibi destek [anlama HTTP kimlik doğrulaması](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md). Kimliğe bürünme düzeyi desteklenen kimlik doğrulama şeması bağlıdır. Aşağıdaki öğeler ile HTTP aktarma kullanılır:  
  
-   `Anonymous` Kimlik doğrulama düzeni, kimliğe bürünme göz ardı eder.  
  
-   `Basic` Kimlik doğrulama düzenini destekler yalnızca `Delegate` düzeyi. Tüm alt kimliğe bürünme düzeyi yükseltilir.  
  
-   `Digest` Kimlik doğrulama düzenini destekler yalnızca `Impersonate` ve `Delegate` düzeyleri.  
  
-   `NTLM` Doğrudan ya da üzerinden anlaşması, kimlik doğrulama düzeni, seçilebilir destekleyen yalnızca `Delegate` yerel makinede düzeyi.  
  
-   Yalnızca anlaşması ile seçilebilir, Kerberos kimlik doğrulama şeması herhangi bir desteklenen kimliğe bürünme düzeyi ile kullanılabilir.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]HTTP taşıma bkz [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [HTTP Kimlik Doğrulamasını Anlama](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)

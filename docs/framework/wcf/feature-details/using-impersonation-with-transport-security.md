---
title: Taşıma Güvenliği ile Kimliğe Bürünme Kullanma
ms.date: 03/30/2017
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
ms.openlocfilehash: f392dbe5806532eba181adef4ba3c8bebce9eddd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637451"
---
# <a name="using-impersonation-with-transport-security"></a>Taşıma Güvenliği ile Kimliğe Bürünme Kullanma
*Kimliğe bürünme* istemci kimliğini almak için bir sunucu uygulaması özelliğidir. Kimliğe bürünme, kaynaklara erişimi doğrularken kullanmak üzere hizmetlerin yaygındır. Bir hizmet hesabı kullanarak sunucu uygulaması çalışır ancak server istemci bağlantısı kabul ettiğinde, istemcinin kimlik bilgilerini kullanarak erişim denetimleri gerçekleştirilmesi, istemci kimliğine bürünür. Aktarım güvenliği hem de kimlik bilgilerini geçirerek ve bu kimlik bilgilerini kullanarak güvenli hale getirmek için bir mekanizma ' dir. Aktarım güvenliği ile kimliğe bürünme özelliğini Windows Communication Foundation (WCF) kullanarak bu konuda açıklanmaktadır. İleti güveliği kullanarak kimliğe bürünme hakkında daha fazla bilgi için bkz. [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Beş kimliğe bürünme düzeyi  
 Aktarım güvenliği kullanır kimliğe bürünme, beş düzeyleri aşağıdaki tabloda açıklandığı gibi.  
  
|Kimliğe bürünme düzeyi|Açıklama|  
|-------------------------|-----------------|  
|Yok.|Sunucu uygulaması istemci kimliğine bürünme çalışmaz.|  
|Anonim|Sunucu uygulaması istemci kimlik bilgilerine yönelik erişim denetimleri gerçekleştirebilirsiniz, ancak istemcinin kimliği hakkında hiçbir bilgi almaz. Bu kimliğe bürünme düzeyi yalnızca adlandırılmış kanallar gibi makinede iletişim için anlamlıdır. Kullanarak `Anonymous` ile bir uzak bağlantı tanımlayın kimliğe bürünme düzeyini yükseltir.|  
|Tanımlayın|Sunucu uygulaması istemci kimliğini bilir ve istemcinin kimlik bilgilerine yönelik erişim doğrulama yapabilirsiniz, ancak istemci kimliğine bürünülemedi. Tanımlamak WCF SSPI kimlik bilgileri ile farklı kimliğe bürünme düzeyi belirteç sağlayıcısı sağlamadığı sürece kullanılan varsayılan kimliğe bürünme düzeyi.|  
|Impersonate|Sunucu uygulaması istemci erişim denetimlerini biçimlendirebilir server makinesinde kaynaklarına erişim sağlayabilir. Sunucu uygulaması başkasının kimliğine bürünülerek gerçekleştirilen belirteç ağ kimlik bilgilerine sahip olmadığından, istemcinin kimliğini kullanarak uzak makinelerde kaynaklarına erişemiyor|  
|Temsilci|Aynı özellikleri sahip olmaya ek olarak `Impersonate`, temsilci kimliğe bürünme düzeyi sunucu uygulaması için istemci kimliğini kullanarak uzak makinelere ve diğer uygulamalar için kimlik geçirmek için kaynaklara erişim de sağlar.<br /><br /> **Önemli** sunucusu etki alanı hesabı işaretlenmelidir bu ek özellikleri kullanmak için etki alanı denetleyicisinde temsilci olarak güvenilir. Bu kimliğe bürünme düzeyini önemli olarak işaretlenmiş istemci etki alanı hesapları kullanılamaz.|  
  
 İle Aktarım güvenliği en sık kullanılan düzeyleri `Identify` ve `Impersonate`. Düzeyleri `None` ve `Anonymous` tipik kullanım için tavsiye edilmez ve bu düzeyleri kimlik doğrulamasını kullanarak birçok taşımalar desteklemez. `Delegate` Düzeyidir dikkatli kullanılmalıdır güçlü bir özelliktir. Yalnızca güvenilen sunucu uygulamaları, kimlik bilgileri temsilcisi izni verilmelidir.  
  
 Kimliğe bürünme sırasında kullanarak `Impersonate` veya `Delegate` düzeyleri için sunucu uygulamasının gerektirir `SeImpersonatePrivilege` ayrıcalık. Bir hizmet SID'si ile (ağ hizmeti, yerel hizmet veya yerel sistem) bir hesap veya Administrators grubunda bir hesap üzerinde çalışıyorsa bir uygulama varsayılan olarak bu ayrıcalığı sahiptir. Kimliğe bürünme, istemci ve sunucu, karşılıklı kimlik doğrulaması gerektirmez. Kimliğe bürünme, NTLM gibi destekleyen bazı kimlik doğrulama düzenleri, karşılıklı kimlik doğrulama ile kullanılamaz.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Kimliğe bürünme aktarım özgü sorunları  
 Wcf'de aktarım seçimi kimliğe bürünme için olası seçimleri etkiler. Bu bölümde, standart HTTP etkileyen sorunları açıklar ve WCF kanalı aktarımları adlı. Özel taşımalar kimliğe bürünme için destek kendi kısıtlamaları vardır.  
  
### <a name="named-pipe-transport"></a>Adlandırılmış kanal taşıma  
 Aşağıdaki öğeler, adlandırılmış kanal taşıma ile kullanılır:  
  
- Adlandırılmış kanal taşıma yalnızca yerel makinede kullanıma yöneliktir. Wcf'de adlandırılmış kanal taşıma, makineler arası bağlantılara açıkça izin vermiyor.  
  
- Adlandırılmış Kanallar ile kullanılamaz `Impersonate` veya `Delegate` kimliğe bürünme düzeyi. Adlandırılmış kanal Bu kimliğe bürünme düzeylerinde makinede garanti zorunlu kılamaz.  
  
 Adlandırılmış kanallar hakkında daha fazla bilgi için bkz: [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
### <a name="http-transport"></a>HTTP taşıma  
 HTTP taşıma kullanan bağlamaları (<xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.BasicHttpBinding>) açıklandığı gibi çeşitli kimlik doğrulama şeması desteği [anlama HTTP kimlik doğrulaması](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md). Kimliğe bürünme düzeyi desteklenen kimlik doğrulama şemasını temel bağlıdır. Aşağıdaki öğeler ile HTTP aktarımı kullanılır:  
  
- `Anonymous` Kimliğe bürünme kimlik doğrulama düzeni yoksayar.  
  
- `Basic` Kimlik doğrulama düzeni destekler yalnızca `Delegate` düzeyi. Tüm alt kimliğe bürünme düzeyi yükseltilir.  
  
- `Digest` Kimlik doğrulama düzeni destekler yalnızca `Impersonate` ve `Delegate` düzeyleri.  
  
- `NTLM` Seçilebilir kimlik doğrulama şemasıyla doğrudan veya anlaşma, üzerinden destekler yalnızca `Delegate` yerel makinede düzeyi.  
  
- Yalnızca anlaşma seçilebilir, Kerberos kimlik doğrulama düzeni, herhangi bir desteklenen kimliğe bürünme düzeyi ile kullanılabilir.  
  
 HTTP taşıma hakkında daha fazla bilgi için bkz. [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Nasıl yapılır: Bir hizmette istemci kimliğine bürünme](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [HTTP Kimlik Doğrulamasını Anlama](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)

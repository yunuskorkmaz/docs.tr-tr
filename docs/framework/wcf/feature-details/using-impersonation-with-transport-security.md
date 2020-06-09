---
title: Taşıma Güvenliği ile Kimliğe Bürünme Kullanma
ms.date: 03/30/2017
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
ms.openlocfilehash: 1d33bfbbb74266aefa538166b4e1aca7d7e315ef
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594978"
---
# <a name="using-impersonation-with-transport-security"></a>Taşıma Güvenliği ile Kimliğe Bürünme Kullanma
*Kimliğe bürünme* , bir sunucu uygulamasının istemcinin kimliğini alma yeteneğidir. Hizmetlerin, kaynaklara erişimi doğrularken kimliğe bürünme özelliğini kullanması yaygındır. Sunucu uygulaması bir hizmet hesabı kullanarak çalışır, ancak sunucu bir istemci bağlantısını kabul ettiğinde, istemci kimlik bilgileri kullanılarak erişim denetimlerinin gerçekleştirilmesi için istemciyi taklit eder. Aktarım güvenliği, kimlik bilgilerinin iletilmesi ve bu kimlik bilgilerini kullanarak iletişimin güvenliğini sağlamak için kullanılan bir mekanizmadır. Bu konu, kimliğe bürünme özelliği ile Windows Communication Foundation (WCF) ' de aktarım güvenliği kullanımını açıklamaktadır. İleti güvenliğini kullanarak kimliğe bürünme hakkında daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Beş kimliğe bürünme düzeyi  
 Taşıma güvenliği, aşağıdaki tabloda açıklandığı gibi beş kimliğe bürünme düzeyini kullanır.  
  
|Kimliğe bürünme düzeyi|Açıklama|  
|-------------------------|-----------------|  
|Yok|Sunucu uygulaması istemcinin kimliğine bürünmeye çalışmaz.|  
|Anonim|Sunucu uygulaması, istemcinin kimlik bilgileriyle erişim denetimleri gerçekleştirebilir, ancak istemcinin kimliğiyle ilgili herhangi bir bilgi almaz. Bu kimliğe bürünme düzeyi yalnızca adlandırılmış kanallar gibi makine içi iletişimde anlamlıdır. `Anonymous`Bir uzak bağlantıyla birlikte kullanmak, kimliğe bürünme düzeyini belirlemek için yükseltir.|  
|Tanıtan|Sunucu uygulaması, istemcinin kimliğini bilir ve istemcinin kimlik bilgileriyle erişim doğrulaması yapabilir, ancak istemcinin kimliğine bürünemezsiniz. Belirleme, belirteç sağlayıcı farklı kimliğe bürünme düzeyi sağladığından WCF 'de SSPI kimlik bilgileriyle kullanılan varsayılan kimliğe bürünme düzeyidir.|  
|Impersonate|Sunucu uygulaması, erişim denetimleri gerçekleştirmeye ek olarak sunucu makinesindeki kaynaklara istemci olarak erişebilir. Kimliğe bürünülmüş belirtecin ağ kimlik bilgilerine sahip olmadığı için sunucu uygulaması, istemcinin kimliğini kullanan uzak makinelerdeki kaynaklara erişemez|  
|Temsilci|Aynı yeteneklere sahip olmanın yanı sıra `Impersonate` , temsilci kimliğe bürünme düzeyi Ayrıca sunucu uygulamasının, istemci kimliğini kullanarak uzak makinelerdeki kaynaklara erişmesini ve kimliği diğer uygulamalara geçmesini sağlar.<br /><br /> **Önemli** Sunucu etki alanı hesabının, bu ek özellikleri kullanabilmesi için etki alanı denetleyicisindeki temsili için güvenilir olarak işaretlenmesi gerekir. Bu kimliğe bürünme düzeyi, hassas olarak işaretlenmiş istemci etki alanı hesaplarıyla kullanılamaz.|  
  
 Aktarım güvenliği ile en yaygın olarak kullanılan düzeyler `Identify` ve ' dir `Impersonate` . Düzeyler `None` ve `Anonymous` tipik kullanım için önerilmez ve birçok aktarım, kimlik doğrulamasıyla Bu düzeylerin kullanımını desteklemez. `Delegate`Düzey, dikkatli bir şekilde kullanılması gereken güçlü bir özelliktir. Kimlik bilgilerini devretmek için yalnızca güvenilir sunucu uygulamalarına izin verilmelidir.  
  
 Veya düzeylerinde kimliğe bürünme özelliğini kullanmak `Impersonate` `Delegate` sunucu uygulamasının ayrıcalığa sahip olmasını gerektirir `SeImpersonatePrivilege` . Bir uygulama, Yöneticiler grubundaki bir hesapta veya hizmet SID 'SI (ağ hizmeti, yerel hizmet veya yerel sistem) olan bir hesapta çalışıyorsa, varsayılan olarak bu ayrıcalığa sahip olur. Kimliğe bürünme, istemci ve sunucu için karşılıklı kimlik doğrulaması gerektirmez. NTLM gibi kimliğe bürünme özelliğini destekleyen bazı kimlik doğrulama şemaları karşılıklı kimlik doğrulama ile kullanılamaz.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Kimliğe bürünme ile ilgili taşıma sorunları  
 WCF 'de bir taşımanın seçimi, kimliğe bürünme için olası seçimleri etkiler. Bu bölümde, WCF 'de standart HTTP ve adlandırılmış kanal taşımalarını etkileyen sorunlar açıklanmaktadır. Özel taşıtlar, kimliğe bürünme desteğiyle ilgili kendi kısıtlamalarına sahiptir.  
  
### <a name="named-pipe-transport"></a>Adlandırılmış kanal taşıması  
 Aşağıdaki öğeler adlandırılmış kanal taşıması ile birlikte kullanılır:  
  
- Adlandırılmış kanal taşıması yalnızca yerel makinede kullanılmak üzere tasarlanmıştır. WCF 'de adlandırılmış kanal taşıması, makineler arası bağlantılara açıkça izin vermez.  
  
- Adlandırılmış Kanallar, `Impersonate` veya `Delegate` kimliğe bürünme düzeyiyle kullanılamaz. Adlandırılmış kanal, bu kimliğe bürünme düzeylerinde makine üzerindeki garantiyi zorunlu kılamaz.  
  
 Adlandırılmış kanallar hakkında daha fazla bilgi için bkz. [bir taşıma seçme](choosing-a-transport.md).  
  
### <a name="http-transport"></a>HTTP taşıması  
 HTTP aktarımını ( <xref:System.ServiceModel.WSHttpBinding> ve) kullanan bağlamalar <xref:System.ServiceModel.BasicHttpBinding> , [http kimlik doğrulamasını anlama](understanding-http-authentication.md)bölümünde açıklandığı gibi çeşitli kimlik doğrulama düzenlerini destekler. Desteklenen kimliğe bürünme düzeyi, kimlik doğrulama şemasına bağlıdır. Aşağıdaki öğeler HTTP taşıması ile birlikte kullanılır:  
  
- `Anonymous`Kimlik doğrulama şeması kimliğe bürünme özelliğini yoksayar.  
  
- `Basic`Kimlik doğrulama düzeni yalnızca düzeyi destekler `Delegate` . Tüm alt kimliğe bürünme düzeyleri yükseltilir.  
  
- `Digest`Kimlik doğrulama düzeni yalnızca `Impersonate` ve düzeylerini destekler `Delegate` .  
  
- `NTLM`Doğrudan veya anlaşma üzerinden seçilebilir olan kimlik doğrulama düzeni yalnızca `Delegate` yerel makinedeki düzeyi destekler.  
  
- Yalnızca anlaşma yoluyla seçilebilen Kerberos kimlik doğrulaması şeması, desteklenen herhangi bir kimliğe bürünme düzeyiyle kullanılabilir.  
  
 HTTP taşıması hakkında daha fazla bilgi için bkz. [bir taşıma seçme](choosing-a-transport.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temsilcilik ve Kimliğe Bürünme](delegation-and-impersonation-with-wcf.md)
- [Yetkilendirme](authorization-in-wcf.md)
- [Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme](../how-to-impersonate-a-client-on-a-service.md)
- [HTTP Kimlik Doğrulamasını Anlama](understanding-http-authentication.md)

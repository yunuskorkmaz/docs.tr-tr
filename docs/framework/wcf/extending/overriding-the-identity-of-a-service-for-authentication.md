---
title: Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: 3ac2d48962dd96535e1a08310570212121eca986
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555425"
---
# <a name="override-the-identity-of-a-service-for-authentication"></a>Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılma

Genellikle, bir hizmetin kimliğini ayarlamanız gerekmez, çünkü bir istemci kimlik bilgisi türü seçimi, hizmet meta verilerinde sunulan kimlik türünü belirler. Örneğin, aşağıdaki yapılandırma kodu [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) öğesini kullanır ve `clientCredentialType` özniteliğini Windows 'a ayarlar.  

 Aşağıdaki Web Hizmetleri Açıklama Dili (WSDL) parçası, daha önce tanımlanan uç noktanın kimliğini gösterir. Bu örnekte, hizmet belirli bir kullanıcı hesabı () altında kendi kendine barındırılan bir hizmet olarak çalışıyor username@contoso.com ve bu nedenle Kullanıcı asıl adı (UPN) kimliği hesap adını içerir. UPN, bir Windows etki alanında Kullanıcı oturum açma adı olarak da bilinir.  

 Kimlik ayarını gösteren örnek bir uygulama için bkz. [hizmet kimliği örneği](../samples/service-identity-sample.md). Hizmet kimliği hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos kimlik doğrulaması ve kimliği  
 Varsayılan olarak, bir hizmet Windows kimlik bilgisi kullanacak şekilde yapılandırıldığında, [\<identity>](../../configure-apps/file-schema/wcf/identity.md) [\<userPrincipalName>](../../configure-apps/file-schema/wcf/userprincipalname.md) WSDL 'de veya öğesi içeren bir öğe [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) oluşturulur. Hizmet,, veya hesabı altında çalışıyorsa `LocalSystem` , `LocalService` `NetworkService` `host/` \<*hostname*> Bu hesapların bilgisayarın SPN verilerine erişimi olduğundan, varsayılan olarak BIR hizmet asıl adı (SPN) oluşturulur. Hizmet farklı bir hesap altında çalışıyorsa, Windows Communication Foundation (WCF) domainName biçiminde bir UPN oluşturur \<*username*> @< *domainName* `>` . Bu durum, Kerberos kimlik doğrulamasının hizmetin kimliğini doğrulamak için bir UPN veya SPN 'nin istemciye sağlanması gerektiğinden oluşur.  
  
 [Setspn](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731241(v=ws.10)) aracını Ayrıca, bir etki alanındaki hizmet hesabına sahip ek bir SPN kaydetmek için de kullanabilirsiniz. Daha sonra SPN 'YI hizmetin kimliği olarak kullanabilirsiniz. Araç hakkında daha fazla bilgi için bkz. [Setspn Overview](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).  
  
> [!NOTE]
> Windows kimlik bilgisi türünü anlaşma olmadan kullanmak için, hizmetin Kullanıcı hesabının Active Directory etki alanına kayıtlı SPN 'ye erişimi olmalıdır. Bunu aşağıdaki yöntemlerle yapabilirsiniz:  
  
- Hizmetinizi çalıştırmak için NetworkService veya LocalSystem hesabını kullanın. Makine Active Directory etki alanına katıldığında, bu hesapların bir makine SPN 'sine erişimi olduğundan, WCF hizmetin meta verilerinde (WSDL) otomatik olarak hizmetin uç noktasındaki uygun SPN öğesini oluşturur.  
  
- Hizmetinizi çalıştırmak için rastgele bir Active Directory etki alanı hesabı kullanın. Bu durumda, bu etki alanı hesabı için bir SPN oluşturun ve bu, Setspn.exe yardımcı program aracını kullanarak yapabilirsiniz. Hizmet hesabı için SPN 'YI oluşturduktan sonra, bu SPN 'YI, meta verileri (WSDL) aracılığıyla hizmetin istemcilerine yayımlamak üzere WCF 'yi yapılandırın. Bu, bir uygulama yapılandırma dosyası ya da kod aracılığıyla, gösterilen uç nokta için uç nokta kimliği ayarlanarak yapılır.  
  
 SPN 'Ler, Kerberos protokolü ve Active Directory hakkında daha fazla bilgi için bkz. [Windows Için Kerberos teknik eki](/previous-versions/msp-n-p/ff649429(v=pandp.10)).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>SPN veya UPN boş dizeye eşitse  
 SPN veya UPN 'yi boş bir dizeye eşit olarak ayarlarsanız, kullanılan güvenlik düzeyi ve kimlik doğrulama moduna bağlı olarak bir dizi farklı işlem gerçekleşir:  
  
- Aktarım düzeyi güvenliği kullanıyorsanız, NT LanMan (NTLM) kimlik doğrulaması seçilir.  
  
- İleti düzeyi güvenliği kullanıyorsanız kimlik doğrulama moduna bağlı olarak kimlik doğrulaması başarısız olabilir:  
  
- `spnego`Modunu kullanıyorsanız ve `AllowNtlm` özniteliği olarak ayarlandıysa `false` , kimlik doğrulaması başarısız olur.  
  
- `spnego`Modunu kullanıyorsanız ve `AllowNtlm` özniteliği olarak AYARLANDıYSA `true` , UPN boş ise kimlik doğrulaması başarısız olur ancak SPN boşsa başarılı olur.  
  
- Kerberos doğrudan ("tek görüntü" olarak da bilinir) kullanıyorsanız, kimlik doğrulaması başarısız olur.  
  
### <a name="use-the-identity-element-in-configuration"></a>\<identity>Yapılandırmada öğesini kullanın  
 Daha önce olarak gösterilen bağlamadaki istemci kimlik bilgisi türünü değiştirirseniz `Certificate` oluşturulan wsdl, kimlik değeri için aşağıdaki kodda gösterildiği gibi Base64 serileştirilmiş X. 509.440 sertifikası içerir. Bu, Windows dışındaki tüm istemci kimlik bilgisi türleri için varsayılandır.  

 `identity`Yapılandırma içindeki <> öğesini kullanarak veya koddaki kimliği ayarlayarak, varsayılan hizmet kimliğinin değerini değiştirebilir veya kimliğin türünü değiştirebilirsiniz. Aşağıdaki yapılandırma kodu, bir etki alanı adı sistemi (DNS) kimliğini değeriyle ayarlar `contoso.com` .  

### <a name="set-identity-programmatically"></a>Kimliği programlı olarak ayarla  
 WCF tarafından otomatik olarak belirlediği için hizmetiniz bir kimlik belirtmek zorunda değildir. Ancak, WCF, gerekirse bir uç nokta üzerinde kimlik belirtmenize olanak tanır. Aşağıdaki kod, belirli bir DNS kimliğine sahip yeni bir hizmet uç noktası ekler.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma](how-to-create-a-custom-client-identity-verifier.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](../feature-details/service-identity-and-authentication.md)

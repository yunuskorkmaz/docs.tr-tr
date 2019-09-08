---
title: Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: eed8a1edaae5fab03ad9e78d29803676debd1b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796918"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma
Genellikle, bir hizmetin kimliğini ayarlamanız gerekmez, çünkü bir istemci kimlik bilgisi türü seçimi, hizmet meta verilerinde sunulan kimlik türünü belirler. Örneğin, aşağıdaki yapılandırma kodu [ \<WSHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) `clientCredentialType` öğesini kullanır ve özniteliğini Windows 'a ayarlar.  

 Aşağıdaki Web Hizmetleri Açıklama Dili (WSDL) parçası, daha önce tanımlanan uç noktanın kimliğini gösterir. Bu örnekte, hizmet belirli bir kullanıcı hesabı (username@contoso.com) altında kendi kendine barındırılan bir hizmet olarak çalışıyor ve bu nedenle Kullanıcı asıl adı (UPN) kimliği hesap adını içerir. UPN, bir Windows etki alanında Kullanıcı oturum açma adı olarak da bilinir.  

 Kimlik ayarını gösteren örnek bir uygulama için bkz. [hizmet kimliği örneği](../samples/service-identity-sample.md). Hizmet kimliği hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos kimlik doğrulaması ve kimliği  
 Varsayılan olarak, bir hizmet Windows kimlik bilgisi kullanacak şekilde yapılandırıldığında, [ \<](../../configure-apps/file-schema/wcf/userprincipalname.md) [ \<](../../configure-apps/file-schema/wcf/identity.md) userPrincipalName > veya [ \<servicePrincipalName >](../../configure-apps/file-schema/wcf/serviceprincipalname.md) öğesi içeren bir kimlik > öğesi WSDL içinde oluşturulur. Hizmet `LocalSystem` \< `host/`, `LocalService` veya`NetworkService` hesabı altında çalışıyorsa, bir hizmet asıl adı (SPN), *ana bilgisayar*adı biçiminde varsayılan olarak oluşturulur > çünkü bu hesaplar için erişim sahibi bilgisayarın SPN verileri. \<Hizmet farklı bir hesap altında çalışıyorsa, Windows Communication Foundation (WCF) *Kullanıcı adı*>@<*domainName*`>`biçiminde bir UPN oluşturur. Bu durum, Kerberos kimlik doğrulamasının hizmetin kimliğini doğrulamak için bir UPN veya SPN 'nin istemciye sağlanması gerektiğinden oluşur.  
  
 Setspn. exe aracını ayrıca bir etki alanında hizmet hesabına sahip ek bir SPN kaydetmek için de kullanabilirsiniz. Daha sonra SPN 'YI hizmetin kimliği olarak kullanabilirsiniz. Aracı indirmek için bkz [. Windows 2000 Kaynak Seti aracı: Setspn. exe](https://go.microsoft.com/fwlink/?LinkId=91752). Araç hakkında daha fazla bilgi için bkz. [Setspn Overview](https://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
> Windows kimlik bilgisi türünü anlaşma olmadan kullanmak için, hizmetin Kullanıcı hesabının Active Directory etki alanına kayıtlı SPN 'ye erişimi olmalıdır. Bunu aşağıdaki yöntemlerle yapabilirsiniz:  
  
- Hizmetinizi çalıştırmak için NetworkService veya LocalSystem hesabını kullanın. Makine Active Directory etki alanına katıldığında, bu hesapların bir makine SPN 'sine erişimi olduğundan, WCF hizmetin meta verilerinde (WSDL) otomatik olarak hizmetin uç noktasındaki uygun SPN öğesini oluşturur.  
  
- Hizmetinizi çalıştırmak için rastgele bir Active Directory etki alanı hesabı kullanın. Bu durumda, Setspn. exe yardımcı programı aracını kullanarak yapabileceğiniz, bu etki alanı hesabı için bir SPN oluşturun. Hizmet hesabı için SPN 'YI oluşturduktan sonra, bu SPN 'YI, meta verileri (WSDL) aracılığıyla hizmetin istemcilerine yayımlamak üzere WCF 'yi yapılandırın. Bu, bir uygulama yapılandırma dosyası ya da kod aracılığıyla, gösterilen uç nokta için uç nokta kimliği ayarlanarak yapılır.  
  
 SPN 'Ler, Kerberos protokolü ve Active Directory hakkında daha fazla bilgi için bkz. [Windows Için Kerberos teknik eki](https://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>SPN veya UPN boş dizeye eşitse  
 SPN veya UPN 'yi boş bir dizeye eşit olarak ayarlarsanız, kullanılan güvenlik düzeyi ve kimlik doğrulama moduna bağlı olarak bir dizi farklı işlem gerçekleşir:  
  
- Aktarım düzeyi güvenliği kullanıyorsanız, NT LanMan (NTLM) kimlik doğrulaması seçilir.  
  
- İleti düzeyi güvenliği kullanıyorsanız kimlik doğrulama moduna bağlı olarak kimlik doğrulaması başarısız olabilir:  
  
- Modunu kullanıyorsanız `spnego` `AllowNtlm` ve özniteliği olarak `false`ayarlandıysa, kimlik doğrulama başarısız olur.  
  
- Modunu kullanıyorsanız `spnego` `AllowNtlm` ve özniteliği olarak `true`ayarlandıysa, UPN boş ise kimlik doğrulaması başarısız olur, ancak SPN boşsa başarılı olur.  
  
- Kerberos doğrudan ("tek görüntü" olarak da bilinir) kullanıyorsanız, kimlik doğrulaması başarısız olur.  
  
### <a name="using-the-identity-element-in-configuration"></a>\<Yapılandırmada kimlik > öğesi kullanma  
 Daha önce sertifikaya`,` gösterilen bağlamadaki istemci kimlik bilgisi türünü değiştirirseniz oluşturulan wsdl, kimlik değeri için aşağıdaki kodda gösterildiği gibi Base64 serileştirilmiş X. 509.440 sertifikası içerir. Bu, Windows dışındaki tüm istemci kimlik bilgisi türleri için varsayılandır.  

 Yapılandırma içindeki <`identity`> öğesini kullanarak veya koddaki kimliği ayarlayarak, varsayılan hizmet kimliğinin değerini değiştirebilir veya kimliğin türünü değiştirebilirsiniz. Aşağıdaki yapılandırma kodu, bir etki alanı adı sistemi (DNS) kimliğini değeriyle `contoso.com`ayarlar.  

### <a name="setting-identity-programmatically"></a>Kimliği programlı olarak ayarlama  
 WCF tarafından otomatik olarak belirlediği için hizmetiniz bir kimlik belirtmek zorunda değildir. Ancak, WCF, gerekirse bir uç nokta üzerinde kimlik belirtmenize olanak tanır. Aşağıdaki kod, belirli bir DNS kimliğine sahip yeni bir hizmet uç noktası ekler.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Özel bir Istemci Kimliği Doğrulayıcısı oluşturma](how-to-create-a-custom-client-identity-verifier.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](../feature-details/service-identity-and-authentication.md)

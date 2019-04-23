---
title: Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: a5a32220ad1f638bf2e93051e9b436d8270aec2f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082197"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma
Genellikle, istemci kimlik bilgisi türü seçiminde kimlik hizmeti metaveri türünü belirler. çünkü bir hizmette kimlik ayarlamak gerekmez. Örneğin, aşağıdaki yapılandırma kodunu kullanır [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ve kümelerini `clientCredentialType` Windows için özniteliği.  

 Aşağıdaki Web Hizmetleri Açıklama Dili (WSDL) parçası için önceden tanımlanmış uç nokta kimliğini gösterir. Bu örnekte, hizmet belirli bir kullanıcı hesabının altında şirket içinde barındırılan bir hizmet olarak çalışıyor (username@contoso.com) ve bu nedenle kullanıcı asıl adı (UPN) kimlik hesap adı içeriyor. UPN bir Windows etki alanı kullanıcı oturum açma adını de denir.  

 Kimlik ayarı gösteren örnek bir uygulama için bkz. [hizmet kimliği örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md). Hizmet kimliği hakkında daha fazla bilgi için bkz: [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos kimlik doğrulaması ve kimlik  
 Bir hizmet, bir Windows kimlik bilgisi kullanmak için yapılandırıldığında varsayılan olarak bir [ \<kimlik >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğesini içeren bir [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) veya [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) öğesi WSDL içinde oluşturulur. Hizmetin altında çalışıyorsa `LocalSystem`, `LocalService`, veya `NetworkService` hesabı, bir hizmet asıl adı (SPN) biçiminde varsayılan olarak oluşturulan `host/` \< *hostname*> çünkü Bu hesapların bilgisayarın SPN verilere erişebilir. Windows Communication Foundation (WCF) hizmeti farklı bir hesabı altında çalışıyorsa, bir UPN biçiminde üretir. \< *kullanıcıadı*>@<*domainName* `>` . Bu durum, UPN veya SPN hizmet kimlik doğrulaması için istemci sağlanması Kerberos kimlik doğrulaması gerektiren kaynaklanır.  
  
 Setspn.exe aracı, bir hizmetin hesabının bir etki alanındaki ek bir SPN kaydetmek için de kullanabilirsiniz. SPN, ardından hizmet kimliği olarak kullanabilirsiniz. Aracı indirmek için bkz: [Windows 2000 Kaynak Seti aracı: Setspn.exe](https://go.microsoft.com/fwlink/?LinkId=91752). Aracı hakkında daha fazla bilgi için bkz. [setspn aracına genel bakış](https://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
>  Anlaşma olmadan Windows kimlik bilgisi türü kullanmak için hizmetin kullanıcı hesabını Active Directory etki alanı ile kayıtlı SPN erişimi olmalıdır. Bunu aşağıdaki yöntemlerle yapabilirsiniz:  
  
-   NetworkService veya LocalSystem hesabı hizmetinizi çalıştırmak için kullanın. Bu hesapların makinenin Active Directory etki alanına katıldığında kurulur SPN makineye erişimi olduğundan, WCF uygun SPN öğe içinde hizmet uç noktası hizmetin meta verilerinde (WSDL) otomatik olarak oluşturur.  
  
-   Hizmetinizi çalıştırmak için rastgele bir Active Directory etki alanı hesabı kullanın. Bu durumda, Setspn.exe yardımcı programı aracı kullanarak bunu yapabilirsiniz, etki alanı hesabı için bir SPN oluşturmak. Hizmet hesabı için SPN oluşturduğunuzda, WCF meta verilerini (WSDL) aracılığıyla hizmetin istemciler söz konusu SPN yayımlamak için yapılandırın. Bu uç nokta kimliğini ortaya çıkarılan uç noktası için bir uygulama yapılandırma dosyası veya kod üzerinden ayarlayarak yapılır.  
  
 SPN hakkında daha fazla bilgi, Kerberos protokolü ve Active Directory için bkz. [Kerberos teknik ek Windows için](https://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Boş bir dize zaman SPN veya UPN eşittir  
 SPN veya UPN boş bir dize eşit ayarlarsanız pek çok farklı, kullanılan güvenlik düzeyini ve kimlik doğrulaması moduna bağlı olarak gerçekleşir:  
  
-   Aktarım düzeyi güvenlik kullanıyorsanız, NT LanMan (NTLM) kimlik doğrulaması seçilir.  
  
-   İleti düzeyi güvenliği kullanıyorsanız, kimlik doğrulaması, kimlik doğrulaması moduna bağlı olarak başarısız olabilir:  
  
-   Kullanıyorsanız `spnego` modu ve `AllowNtlm` özniteliği `false`, kimlik doğrulaması başarısız.  
  
-   Kullanıyorsanız `spnego` modu ve `AllowNtlm` özniteliği `true`, kimlik doğrulama başarısız olursa, UPN boşsa, ancak SPN boşsa başarılı olur.  
  
-   Kullanıyorsanız (diğer adıyla "kesin") doğrudan Kerberos, kimlik doğrulaması başarısız olur.  
  
### <a name="using-the-identity-element-in-configuration"></a>Kullanarak \<kimlik > yapılandırma öğesi  
 Sertifika için daha önce gösterilen bağlamasında istemci kimlik bilgileri türünü değiştirirseniz`,` oluşturulan WSDL seri hale getirilmiş bir Base64 içeriyorsa aşağıdaki kodda gösterildiği gibi kimlik değeri için X.509 sertifikası. Windows dışındaki tüm istemci kimlik bilgisi türleri için varsayılan değer budur.  

 Varsayılan hizmet kimliği değerini değiştirin ya da kullanarak kimlik türünü değiştirme <`identity`> öğesi yapılandırma veya kod kimliği ayarlama. Bir etki alanı adı sistemi (DNS) kimlik değerine sahip aşağıdaki yapılandırma kodunu ayarlar `contoso.com`.  

### <a name="setting-identity-programmatically"></a>Kimlik programlı olarak ayarlama  
 WCF formu otomatik olarak belirlediğinden hizmetiniz bir kimlik açıkça belirtmek yok. Ancak, WCF, bir kimlik bir uç nokta belirtmek gerekirse sağlar. Aşağıdaki kod, belirli bir DNS kimliği ile yeni bir hizmet uç noktası ekler.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)

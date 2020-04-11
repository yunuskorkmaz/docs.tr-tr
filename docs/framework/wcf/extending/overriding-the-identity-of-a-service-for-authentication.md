---
title: Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: e7273c1e140e52eb37a30b6cabeb9e9a83a6fa2d
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121553"
---
# <a name="override-the-identity-of-a-service-for-authentication"></a>Kimlik doğrulama için bir hizmetin kimliğini geçersiz kılma

Genellikle, istemci kimlik bilgisi türü seçimi hizmet meta verilerinde açığa çıkan kimlik türünü belirlediğinden, bir hizmette kimliği ayarlamanız gerekmez. Örneğin, aşağıdaki yapılandırma kodu [ \<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) öğesini `clientCredentialType` kullanır ve Windows özniteliğini ayarlar.  

 Aşağıdaki Web Hizmetleri Açıklama Dili (WSDL) parçası, daha önce tanımlanan bitiş noktasının kimliğini gösterir. Bu örnekte, hizmet belirli bir kullanıcı hesabı altında kendiusername@contoso.comkendine barındırılan bir hizmet olarak çalışıyor ( ) ve bu nedenle kullanıcı anaadı (UPN) kimliği hesap adını içerir. UPN, windows etki alanında kullanıcı oturum açma adı olarak da bilinir.  

 Kimlik ayarını gösteren örnek bir uygulama için [Hizmet Kimliği Örneği'ne](../samples/service-identity-sample.md)bakın. Hizmet kimliği hakkında daha fazla bilgi için [Hizmet Kimliği ve Kimlik Doğrulama'ya](../feature-details/service-identity-and-authentication.md)bakın.  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos Kimlik Doğrulama ve Kimlik  
 Varsayılan olarak, bir hizmet Windows kimlik bilgilerini kullanacak şekilde yapılandırıldığında, WSDL'de [ \<userPrincipalName>](../../configure-apps/file-schema/wcf/userprincipalname.md) veya [ \<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) öğesi içeren bir [ \<kimlik>](../../configure-apps/file-schema/wcf/identity.md) öğesi oluşturulur. `LocalSystem`Hizmet `LocalService`, , veya `NetworkService` hesap altında çalışıyorsa, bu hesaplar bilgisayarın SPN verilerine `host/` \<erişebildiği için varsayılan olarak *ana bilgisayar adı*> şeklinde bir hizmet anaadı (SPN) oluşturulur. Hizmet farklı bir hesap altında çalışıyorsa, Windows Communication Foundation (WCF) \< *kullanıcı adı*>@<*alan adı*`>`şeklinde bir UPN oluşturur. Bunun nedeni, Kerberos kimlik doğrulaması, hizmetin kimliğini doğrulamak için istemciye bir UPN veya SPN sağlanmasını gerektirdiğinden oluşur.  
  
 Bir etki alanında bir hizmetin hesabına ek bir SPN kaydetmek için [Setspn](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731241(v=ws.10)?redirectedfrom=MSDN) aracını da kullanabilirsiniz. Daha sonra Hizmetin kimliği olarak SPN kullanabilirsiniz. Araç hakkında daha fazla bilgi için [Setspn Genel Bakış'a](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))bakın.  
  
> [!NOTE]
> Windows kimlik bilgisi türünü anlaşma olmadan kullanmak için, hizmetin kullanıcı hesabının Active Directory etki alanına kayıtlı SPN erişimi olmalıdır. Bunu aşağıdaki şekillerde yapabilirsiniz:  
  
- Hizmetinizi çalıştırmak için NetworkService veya LocalSystem hesabını kullanın. Bu hesaplar, makine Active Directory etki alanına katıldığında kurulan makine SPN'sine erişebildiği için, WCF hizmetin meta verilerinde (WSDL) hizmetin bitiş noktası içinde uygun SPN öğesini otomatik olarak oluşturur.  
  
- Hizmetinizi çalıştırmak için rasgele bir Active Directory etki alanı hesabı kullanın. Bu durumda, setspn.exe yardımcı programı aracını kullanarak yapabileceğiniz bu etki alanı hesabı için bir SPN belirleyin. Hizmetin hesabı için SPN oluşturduktan sonra, WCF'yi bu SPN'yi meta verileri (WSDL) aracılığıyla hizmetin istemcilerine yayımlayacak şekilde yapılandırın. Bu, bir uygulama yapılandırma dosyası veya kodu aracılığıyla, açıklanmış uç nokta için uç nokta kimliğini ayarlayarak yapılır.  
  
 SPN'ler, Kerberos protokolü ve Active Directory hakkında daha fazla bilgi [için Windows için Kerberos Teknik Eki'ne](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10))bakın.  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>SPN veya UPN Boş Dize Eşit olduğunda  
 SPN veya UPN'yi boş bir dize eşit ayarlarsanız, kullanılan güvenlik düzeyine ve kimlik doğrulama moduna bağlı olarak bir dizi farklı şey olur:  
  
- Aktarım düzeyi güvenliğini kullanıyorsanız, NT LanMan (NTLM) kimlik doğrulaması seçilir.  
  
- İleti düzeyi güvenliği kullanıyorsanız, kimlik doğrulama moduna bağlı olarak kimlik doğrulama başarısız olabilir:  
  
- Modu kullanıyorsanız `spnego` ve `AllowNtlm` öznitelik `false`ayarlanmışsa, kimlik doğrulama başarısız olur.  
  
- Modu kullanıyorsanız `spnego` ve `AllowNtlm` öznitelik `true`ayarlanmışsa, UPN boşsa kimlik doğrulama başarısız olur, ancak SPN boşsa başarılı olur.  
  
- Kerberos direct kullanıyorsanız ("tek çekim" olarak da bilinir), kimlik doğrulama başarısız olur.  
  
### <a name="using-the-identity-element-in-configuration"></a>Yapılandırmada \<> Öğesi'ni kullanma  
 Daha önce Sertifika'da`,` gösterilen bağlamadaki istemci kimlik bilgilerini değiştirirseniz, oluşturulan WSDL, aşağıdaki kodda gösterildiği gibi kimlik değeri için base64 seri leştirilmiş X.509 sertifikası içerir. Bu, Windows dışındaki tüm istemci kimlik bilgileri türleri için varsayılan dır.  

 Yapılandırmada <`identity`> öğesini kullanarak veya kimliği kodda ayarlayarak varsayılan hizmet kimliğinin değerini değiştirebilir veya kimlik türünü değiştirebilirsiniz. Aşağıdaki yapılandırma kodu değeri `contoso.com`ile bir etki alanı adı sistemi (DNS) kimlik ayarlar.  

### <a name="setting-identity-programmatically"></a>Kimlik Programlamalı Olarak Ayar  
 WCF otomatik olarak belirlediğinden, hizmetiniz bir kimliği açıkça belirtmek zorunda değildir. Ancak WCF, gerekirse bir bitiş noktasında bir kimlik belirtmenize olanak tanır. Aşağıdaki kod, belirli bir DNS kimliğine sahip yeni bir hizmet bitiş noktası ekler.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma](how-to-create-a-custom-client-identity-verifier.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](../feature-details/service-identity-and-authentication.md)

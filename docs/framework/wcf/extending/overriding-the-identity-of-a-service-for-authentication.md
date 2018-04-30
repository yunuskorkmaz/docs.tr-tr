---
title: Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f5383a1d241134318ce48c8c0c9f39f831396730
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma
Genellikle, bir istemci kimlik bilgisi türü seçimi hizmet metaveri kimliği türü belirler olduğu bir hizmette kimlik Ayarla gerekmez. Örneğin, aşağıdaki yapılandırma kodunu kullanan [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ve kümelerini `clientCredentialType` özniteliği Windows.  
  
  
  
 Aşağıdaki Web Hizmetleri Açıklama Dili (WSDL) parça kimliği önceden tanımlanmış uç nokta için gösterir. Bu örnekte, belirli bir kullanıcı hesabının altında kendini barındıran hizmet hizmetinin çalıştığı (username@contoso.com) ve bu nedenle kullanıcı asıl adı (UPN) kimlik hesap adını içerir. UPN bir Windows etki alanındaki kullanıcı oturum açma adı da denir.  
  
  
  
 Kimlik ayarı gösteren örnek bir uygulama için bkz: [hizmet kimliği örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md). Hizmet kimliği hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos kimlik doğrulaması ve kimlik  
 Bir hizmeti bir Windows kimlik bilgisi kullanmak için yapılandırıldığında varsayılan olarak, bir [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) içeren öğe bir [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) veya [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) öğesi WSDL içinde oluşturulur. Hizmet altında çalışıyorsa, `LocalSystem`, `LocalService`, veya `NetworkService` hesabı, bir hizmet asıl adı (SPN) biçiminde varsayılan oluşturulur `host/` \< *ana bilgisayar adı*> için Bu hesaplar bilgisayarın SPN veri erişimi. Hizmet başka bir hesap altında çalışıyorsa, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] UPN biçiminde üretir \< *kullanıcıadı*>@<*domainName*`>`. Bu durum, UPN veya SPN bir hizmetin kimliğini istemciye sağlanması Kerberos kimlik doğrulaması gerektiren kaynaklanır.  
  
 Bir hizmetin hesabının bir etki alanındaki ek bir SPN kaydolmak için Setspn.exe Aracı'nı da kullanabilirsiniz. Bu gibi durumlarda, SPN sonra hizmet kimliği olarak kullanabilirsiniz. Aracı indirmek için bkz: [Windows 2000 Kaynak Seti aracı: Setspn.exe](http://go.microsoft.com/fwlink/?LinkId=91752). Aracı hakkında daha fazla bilgi için bkz: [setspn aracına genel bakış](http://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
>  Windows kimlik bilgisi türü anlaşma olmadan kullanmak için hizmetin kullanıcı hesabının Active Directory etki alanı ile kayıtlı SPN erişiminiz olmalıdır. Bunu aşağıdaki yöntemlerle yapabilirsiniz:  
  
-   NetworkService veya LocalSystem hesabı, hizmetinizi çalıştırmak için kullanın. Bu hesapların makine Active Directory etki alanına katıldığında, kurulur SPN makine erişiminiz olduğundan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygun SPN öğe içinde hizmet uç noktası hizmetin meta veriler (WSDL) otomatik olarak oluşturur.  
  
-   Hizmetinizi çalıştırmak için rasgele bir Active Directory etki alanı hesabı kullanın. Bu durumda, Setspn.exe yardımcı programı aracını kullanarak yapabilirsiniz, etki alanı hesabı için bir SPN kurun. Hizmet hesabı SPN'yi oluşturduktan sonra yapılandırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bu SPN hizmetin istemcileri meta verilerini (WSDL) aracılığıyla yayımlamak için. Bu uç noktası kimlik gösterilen uç noktası için bir uygulama yapılandırma dosyası veya kod aracılığıyla ya da ayarlayarak yapılır.  
  
 SPN'ler hakkında daha fazla bilgi, Kerberos protokolü ve Active Directory için bkz: [Kerberos teknik Eki'ni Windows için](http://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Ne zaman boş dize SPN veya UPN'e eşittir  
 SPN veya UPN boş bir dize eşit ayarlarsanız birkaç farklı işlemler, kullanılan güvenlik düzeyini ve kimlik doğrulama modu bağlı olarak gerçekleşir:  
  
-   Aktarım düzeyi güvenlik kullanıyorsanız, NT LanMan (NTLM) kimlik doğrulamasını seçilir.  
  
-   İleti düzeyi güvenlik kullanıyorsanız, kimlik doğrulaması, kimlik doğrulama modu bağlı olarak başarısız olabilir:  
  
-   Kullanıyorsanız `spnego` modu ve `AllowNtlm` özniteliği `false`, kimlik doğrulama başarısız.  
  
-   Kullanıyorsanız `spnego` modu ve `AllowNtlm` özniteliği `true`, UPN boş ancak SPN boşsa, başarılı kimlik doğrulaması başarısız olur.  
  
-   Kullanıyorsanız Kerberos doğrudan (olarak da bilinen "tek adımda"), kimlik doğrulaması başarısız olur.  
  
### <a name="using-the-identity-element-in-configuration"></a>Kullanarak \<kimliği > yapılandırma öğesi  
 Sertifika için daha önce gösterilen bağlamadaki istemci kimlik bilgisi türü değiştirirseniz`,` oluşturulan WSDL seri hale getirilmiş bir Base64 içeriyorsa aşağıdaki kodda gösterildiği gibi kimlik değeri X.509 sertifikası. Bu Windows dışındaki tüm istemci kimlik bilgisi türü için varsayılan değerdir.  
  
  
  
 Varsayılan hizmet kimliği değerini değiştirin ya da kullanarak kimliği türü değiştirme <`identity`> öğesi yapılandırmasında veya kodda kimliği ayarlayarak. Bir etki alanı adı sistemi (DNS) kimlik değeri olan aşağıdaki yapılandırma kodunu ayarlar `contoso.com`.  
  
  
  
### <a name="setting-identity-programmatically"></a>Kimlik programlı olarak ayarlama  
 Çünkü, bir kimlik açıkça belirtmek, hizmet yok. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] otomatik olarak belirler. Ancak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerekli olursa bir uç nokta üzerinde bir kimlik belirtmenize olanak tanır. Aşağıdaki kod, belirli bir DNS kimlik ile yeni bir hizmet uç noktası ekler.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)

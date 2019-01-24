---
title: Windows Kimlik Doğrulama Hatalarını Ayıklama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: a68a291b1974e86c9a4f16f9d90a879649076533
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595142"
---
# <a name="debugging-windows-authentication-errors"></a>Windows Kimlik Doğrulama Hatalarını Ayıklama
Windows kimlik doğrulaması, bir güvenlik mekanizması olarak kullanırken, Güvenlik Desteği Sağlayıcısı Arabirimi (SSPI), güvenlik işlemlerini işler. SSPI katmanında güvenlik hatası meydana geldiğinde, Windows Communication Foundation (WCF) tarafından takip edilir. Bu konu, çerçeve ve hataları tanılamak üzere soruları sağlar.  
  
 Kerberos protokolü genel bakış için bkz. [Kerberos açıklanan](https://go.microsoft.com/fwlink/?LinkID=86946); SSPI, genel bir bakış için bkz [SSPI](https://go.microsoft.com/fwlink/?LinkId=88941).  
  
 WCF genellikle Windows kimlik doğrulaması için kullandığı *anlaş* Kerberos hizmet ve istemci arasında karşılıklı kimlik doğrulaması gerçekleştiren Güvenlik Desteği Sağlayıcısı'ne (SSP). Kerberos protokolü, kullanılabilir durumda değilse, varsayılan olarak WCF NT LAN Manager (NTLM) geri döner. Ancak, WCF yalnızca Kerberos protokolünü kullanma (ve Kerberos mevcut değilse bir özel durum) yapılandırabilirsiniz. Ayrıca kısıtlı Kerberos protokolü biçimlerinin kullanmak için WCF yapılandırabilirsiniz.  
  
## <a name="debugging-methodology"></a>Hata ayıklama yöntemi  
 Temel yöntem aşağıdaki gibidir:  
  
1.  Windows kimlik doğrulaması kullandığınızı belirleyin. Başka bir düzen kullanıyorsanız, bu konuda geçerli değildir.  
  
2.  Windows kimlik doğrulaması kullanıyorsanız eminseniz, WCF yapılandırma doğrudan Kerberos veya anlaşma kullanıp kullanmadığını belirleyin.  
  
3.  Yapılandırmanızı NTLM ve Kerberos protokolünü kullanıp kullanmadığını belirledikten sonra hata iletileri doğru bağlamda anlayabilirsiniz.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>NTLM ve Kerberos protokolü kullanılabilirliği  
 Kerberos SSP Kerberos Anahtar Dağıtım Merkezi (KDC) olarak görev yapacak bir etki alanı denetleyicisi gerektirir. Kerberos protokolü, yalnızca etki alanı kimlikleri hem istemci hem de hizmet kullanırken kullanılabilir. Diğer hesap birleşimler, NTLM, aşağıdaki tabloda özetlendiği gibi kullanılır.  
  
 Olası hesap türleri için sunucu tarafından kullanılan tablo üst bilgileri gösterin. Sol sütunda, istemci tarafından kullanılan olası hesap türleri gösterir.  
  
||Yerel kullanıcı|Yerel Sistem|Domain User|Domain Machine|  
|-|----------------|------------------|-----------------|--------------------|  
|Yerel kullanıcı|NTLM|NTLM|NTLM|NTLM|  
|Yerel Sistem|Anonim NTLM|Anonim NTLM|Anonim NTLM|Anonim NTLM|  
|Domain User|NTLM|NTLM|Kerberos|Kerberos|  
|Domain Machine|NTLM|NTLM|Kerberos|Kerberos|  
  
 Özellikle, dört hesap türleri şunlardır:  
  
-   Yerel kullanıcı: Yalnızca makine kullanıcı profili. Örneğin: `MachineName\Administrator` veya `MachineName\ProfileName`.  
  
-   Yerel sistemi: Bir etki alanına katılmamış bir makinede yerleşik hesap sistem.  
  
-   Etki alanı kullanıcısı: Bir Windows etki alanı kullanıcı hesabı. Örneğin: `DomainName\ProfileName`  
  
-   Makine etki alanı: Makine kimliğini bir Windows etki alanına katılmış bir makinede çalışan bir işlem. Örneğin: `MachineName\Network Service`  
  
> [!NOTE]
>  Hizmet kimlik bilgisi yakalanan olduğunda <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi <xref:System.ServiceModel.ServiceHost> sınıfı çağrılır. İstemci kimlik bilgilerini okuma her istemciye bir ileti gönderir.  
  
## <a name="common-windows-authentication-problems"></a>Ortak Windows kimlik doğrulama sorunları  
 Bu bölümde, bazı ortak Windows kimlik doğrulama sorunları ve olası çözümler ele alınmaktadır.  
  
### <a name="kerberos-protocol"></a>Kerberos protokolü  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Kerberos protokolü SPN/UPN sorunları  
 Windows kimlik doğrulaması ve Kerberos protokolü kullanılan ya da SSPI tarafından anlaşılan kullanırken, istemci uç noktası kullandığı URL'yi hizmetin ana bilgisayar hizmeti URL içinde tam etki alanı adı içermelidir. Bu hizmetin altında çalıştığı hesabın altında hizmete çalıştırarak en yaygın olarak yapılır Active Directory etki alanına bilgisayar eklendiğinde, oluşturulan makine (varsayılan) hizmet asıl adı (SPN) anahtarı erişimi olduğunu varsayar. Ağ hizmeti hesabı. Hizmet makine SPN anahtarına erişimi yoksa, hizmet, istemcinin uç nokta kimliğinde çalıştırıldığı hesabın doğru SPN veya kullanıcı asıl adı (UPN) sağlamanız gerekir. WCF SPN ve UPN ile nasıl çalıştığı hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 Yük Dengeleme, Web grupları veya Web bahçelerinde gibi senaryoları yaygın bir uygulamadır her uygulama için benzersiz bir hesabı tanımlamak, SPN'yi ilgili hesabı atama ve bu hesapta bulunan tüm uygulama hizmetlerini çalıştırdığınızdan emin olun.  
  
 Hizmet hesabı için bir SPN elde etmek için bir Active Directory etki alanı yöneticisi olmanız gerekir. Daha fazla bilgi için [Kerberos teknik ek Windows için](https://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Kerberos protokolü doğrudan hizmeti bir etki alanı makine hesabı altında çalıştırılacak gerektirir  
 Böyle durumlarda `ClientCredentialType` özelliği `Windows` ve <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> özelliği `false`aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Çözümü, bir etki alanında ağ hizmeti gibi bir etki alanı makine hesabı kullanarak hizmeti çalıştırmak için makine katıldı.  
  
### <a name="delegation-requires-credential-negotiation"></a>Kimlik bilgileri görüşmesi temsilci gerektirir  
 Temsilci ile Kerberos kimlik doğrulama protokolünü kullanmak için Kerberos protokolü ile kimlik bilgileri görüşmesi (bazen "çok oluşturan" veya "çok adımlı" Kerberos denir) uygulamalıdır. Kerberos kimlik doğrulaması (bazen "kesin" veya "oluşturan tek" Kerberos denir) kimlik bilgileri görüşmesi uygularsanız, bir özel durum oluşturulur.  
  
 Kerberos ile kimlik bilgileri görüşmesi uygulamak için aşağıdaki adımları uygulayın:  
  
1.  Uygulama temsilcisi ayarlayarak <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> için <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2.  SSPI anlaşması gerektirir:  
  
    1.  Standart bağlamaları kullanıyorsanız `NegotiateServiceCredential` özelliğini `true`.  
  
    2.  Özel bağlamalar kullanıyorsanız `AuthenticationMode` özniteliği `Security` öğesine `SspiNegotiated`.  
  
3.  Kerberos, NTLM kullanımını engelleyerek kullanmak için SSPI anlaşması gerektirir:  
  
    1.  Bu kodda, aşağıdaki deyimi yapın: `ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2.  Veya yapılandırma dosyasında ayarlayarak bunu yapabilirsiniz `allowNtlm` özniteliğini `false`. Bu öznitelik bulunan [ \<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>NTLM protokolü  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Anlaşma geri NTLM SSP döner, ancak NTLM devre dışıdır  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> Özelliği `false`, bir NTLM kullanılırsa, bir özel durum için mümkün olan en iyi hale getirmek için Windows Communication Foundation (WCF) neden olur. Unutmayın, bu özelliği ayarlamak `false` NTLM kimlik bilgileri kablo üzerinden gönderilen engelleyemeyebilir.  
  
 Geri dönüş için NTLM devre dışı bırakma gösterir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>NTLM oturum açma başarısız  
 İstemci kimlik bilgileri, hizmette geçerli değildir. Kullanıcı adını ve parolasını doğru ayarlandığından ve hizmetin çalıştığı bilgisayarda bilinen bir hesaba karşılık denetleyin. NTLM, hizmetin bilgisayarda oturum açmak için belirtilen kimlik bilgilerini kullanır. Kimlik bilgilerini istemci çalıştığı bilgisayarda geçerli olabilir, ancak kimlik bilgileri, hizmetin bilgisayarda geçerli değil. Bu oturum açma başarısız olur.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Anonim bir NTLM oturum açma gerçekleşir, ancak anonim oturum açma işlemi olan varsayılan olarak devre dışı  
 Bir istemci oluştururken <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>sunucu izin vermiyor anonim oturum açma işlemi aşağıdaki örnekte, ancak varsayılan olarak gösterildiği gibi. Bu durum oluşur varsayılan değeri <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> özelliği <xref:System.ServiceModel.Security.WindowsServiceCredential> sınıfı `false`.  
  
 Aşağıdaki istemci kodu, anonim olarak oturum açmayı etkinleştirmeniz dener (varsayılan özellik Not `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Aşağıdaki hizmet kodu, sunucu tarafından anonim olarak oturum açmayı etkinleştirmeniz varsayılan değiştirir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Kimliğe bürünme hakkında daha fazla bilgi için bkz. [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Alternatif olarak, istemci, yerleşik sistem hesabı kullanılarak bir Windows hizmeti olarak çalıştırılır.  
  
### <a name="other-problems"></a>Diğer sorunlar  
  
#### <a name="client-credentials-are-not-set-correctly"></a>İstemci kimlik bilgileri doğru ayarlanmadı  
 Windows kimlik doğrulaması kullanan <xref:System.ServiceModel.Security.WindowsClientCredential> tarafından döndürülen örnek <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı değil, <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. Aşağıda, yanlış bir örnek gösterilmektedir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 Doğru örnek gösterir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>SSPI kullanılamıyor  
 Aşağıdaki işletim sistemleri, bir sunucu olarak kullanıldığında Windows kimlik doğrulamasını desteklemez: [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition ve [!INCLUDE[wv](../../../../includes/wv-md.md)]Home sürümleri.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Geliştirme ve farklı kimlikler ile dağıtma  
 Bir makine, uygulama geliştirmek ve başka dağıtma ve farklı hesap türlerinin her makinede kimlik doğrulaması için kullanmak, farklı bir davranış karşılaşabilirsiniz. Örneğin, Windows XP Pro makine kullanarak uygulamanızı geliştirdiğiniz varsayalım `SSPI Negotiated` kimlik doğrulama modu. Kimlik doğrulaması yapmak için bir yerel kullanıcı hesabı kullanıyorsanız, NTLM protokolü kullanılır. Uygulamanın geliştirilme yöntemi sonra etki alanı hesabı altında çalıştığı Windows Server 2003 makineye hizmeti dağıtın. Bu noktada istemci Kerberos ve bir etki alanı denetleyicisi kullanacak için hizmet kimlik doğrulaması mümkün olmayacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)

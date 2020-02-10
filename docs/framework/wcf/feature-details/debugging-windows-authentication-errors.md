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
ms.openlocfilehash: 4a5e56f6b7f33a4c6f29aa384635737eeee37ddd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095040"
---
# <a name="debug-windows-authentication-errors"></a>Windows kimlik doğrulama hatalarını ayıklama

Windows kimlik doğrulamasını bir güvenlik mekanizması olarak kullanırken, güvenlik desteği sağlayıcısı arabirimi (SSPI) güvenlik süreçlerini işler. SSPI katmanında güvenlik hataları oluştuğunda, bunlar Windows Communication Foundation (WCF) ile ortaya çıkar. Bu konu, hataları tanılamanıza yardımcı olmak için bir çerçeve ve soru kümesi sağlar.  
  
 Kerberos protokolüne genel bakış için bkz. [Kerberos açıklanıyor](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10)); SSPI 'ye genel bakış için bkz. [SSPI](/windows/win32/secauthn/sspi).  
  
 WCF, Windows kimlik doğrulaması için genellikle istemci ve hizmet arasında Kerberos karşılıklı kimlik doğrulaması gerçekleştiren *Negotiate* güvenlik desteği sağlayıcısı 'Nı (SSP) kullanır. Kerberos protokolü kullanılamıyorsa, varsayılan olarak WCF, NT LAN Manager 'a (NTLM) geri döner. Ancak, WCF 'yi yalnızca Kerberos protokolünü kullanacak şekilde yapılandırabilirsiniz (ve Kerberos kullanılamıyorsa bir özel durum oluşturur). WCF 'yi, Kerberos protokolünün kısıtlı biçimlerini kullanacak şekilde de yapılandırabilirsiniz.  
  
## <a name="debugging-methodology"></a>Hata ayıklama yöntemi  
 Temel yöntem aşağıdaki gibidir:  
  
1. Windows kimlik doğrulaması kullanıp kullanmayacağınızı belirleme. Başka bir düzen kullanıyorsanız, bu konu uygulanmaz.  
  
2. Windows kimlik doğrulamasını kullandığınızdan eminseniz, WCF yapılandırmanızın Kerberos Direct veya Negotiate kullanıp kullanmadığını saptayın.  
  
3. Yapılandırmanızın Kerberos protokolünü mi yoksa NTLM mi kullandığını belirledikten sonra, hata iletilerini doğru bağlamda anlayabilirsiniz.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Kerberos protokolünün ve NTLM 'nin kullanılabilirliği  
 Kerberos SSP, Kerberos Anahtar Dağıtım Merkezi (KDC) olarak görev yapması için bir etki alanı denetleyicisi gerektirir. Kerberos protokolü yalnızca, istemci ve hizmet etki alanı kimliklerini kullanıyorsa kullanılabilir. Diğer hesap birleşimlerinde, aşağıdaki tabloda özetlenen NTLM kullanılır.  
  
 Tablo üstbilgileri sunucu tarafından kullanılan olası hesap türlerini gösterir. Sol sütunda istemci tarafından kullanılan olası hesap türleri görüntülenir.  
  
||Yerel Kullanıcı|Yerel Sistem|Etki alanı kullanıcısı|Etki alanı makinesi|  
|-|----------------|------------------|-----------------|--------------------|  
|Yerel Kullanıcı|NT|NT|NT|NT|  
|Yerel Sistem|Anonim NTLM|Anonim NTLM|Anonim NTLM|Anonim NTLM|  
|Etki alanı kullanıcısı|NT|NT|Kerberos|Kerberos|  
|Etki alanı makinesi|NT|NT|Kerberos|Kerberos|  
  
 Özellikle, dört hesap türü şunları içerir:  
  
- Yerel Kullanıcı: yalnızca makine Kullanıcı profili. Örneğin: `MachineName\Administrator` veya `MachineName\ProfileName`.  
  
- Yerel Sistem: bir etki alanına katılmamış bir makinedeki yerleşik hesap SISTEMI.  
  
- Etki alanı kullanıcısı: Windows etki alanındaki bir kullanıcı hesabı. Örneğin: `DomainName\ProfileName`.  
  
- Etki alanı makinesi: bir Windows etki alanına katılmış bir makinede çalışan makine kimliğine sahip bir işlem. Örneğin: `MachineName\Network Service`.  
  
> [!NOTE]
> <xref:System.ServiceModel.ServiceHost> sınıfının <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi çağrıldığında hizmet kimlik bilgisi yakalanır. İstemci bir ileti gönderdiğinde istemci kimlik bilgileri okundu.  
  
## <a name="common-windows-authentication-problems"></a>Yaygın Windows kimlik doğrulama sorunları  
 Bu bölümde bazı yaygın Windows kimlik doğrulama sorunları ve olası düzeltmeler açıklanmaktadır.  
  
### <a name="kerberos-protocol"></a>Kerberos protokolü  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Kerberos protokolüyle SPN/UPN sorunları  
 Windows kimlik doğrulaması kullanılırken ve Kerberos protokolü SSPI tarafından kullanıldığında veya anlaşılırsa, istemci uç noktasının kullandığı URL, hizmet URL 'SI içindeki hizmetin ana bilgisayarının tam etki alanı adını içermelidir. Bu, hizmetin çalıştığı hesabın, bilgisayar Active Directory etki alanına eklendiğinde oluşturulan makine (varsayılan) hizmet asıl adı (SPN) anahtarına erişim sahibi olduğunu varsayar; bu, en yaygın olarak hizmetin Ağ hizmeti hesabı. Hizmetin, makine SPN anahtarına erişimi yoksa, istemcinin uç nokta kimliğinde hizmetin çalıştığı hesabın doğru SPN 'sini veya Kullanıcı asıl adını (UPN) sağlamanız gerekir. WCF 'nin SPN ve UPN ile nasıl çalıştığı hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 Web grupları veya Web bahçeleri gibi yük dengeleme senaryolarında, yaygın bir yöntem her bir uygulama için benzersiz bir hesap tanımlamak, bu hesaba bir SPN atamak ve tüm uygulama hizmetlerinin bu hesapta çalıştığından emin olmak içindir.  
  
 Hizmetinizin hesabı için bir SPN elde etmek üzere bir Active Directory etki alanı yöneticisi olmanız gerekir. Daha fazla bilgi için bkz. [Windows Için Kerberos teknik eki](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Kerberos protokolü doğrudan, hizmetin bir etki alanı makine hesabı altında çalışmasını gerektirir  
 Bu, `ClientCredentialType` özelliği `Windows` olarak ayarlandığında ve <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> özelliği aşağıdaki kodda gösterildiği gibi `false`olarak ayarlandığında oluşur.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Sorunu gidermek için, etki alanına katılmış bir makinede ağ hizmeti gibi bir etki alanı makine hesabı kullanarak hizmeti çalıştırın.  
  
### <a name="delegation-requires-credential-negotiation"></a>Temsili kimlik bilgisi anlaşması gerektirir  
 Kerberos kimlik doğrulama protokolünü temsilcisiyle birlikte kullanmak için, Kerberos protokolünü kimlik bilgisi anlaşmasına uygulamanız gerekir (bazen "Multi-BAI" veya "multi-step" Kerberos olarak adlandırılır). Kimlik bilgisi anlaşması olmadan Kerberos kimlik doğrulaması uygularsanız (bazen "tek bir görüntü" veya "tek seferlik" Kerberos olarak adlandırılır), bir özel durum oluşturulur.  
  
 Kimlik bilgisi anlaşmasına sahip Kerberos uygulamak için aşağıdaki adımları uygulayın:  
  
1. <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>olarak ayarlayarak temsilciyi uygulayın.  
  
2. SSPI anlaşması gerektir:  
  
    1. Standart bağlamalar kullanıyorsanız, `NegotiateServiceCredential` özelliğini `true`olarak ayarlayın.  
  
    2. Özel Bağlamalar kullanıyorsanız, `Security` öğesinin `AuthenticationMode` özniteliğini `SspiNegotiated`olarak ayarlayın.  
  
3. NTLM kullanımını engelleyerek SSPI anlaşmasının Kerberos kullanması gerekir:  
  
    1. Aşağıdaki ifadesiyle kodda bunu yapın: `ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2. Ya da bunu yapılandırma dosyasında `allowNtlm` özniteliğini `false`olarak ayarlayarak yapabilirsiniz. Bu öznitelik [\<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)bulunur.  
  
### <a name="ntlm-protocol"></a>NTLM protokolü  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Negotiate SSP, NTLM 'ye geri döner, ancak NTLM devre dışı bırakılır  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> özelliği, NTLM kullanılıyorsa, Windows Communication Foundation (WCF) bir özel durum oluşturmak için en iyi çaba oluşturulmasına neden olan `false`olarak ayarlanır. Bu özelliğin `false` olarak ayarlanması, NTLM kimlik bilgilerinin kablo üzerinden gönderilmesini engelleyemeyebilir.  
  
 Aşağıda, NTLM 'ye geri dönüşü devre dışı bırakma gösterilmektedir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>NTLM oturum açma başarısız  
 İstemci kimlik bilgileri hizmette geçerli değil. Kullanıcı adının ve parolanın doğru şekilde ayarlandığından ve hizmetin çalıştığı bilgisayar tarafından bilinen bir hesaba karşılık geldiğinden emin olun. NTLM, hizmetin bilgisayarında oturum açmak için belirtilen kimlik bilgilerini kullanır. Kimlik bilgileri, istemcinin çalıştırıldığı bilgisayarda geçerli olabilir, ancak kimlik bilgileri hizmetin bilgisayarında geçerli değilse bu oturum açma işlemi başarısız olur.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Anonim NTLM oturum açma oluşur, ancak anonim oturum açma Işlemleri varsayılan olarak devre dışıdır  
 İstemci oluştururken, aşağıdaki örnekte gösterildiği gibi <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>olarak ayarlanır, ancak varsayılan olarak sunucu anonim oturum açma işlemlerine izin vermez. Bu, <xref:System.ServiceModel.Security.WindowsServiceCredential> sınıfının <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> özelliğinin varsayılan değeri `false`olduğu için oluşur.  
  
 Aşağıdaki istemci kodu anonim oturum açmaları etkinleştirmeye çalışır (varsayılan özelliğin `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Aşağıdaki hizmet kodu, sunucu tarafından adsız oturum açmaları etkinleştirmek için varsayılan ayarı değiştirir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Kimliğe bürünme hakkında daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Alternatif olarak, istemci yerleşik hesap SISTEMINI kullanarak bir Windows hizmeti olarak çalışır.  
  
### <a name="other-problems"></a>Diğer Sorunlar  
  
#### <a name="client-credentials-are-not-set-correctly"></a>İstemci kimlik bilgileri doğru ayarlanmadı  
 Windows kimlik doğrulaması, <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>değil <xref:System.ServiceModel.ClientBase%601> sınıfının <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği tarafından döndürülen <xref:System.ServiceModel.Security.WindowsClientCredential> örneğini kullanır. Aşağıda yanlış bir örnek gösterilmektedir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 Aşağıda doğru örnek gösterilmektedir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>SSPI kullanılamıyor  
 Aşağıdaki işletim sistemleri, sunucu olarak kullanıldığında Windows kimlik doğrulamasını desteklemez: Windows XP Home Edition, Windows XP Media Center Edition ve Windows Vista Home Edition.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Farklı kimliklerle geliştirme ve dağıtma  
 Uygulamanızı tek bir makinede geliştirir ve başka bir makineye dağıtırsanız ve her makinede kimlik doğrulamak için farklı hesap türleri kullanırsanız, farklı davranışlar yaşayabilirsiniz. Örneğin, `SSPI Negotiated` kimlik doğrulama modunu kullanarak uygulamanızı bir Windows XP Pro makinesi üzerinde geliştirdiğinizi varsayalım. Kimlik doğrulaması için yerel bir kullanıcı hesabı kullanıyorsanız, NTLM protokolü kullanılacaktır. Uygulama geliştirildikten sonra, hizmeti bir etki alanı hesabı altında çalıştığı bir Windows Server 2003 makinesine dağıtırsınız. Bu noktada, istemci Kerberos ve bir etki alanı denetleyicisi kullandığından hizmetin kimliğini doğrulayamayacak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)

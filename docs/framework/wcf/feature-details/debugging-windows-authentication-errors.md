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
ms.openlocfilehash: d9226324b69e5c27738abb35bb155a43964b9127
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-windows-authentication-errors"></a>Windows Kimlik Doğrulama Hatalarını Ayıklama
Windows kimlik doğrulaması bir güvenlik mekanizması olarak kullanırken, Güvenlik Desteği Sağlayıcısı Arabirimi (SSPI) güvenlik işlemleri işler. SSPI katmanında güvenlik hatası meydana geldiğinde, bunlar Windows Communication Foundation (WCF) tarafından çıkmış. Bu konu, hataları tanılamak için sorularını kümesi ve bir çerçeve sağlar.  
  
 Kerberos protokolü genel bakış için bkz: [Kerberos açıklandığı](http://go.microsoft.com/fwlink/?LinkID=86946); SSPI, genel bir bakış için bkz [SSPI](http://go.microsoft.com/fwlink/?LinkId=88941).  
  
 Windows kimlik doğrulaması için WCF genellikle kullandığı *anlaş* Kerberos hizmet ve istemci arasında karşılıklı kimlik doğrulaması gerçekleştiren Güvenlik Desteği Sağlayıcısı'ne (SSP). Kerberos protokolü kullanılabilir durumda değilse, varsayılan olarak WCF NT LAN Yöneticisi (NTLM) geri döner. Ancak, WCF yalnızca Kerberos protokolünü kullanır (ve Kerberos kullanılabilir değilse, bir özel durum) yapılandırabilirsiniz. Kerberos protokolünün Kısıtlanmış formlar kullanmak için WCF da yapılandırabilirsiniz.  
  
## <a name="debugging-methodology"></a>Hata ayıklama yöntemi  
 Temel yöntemi aşağıdaki gibidir:  
  
1.  Windows kimlik doğrulaması kullanarak olup olmadığını belirler. Başka bir düzen kullanıyorsanız, bu konuda geçerli değildir.  
  
2.  Windows kimlik doğrulaması kullanıyorsanız eminseniz, WCF yapılandırmanızı Kerberos doğrudan veya anlaşma kullanıp kullanmadığını belirleyin.  
  
3.  Yapılandırmanızı NTLM ve Kerberos protokolünü kullanarak belirledikten sonra hata iletileri doğru bağlamında anlayabilirsiniz.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>NTLM ve Kerberos protokolü kullanılabilirliği  
 Kerberos SSP Kerberos Anahtar Dağıtım Merkezi (KDC) olarak hareket edecek bir etki alanı denetleyicisi gerektirir. Kerberos protokolü, yalnızca etki alanı kimlikleri hem istemci hem de hizmet kullanırken kullanılabilir. Diğer hesap bileşimlerde NTLM, aşağıdaki tabloda özetlendiği gibi kullanılır.  
  
 Tablo üstbilgileri olası hesap türleri için sunucu tarafından kullanılan gösterir. Sol sütunda, istemci tarafından kullanılan olası hesap türünü gösterir.  
  
||Yerel kullanıcı|Yerel Sistem|Etki alanı kullanıcısı|Etki alanı makine|  
|-|----------------|------------------|-----------------|--------------------|  
|Yerel kullanıcı|NTLM|NTLM|NTLM|NTLM|  
|Yerel Sistem|Anonim NTLM|Anonim NTLM|Anonim NTLM|Anonim NTLM|  
|Etki alanı kullanıcısı|NTLM|NTLM|Kerberos|Kerberos|  
|Etki alanı makine|NTLM|NTLM|Kerberos|Kerberos|  
  
 Özellikle, dört hesap türleri şunlardır:  
  
-   Yerel kullanıcı: Yalnızca makine kullanıcı profili. Örneğin: `MachineName\Administrator` veya `MachineName\ProfileName`.  
  
-   : Yerel yerleşik sistem Hesabını sistemi bir etki alanına katılmamış bir makinede.  
  
-   Etki alanı kullanıcısı: Bir Windows etki alanı kullanıcı hesabı. Örneğin: `DomainName\ProfileName`.  
  
-   Etki alanı makine: Makine kimliğini bir Windows etki alanına katılmış bir makinede çalışan bir işlem. Örneğin: `MachineName\Network Service`.  
  
> [!NOTE]
>  Hizmet kimlik bilgilerini yakalanan zaman <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi <xref:System.ServiceModel.ServiceHost> sınıfı çağrılır. İstemci kimlik bilgileri okuyun her istemci bir ileti gönderir.  
  
## <a name="common-windows-authentication-problems"></a>Genel Windows kimlik doğrulama sorunları  
 Bu bölümde bazı yaygın Windows kimlik doğrulama sorunları ve olası çözümler açıklanmaktadır.  
  
### <a name="kerberos-protocol"></a>Kerberos protokolü  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Kerberos protokolü SPN/UPN sorunları  
 Windows kimlik doğrulaması ve Kerberos protokolü kullanılan veya SSPI tarafından anlaşılan kullanırken, istemci uç nokta kullandığı URL'yi hizmetin konak hizmeti URL'si içinde tam olarak nitelenmiş etki alanı adını içermelidir. Bu hizmetinin altında çalıştığı hesabın en yaygın olarak hizmetin altında çalıştırılarak yapılır Active Directory etki alanına bilgisayar eklendiğinde oluşturduğunuz makine (varsayılan) hizmet asıl adı (SPN) anahtarı erişimi olduğunu varsayar. Ağ hizmeti hesabı. Hizmet makine SPN anahtarına erişimi yoksa, istemcinin uç noktası kimlik hizmetin çalıştığı hesabın doğru SPN veya kullanıcı asıl adı (UPN) sağlamanız gerekir. WCF SPN ve UPN ile nasıl çalıştığı hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 Yük Dengeleme içindeki Web grupları veya Web bahçelerinde gibi senaryolara yaygın bir uygulamadır her uygulama için benzersiz bir hesap tanımlayın, bu hesap için bir SPN atayın ve bu hesabın tüm uygulama hizmetleri çalıştırdığınızdan emin olun.  
  
 Hizmet hesabı için bir SPN elde etmek için bir Active Directory etki alanı yöneticisi olmanız gerekir. Daha fazla bilgi için bkz: [Kerberos teknik Eki'ni Windows için](http://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Kerberos protokolü doğrudan bir etki alanı makine hesabı altında Çalıştır hizmetine gerektirir  
 Bu meydana zaman `ClientCredentialType` özelliği ayarlanmış `Windows` ve <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> özelliği ayarlanmış `false`aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Sorunu gidermek için bir etki alanında ağ hizmeti gibi bir etki alanı makine hesabı kullanarak hizmeti çalıştırın makine katıldı.  
  
### <a name="delegation-requires-credential-negotiation"></a>Kimlik bilgileri görüşmesi temsilci gerektirir  
 Temsilci ile Kerberos kimlik doğrulama protokolünü kullanmak için Kerberos protokolü (bazen "çok leg" veya "çok adımlı" Kerberos denir) kimlik bilgileri görüşmesi ile uygulamanız gerekir. Kerberos kimlik doğrulaması (bazen "tek adımda" veya "tek leg" Kerberos denir) kimlik bilgileri görüşmesi uygularsanız, bir özel durum.  
  
 Kerberos ile kimlik bilgileri görüşmesi uygulamak için aşağıdaki adımları uygulayın:  
  
1.  Uygulama temsilci ayarlayarak <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> için <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2.  SSPI anlaşması gerektirir:  
  
    1.  Standart bağlamaları kullanıyorsanız ayarlamak `NegotiateServiceCredential` özelliğine `true`.  
  
    2.  Özel bağlamalar kullanıyorsanız ayarlamak `AuthenticationMode` özniteliği `Security` öğesine `SspiNegotiated`.  
  
3.  Kerberos, NTLM kullanımını engelleyerek kullanmak için SSPI anlaşması gerektirir:  
  
    1.  Bu kod, aşağıdaki deyim ile yapın: `ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2.  Veya yapılandırma dosyasında ayarlayarak bunu yapabilirsiniz `allowNtlm` özniteliğini `false`. Bu öznitelik yer [ \<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>NTLM protokolü  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Geri NTLM SSP döner anlaşma ancak NTLM devre dışı  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> Özelliği ayarlanmış `false`, NTLM kullanılırsa, bir özel durum için bir en iyi çaba yapmak için Windows Communication Foundation (WCF) neden olur. Bu özelliği ayarlamak Not `false` NTLM kimlik bilgileri kablo üzerinden gönderilen engelleyebilir değil.  
  
 Geri dönüş için NTLM devre dışı bırakma gösterir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>NTLM oturum açma başarısız  
 İstemci kimlik bilgileri üzerindeki hizmeti geçerli değil. Kullanıcı adı ve parola doğru ayarlandığından ve hizmetin çalıştığı bilgisayara bilinen bir hesaba karşılık denetleyin. NTLM, hizmetin bilgisayara oturum açmak için belirtilen kimlik bilgilerini kullanır. Kimlik bilgileri istemci çalıştığı bilgisayarda geçerli olabilir, ancak kimlik hizmetin bilgisayarda geçerli değilse bu oturum açma başarısız olur.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Anonim NTLM oturum açma oluşur, ancak anonim oturum açma olan varsayılan olarak devre dışı  
 Bir istemci oluştururken <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği ayarlanmış <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>sunucu anonim oturum açma izin vermez aşağıdaki örnekte, ancak varsayılan olarak gösterildiği gibi. Bu kaynaklanır varsayılan değerini <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> özelliği <xref:System.ServiceModel.Security.WindowsServiceCredential> sınıfı `false`.  
  
 Anonim oturumları etkinleştirmek aşağıdaki istemci kodu çalışır (varsayılan özellik olduğuna dikkat edin `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Aşağıdaki hizmet kodu sunucu tarafından anonim oturumları etkinleştirmek için varsayılan değiştirir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Kimliğe bürünme hakkında daha fazla bilgi için bkz: [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Alternatif olarak, istemci, yerleşik sistem hesabı kullanarak bir Windows hizmet olarak çalışıyor.  
  
### <a name="other-problems"></a>Diğer sorunlar  
  
#### <a name="client-credentials-are-not-set-correctly"></a>İstemci kimlik bilgileri düzgün bir şekilde ayarlanmadı  
 Windows kimlik doğrulamasını kullanan <xref:System.ServiceModel.Security.WindowsClientCredential> tarafından döndürülen örnek <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı değil, <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. Yanlış bir örnek gösterilmektedir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 Doğru örnek gösterilmektedir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>SSPI kullanılamıyor  
 Aşağıdaki işletim sistemlerinden bir sunucu olarak kullanıldığında Windows kimlik doğrulamasını desteklemez: [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition ve [!INCLUDE[wv](../../../../includes/wv-md.md)]Home sürümleri.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Geliştirme ve farklı kimliklerle dağıtma  
 Tek bir makinede uygulamanızı geliştirin ve başka dağıtırsanız ve her makinede kimlik doğrulaması için farklı bir hesap türleri kullanın, farklı bir davranış karşılaşabilirsiniz. Örneğin, Windows XP Pro makine kullanarak uygulamanızı geliştirin varsayalım `SSPI Negotiated` kimlik doğrulama modu. Kimlik doğrulaması yapmak için yerel bir kullanıcı hesabı kullanırsanız, NTLM protokolü kullanılır. Uygulama geliştirilen sonra bir etki alanı hesabı altında çalıştığı bir Windows Server 2003 makineye hizmetini dağıtın. Bu noktada istemci Kerberos ve bir etki alanı denetleyicisi kullanacak çünkü hizmetin kimliğini olmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)

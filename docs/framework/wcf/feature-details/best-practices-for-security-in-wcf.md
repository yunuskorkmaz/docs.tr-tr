---
title: WCF'de Güvenlik için En İyi Uygulamalar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
ms.openlocfilehash: c8c0c084ac3b1cf06fc5f2b3df85fa979744e17b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185413"
---
# <a name="best-practices-for-security-in-wcf"></a>WCF'de Güvenlik için En İyi Uygulamalar
Aşağıdaki bölümlerde, Windows Communication Foundation (WCF) kullanılarak güvenli uygulamalar oluşturulurken göz önünde bulundurulması gereken en iyi uygulamalar listelenmiştir. Güvenlik hakkında daha fazla bilgi için bkz: [Güvenlik Hususları,](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) [Veriler için Güvenlik Hususları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)ve Meta [verilerle Güvenlik Hususları.](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>SPN'lerle Windows Kimlik Doğrulaması Gerçekleştiren Hizmetleri Belirleme  
 Hizmetler, kullanıcı ana adı (UPNs) veya hizmet temel adları (SPNs) ile tanımlanabilir. Ağ hizmeti gibi makine hesapları altında çalışan hizmetlerin, çalıştırdıkları makineye karşılık gelen bir SPN kimliği vardır. Kullanıcı hesapları altında çalışan hizmetler, kullanıcı hesabına bir SPN `setspn` atamak için kullanılabilse de, çalıştıkları kullanıcıya karşılık gelen bir UPN kimliğine sahiptir. Bir hizmeti SPN üzerinden tanımlanabilecek şekilde yapılandırmak ve hizmete bağlanan istemcileri SPN'nin belirli saldırıları zorlaştırabileceği şekilde kullanmak üzere yapılandırmak. Bu kılavuz, Kerberos veya SSPI anlaşması kullanan bağlayıcılar için geçerlidir.  İstemciler, SSPI'nin NTLM'ye geri düştüğü durumlarda yine de bir SPN belirtmelidir.  
  
## <a name="verify-service-identities-in-wsdl"></a>WSDL'deki Hizmet Kimliklerini Doğrula  
 WS-SecurityPolicy, hizmetlerin meta verilerde kendi kimlikleri hakkında bilgi yayımlamasına olanak tanır. Bu kimlik `svcutil` <xref:System.ServiceModel.Description.WsdlImporter>bilgileri, WCF hizmet bitiş noktası adreslerinin kimlik özelliklerine çevrildiğinde veya başka yöntemlerle alındığı zaman. Bu hizmet kimliklerinin doğru olduğunu ve geçerli olduğunu doğrulamayan istemciler hizmet kimlik doğrulamasını etkin bir şekilde atlar. Kötü amaçlı bir hizmet, WSDL'sinde iddia edilen kimliği değiştirerek kimlik bilgisi yönlendirme ve diğer "ortadaki adam" saldırılarını gerçekleştirmek için bu tür istemcilerden yararlanabilir.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>NTLM Yerine X509 Sertifikaları Kullanın  
 WCF, eşler arası kimlik doğrulaması için iki mekanizma sunar: X509 sertifikaları (eş ler tarafından kullanılır) ve Bir SSPI anlaşmasının Kerberos'tan NTLM'ye düşürüldüğü Windows kimlik doğrulaması.  1024 bit veya daha fazla anahtar boyutları kullanılarak sertifika tabanlı kimlik doğrulama sı çeşitli nedenlerle NTLM'ye tercih edilir:  
  
- karşılıklı kimlik doğrulamanın kullanılabilirliği,  
  
- daha güçlü şifreleme algoritmalarının kullanımı ve  
  
- iletilen X509 kimlik bilgilerini kullanmanın daha büyük zorluğu.  

## <a name="always-revert-after-impersonation"></a>Kimliğe Bürünmeden Sonra Her Zaman Geri Dön  
 İstemci kimliğe bürünmesini sağlayan API'leri kullanırken, özgün kimliğe geri dönüldüğünden emin olun. Örneğin, aşağıdaki kodda <xref:System.Security.Principal.WindowsImpersonationContext>gösterildiği gibi `using` C# deyimini`Using` veya Visual Basic deyimini kullanırken <xref:System.Security.Principal.WindowsIdentity> kullanın. Sınıf <xref:System.Security.Principal.WindowsImpersonationContext> <xref:System.IDisposable> arabirimi uygular ve bu nedenle ortak dil çalışma süresi (CLR) kod `using` blokayrıldığında otomatik olarak özgün kimliğe geri döner.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Yalnızca Gerektiği Gibi Kimliğin Kimliği  
 <xref:System.Security.Principal.WindowsIdentity> Sınıfın yöntemini <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> kullanarak, çok kontrollü bir kapsamda kimliğe bürünme kullanmak mümkündür. Bu, tüm işlemin <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> kapsamı için kimliğe bürünme sağlayan , özelliğini kullanarak aksine. <xref:System.ServiceModel.OperationBehaviorAttribute> Mümkün olduğunda, daha kesin <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> yöntemi kullanarak kimliğe bürünme kapsamını denetler.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Güvenilir Kaynaklardan Meta Veri Elde Etme  
 Meta verilerinizin kaynağına güvendiğinizden ve kimsenin meta verileri kurcaladığından emin olun. HTTP protokolü kullanılarak alınan meta veriler açık metin olarak gönderilir ve kurcalanabilir. Hizmet özellikleri <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> özelliklerini kullanıyorsa, https protokolünü kullanarak verileri indirmek için hizmet oluşturucutarafından sağlanan URL'yi kullanın.  
  
## <a name="publish-metadata-using-security"></a>Güvenlik Kullanarak Meta Veri Yayımlama  
 Bir hizmetin yayımlanmış meta verileriyle oynanmasını önlemek için, meta veri alışverişi bitiş noktasını aktarım veya ileti düzeyi güvenliğiyle güvence altına alametinin i Daha fazla bilgi için meta [veri uçnoktalarını yayımlama](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) ve nasıl yapılacağını şu bilgileriçin: [Kod Kullanan Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)bölümüne bakın.  
  
## <a name="ensure-use-of-local-issuer"></a>Yerel İhraççının Kullanımını Sağlama  
 Belirli bir bağlama için bir veren adresi ve bağlama belirtilirse, yerel veren bu bağlamayı kullanan uç noktalar için kullanılmaz. Her zaman yerel vereni kullanmayı bekleyen istemciler, bu tür bir bağlayıcı kullanmadıklarından veya veren adresinin null olacak şekilde bağlamayı değiştirdiğinden emin olmalıdır.  
  
## <a name="saml-token-size-quotas"></a>SAML Jeton Boyutu Kotaları  
 Güvenlik İddiaları İşaretleme Dili (SAML) belirteçleri iletilerde seri hale geldiğinde, bir Güvenlik Belirteç Hizmeti (STS) tarafından verildiğinde veya istemciler bunları kimlik doğrulamanın bir parçası olarak hizmetlere sunduklarında, maksimum ileti boyutu kotası yeterli olmalıdır SAML belirteci ve diğer ileti parçaları karşılamak için büyük. Normal durumlarda, varsayılan ileti boyutu kotaları yeterlidir. Ancak, saml belirteci yüzlerce talep içerdiğinden büyük olduğu durumlarda, kotalar serileştirilmiş belirteci karşılamak için artırılmalıdır. Kotalar hakkında daha fazla bilgi için, [Veriler için Güvenlik Hususları'na](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)bakın.  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Özel Ciltlemelerde SecurityBindingElement.IncludeTimestamp'ı Doğru olarak ayarlayın  
 Özel bir bağlama oluşturduğunuzda, <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> `true`'ye ayarlamanız gerekir. Aksi takdirde, <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> `false`'' olarak ayarlanmışsa ve istemci X509 sertifikası gibi asimetrik anahtar tabanlı bir belirteç kullanıyorsa, ileti imzalanmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Hususları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Veriler için Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)
- [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)

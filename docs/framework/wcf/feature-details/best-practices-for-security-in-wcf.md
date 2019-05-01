---
title: WCF'de Güvenlik için En İyi Uygulamalar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
ms.openlocfilehash: f0305807e76ca27e1979aa23bf0797c505fee566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048250"
---
# <a name="best-practices-for-security-in-wcf"></a>WCF'de Güvenlik için En İyi Uygulamalar
Aşağıdaki bölümlerde Windows Communication Foundation (WCF) kullanan güvenli uygulamalar oluştururken dikkate alınması gereken en iyi yöntemler listelenmiştir. Güvenlik hakkında daha fazla bilgi için bkz: [güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md), [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md), ve [meta veriler hakkında güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>SPN ile Windows kimlik doğrulaması gerçekleştirme Hizmetleri tanımlayın  
 Hizmetleri, kullanıcı asıl adlarından (UPN) veya hizmet asıl adı (SPN) ile tanımlanabilir. Ağ hizmeti gibi makine hesapları altında çalışan hizmetleri çalıştırdıkları makineye karşılık gelen bir SPN kimliği vardır. Kullanıcı hesapları altında çalışan hizmetleri sahip çalışan, kullanıcıya ancak karşılık gelen bir UPN varlığı `setspn` aracı, kullanıcı hesabı için bir SPN atamak için kullanılabilir. SPN tanımlanabilir ve bu SPN kullanılacak hizmetine istemcilerini yapılandırma belirli yaptığınız şekilde bir hizmet yapılandırma daha zor saldırıları. Bu kılavuz, Kerberos ya da SSPI anlaşması kullanılarak bağlamaları için geçerlidir.  İstemciler, burada SSPI NTLM'ye geri döner durumda SPN yine de belirtmeniz gerekir.  
  
## <a name="verify-service-identities-in-wsdl"></a>WSDL hizmet kimliklerini doğrulayın  
 WS-SecurityPolicy kendi kimlik bilgileri hakkındaki meta verileri yayımlamak hizmetler sağlar. Aracılığıyla alınırken `svcutil` veya diğer yöntemler gibi <xref:System.ServiceModel.Description.WsdlImporter>, bu kimlik bilgileri, WCF Hizmeti uç nokta adresleri kimlik özelliklerinin çevrilir. Bu hizmet kimlikleri etkili bir şekilde doğru ve geçerli olduğunu doğrulamaz istemcilerin hizmeti kimlik doğrulama atlama. Kötü amaçlı bir hizmet içinde WSDL talep kimliğini değiştirerek kimlik bilgisi iletme ve diğer "ortadaki adam" saldırılarına yürütmek için bu gibi istemcilerde yararlanabilir.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>NTLM yerine sertifikaları kullan X509  
 WCF eşler arası kimlik doğrulaması için iki mekanizma sunar: X509 (eş kanalı tarafından kullanılır) sertifikaları ve burada SSPI anlaşması daha aşağı düşürmeden Kerberos'tan için NTLM Windows kimlik doğrulaması.  Sertifika tabanlı kimlik doğrulaması kullanarak anahtar boyutları 1024 bit veya daha pek çok nedenden dolayı NTLM için tercih edilen:  
  
- Kullanılabilirlik karşılıklı kimlik doğrulama  
  
- daha güçlü şifreleme algoritmalarının kullanımını ve  
  
- kullanma büyük zorluk X509 iletilen kimlik bilgileri.  
   
## <a name="always-revert-after-impersonation"></a>Kimliğe bürünme sonra her zaman geri dön  
 İstemcinin kimliğe bürünme sağlayan API'leri kullanırken, özgün kimliğine geri dönülemiyor emin olun. Örneğin kullanırken <xref:System.Security.Principal.WindowsIdentity> ve <xref:System.Security.Principal.WindowsImpersonationContext>, C# kullanın `using` deyimi veya Visual Basic`Using` deyimi, aşağıdaki kodda gösterildiği gibi. <xref:System.Security.Principal.WindowsImpersonationContext> Sınıfının Implements <xref:System.IDisposable> arabirimi ve bu nedenle ortak dil çalışma zamanı (CLR) otomatik olarak özgün kimliğine geri döner kodu ayrıldığında `using` blok.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Yalnızca gerektiğinde kimliğine bürün  
 Kullanarak <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> yöntemi <xref:System.Security.Principal.WindowsIdentity> sınıfı mümkündür çok denetlenen kapsamda kimliğe bürünme özelliğini kullanın. Bu kullanarak aksine, <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliği <xref:System.ServiceModel.OperationBehaviorAttribute>, tüm işlemin kapsamı için kimliğe bürünme sağlar. Mümkün olduğunda, daha kesin kullanarak kimliğe bürünme kapsamını denetleme <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> yöntemi.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Güvenilen kaynaklardan gelen meta verilerini alın  
 Meta verilerinizi kaynağına güveniyorsanız ve hiç meta verileriyle yapmadığından emin emin olun. HTTP protokolü kullanılarak alınan meta verileri açık metin olarak gönderilir ve bozuabilir. Hizmet kullanıyorsa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> özelliklerini, HTTPS protokolünü kullanarak verileri yüklemek için hizmet oluşturucusu tarafından sağlanan URL kullanın.  
  
## <a name="publish-metadata-using-security"></a>Güvenlik kullanarak meta verileri yayımlama  
 Bir hizmetin yayımlanan meta verilerle oynanmasını önlemek için meta veri değişimi uç noktası taşıma veya ileti düzeyi güvenlik ile güvenli hale getirin. Daha fazla bilgi için [meta veri uç noktalarını yayımlama](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) ve [nasıl yapılır: Kod kullanarak bir hizmet için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Yerel verici kullanımı emin olun  
 Belirli bir bağlama için bir veren adresi ve bağlama belirtilirse, yerel sertifika verenin bu bağlamayı kullanan uç noktaları için kullanılmaz. Her zaman yerel dağıtımcının kullanmayı düşündüğünüz istemciler, böyle bir bağlamanın kullanmayın veya veren adresin null olduğundan, bunlar bağlama değiştirme emin olun.  
  
## <a name="saml-token-size-quotas"></a>SAML belirteci boyutu kotaları  
 En büyük ileti boyutu kotası güvenlik onaylama işaretleme dili (SAML) belirteçleri, iletileri bir güvenlik belirteci hizmeti (STS) tarafından verilen veya istemciler bunları Hizmetleri kimlik doğrulaması bir parçası olarak olduğunda serileştirildiği zaman yeterince olmalıdır SAML belirtecindeki ve diğer ileti bölümlerini içerecek kadar büyük. Normal durumlarda, varsayılan ileti boyutu kotası yeterlidir. Ancak, talep yüzlerce içerdiğinden SAML belirteci büyük olduğu durumlarda, kotalar serileştirilmiş belirteci uyum sağlayacak şekilde artırılması gereken. Kotaları hakkında daha fazla bilgi için bkz: [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>SecurityBindingElement.IncludeTimestamp özel bağlamalar True olarak ayarlayın  
 Özel bağlama oluşturduğunuzda ayarlamalısınız <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> için `true`. Aksi takdirde <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> ayarlanır `false`, ve bir asimetrik anahtar tabanlı belirteci x X509 gibi istemcinin kullandığı sertifika, ileti imzalanmamış.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Veriler için Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)
- [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)

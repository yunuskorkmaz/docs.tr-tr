---
title: WCF'de Güvenlik için En İyi Uygulamalar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
ms.openlocfilehash: c99ab5e1e72aefc688df1692091e60caf930d5e4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597624"
---
# <a name="best-practices-for-security-in-wcf"></a>WCF'de Güvenlik için En İyi Uygulamalar
Aşağıdaki bölümlerde, Windows Communication Foundation (WCF) kullanarak güvenli uygulamalar oluştururken dikkate alınması gereken en iyi uygulamalar listelenmektedir. Güvenlik hakkında daha fazla bilgi için bkz. [güvenlik konuları](security-considerations-in-wcf.md), [veriler için güvenlik konuları](security-considerations-for-data.md)ve [meta veriler ile ilgili güvenlik konuları](security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>SPN 'Ler ile Windows kimlik doğrulaması gerçekleştiren Hizmetleri tanımla  
 Hizmetler, Kullanıcı asıl adları (UPN) veya hizmet sorumlusu adları (SPN 'Ler) ile tanımlanabilir. Ağ hizmeti gibi makine hesapları altında çalışan hizmetlerin, çalıştırdığı makineye karşılık gelen bir SPN kimliği vardır. Kullanıcı hesapları altında çalışan hizmetlerin, çalıştırdığı kullanıcıya karşılık gelen UPN kimliği vardır, ancak `setspn` araç Kullanıcı hesabına BIR SPN atamak için kullanılabilir. SPN aracılığıyla tanımlanabilmesi ve bu SPN 'yi kullanmak üzere hizmete bağlanan istemcileri yapılandırmak, belirli saldırıları daha zor hale getirebileceği şekilde yapılandırmak için bir hizmeti yapılandırma. Bu kılavuz, Kerberos veya SSPI anlaşması kullanılarak bağlamalar için geçerlidir.  İstemciler yine de SSPI 'nin NTLM 'ye geri dönmesi durumunda bir SPN belirtmelidir.  
  
## <a name="verify-service-identities-in-wsdl"></a>WSDL 'de hizmet kimliklerini doğrulama  
 WS-SecurityPolicy, hizmetlerin meta verilerde kendi kimlikleri hakkında bilgi yayımlamasına olanak sağlar. `svcutil`Veya gibi diğer yöntemler aracılığıyla alındığında <xref:System.ServiceModel.Description.WsdlImporter> , bu KIMLIK bilgileri WCF hizmeti uç noktası adreslerinin kimlik özelliklerine çevrilir. Bu hizmet kimliklerinin doğru olduğunu ve geçerli etkin bir şekilde hizmet kimlik doğrulamasını atlayan istemciler. Kötü amaçlı bir hizmet, WSDL içinde talep edilen kimliği değiştirerek kimlik bilgisi iletmeyi ve diğer "orman adam" saldırıları yürütmek için bu tür istemcilerden yararlanabilir.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>NTLM yerine x509 sertifikaları kullanma  
 WCF eşler arası kimlik doğrulaması için iki mekanizma sunar: x509 sertifikaları (eş kanal tarafından kullanılır) ve bir SSPI anlaşmasının Kerberos 'dan NTLM 'ye indirgenme yaptığı Windows kimlik doğrulaması.  1024 bit veya daha fazlası için anahtar boyutlarını kullanarak sertifika tabanlı kimlik doğrulaması, birkaç nedenden dolayı NTLM için tercih edilir:  
  
- karşılıklı kimlik doğrulamanın kullanılabilirliği,  
  
- daha güçlü şifreleme algoritmalarının kullanımı ve  
  
- iletilen x509 kimlik bilgilerinin kullanılmasıyla daha fazla zorluk.  

## <a name="always-revert-after-impersonation"></a>Kimliğe bürünme sonrasında her zaman dön  
 Bir istemciyi kimliğe bürünme özelliğini etkinleştiren API 'Ler kullanırken, özgün kimliğe döndiğinizden emin olun. Örneğin, ve kullanarak, <xref:System.Security.Principal.WindowsIdentity> <xref:System.Security.Principal.WindowsImpersonationContext> `using` aşağıdaki kodda gösterildiği gibi C# ifadesini veya Visual Basic ifadesini kullanın `Using` . <xref:System.Security.Principal.WindowsImpersonationContext>Sınıfı, arabirimini uygular <xref:System.IDisposable> ve bu nedenle, kod bloğundan ayrıldıktan sonra ortak dil çalışma zamanı (CLR) otomatik olarak özgün kimliğe geri döner `using` .  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Yalnızca gerektiğinde kimliğe bürün  
 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>Sınıfının yöntemini kullanarak <xref:System.Security.Principal.WindowsIdentity> , çok kontrollü bir kapsamda kimliğe bürünme kullanmak mümkündür. Bu, <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> <xref:System.ServiceModel.OperationBehaviorAttribute> tüm işlemin kapsamı için kimliğe bürünmeye izin veren öğesinin özelliğini kullanmanın aksine. Mümkün olduğunda, daha kesin bir yöntemi kullanarak kimliğe bürünme kapsamını kontrol edin <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> .  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Güvenilir kaynaklardan meta verileri al  
 Meta verilerinizin kaynağına güvendiğinizden emin olun ve meta verileri hiç kimse üzerinde hiç bulunmadığından emin olun. HTTP protokolü kullanılarak alınan meta veriler şifresiz metin olarak gönderilir ve üzerinde oynanmış olabilir. Hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> özelliklerini KULLANıYORSA, https protokolünü kullanarak verileri indirmek için hizmet Oluşturucu tarafından sağlanan URL 'yi kullanın.  
  
## <a name="publish-metadata-using-security"></a>Güvenliği kullanarak meta verileri yayımlama  
 Hizmetin yayımlanan meta verilerinde izinsiz değişiklik yapılmasını engellemek için, aktarım veya ileti düzeyi güvenlik ile meta veri değişimi uç noktası güvenliğini sağlayın. Daha fazla bilgi için bkz. [meta veri uç noktalarını yayımlama](../publishing-metadata-endpoints.md) ve [nasıl yapılır: kod kullanarak bir hizmet Için meta verileri yayımlama](how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Yerel verenin kullanımını sağlayın  
 Belirli bir bağlama için bir veren adresi ve bağlama belirtilirse, bu bağlamayı kullanan uç noktalar için yerel veren kullanılmaz. Her zaman yerel vereni kullanması beklenen istemciler böyle bir bağlamayı kullanmamalıdır veya veren adresinin null olması gibi bağlamayı değiştirdiklerinden emin olmalıdır.  
  
## <a name="saml-token-size-quotas"></a>SAML belirteci boyut kotaları  
 Güvenlik onaylama işlemi Işaretleme dili (SAML) belirteçleri iletilerde, bir güvenlik belirteci hizmeti (STS) tarafından verildiğinde veya istemciler bunları kimlik doğrulamanın bir parçası olarak hizmetlere sunduklarında, en büyük ileti boyutu kotasının SAML belirtecini ve diğer ileti parçalarını barındırmak için yeterince büyük olması gerekir. Normal durumlarda, varsayılan ileti boyutu kotaları yeterlidir. Ancak, yüzlerce talep içerdiğinden SAML belirtecinin büyük olduğu durumlarda, Kotalar serileştirilmiş belirtece uyum sağlayacak şekilde artmalıdır. Kotalar hakkında daha fazla bilgi için bkz. [veriler Için güvenlik konuları](security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Özel bağlamalarda SecurityBindingElement. IncludeTimestamp 'ı true olarak ayarla  
 Özel bir bağlama oluşturduğunuzda, olarak ayarlamanız gerekir <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> `true` . Aksi takdirde, olarak <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> ayarlanmışsa `false` ve istemci x509 sertifikası gibi asimetrik anahtar tabanlı bir belirteç kullanıyorsa, ileti imzalanmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik konuları](security-considerations-in-wcf.md)
- [Veriler için Güvenlik Konuları](security-considerations-for-data.md)
- [Meta Veriler Hakkında Güvenlik Konuları](security-considerations-with-metadata.md)

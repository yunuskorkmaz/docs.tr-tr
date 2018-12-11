---
title: 'Nasıl Yapılır: Özel güvenlik belirteci sağlayıcı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
ms.openlocfilehash: 88200b41346a18732647602fb16774610014330c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131072"
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Nasıl Yapılır: Özel güvenlik belirteci sağlayıcı oluşturma
Bu konu, yeni belirteç türleri ile özel güvenlik belirteci sağlayıcı oluşturma ve sağlayıcı bir özel güvenlik belirteci yöneticisi ile tümleştirmek nasıl gösterir.  
  
> [!NOTE]
>  Sistem tarafından sağlanan belirteç bulunamazsa özel bir belirteç sağlayıcısını oluşturma <xref:System.IdentityModel.Tokens> ad alanı gereksinimlerinizi eşleşmiyor.  
  
 Güvenlik belirteci sağlayıcı, istemci veya hizmet kimlik bilgilerini içindeki bilgileri temel alan bir güvenlik belirteci temsilini oluşturur. Windows Communication Foundation (WCF) güvenlik özel güvenlik belirteci sağlayıcı kullanmak için özel kimlik bilgileri ve güvenlik belirteci Yöneticisi uygulamaları oluşturmanız gerekir.  
  
 Özel kimlik bilgileri ve güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için bkz: [izlenecek yol: Özel istemci ve hizmet kimlik bilgilerini oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Kimlik bilgileri hakkında daha fazla bilgi için bkz: güvenlik belirteci yöneticisi, sağlayıcı ve authenticator sınıfları [güvenlik mimarisi](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
### <a name="to-create-a-custom-security-token-provider"></a>Özel güvenlik belirteci sağlayıcı oluşturma  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı.  
  
2.  Uygulama <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> yöntemi. Yöntemi, oluşturma ve güvenlik belirteci örneği döndüren sorumludur. Aşağıdaki örnekte adlı bir sınıf oluşturur `MySecurityTokenProvider`ve geçersiz kılmaları <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> örneği döndürülecek yöntemi <xref:System.IdentityModel.Tokens.X509SecurityToken> sınıfı. Sınıf oluşturucusu bir örneğini gerektirir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfı.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Özel güvenlik belirteci sağlayıcı bir özel güvenlik belirteci yöneticisi ile tümleştirmek için  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.IdentityModel.Selectors.SecurityTokenManager> sınıfı. (Aşağıdaki örnekte türetildiği <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> türetilen sınıf <xref:System.IdentityModel.Selectors.SecurityTokenManager> sınıfı.)  
  
2.  Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> değil zaten geçersiz kılınırsa yöntemi.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Yöntemi örneği döndürmekten sorumludur <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı uygun <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametresi WCF güvenlik çerçevesi tarafından yönteme geçirilmesi. Değiştir (önceki yordamda oluşturduğunuz) özel güvenlik belirteci sağlayıcı uygulaması döndürmek için yöntemin ne zaman yöntemi çağrıldığında bir uygun güvenlik belirteci parametresi ile. Güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için bkz: [izlenecek yol: Özel istemci ve hizmet kimlik bilgilerini oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
3.  Temel, özel güvenlik belirteci sağlayıcı döndürülecek etkinleştirmek için yöntem Özel mantık eklemek <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametresi. Aşağıdaki örnek, belirteci gereksinimleri karşılanırsa özel güvenlik belirteci sağlayıcı döndürür. , Bir X.509 güvenlik belirteci ve ileti yönü (belirteç iletiyi çıkış için kullanıldığını) gereklidir. Diğer tüm durumlarda, diğer güvenlik belirteci gereksinimleri için sistem tarafından sağlanan davranışı korumak için temel sınıf kodu çağırır.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki tam gösterir <xref:System.IdentityModel.Selectors.SecurityTokenProvider> karşılık gelen yanı sıra uygulama <xref:System.IdentityModel.Selectors.SecurityTokenManager> uygulaması.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.X509SecurityToken>  
 [İzlenecek yol: Özel istemci ve hizmet kimlik bilgilerini oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Nasıl Yapılır: Özel güvenlik belirteci kimlik doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Güvenlik mimarisi](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)

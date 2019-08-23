---
title: 'Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
ms.openlocfilehash: 8daf025212e34c5d37d09ae5108d186d13b99eca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951818"
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma
Bu konuda, özel bir güvenlik belirteci sağlayıcısıyla yeni belirteç türleri oluşturma ve sağlayıcıyı özel bir güvenlik belirteci yöneticisiyle tümleştirme gösterilmektedir.  
  
> [!NOTE]
> <xref:System.IdentityModel.Tokens> Ad alanında bulunan sistem tarafından sağlanmış belirteçler gereksinimlerle eşleşmezse özel bir belirteç sağlayıcısı oluşturun.  
  
 Güvenlik belirteci sağlayıcısı, istemci veya hizmet kimlik bilgileriyle ilgili bilgileri temel alarak bir güvenlik belirteci temsili oluşturur. Windows Communication Foundation (WCF) güvenlik sürümünde özel güvenlik belirteci sağlayıcısını kullanmak için özel kimlik bilgileri ve güvenlik belirteci Yöneticisi uygulamaları oluşturmanız gerekir.  
  
 Özel kimlik bilgileri ve güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için [bkz. İzlenecek yol: Özel Istemci ve hizmet kimlik bilgileri](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)oluşturuluyor.  
  
### <a name="to-create-a-custom-security-token-provider"></a>Özel bir güvenlik belirteci sağlayıcısı oluşturmak için  
  
1. <xref:System.IdentityModel.Selectors.SecurityTokenProvider> Sınıfından türetilmiş yeni bir sınıf tanımlayın.  
  
2. <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> Yöntemini uygulayın. Yöntemi, güvenlik belirtecinin bir örneğini oluşturup döndürmekten sorumludur. Aşağıdaki örnek adlı `MySecurityTokenProvider`bir sınıf oluşturur ve <xref:System.IdentityModel.Tokens.X509SecurityToken> sınıfının bir örneğini döndürmek <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> için yöntemini geçersiz kılar. Sınıf oluşturucusu, <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfının bir örneğini gerektirir.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Özel bir güvenlik belirteci sağlayıcısını özel bir güvenlik belirteci Yöneticisi ile tümleştirme  
  
1. <xref:System.IdentityModel.Selectors.SecurityTokenManager> Sınıfından türetilmiş yeni bir sınıf tanımlayın. (Aşağıdaki örnek sınıfından türetilen <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfından <xref:System.IdentityModel.Selectors.SecurityTokenManager> türetilir.)  
  
2. Önceden geçersiz kılınmamışsa yöntemi geçersiz kılın. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29>  
  
     Yöntemi, WCF güvenlik çerçevesi tarafından metoduna geçirilen <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametreye uygun <xref:System.IdentityModel.Selectors.SecurityTokenProvider> bir sınıf örneğini döndürmekten sorumludur. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Yöntemi uygun bir güvenlik belirteci parametresiyle çağrıldığında özel güvenlik belirteci sağlayıcısı uygulamasını (önceki yordamda oluşturulan) döndürmek için yöntemini değiştirin. Güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için bkz [. İzlenecek yol: Özel Istemci ve hizmet kimlik bilgileri](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)oluşturuluyor.  
  
3. Metoda göre <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> özel güvenlik belirteci sağlayıcınızı döndürmesini sağlamak için yöntemine özel mantık ekleyin. Aşağıdaki örnek, belirteç gereksinimleri karşılanıyorsa özel güvenlik belirteci sağlayıcısını döndürür. Gereksinimler bir X. 509.440 güvenlik belirteci ve ileti yönü (belirtecin ileti çıktısı için kullanıldığı) içerir. Diğer tüm durumlarda, kod, diğer güvenlik belirteci gereksinimleri için sistem tarafından sağlanmış davranışı sürdürmek üzere temel sınıfı çağırır.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıda, karşılık gelen <xref:System.IdentityModel.Selectors.SecurityTokenProvider> <xref:System.IdentityModel.Selectors.SecurityTokenManager> bir uygulamayla birlikte tamamlanmış bir uygulama gösterilmektedir.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.X509SecurityToken>
- [İzlenecek yol: Özel Istemci ve hizmet kimlik bilgileri oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [Nasıl yapılır: Özel güvenlik belirteci kimlik doğrulayıcısı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)

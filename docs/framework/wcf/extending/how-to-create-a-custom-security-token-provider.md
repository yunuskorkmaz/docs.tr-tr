---
title: 'Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
ms.openlocfilehash: 94de506b16d97ec82b84ec6eed34111e99f62977
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249273"
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma

Bu konuda, özel bir güvenlik belirteci sağlayıcısıyla yeni belirteç türleri oluşturma ve sağlayıcıyı özel bir güvenlik belirteci yöneticisiyle tümleştirme gösterilmektedir.  
  
> [!NOTE]
> Ad alanında bulunan sistem tarafından sağlanmış belirteçler gereksinimlerle eşleşmezse özel bir belirteç sağlayıcısı oluşturun <xref:System.IdentityModel.Tokens> .  
  
 Güvenlik belirteci sağlayıcısı, istemci veya hizmet kimlik bilgileriyle ilgili bilgileri temel alarak bir güvenlik belirteci temsili oluşturur. Windows Communication Foundation (WCF) güvenlik sürümünde özel güvenlik belirteci sağlayıcısını kullanmak için özel kimlik bilgileri ve güvenlik belirteci Yöneticisi uygulamaları oluşturmanız gerekir.  
  
 Özel kimlik bilgileri ve güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için [Izlenecek yol: özel istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)konusuna bakın.  
  
### <a name="to-create-a-custom-security-token-provider"></a>Özel bir güvenlik belirteci sağlayıcısı oluşturmak için  
  
1. Sınıfından türetilmiş yeni bir sınıf tanımlayın <xref:System.IdentityModel.Selectors.SecurityTokenProvider> .  
  
2. Yöntemini uygulayın <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> . Yöntemi, güvenlik belirtecinin bir örneğini oluşturup döndürmekten sorumludur. Aşağıdaki örnek adlı bir sınıf oluşturur `MySecurityTokenProvider` ve <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> sınıfının bir örneğini döndürmek için yöntemini geçersiz kılar <xref:System.IdentityModel.Tokens.X509SecurityToken> . Sınıf oluşturucusu, sınıfının bir örneğini gerektirir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> .  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Özel bir güvenlik belirteci sağlayıcısını özel bir güvenlik belirteci Yöneticisi ile tümleştirme  
  
1. Sınıfından türetilmiş yeni bir sınıf tanımlayın <xref:System.IdentityModel.Selectors.SecurityTokenManager> . (Aşağıdaki örnek sınıfından türetilen sınıfından türetilir <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> <xref:System.IdentityModel.Selectors.SecurityTokenManager> .)  
  
2. Önceden geçersiz <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> kılınmamışsa yöntemi geçersiz kılın.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29>Yöntemi, <xref:System.IdentityModel.Selectors.SecurityTokenProvider> <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> WCF güvenlik çerçevesi tarafından metoduna geçirilen parametreye uygun bir sınıf örneğini döndürmekten sorumludur. Yöntemi uygun bir güvenlik belirteci parametresiyle çağrıldığında özel güvenlik belirteci sağlayıcısı uygulamasını (önceki yordamda oluşturulan) döndürmek için yöntemini değiştirin. Güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için [Izlenecek yol: özel istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)konusuna bakın.  
  
3. Metoda göre özel güvenlik belirteci sağlayıcınızı döndürmesini sağlamak için yöntemine özel mantık ekleyin <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> . Aşağıdaki örnek, belirteç gereksinimleri karşılanıyorsa özel güvenlik belirteci sağlayıcısını döndürür. Gereksinimler bir X. 509.440 güvenlik belirteci ve ileti yönü (belirtecin ileti çıktısı için kullanıldığı) içerir. Diğer tüm durumlarda, kod, diğer güvenlik belirteci gereksinimleri için sistem tarafından sağlanmış davranışı sürdürmek üzere temel sınıfı çağırır.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Örnek  

 Aşağıda, <xref:System.IdentityModel.Selectors.SecurityTokenProvider> karşılık gelen bir uygulamayla birlikte tamamlanmış bir uygulama gösterilmektedir <xref:System.IdentityModel.Selectors.SecurityTokenManager> .  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.X509SecurityToken>
- [İzlenecek yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)
- [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](how-to-create-a-custom-security-token-authenticator.md)

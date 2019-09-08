---
title: 'Nasıl yapılır: Bir X.509 Sertifikasının Şifreleme Sağlayıcısını Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: 8101c0d1214eed2c6ea42a4faab774207aab3a79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797285"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificates-private-key"></a>Nasıl yapılır: Bir X.509 Sertifikasının Şifreleme Sağlayıcısını Değiştirme
Bu konuda, bir X. 509.440 sertifikasının özel anahtarını sağlamak için kullanılan şifreleme sağlayıcısının nasıl değiştirileceği ve sağlayıcının Windows Communication Foundation (WCF) güvenlik çerçevesiyle nasıl tümleştirileceği gösterilmektedir. Sertifikaları kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../feature-details/working-with-certificates.md).  
  
 WCF güvenlik çerçevesi, [nasıl yapılacağı konusunda açıklandığı gibi yeni güvenlik belirteci türlerini tanıtmak için bir yol sağlar: Özel bir belirteç](how-to-create-a-custom-token.md)oluşturun. Ayrıca, sistem tarafından sunulan mevcut belirteç türlerini değiştirmek için özel bir belirteç kullanmak mümkündür.  
  
 Bu konuda, sistem tarafından sağlanan X. 509.440 güvenlik belirteci, sertifika özel anahtarı için farklı bir uygulama sağlayan özel bir X. 509.440 belirteci ile değiştirilmiştir. Bu, gerçek özel anahtarın varsayılan Windows şifreleme sağlayıcısından farklı bir şifreleme sağlayıcısı tarafından sağlandığı senaryolarda yararlıdır. Alternatif bir şifreleme sağlayıcısına örnek olarak, tüm özel anahtarla ilgili şifreleme işlemlerini gerçekleştiren ve özel anahtarları bellekte depolamaz ve bu nedenle sistemin güvenliğini geliştirecek bir donanım güvenlik modülü vardır.  
  
 Aşağıdaki örnek yalnızca tanıtım amaçlıdır. Varsayılan Windows şifreleme sağlayıcısı 'nın yerini almaz, ancak böyle bir sağlayıcının tümleştirildiği yeri gösterir.  
  
## <a name="procedures"></a>Yordamlar  
 İlişkili bir güvenlik anahtarı veya anahtarlarına sahip olan her güvenlik belirtecinin, güvenlik belirteci <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> örneğinden bir anahtarlar koleksiyonu döndüren özelliği uygulaması gerekir. Belirteç bir X. 509.952 güvenlik belirtecidir, koleksiyon, hem ortak hem de sertifikayla ilişkili özel anahtarları <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> temsil eden sınıfın tek bir örneğini içerir. Sertifikanın anahtarlarını sağlamak için kullanılan varsayılan şifreleme sağlayıcısını değiştirmek için, bu sınıfın yeni bir uygulamasını oluşturun.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Özel bir X. 509.440 asimetrik anahtar oluşturmak için  
  
1. <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> Sınıfından türetilmiş yeni bir sınıf tanımlayın.  
  
2. <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> Salt okunurdur özelliğini geçersiz kılın. Bu özellik, sertifikanın ortak/özel anahtar çiftinin gerçek anahtar boyutunu döndürür.  
  
3. Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> yöntemi. Bu yöntem, sertifika özel anahtarıyla bir simetrik anahtarın şifresini çözmek için WCF güvenlik çerçevesi tarafından çağırılır. (Anahtar daha önce sertifikanın ortak anahtarıyla şifrelendi.)  
  
4. Geçersiz kılma <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> yöntemi. Bu yöntem, metoda geçirilen parametrelere bağlı olarak, sertifikanın özel veya ortak anahtarı için <xref:System.Security.Cryptography.AsymmetricAlgorithm> şifreleme sağlayıcısını temsil eden sınıfının bir örneğini almak için WCF güvenlik çerçevesi tarafından çağrılır.  
  
5. İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> yöntemi. <xref:System.Security.Cryptography.HashAlgorithm> Sınıfının farklı bir uygulamasý gerekliyse bu yöntemi geçersiz kılın.  
  
6. Geçersiz kılma <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> yöntemi. Bu yöntem, sertifikanın özel anahtarıyla ilişkili <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> sınıfının bir örneğini döndürür.  
  
7. Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> yöntemi. Bu yöntem, belirli bir şifreleme algoritmasından güvenlik anahtarı uygulamasının desteklenip desteklenmediğini göstermek için kullanılır.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 Aşağıdaki yordamda, sistem tarafından sunulan X. 509.440 güvenlik belirtecini değiştirmek için önceki yordamda oluşturulan özel X. 509.440 asimetrik güvenlik anahtarı uygulamasının WCF güvenlik çerçevesiyle nasıl tümleştirileceği gösterilmektedir.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Sistem tarafından belirtilen X. 509.440 güvenlik belirtecini özel bir X. 509.952 asimetrik güvenlik anahtarı belirteci ile değiştirmek için  
  
1. Aşağıdaki örnekte gösterildiği gibi, sistem tarafından sağlanmış güvenlik anahtarı yerine özel X. 509.952 asimetrik güvenlik anahtarını döndüren özel bir X. 509.440 güvenlik belirteci oluşturun. Özel güvenlik belirteçleri hakkında daha fazla bilgi için bkz [. nasıl yapılır: Özel bir belirteç](how-to-create-a-custom-token.md)oluşturun.  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2. Örnekte gösterildiği gibi özel bir X. 509.440 güvenlik belirteci döndüren özel bir güvenlik belirteci sağlayıcısı oluşturun. Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz [. nasıl yapılır: Özel bir güvenlik belirteci sağlayıcısı](how-to-create-a-custom-security-token-provider.md)oluşturun.  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3. Özel güvenlik anahtarının Başlatıcı tarafında kullanılması gerekiyorsa, aşağıdaki örnekte gösterildiği gibi özel bir istemci güvenlik belirteci Yöneticisi ve özel istemci kimlik bilgileri sınıfları oluşturun. Özel istemci kimlik bilgileri ve istemci güvenlik belirteci yöneticileri hakkında daha fazla bilgi için [bkz. İzlenecek yol: Özel Istemci ve hizmet kimlik bilgileri](walkthrough-creating-custom-client-and-service-credentials.md)oluşturuluyor.  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4. Özel güvenlik anahtarının alıcı tarafında kullanılması gerekiyorsa, aşağıdaki örnekte gösterildiği gibi özel bir hizmet güvenlik belirteci Yöneticisi ve özel hizmet kimlik bilgileri oluşturun. Özel hizmet kimlik bilgileri ve hizmet güvenliği belirteç yöneticileri hakkında daha fazla bilgi için [bkz. İzlenecek yol: Özel Istemci ve hizmet kimlik bilgileri](walkthrough-creating-custom-client-and-service-credentials.md)oluşturuluyor.  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.Security.Cryptography.AsymmetricAlgorithm>
- <xref:System.Security.Cryptography.HashAlgorithm>
- <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>
- [İzlenecek yol: Özel Istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)
- [Nasıl yapılır: Özel güvenlik belirteci kimlik doğrulayıcısı oluşturma](how-to-create-a-custom-security-token-authenticator.md)
- [Nasıl yapılır: Özel güvenlik belirteci sağlayıcısı oluşturma](how-to-create-a-custom-security-token-provider.md)
- [Nasıl yapılır: Özel belirteç oluşturma](how-to-create-a-custom-token.md)

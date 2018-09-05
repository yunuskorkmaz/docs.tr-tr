---
title: 'Nasıl yapılır: bir X.509 sertifikasının şifreleme sağlayıcısını değiştirme&#39;s özel anahtar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: bb345b3106895a75c00a0d80b8665a0e9239598f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510485"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificate39s-private-key"></a>Nasıl yapılır: bir X.509 sertifikasının şifreleme sağlayıcısını değiştirme&#39;s özel anahtar
Bu konu nasıl bir X.509 sertifikasının özel anahtar sağlamak için kullanılan şifreleme sağlayıcısını değiştirme ve Windows Communication Foundation (WCF) güvenlik altyapısına sağlayıcı tümleştirmek nasıl gösterir. Sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 WCF güvenlik çerçevesi açıklandığı gibi yeni güvenlik belirteç türleri tanıtmak için bir yol sağlar [nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md). Var olan sistem tarafından sağlanan belirteç türleri değiştirmek için özel bir belirteç kullanmak da mümkündür.  
  
 Bu konu başlığında, sistem tarafından sağlanan X.509 güvenlik belirteci, sertifika özel anahtar için farklı bir uygulama sağlayan özel bir X.509 belirteç değiştirilir. Bu, burada gerçek özel anahtarı varsayılan Windows şifreleme sağlayıcısı değerinden farklı bir şifreleme sağlayıcısı tarafından sağlanan senaryolarda kullanışlıdır. Bir alternatif bir şifreleme sağlayıcısı, tüm özel anahtarı ilgili şifreleme işlemlerini gerçekleştirir ve özel anahtarlar, böylece sistem güvenliğini artırma bellekte depolamaz bir donanım güvenlik modülüne örneğidir.  
  
 Aşağıdaki örnek yalnızca gösterim amaçlıdır. Windows şifreleme sağlayıcısı varsayılan yerini almaz ancak böyle bir sağlayıcı burada tümleşik gösterir.  
  
## <a name="procedures"></a>Yordamlar  
 İlişkili güvenlik anahtarı veya anahtarlarının her güvenlik belirteci uygulamalıdır <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> özelliği güvenlik belirteci örneğinden anahtarların bir koleksiyonunu döndürür. Belirteç bir X.509 güvenlik belirteci ise, koleksiyonun tek bir örneğini içerir <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> sertifikayla ilişkili ortak ve özel anahtarları temsil eden sınıf. Sertifikanın anahtar sağlamak için kullanılan varsayılan şifreleme sağlayıcısı değiştirmek için bu sınıfın yeni bir uygulama oluşturun.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Özel X.509 asimetrik anahtar oluşturmak için  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> sınıfı.  
  
2.  Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> salt okunur özelliği. Bu özellik, sertifikanın ortak/özel anahtar çifti gerçek anahtar boyutunu döndürür.  
  
3.  Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> yöntemi. Bu yöntem, sertifikanın özel anahtara sahip bir simetrik anahtarın şifresini çözmek için WCF güvenlik çerçevesi tarafından çağrılır. (Anahtarı daha önce sertifikanın ortak anahtar ile şifrelenmiş.)  
  
4.  Geçersiz kılma <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> yöntemi. Bu yöntem bir örneği elde etmek için WCF güvenlik çerçevesi tarafından çağrılır <xref:System.Security.Cryptography.AsymmetricAlgorithm> geçirilen yönteme parametreleri bağlı olarak sertifikanın özel veya ortak anahtar şifreleme sağlayıcısını temsil eden sınıf.  
  
5.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> yöntemi. Farklı bir uygulaması, bu yöntemi yok sayın <xref:System.Security.Cryptography.HashAlgorithm> sınıfı gereklidir.  
  
6.  Geçersiz kılma <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> yöntemi. Bu yöntem bir örneğini döndürür <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> sertifikanın özel anahtarı ile ilişkili sınıf.  
  
7.  Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> yöntemi. Bu yöntem, belirli bir şifreleme algoritması güvenlik anahtar uygulama tarafından desteklenip desteklenmediğini belirtmek için kullanılır.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 Aşağıdaki yordam, sistem tarafından sağlanan X.509 güvenlik değiştirmek için önceki yordamda WCF güvenlik çerçevesi ile oluşturulan özel X.509 asimetrik güvenlik anahtar tümleştirmenize nasıl belirteci gösterir.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Sistem tarafından sağlanan X.509 güvenlik belirteci özel X.509 asimetrik güvenlik anahtar belirteciyle değiştirilecek  
  
1.  Özel X.509 asimetrik güvenlik anahtarı yerine sistem tarafından sağlanan güvenlik anahtarı döndüren özel bir X.509 güvenlik belirteci, aşağıdaki örnekte gösterildiği gibi oluşturun. Özel güvenlik belirteçleri hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2.  Örnekte gösterildiği gibi özel bir X.509 güvenlik belirteci döndüren bir özel güvenlik belirteci sağlayıcı oluşturma. Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel bir güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3.  Özel güvenlik anahtarı Başlatıcı tarafında kullanılacak gerekiyorsa özel bir istemci güvenlik belirteci yöneticisi ve özel istemci kimlik bilgileri sınıfları, aşağıdaki örnekte gösterildiği gibi oluşturun. Özel istemci kimlik bilgileri ve istemci güvenlik belirteci yöneticileri hakkında daha fazla bilgi için bkz. [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4.  Alıcı tarafında kullanılacak özel güvenlik anahtarı gerekiyorsa, bir özel hizmet güvenlik belirteci yöneticisi ve özel hizmet kimlik bilgilerini, aşağıdaki örnekte gösterildiği gibi oluşturun. Özel hizmet kimlik bilgilerini ve hizmeti güvenlik belirteci yöneticileri hakkında daha fazla bilgi için bkz. [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>  
 <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.Security.Cryptography.AsymmetricAlgorithm>  
 <xref:System.Security.Cryptography.HashAlgorithm>  
 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>  
 [İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Nasıl yapılır: Özel Belirteç Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)  
 [Güvenlik mimarisi](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)

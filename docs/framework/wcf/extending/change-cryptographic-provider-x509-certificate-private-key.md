---
title: "Nasıl yapılır: değişiklik şifreleme sağlayıcısı için bir X.509 sertifikası &#39; s özel anahtarı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1158d1fc2d906737087fa4bdf7d2070e5ff4cfae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificate39s-private-key"></a>Nasıl yapılır: değişiklik şifreleme sağlayıcısı için bir X.509 sertifikası &#39; s özel anahtarı
Bu konuda bir X.509 sertifikasının özel anahtarı sağlamak için kullanılan şifreleme sağlayıcısını değiştirme ve sağlayıcısını tümleştirme gösterilmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security çerçevesi. Sertifika kullanma hakkında daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Güvenlik framework açıklandığı gibi yeni güvenlik belirteci türleri tanıtmak için bir yöntem sunar [nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md). Var olan sistem tarafından sağlanan belirteç türleri değiştirmek için özel bir belirteç kullanmak da mümkündür.  
  
 Bu konuda, sistem tarafından sağlanan X.509 güvenlik belirteci, sertifika özel anahtarı için farklı bir uygulama sağlayan özel bir X.509 belirteci ile değiştirilir. Bu, burada gerçek özel anahtarı varsayılan Windows şifreleme sağlayıcısı'den farklı bir şifreleme sağlayıcısı sağladığı senaryolarda kullanışlıdır. Bir alternatif bir şifreleme sağlayıcısı, tüm özel anahtar ilgili şifreleme işlemlerini gerçekleştirir ve özel anahtarlar, böylece sistem güvenliğini geliştirme bellekte depolamaz bir donanım güvenlik modülü örnektir.  
  
 Aşağıdaki örnekte, yalnızca tanıtım amacıyla kullanılır. Varsayılan Windows şifreleme sağlayıcısı değiştirmez, ancak böyle bir sağlayıcı burada tümleşik gösterir.  
  
## <a name="procedures"></a>Yordamlar  
 İlişkili güvenlik anahtarı veya anahtarlara sahip her güvenlik belirteci uygulamalıdır <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> güvenlik belirteci örneğinden anahtarların bir koleksiyonunu döndürür özelliği. Belirtecin bir X.509 güvenlik belirteci ise, koleksiyon tek bir örneğini içerir <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> sertifikayla ilişkili ortak ve özel anahtarları temsil eden sınıf. Sertifikanın anahtar sağlamak için kullanılan varsayılan şifreleme sağlayıcısı değiştirmek için bu sınıfın yeni bir uygulama oluşturun.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Özel bir X.509 asimetrik anahtar oluşturmak için  
  
1.  Türetilen yeni bir sınıf tanımlama <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> sınıfı.  
  
2.  Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> özelliği salt okunur. Bu özellik, sertifikanın ortak/özel anahtar çifti gerçek anahtar boyutu döndürür.  
  
3.  Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> yöntemi. Bu yöntem tarafından çağrılır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sertifikanın özel anahtarı ile simetrik anahtarın şifresini çözmek için güvenlik çerçevesi. (Anahtar önceden sertifikanın ortak anahtar ile şifrelenmiş.)  
  
4.  Geçersiz kılma <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> yöntemi. Bu yöntem tarafından çağrılır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir örneği elde etmek için güvenlik framework <xref:System.Security.Cryptography.AsymmetricAlgorithm> metoduna geçirilen parametreler bağlı olarak sertifikanın özel veya ortak anahtar şifreleme sağlayıcısını temsil eden sınıf.  
  
5.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> yöntemi. Farklı bir uygulama olarak, bu yöntemi geçersiz kılın <xref:System.Security.Cryptography.HashAlgorithm> sınıfı gereklidir.  
  
6.  Geçersiz kılma <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> yöntemi. Bu yöntem örneğini döndürür <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> sertifikanın özel anahtarı ile ilişkilendirilmiş sınıfı.  
  
7.  Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> yöntemi. Bu yöntem, belirli bir şifreleme algoritması güvenlik anahtar uygulaması tarafından desteklenip desteklenmediğini belirtmek için kullanılır.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 Aşağıdaki yordamda, önceki yordamda ile oluşturulan özel X.509 asimetrik güvenlik anahtar uygulamanız tümleştirmek gösterilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistem tarafından sağlanan X.509 güvenlik belirteci değiştirmek için güvenlik çerçevesi.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Sistem tarafından sağlanan X.509 güvenlik belirteci bir özel X.509 asimetrik anahtar sahip güvenlik belirteci değiştirmek için  
  
1.  Sistem tarafından sağlanan güvenlik anahtarı yerine özel X.509 asimetrik güvenlik anahtarı döndüren özel bir X.509 güvenlik belirteci aşağıdaki örnekte gösterildiği gibi oluşturun. Özel güvenlik belirteçleri hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2.  Özel bir X.509 güvenlik belirteci verir bir özel güvenlik belirteci sağlayıcısı örnekte gösterildiği gibi oluşturun. Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel bir güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3.  Özel güvenlik anahtarı Başlatıcı tarafında kullanılması gerekiyorsa, özel bir istemci güvenlik belirteci yöneticisi ve özel istemci kimlik bilgileri sınıfları, aşağıdaki örnekte gösterildiği gibi oluşturun. Özel istemci kimlik bilgileri ve istemci güvenlik belirteci yöneticileri hakkında daha fazla bilgi için bkz: [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4.  Özel güvenlik anahtarı alıcı tarafında kullanılması gerekiyorsa, bir özel hizmet güvenlik belirteci yöneticisi ve özel hizmeti kimlik bilgileri, aşağıdaki örnekte gösterildiği gibi oluşturun. Özel hizmet kimlik bilgileri ve hizmet güvenlik belirteci yöneticileri hakkında daha fazla bilgi için bkz: [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
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
 [İzlenecek yol: Özel istemci ve hizmet kimlik bilgileri oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Nasıl yapılır: özel güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)  
 [Güvenlik mimarisi](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)

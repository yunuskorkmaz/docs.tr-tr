---
title: Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma
description: .NET 'te şifreleme ve şifre çözme için simetrik ve asimetrik anahtarlar oluşturmayı ve yönetmeyi anlayın.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET], keys
- symmetric keys
- asymmetric keys [.NET]
- cryptography [.NET], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 7ce19dc465fb1fac22545398e0724e6b76dd7098
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556949"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma
Anahtarları oluşturmak ve yönetmek, şifreleme işleminin önemli bir parçasıdır. Simetrik algoritmalar, bir anahtarın ve başlangıç vektörünün (IV) oluşturulmasını gerektirir. Anahtar, verinizin şifresini çözmemesi gereken herkesten gizli tutulmalıdır. IV'nin gizli olması gerekmez ancak her oturum için değiştirilmesi gerekir. Asimetrik algoritmalar bir ortak anahtarın, bir de özel anahtarın oluşturulmasını gerektirir. Ortak anahtar herhangi birine verilebilirken, özel anahtar yalnızca ortak anahtar ile şifrelenen verilerin şifresini çözecek tarafça bilinmelidir. Bu bölümde, hem simetrik, hem de asimetrik algoritmalar için anahtarların nasıl oluşturulacağı ve yönetileceği açıklanmaktadır.  
  
## <a name="symmetric-keys"></a>Simetrik Anahtarlar  
 .NET tarafından sağlanan simetrik şifreleme sınıfları, verileri şifrelemek ve şifrelerini çözmek için bir anahtar ve yeni bir başlatma vektörü (IV) gerektirir. Parametresiz yöntemi kullanarak yönetilen simetrik şifreleme sınıflarından birinin yeni bir örneğini oluşturduğunuzda `Create()` , otomatik olarak yeni bir anahtar ve IV oluşturulur. Verilerinizin şifresini çözmesine izin verdiğiniz kişilerin aynı anahtara ve IV'ye sahip olup aynı algoritmayı kullanması gerekir. Genellikle, her oturum için yeni bir anahtar ve IV oluşturulmalıdır, ve ne anahtar ne de IV daha sonraki bir oturumda kullanılmak üzere saklanmalıdır.  
  
 Bir simetrik anahtarı ve IV'yi uzaktaki bir kişiye iletmek için, genellikle simetrik anahtarı asimetrik şifreleme kullanarak şifrelersiniz. Anahtarı güvenli olmayan bir ağ üzerinde şifrelemeden göndermek güvenli değildir, çünkü anahtarı ve IV'yi yakalayan herhangi biri verilerinizin şifresini çözebilir.  
  
 Aşağıdaki örnek, algoritma için varsayılan uygulama sınıfının yeni bir örneğinin oluşturulmasını gösterir <xref:System.Security.Cryptography.Aes> .  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 Önceki kod yürütüldüğünde, yeni bir anahtar ve IV oluşturulur ve sırasıyla **anahtar** ve **IV** özelliklerine yerleştirilir.  
  
 Bazen birden çok anahtar oluşturmanız gerekebilir. Bu durumda, simetrik algoritma uygulayan bir sınıfın yeni bir örneğini oluşturabilir ve ardından **GenerateKey** ve **GenerateIV** yöntemlerini çağırarak yenı bir anahtar ve IV oluşturabilirsiniz. Aşağıdaki kod örneği, simetrik şifreleme sınıfının yeni bir örneği yapıldıktan sonra yeni anahtarların ve IVS 'nin nasıl oluşturulacağını göstermektedir.  
  
```vb  
Dim aes As Aes = Aes.Create()  
aes.GenerateIV()  
aes.GenerateKey()  
```  
  
```csharp  
Aes aes = Aes.Create();  
aes.GenerateIV();  
aes.GenerateKey();  
```  
  
 Yukarıdaki kod yürütüldüğünde, yeni **AES** örneği yapıldığında bir anahtar ve IV oluşturulur. **GenerateKey** ve **GenerateIV** yöntemleri çağrıldığında başka bir anahtar ve IV oluşturulur.
  
## <a name="asymmetric-keys"></a>Asimetrik Anahtarlar

 .NET, <xref:System.Security.Cryptography.RSA> asimetrik şifreleme için sınıfı sağlar. Bu sınıf, `Create()` Yeni bir örnek oluşturmak için parametresiz metodunu kullandığınızda ortak/özel anahtar çifti oluşturur. Asimetrik anahtarlar birden çok oturumda kullanılmak üzere saklanabilir ya da yalnızca tek bir oturum için oluşturulabilir. Ortak anahtar genel olarak kullanılabilir olabilse de, özel anahtar dikkatle korunmalıdır.  
  
 Bir asimetrik sınıfın her yeni örneği oluşturulduğunda bir ortak/özel anahtar çifti oluşturulur. Sınıfının yeni bir örneği oluşturulduktan sonra anahtar bilgileri, <xref:System.Security.Cryptography.RSA.ExportParameters%2A> anahtar bilgilerini tutan bir yapıyı döndüren yöntemi kullanılarak ayıklanabilir <xref:System.Security.Cryptography.RSAParameters> . Yöntemi, yalnızca ortak anahtar bilgisinin döndürülüp döndürülmeyeceğini veya hem ortak anahtar hem de özel anahtar bilgilerini döndürmesinin gerekip gerekmediğini belirten bir Boole değeri kabul eder.

Ayrıca, şu gibi önemli bilgileri ayıklamanızı sağlayan başka yöntemler de vardır:

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

Bir **RSA** örneği, yöntemi kullanılarak **RSAParameters** yapısının değerine başlatılabilir <xref:System.Security.Cryptography.RSA.ImportParameters%2A> . Veya yöntemini kullanarak yeni bir örnek oluşturun <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> .  
  
 Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır. Özel anahtarı depolamanız gerekiyorsa, bir anahtar kapsayıcısı kullanmanız gerekir. Bir özel anahtarı bir anahtar kapsayıcısında nasıl depolayabileceği hakkında daha fazla bilgi için bkz. [nasıl yapılır: asimetrik anahtarları bir anahtar kapsayıcısında depolama](how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Aşağıdaki kod örneği, bir **RSA** sınıfının yeni bir örneğini oluşturur, ortak/özel anahtar çifti oluşturur ve ortak anahtar bilgilerini bir **RSAParameters** yapısına kaydeder.  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSA = RSA.Create()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSA rsa = RSA.Create();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Şifreleme](encrypting-data.md)
- [Verilerin Şifresini Çözme](decrypting-data.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama](how-to-store-asymmetric-keys-in-a-key-container.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)

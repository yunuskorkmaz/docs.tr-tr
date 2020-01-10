---
title: Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 88d8dac83c3d5bf267ed90ffb313cd9e24b42dea
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706194"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma
Anahtarları oluşturmak ve yönetmek, şifreleme işleminin önemli bir parçasıdır. Simetrik algoritmalar, bir anahtarın ve başlangıç vektörünün (IV) oluşturulmasını gerektirir. Anahtar, verinizin şifresini çözmemesi gereken herkesten gizli tutulmalıdır. IV'nin gizli olması gerekmez ancak her oturum için değiştirilmesi gerekir. Asimetrik algoritmalar bir ortak anahtarın, bir de özel anahtarın oluşturulmasını gerektirir. Ortak anahtar herhangi birine verilebilirken, özel anahtar yalnızca ortak anahtar ile şifrelenen verilerin şifresini çözecek tarafça bilinmelidir. Bu bölümde, hem simetrik, hem de asimetrik algoritmalar için anahtarların nasıl oluşturulacağı ve yönetileceği açıklanmaktadır.  
  
## <a name="symmetric-keys"></a>Simetrik Anahtarlar  
 .NET Framework tarafından sağlanan simetrik şifreleme sınıfları, veriler üzerine şifreleme ve şifre çözme yapabilmek için bir anahtar ve yeni bir başlatma vektörü (IV) gerektirir. Parametresiz oluşturucuyu kullanarak yönetilen simetrik şifreleme sınıflarından birinin yeni bir örneğini oluşturduğunuzda, yeni bir anahtar ve IV otomatik olarak oluşturulur. Verilerinizin şifresini çözmesine izin verdiğiniz kişilerin aynı anahtara ve IV'ye sahip olup aynı algoritmayı kullanması gerekir. Genellikle, her oturum için yeni bir anahtar ve IV oluşturulmalıdır, ve ne anahtar ne de IV daha sonraki bir oturumda kullanılmak üzere saklanmalıdır.  
  
 Bir simetrik anahtarı ve IV'yi uzaktaki bir kişiye iletmek için, genellikle simetrik anahtarı asimetrik şifreleme kullanarak şifrelersiniz. Anahtarı güvenli olmayan bir ağ üzerinde şifrelemeden göndermek güvenli değildir, çünkü anahtarı ve IV'yi yakalayan herhangi biri verilerinizin şifresini çözebilir. Şifreleme kullanarak veri değişimi hakkında daha fazla bilgi için bkz. [şifreleme şeması oluşturma](../../../docs/standard/security/creating-a-cryptographic-scheme.md).  
  
 Aşağıdaki örnek, TripleDES algoritmasını uygulayan <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> sınıfının yeni bir örneğinin oluşturulmasını gösterir.  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 Önceki kod yürütüldüğünde, yeni bir anahtar ve IV oluşturulur ve sırasıyla **anahtar** ve **IV** özelliklerine yerleştirilir.  
  
 Bazen birden çok anahtar oluşturmanız gerekebilir. Bu durumda, simetrik algoritma uygulayan bir sınıfın yeni bir örneğini oluşturabilir ve ardından **GenerateKey** ve **GenerateIV** yöntemlerini çağırarak yenı bir anahtar ve IV oluşturabilirsiniz. Aşağıdaki kod örneği, simetrik şifreleme sınıfının yeni bir örneği yapıldıktan sonra yeni anahtarların ve IVS 'nin nasıl oluşturulacağını göstermektedir.  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 Önceki kod yürütüldüğünde, **üç aylık** dönemin yeni örneği yapıldığında bir anahtar ve IV oluşturulur. **GenerateKey** ve **GenerateIV** yöntemleri çağrıldığında başka bir anahtar ve IV oluşturulur.  
  
## <a name="asymmetric-keys"></a>Asimetrik Anahtarlar  
 .NET Framework, asimetrik şifreleme için <xref:System.Security.Cryptography.RSACryptoServiceProvider> ve <xref:System.Security.Cryptography.DSACryptoServiceProvider> sınıflarını sağlar. Bu sınıflar, yeni bir örnek oluşturmak için parametresiz oluşturucuyu kullandığınızda ortak/özel anahtar çifti oluşturur. Asimetrik anahtarlar birden çok oturumda kullanılmak üzere saklanabilir ya da yalnızca tek bir oturum için oluşturulabilir. Ortak anahtar genel olarak kullanılabilir olabilse de, özel anahtar dikkatle korunmalıdır.  
  
 Bir asimetrik sınıfın her yeni örneği oluşturulduğunda bir ortak/özel anahtar çifti oluşturulur. Sınıfın yeni bir örneği oluşturulduktan sonra, anahtar bilgileri şu iki yöntemden biriyle alınabilir:  
  
- Anahtar bilgisinin XML gösterimini döndüren <xref:System.Security.Cryptography.RSA.ToXmlString%2A> yöntemi.  
  
- Anahtar bilgilerini tutan bir <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> yapısı döndüren <xref:System.Security.Cryptography.RSAParameters> yöntemi.  
  
 İki yöntem de yalnızca ortak anahtar bilgisinin mi dönüleceğini yoksa hem ortak anahtar hem de özel anahtar bilgisinin mi dönüleceğini belirten bir Boolean değerini kabul eder. Bir **RSACryptoServiceProvider** sınıfı, <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> yöntemi kullanılarak **RSAParameters** yapısının değerine başlatılabilir.  
  
 Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır. Özel anahtarı depolamanız gerekiyorsa, bir anahtar kapsayıcısı kullanmanız gerekir. Bir anahtar kapsayıcısında özel anahtar depolama hakkında daha fazla bilgi için bkz. [nasıl yapılır: asimetrik anahtarları bir anahtar kapsayıcısında depolama](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Aşağıdaki kod örneği, **RSACryptoServiceProvider** sınıfının yeni bir örneğini oluşturur, ortak/özel anahtar çifti oluşturur ve ortak anahtar bilgilerini bir **RSAParameters** yapısına kaydeder.  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Şifreleme](../../../docs/standard/security/encrypting-data.md)
- [Verilerin Şifresini Çözme](../../../docs/standard/security/decrypting-data.md)
- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
- [Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)

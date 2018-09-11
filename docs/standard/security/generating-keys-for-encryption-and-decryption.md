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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 839a04d8a06e782582705cf0d9ad92d2e2df6af6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44265123"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma
Anahtarları oluşturmak ve yönetmek, şifreleme işleminin önemli bir parçasıdır. Simetrik algoritmalar, bir anahtarın ve başlangıç vektörünün (IV) oluşturulmasını gerektirir. Anahtar, verinizin şifresini çözmemesi gereken herkesten gizli tutulmalıdır. IV'nin gizli olması gerekmez ancak her oturum için değiştirilmesi gerekir. Asimetrik algoritmalar bir ortak anahtarın, bir de özel anahtarın oluşturulmasını gerektirir. Ortak anahtar herhangi birine verilebilirken, özel anahtar yalnızca ortak anahtar ile şifrelenen verilerin şifresini çözecek tarafça bilinmelidir. Bu bölümde, hem simetrik, hem de asimetrik algoritmalar için anahtarların nasıl oluşturulacağı ve yönetileceği açıklanmaktadır.  
  
## <a name="symmetric-keys"></a>Simetrik Anahtarlar  
 .NET Framework tarafından sağlanan simetrik şifreleme sınıfları, veriler üzerine şifreleme ve şifre çözme yapabilmek için bir anahtar ve yeni bir başlatma vektörü (IV) gerektirir. Varsayılan oluşturucuyu kullanarak yönetilen simetrik şifreleme sınıflarından birinin yeni bir örneğini oluşturduğunuzda, otomatik olarak yeni bir anahtar ve IV oluşturulur. Verilerinizin şifresini çözmesine izin verdiğiniz kişilerin aynı anahtara ve IV'ye sahip olup aynı algoritmayı kullanması gerekir. Genellikle, her oturum için yeni bir anahtar ve IV oluşturulmalıdır, ve ne anahtar ne de IV daha sonraki bir oturumda kullanılmak üzere saklanmalıdır.  
  
 Bir simetrik anahtarı ve IV'yi uzaktaki bir kişiye iletmek için, genellikle simetrik anahtarı asimetrik şifreleme kullanarak şifrelersiniz. Anahtarı güvenli olmayan bir ağ üzerinde şifrelemeden göndermek güvenli değildir, çünkü anahtarı ve IV'yi yakalayan herhangi biri verilerinizin şifresini çözebilir. Şifreleme kullanarak veri değişimi hakkında daha fazla bilgi için bkz. [şifreleme düzeni oluşturma](../../../docs/standard/security/creating-a-cryptographic-scheme.md).  
  
 Aşağıdaki örnek, TripleDES algoritmasını uygulayan <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> sınıfının yeni bir örneğinin oluşturulmasını gösterir.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
```  
  
 Önceki kod yürütüldüğünde, yeni bir anahtar ve IV oluşturulur ve bulundukları **anahtarı** ve **IV** özellikleri, sırasıyla.  
  
 Bazen birden çok anahtar oluşturmanız gerekebilir. Bu durumda, Simetrik algoritma uygulayan bir sınıf yeni bir örneğini oluşturabilir ve çağırarak yeni bir anahtar ve IV oluşturma **GenerateKey** ve **Generateıv** yöntemleri. Aşağıdaki kod örneği, asimetrik şifreleme sınıfının yeni bir örneği oluşturulduktan sonra yeni anahtar ve IV'lerin nasıl oluşturulduğunu gösterir.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
TDES.GenerateIV()  
TDES.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
TDES.GenerateIV();  
TDES.GenerateKey();  
```  
  
 Önceki kod yürütüldüğünde, bir anahtar ve IV oluşturulur, yeni bir örneğini **TripleDESCryptoServiceProvider** yapılır. Başka bir anahtar ve IV oluşturulur **GenerateKey** ve **Generateıv** yöntemi çağrılır.  
  
## <a name="asymmetric-keys"></a>Asimetrik Anahtarlar  
 .NET Framework, asimetrik şifreleme için <xref:System.Security.Cryptography.RSACryptoServiceProvider> ve <xref:System.Security.Cryptography.DSACryptoServiceProvider> sınıflarını sağlar. Bu sınıflar, yeni bir örnek oluşturmak için varsayılan oluşturucuyu kullandığınızda bir ortak/özel anahtar çifti oluşturur. Asimetrik anahtarlar birden çok oturumda kullanılmak üzere saklanabilir ya da yalnızca tek bir oturum için oluşturulabilir. Ortak anahtar genel olarak kullanılabilir olabilse de, özel anahtar dikkatle korunmalıdır.  
  
 Bir asimetrik sınıfın her yeni örneği oluşturulduğunda bir ortak/özel anahtar çifti oluşturulur. Sınıfın yeni bir örneği oluşturulduktan sonra, anahtar bilgileri şu iki yöntemden biriyle alınabilir:  
  
-   <xref:System.Security.Cryptography.RSA.ToXmlString%2A> Anahtar bilgilerini bir XML temsilini döndüren bir yöntem.  
  
-   Anahtar bilgilerini tutan bir <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> yapısı döndüren <xref:System.Security.Cryptography.RSAParameters> yöntemi.  
  
 İki yöntem de yalnızca ortak anahtar bilgisinin mi dönüleceğini yoksa hem ortak anahtar hem de özel anahtar bilgisinin mi dönüleceğini belirten bir Boolean değerini kabul eder. Bir **RSACryptoServiceProvider** sınıfı değeri olarak başlatılabilir bir **RSAParameters** kullanarak yapısı <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> yöntemi.  
  
 Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır. Özel anahtarı depolamanız gerekiyorsa, bir anahtar kapsayıcısı kullanmanız gerekir. Özel bir anahtarı bir anahtar kapsayıcısı içinde saklamak hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir anahtar kapsayıcısında asimetrik anahtarlar Store](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Aşağıdaki kod örneğinde yeni bir örneğini oluşturur **RSACryptoServiceProvider** sınıfı, bir ortak/özel anahtar çifti oluşturma ve ortak anahtar bilgisini kaydeder bir **RSAParameters** yapısı.  
  
```vb  
'Generate a public/private key pair.  
Dim RSA as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim RSAKeyInfo As RSAParameters = RSA.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters RSAKeyInfo = RSA.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Şifreleme](../../../docs/standard/security/encrypting-data.md)  
- [Verilerin Şifresini Çözme](../../../docs/standard/security/decrypting-data.md)  
- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)  
- [Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)

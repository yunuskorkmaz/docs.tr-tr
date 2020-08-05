---
title: Veri Şifreleme
description: Simetrik bir algoritma veya asimetrik algoritma kullanarak .NET 'teki verileri şifrelemeyi öğrenin.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], symmetric
- symmetric encryption
- cryptography [.NET], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 8a8b5988a13ab571284b08c7aaece3542467aa71
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556975"
---
# <a name="encrypting-data"></a>Veri Şifreleme

Simetrik şifreleme ve asimetrik şifreleme farklı süreçler kullanılarak gerçekleştirilir. Simetrik şifreleme, akışlarda gerçekleştirilir ve bu nedenle büyük miktarlarda veriyi şifrelemek yararlı olur. Asimetrik şifreleme, az sayıda bayt üzerinde gerçekleştirilir ve bu nedenle yalnızca küçük miktarlarda veri için yararlıdır.  
  
## <a name="symmetric-encryption"></a>Simetrik şifreleme  

Yönetilen simetrik şifreleme sınıfları, <xref:System.Security.Cryptography.CryptoStream> akışa okunan verileri şifreleyen, adlı özel bir akış sınıfıyla kullanılır. **CryptoStream** sınıfı, yönetilen bir Stream sınıfı, arabirimini uygulayan bir sınıf <xref:System.Security.Cryptography.ICryptoTransform> (şifreleme algoritması uygulayan bir sınıftan oluşturulan) ve <xref:System.Security.Cryptography.CryptoStreamMode> **CryptoStream**için izin verilen erişim türünü açıklayan bir sabit değer ile başlatılır. **CryptoStream** sınıfı,, <xref:System.IO.Stream> ve dahil olmak üzere sınıfından türetilen herhangi bir sınıf kullanılarak başlatılabilir <xref:System.IO.FileStream> <xref:System.IO.MemoryStream> <xref:System.Net.Sockets.NetworkStream> . Bu sınıfları kullanarak, çeşitli Stream nesnelerinde simetrik şifreleme yapabilirsiniz.  
  
Aşağıdaki örnek, algoritma için varsayılan uygulama sınıfının yeni bir örneğinin nasıl oluşturulacağını göstermektedir <xref:System.Security.Cryptography.Aes> . Örnek, bir **CryptoStream** sınıfında şifrelemeyi gerçekleştirmek için kullanılır. Bu örnekte, **CryptoStream** , `myStream` herhangi bir tür yönetilen akış olabilecek adlı bir Stream nesnesi ile başlatılır. **AES** sınıfından **CreateEncryptor** yöntemi, şifreleme IÇIN kullanılan anahtarı ve IV ' i geçti. Bu durumda, varsayılan anahtar ve IV tarafından oluşturulan IV `aes` kullanılır.
  
```vb  
Dim aes As Aes = Aes.Create()  
Dim cryptStream As New CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
```  
  
```csharp  
Aes aes = Aes.Create();  
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write);  
```  
  
Bu kod yürütüldükten sonra, **CryptoStream** nesnesine yazılan tüm veriler AES algoritması kullanılarak şifrelenir.  
  
Aşağıdaki örnek, bir akış oluşturma, akışı şifreleme, akışa yazma ve akışı kapatma sürecinin tamamını gösterir. Bu örnek, **CryptoStream** sınıfı ve **AES** sınıfı kullanılarak şifrelenen bir dosya akışı oluşturur. Şifrelenmiş akışa bir ileti yazılır <xref:System.IO.StreamWriter> .
  
:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

Kod, AES Simetrik algoritmasını kullanarak akışı şifreler ve "Merhaba Dünya!" yaztır akışa. Kod başarılı olursa, *TestData.txt* adlı şifreli bir dosya oluşturur ve konsola aşağıdaki metni görüntüler:  
  
```console  
The text was encrypted.  
```  

[Verileri şifrelerini çözmek](decrypting-data.md)için simetrik şifre çözme örneğini kullanarak dosyanın şifresini çözebilirsiniz. Bu örnek ve bu örnekte aynı anahtar ve IV belirtilmelidir.

Ancak, bir özel durum ortaya çıktığında, kod konsola aşağıdaki metni görüntüler:  
  
```console  
The encryption failed.  
```

## <a name="asymmetric-encryption"></a>Asimetrik şifreleme

Asimetrik algoritmalar genellikle simetrik anahtar ve IV Şifrelemesi gibi küçük miktarlarda verileri şifrelemek için kullanılır. Genellikle, bir asimetrik şifreleme gerçekleştiren bir kişi, başka bir tarafın oluşturduğu ortak anahtarı kullanır. <xref:System.Security.Cryptography.RSA>Sınıfı bu amaçla .NET tarafından sağlanır.  
  
Aşağıdaki örnek, bir simetrik anahtar ve IV şifrelemek için ortak anahtar bilgilerini kullanır. Üçüncü bir tarafın ortak anahtarını temsil eden iki baytlık diziler başlatılır. Bir <xref:System.Security.Cryptography.RSAParameters> nesne bu değerlere başlatılır. Ardından, **RSAParameters** nesnesi (temsil ettiği ortak anahtarla birlikte) yöntemi kullanılarak bir **RSA** örneğine aktarılır <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> . Son olarak, bir sınıf tarafından oluşturulan özel anahtar ve IV <xref:System.Security.Cryptography.Aes> şifrelenir. Bu örnek, sistemlerde 128 bit şifrelemenin yüklü olmasını gerektirir.  
  
```vb  
Imports System
Imports System.Security.Cryptography

Module Module1

    Sub Main()
        'Initialize the byte arrays to the public key information.  
        Dim modulus As Byte() = {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19, 202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}

        Dim exponent As Byte() = {1, 0, 1}

        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte
        Dim encryptedSymmetricIV() As Byte

        'Create a new instance of the default RSA implementation class.
        Dim rsa As RSA = RSA.Create()

        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()

        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus
        rsaKeyInfo.Exponent = exponent

        'Import key parameters into rsa
        rsa.ImportParameters(rsaKeyInfo)

        'Create a new instance of the default Aes implementation class.  
        Dim aes As Aes = Aes.Create()

        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1)
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1)
    End Sub

End Module
```  
  
```csharp  
using System;
using System.Security.Cryptography;

class Class1
{
    static void Main()
    {
        //Initialize the byte arrays to the public key information.  
        byte[] modulus = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};

        byte[] exponent = { 1, 0, 1 };

        //Create values to store encrypted symmetric keys.  
        byte[] encryptedSymmetricKey;
        byte[] encryptedSymmetricIV;

        //Create a new instance of the RSA class.  
        RSA rsa = RSA.Create();

        //Create a new instance of the RSAParameters structure.  
        RSAParameters rsaKeyInfo = new RSAParameters();

        //Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus;
        rsaKeyInfo.Exponent = exponent;

        //Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo);

        //Create a new instance of the default Aes implementation class.  
        Aes aes = Aes.Create();

        //Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1);
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1);
    }
}
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma](generating-keys-for-encryption-and-decryption.md)
- [Verilerin Şifresini Çözme](decrypting-data.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları](vulnerabilities-cbc-mode.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)

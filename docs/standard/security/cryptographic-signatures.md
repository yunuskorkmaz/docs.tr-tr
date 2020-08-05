---
title: Şifreleme İmzası
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET], signatures
- security [.NET], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: ce2be1d509da4e399bf87e1c8df7ba061fc2707c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557014"
---
# <a name="cryptographic-signatures"></a>Şifreleme İmzası

Şifreleme dijital imzaları, veri bütünlüğü sağlamak için ortak anahtar algoritmaları kullanır. Verileri dijital imzayla imzaladığınızda, başka biri imzayı doğrulayabilirler ve verilerin sizi imzaladıktan sonra değiştirilmediğini kanıtlayabilirler. Dijital imzalar hakkında daha fazla bilgi için bkz. [Şifreleme Hizmetleri](cryptographic-services.md).

Bu konu, ad alanındaki sınıfları kullanarak dijital imzaların nasıl oluşturulacağını ve doğrulandığını açıklamaktadır <xref:System.Security.Cryptography> .

## <a name="generating-signatures"></a>Imza oluşturma

Dijital imzalar genellikle daha büyük verileri temsil eden karma değerlere uygulanır. Aşağıdaki örnek bir karma değere dijital imza uygular. İlk olarak, <xref:System.Security.Cryptography.RSA> ortak/özel anahtar çifti oluşturmak için sınıfının yeni bir örneği oluşturulur. Ardından,, <xref:System.Security.Cryptography.RSA> sınıfının yeni bir örneğine geçirilir <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> . Bu, özel anahtarı <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> aslında dijital imzalamayı gerçekleştirecek olan öğesine aktarır. Karma kodu imzalayabilmeniz için önce kullanmak üzere bir karma algoritması belirtmeniz gerekir. Bu örnek, SHA1 algoritmasını kullanır. Son olarak, <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> yöntemi imzalamayı gerçekleştirmek için çağrılır.

SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneririz.

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As RSA = RSA.Create()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSA instance to transfer the private key.
        Dim rsaFormatter As New RSAPKCS1SignatureFormatter(rsa)

        'Set the hash algorithm to SHA1.
        rsaFormatter.SetHashAlgorithm("SHA1")

        'Create a signature for hashValue and assign it to
        'signedHashValue.
        signedHashValue = rsaFormatter.CreateSignature(hashValue)
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
      //The hash value to sign.
      byte[] hashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};

      //The value to hold the signed value.
      byte[] signedHashValue;

      //Generate a public/private key pair.
      RSA rsa = RSA.Create();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSA instance to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

## <a name="verifying-signatures"></a>Imzalar doğrulanıyor

Verilerin belirli bir taraflarca imzalandığını doğrulamak için aşağıdaki bilgilere sahip olmanız gerekir:

- Verileri imzalayan tarafın ortak anahtarı.

- Dijital imza.

- İmzalanmış veriler.

- İmzalayan tarafından kullanılan karma algoritması.

Sınıfı tarafından imzalanan bir imzayı doğrulamak için <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfını kullanın. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>Sınıf, imzalayanın ortak anahtarı sağlanmalıdır. RSA için, genel anahtarı belirtmek üzere mod ve üs değerlerinin değerlerini kullanmanız gerekecektir. (Ortak/özel anahtar çiftini oluşturan tarafın bu değerleri sağlaması gerekir.) İlk olarak, <xref:System.Security.Cryptography.RSA> imzayı doğrulayacak ortak anahtarı tutacak bir nesne oluşturun ve sonra <xref:System.Security.Cryptography.RSAParameters> ortak anahtarı belirten mod ve üs değerlerine bir yapı başlatın.

Aşağıdaki kod, bir yapının oluşturulmasını gösterir <xref:System.Security.Cryptography.RSAParameters> . `Modulus`Özelliği adlı bir bayt dizisinin değerine ayarlanır `modulusData` ve `Exponent` özelliği adlı bir bayt dizisinin değerine ayarlanır `exponentData` .

```vb
Dim rsaKeyInfo As RSAParameters
rsaKeyInfo.Modulus = modulusData
rsaKeyInfo.Exponent = exponentData
```

```csharp
RSAParameters rsaKeyInfo;
rsaKeyInfo.Modulus = modulusData;
rsaKeyInfo.Exponent = exponentData;
```

Nesneyi oluşturduktan sonra <xref:System.Security.Cryptography.RSAParameters> , uygulama sınıfının yeni bir örneğini <xref:System.Security.Cryptography.RSA> ' de belirtilen değerlere başlatabilirsiniz <xref:System.Security.Cryptography.RSAParameters> . <xref:System.Security.Cryptography.RSA>Örnek, <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> anahtarı aktarmak için öğesinin oluşturucuya geçirilir.

Aşağıdaki örnek bu süreci göstermektedir. Bu örnekte, `hashValue` ve `signedHashValue` bir uzak tarafın sağladığı bayt dizilerdir. Uzak taraf, `hashValue` dijital imzayı üreten SHA1 algoritmasını kullanan imzalı `signedHashValue` . <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>Yöntemi, dijital imzanın geçerli olduğunu ve imzalamak için kullanıldığını doğrular `hashValue` .

SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneririz.  Ancak, imzayı oluşturmak için SHA1 kullanılmışsa, imzayı doğrulamak için SHA1 kullanmanız gerekir.

```vb
Dim rsa As RSA = RSA.Create()
rsa.ImportParameters(rsaKeyInfo)
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)
rsaDeformatter.SetHashAlgorithm("SHA1")
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then
   Console.WriteLine("The signature is valid.")
Else
   Console.WriteLine("The signature is not valid.")
End If
```

```csharp
RSA rsa = RSA.Create();
rsa.ImportParameters(rsaKeyInfo);
RSAPKCS1SignatureDeformatter rsaDeformatter = new RSAPKCS1SignatureDeformatter(rsa);
rsaDeformatter.SetHashAlgorithm("SHA1");
if(rsaDeformatter.VerifySignature(hashValue, signedHashValue))
{
   Console.WriteLine("The signature is valid.");
}
else
{
   Console.WriteLine("The signature is not valid.");
}
```

Bu kod parçası, imza geçerliyse "" ve değilse "" görüntülenir `The signature is valid` `The signature is not valid` .

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Şifreleme Modeli](cryptography-model.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)

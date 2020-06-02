---
title: Şifreleme İmzası
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET Framework], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET Framework], signatures
- security [.NET Framework], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: 9e69578ceffeeacb73cf059f5b577fe7c137b599
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288400"
---
# <a name="cryptographic-signatures"></a>Şifreleme İmzası

Şifreleme dijital imzaları, veri bütünlüğü sağlamak için ortak anahtar algoritmaları kullanır. Verileri dijital imzayla imzaladığınızda, başka biri imzayı doğrulayabilirler ve verilerin sizi imzaladıktan sonra değiştirilmediğini kanıtlayabilirler. Dijital imzalar hakkında daha fazla bilgi için bkz. [Şifreleme Hizmetleri](cryptographic-services.md).

Bu konu, ad alanındaki sınıfları kullanarak dijital imzaların nasıl oluşturulacağını ve doğrulandığını açıklamaktadır <xref:System.Security.Cryptography?displayProperty=nameWithType> .

## <a name="generating-signatures"></a>Imza oluşturma

Dijital imzalar genellikle daha büyük verileri temsil eden karma değerlere uygulanır. Aşağıdaki örnek bir karma değere dijital imza uygular. İlk olarak, <xref:System.Security.Cryptography.RSACryptoServiceProvider> ortak/özel anahtar çifti oluşturmak için sınıfının yeni bir örneği oluşturulur. Ardından,, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfının yeni bir örneğine geçirilir <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> . Bu, özel anahtarı <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> aslında dijital imzalamayı gerçekleştirecek olan öğesine aktarır. Karma kodu imzalayabilmeniz için önce kullanmak üzere bir karma algoritması belirtmeniz gerekir. Bu örnek, SHA1 algoritmasını kullanır. Son olarak, <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> yöntemi imzalamayı gerçekleştirmek için çağrılır.

Microsoft, SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneriyor.

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As New RSACryptoServiceProvider()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSACryptoServiceProvider to transfer the private key.
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
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSACryptoServiceProvider to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

### <a name="signing-xml-files"></a>XML dosyalarını imzalama

.NET Framework, <xref:System.Security.Cryptography.Xml> XML imzalamayı sağlayan ad alanını sağlar. XML 'nin belirli bir kaynaktan kaynaklandığını doğrulamak istediğinizde XML imzalama önemlidir. Örneğin, XML kullanan bir stok teklif hizmeti kullanıyorsanız, imzalanmışsa XML kaynağını doğrulayabilirsiniz.

Bu ad alanındaki sınıflar, World Wide Web Konsorsiyumu [XML Imza söz dizimini ve işlem](https://www.w3.org/TR/xmldsig-core/) önerilerini izler.

## <a name="verifying-signatures"></a>Imzalar doğrulanıyor

Verilerin belirli bir taraflarca imzalandığını doğrulamak için aşağıdaki bilgilere sahip olmanız gerekir:

- Verileri imzalayan tarafın ortak anahtarı.

- Dijital imza.

- İmzalanmış veriler.

- İmzalayan tarafından kullanılan karma algoritması.

Sınıfı tarafından imzalanan bir imzayı doğrulamak için <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfını kullanın. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>Sınıf, imzalayanın ortak anahtarı sağlanmalıdır. Ortak anahtarı belirtmek için mod ve üs değerlerinin değerlerine ihtiyacınız olacaktır. (Ortak/özel anahtar çiftini oluşturan tarafın bu değerleri sağlaması gerekir.) İlk olarak, <xref:System.Security.Cryptography.RSACryptoServiceProvider> imzayı doğrulayacak ortak anahtarı tutacak bir nesne oluşturun ve sonra <xref:System.Security.Cryptography.RSAParameters> ortak anahtarı belirten mod ve üs değerlerine bir yapı başlatın.

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

Nesneyi oluşturduktan sonra <xref:System.Security.Cryptography.RSAParameters> , sınıfının yeni bir örneğini <xref:System.Security.Cryptography.RSACryptoServiceProvider> ' de belirtilen değerlere başlatabilirsiniz <xref:System.Security.Cryptography.RSAParameters> . , Buna karşılık, <xref:System.Security.Cryptography.RSACryptoServiceProvider> anahtarı aktarmak için bir öğesinin oluşturucusuna geçirilir <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> .

Aşağıdaki örnek bu süreci göstermektedir. Bu örnekte, `hashValue` ve `signedHashValue` bir uzak tarafın sağladığı bayt dizilerdir. Uzak taraf, `hashValue` dijital imzayı üreten SHA1 algoritmasını kullanan imzalı `signedHashValue` . <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>Yöntemi, dijital imzanın geçerli olduğunu ve imzalamak için kullanıldığını doğrular `hashValue` .

```vb
Dim rsa As New RSACryptoServiceProvider()
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
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();
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

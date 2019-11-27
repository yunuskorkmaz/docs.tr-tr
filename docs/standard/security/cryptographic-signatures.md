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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de64af1a4617af39b0ef8e054292a402d6a145e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350466"
---
# <a name="cryptographic-signatures"></a>Şifreleme İmzası

Şifreleme dijital imzaları, veri bütünlüğü sağlamak için ortak anahtar algoritmaları kullanır. Verileri dijital imzayla imzaladığınızda, başka biri imzayı doğrulayabilirler ve verilerin sizi imzaladıktan sonra değiştirilmediğini kanıtlayabilirler. Dijital imzalar hakkında daha fazla bilgi için bkz. [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md).

Bu konu, <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanındaki sınıfları kullanarak dijital imzaların nasıl oluşturulacağını ve doğrulandığını açıklamaktadır.

## <a name="generating-signatures"></a>Imza oluşturma

Dijital imzalar genellikle daha büyük verileri temsil eden karma değerlere uygulanır. Aşağıdaki örnek bir karma değere dijital imza uygular. İlk olarak, ortak/özel anahtar çifti oluşturmak için <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfının yeni bir örneği oluşturulur. Sonra <xref:System.Security.Cryptography.RSACryptoServiceProvider>, <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfının yeni bir örneğine geçirilir. Bu, özel anahtarı, aslında dijital imzalamayı gerçekleştiren <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>aktarır. Karma kodu imzalayabilmeniz için önce kullanmak üzere bir karma algoritması belirtmeniz gerekir. Bu örnek, SHA1 algoritmasını kullanır. Son olarak, imzalamayı gerçekleştirmek için <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> yöntemi çağırılır.

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

.NET Framework, XML imzalamayı sağlayan <xref:System.Security.Cryptography.Xml> ad alanını sağlar. XML 'nin belirli bir kaynaktan kaynaklandığını doğrulamak istediğinizde XML imzalama önemlidir. Örneğin, XML kullanan bir stok teklif hizmeti kullanıyorsanız, imzalanmışsa XML kaynağını doğrulayabilirsiniz.

Bu ad alanındaki sınıflar, World Wide Web Konsorsiyumu [XML Imza söz dizimini ve işlem](https://www.w3.org/TR/xmldsig-core/) önerilerini izler.

## <a name="verifying-signatures"></a>Imzalar doğrulanıyor

Verilerin belirli bir taraflarca imzalandığını doğrulamak için aşağıdaki bilgilere sahip olmanız gerekir:

- Verileri imzalayan tarafın ortak anahtarı.

- Dijital imza.

- İmzalanmış veriler.

- İmzalayan tarafından kullanılan karma algoritması.

<xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfı tarafından imzalanan bir imzayı doğrulamak için <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfını kullanın. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfı, imzalayanın ortak anahtarı sağlanmalıdır. Ortak anahtarı belirtmek için mod ve üs değerlerinin değerlerine ihtiyacınız olacaktır. (Ortak/özel anahtar çiftini oluşturan tarafın bu değerleri sağlaması gerekir.) Önce imzayı doğrulayacak ortak anahtarı tutmak üzere bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesi oluşturun ve sonra ortak anahtarı belirten mod ve üs değerlerini bir <xref:System.Security.Cryptography.RSAParameters> yapısını başlatın.

Aşağıdaki kod <xref:System.Security.Cryptography.RSAParameters> yapısını oluşturmayı gösterir. `Modulus` özelliği, `modulusData` adlı bir bayt dizisinin değerine ayarlanır ve `Exponent` özelliği `exponentData`adlı bir bayt dizisinin değerine ayarlanır.

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

<xref:System.Security.Cryptography.RSAParameters> nesnesini oluşturduktan sonra, <xref:System.Security.Cryptography.RSAParameters>belirtilen değerlere <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfının yeni bir örneğini başlatabilirsiniz. <xref:System.Security.Cryptography.RSACryptoServiceProvider>, anahtarı aktarmak için <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> oluşturucusuna geçirilir.

Aşağıdaki örnek bu süreci göstermektedir. Bu örnekte, `hashValue` ve `signedHashValue`, uzak bir tarafın sağladığı bayt dizilerdir. Uzak taraf, dijital imza `signedHashValue`üreten SHA1 algoritmasını kullanarak `hashValue` imzalamıştır. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> yöntemi, dijital imzanın geçerli olduğunu ve `hashValue`imzalamak için kullanıldığını doğrular.

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

İmza geçerliyse, bu kod parçası "`The signature is valid`" ve değilse "`The signature is not valid`" görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)

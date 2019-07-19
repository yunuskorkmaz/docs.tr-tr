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
ms.openlocfilehash: 862d520073dde1b935510bc7c68782c1204c6111
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331645"
---
# <a name="cryptographic-signatures"></a>Şifreleme İmzası

<a name="top"></a>Şifreleme dijital imzaları, veri bütünlüğü sağlamak için ortak anahtar algoritmaları kullanır. Verileri dijital imzayla imzaladığınızda, başka biri imzayı doğrulayabilirler ve verilerin sizi imzaladıktan sonra değiştirilmediğini kanıtlayabilirler. Dijital imzalar hakkında daha fazla bilgi için bkz. [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md).

Bu konu, <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanındaki sınıfları kullanarak dijital imzaların nasıl oluşturulacağını ve doğrulandığını açıklamaktadır.

- [Imza oluşturma](#generate)

- [Imzalar doğrulanıyor](#verify)

<a name="generate"></a>

## <a name="generating-signatures"></a>Imza oluşturma

Dijital imzalar genellikle daha büyük verileri temsil eden karma değerlere uygulanır. Aşağıdaki örnek bir karma değere dijital imza uygular. İlk olarak, ortak/özel anahtar <xref:System.Security.Cryptography.RSACryptoServiceProvider> çifti oluşturmak için sınıfının yeni bir örneği oluşturulur. Ardından,, <xref:System.Security.Cryptography.RSACryptoServiceProvider> <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfının yeni bir örneğine geçirilir. Bu, özel anahtarı aslında dijital imzalamayı <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>gerçekleştirecek olan öğesine aktarır. Karma kodu imzalayabilmeniz için önce kullanmak üzere bir karma algoritması belirtmeniz gerekir. Bu örnek, SHA1 algoritmasını kullanır. Son olarak, <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> yöntemi imzalamayı gerçekleştirmek için çağrılır.

Microsoft, SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneriyor.

```vb
Imports System
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

.NET Framework, XML imzalamayı <xref:System.Security.Cryptography.Xml> sağlayan ad alanını sağlar. XML 'nin belirli bir kaynaktan kaynaklandığını doğrulamak istediğinizde XML imzalama önemlidir. Örneğin, XML kullanan bir stok teklif hizmeti kullanıyorsanız, imzalanmışsa XML kaynağını doğrulayabilirsiniz.

Bu ad alanındaki sınıflar, World Wide Web Konsorsiyumu [XML Imza söz dizimini ve işlem](https://www.w3.org/TR/xmldsig-core/) önerilerini izler.

[Başa dön](#top)

<a name="verify"></a>

## <a name="verifying-signatures"></a>Imzalar doğrulanıyor

Verilerin belirli bir taraflarca imzalandığını doğrulamak için aşağıdaki bilgilere sahip olmanız gerekir:

- Verileri imzalayan tarafın ortak anahtarı.

- Dijital imza.

- İmzalanmış veriler.

- İmzalayan tarafından kullanılan karma algoritması.

<xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> Sınıfı tarafından imzalanan bir imzayı doğrulamak için <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfını kullanın. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Sınıf, imzalayanın ortak anahtarı sağlanmalıdır. Ortak anahtarı belirtmek için mod ve üs değerlerinin değerlerine ihtiyacınız olacaktır. (Ortak/özel anahtar çiftini oluşturan tarafın bu değerleri sağlaması gerekir.) İlk olarak, <xref:System.Security.Cryptography.RSACryptoServiceProvider> imzayı doğrulayacak ortak anahtarı tutacak bir nesne oluşturun ve sonra ortak anahtarı belirten mod ve üs <xref:System.Security.Cryptography.RSAParameters> değerlerine bir yapı başlatın.

Aşağıdaki kod, bir <xref:System.Security.Cryptography.RSAParameters> yapının oluşturulmasını gösterir. Özelliği adlı `modulusData` bir bayt dizisinin değerine ayarlanır ve `Exponent` özelliği adlı `exponentData`bir bayt dizisinin değerine ayarlanır. `Modulus`

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

Nesneyi oluşturduktan sonra, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfının yeni bir örneğini ' de <xref:System.Security.Cryptography.RSAParameters>belirtilen değerlere başlatabilirsiniz. <xref:System.Security.Cryptography.RSAParameters> , Buna karşılık, anahtarı aktarmak için bir <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> öğesinin oluşturucusuna geçirilir. <xref:System.Security.Cryptography.RSACryptoServiceProvider>

Aşağıdaki örnek bu süreci göstermektedir. Bu örnekte, `hashValue` ve `signedHashValue` bir uzak tarafın sağladığı bayt dizilerdir. Uzak taraf, dijital imzayı `hashValue` `signedHashValue`üreten SHA1 algoritmasını kullanan imzalı. Yöntemi, dijital imzanın geçerli olduğunu ve `hashValue`imzalamak için kullanıldığını doğrular. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>

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

Bu kod parçası, imza geçerliyse`The signature is valid`""`The signature is not valid`ve değilse "" görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)

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
# <a name="cryptographic-signatures"></a><span data-ttu-id="2bc0a-102">Şifreleme İmzası</span><span class="sxs-lookup"><span data-stu-id="2bc0a-102">Cryptographic Signatures</span></span>

<a name="top"></a><span data-ttu-id="2bc0a-103">Şifreleme dijital imzaları, veri bütünlüğü sağlamak için ortak anahtar algoritmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="2bc0a-104">Verileri dijital imzayla imzaladığınızda, başka biri imzayı doğrulayabilirler ve verilerin sizi imzaladıktan sonra değiştirilmediğini kanıtlayabilirler.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="2bc0a-105">Dijital imzalar hakkında daha fazla bilgi için bkz. [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="2bc0a-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>

<span data-ttu-id="2bc0a-106">Bu konu, <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanındaki sınıfları kullanarak dijital imzaların nasıl oluşturulacağını ve doğrulandığını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

- [<span data-ttu-id="2bc0a-107">Imza oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bc0a-107">Generating Signatures</span></span>](#generate)

- [<span data-ttu-id="2bc0a-108">Imzalar doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="2bc0a-108">Verifying Signatures</span></span>](#verify)

<a name="generate"></a>

## <a name="generating-signatures"></a><span data-ttu-id="2bc0a-109">Imza oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bc0a-109">Generating Signatures</span></span>

<span data-ttu-id="2bc0a-110">Dijital imzalar genellikle daha büyük verileri temsil eden karma değerlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="2bc0a-111">Aşağıdaki örnek bir karma değere dijital imza uygular.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="2bc0a-112">İlk olarak, ortak/özel anahtar <xref:System.Security.Cryptography.RSACryptoServiceProvider> çifti oluşturmak için sınıfının yeni bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="2bc0a-113">Ardından,, <xref:System.Security.Cryptography.RSACryptoServiceProvider> <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfının yeni bir örneğine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="2bc0a-114">Bu, özel anahtarı aslında dijital imzalamayı <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>gerçekleştirecek olan öğesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="2bc0a-115">Karma kodu imzalayabilmeniz için önce kullanmak üzere bir karma algoritması belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="2bc0a-116">Bu örnek, SHA1 algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="2bc0a-117">Son olarak, <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> yöntemi imzalamayı gerçekleştirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="2bc0a-118">Microsoft, SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneriyor.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-118">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>

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

### <a name="signing-xml-files"></a><span data-ttu-id="2bc0a-119">XML dosyalarını imzalama</span><span class="sxs-lookup"><span data-stu-id="2bc0a-119">Signing XML Files</span></span>

<span data-ttu-id="2bc0a-120">.NET Framework, XML imzalamayı <xref:System.Security.Cryptography.Xml> sağlayan ad alanını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-120">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="2bc0a-121">XML 'nin belirli bir kaynaktan kaynaklandığını doğrulamak istediğinizde XML imzalama önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-121">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="2bc0a-122">Örneğin, XML kullanan bir stok teklif hizmeti kullanıyorsanız, imzalanmışsa XML kaynağını doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-122">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="2bc0a-123">Bu ad alanındaki sınıflar, World Wide Web Konsorsiyumu [XML Imza söz dizimini ve işlem](https://www.w3.org/TR/xmldsig-core/) önerilerini izler.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-123">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

[<span data-ttu-id="2bc0a-124">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2bc0a-124">Back to top</span></span>](#top)

<a name="verify"></a>

## <a name="verifying-signatures"></a><span data-ttu-id="2bc0a-125">Imzalar doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="2bc0a-125">Verifying Signatures</span></span>

<span data-ttu-id="2bc0a-126">Verilerin belirli bir taraflarca imzalandığını doğrulamak için aşağıdaki bilgilere sahip olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2bc0a-126">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="2bc0a-127">Verileri imzalayan tarafın ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-127">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="2bc0a-128">Dijital imza.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-128">The digital signature.</span></span>

- <span data-ttu-id="2bc0a-129">İmzalanmış veriler.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-129">The data that was signed.</span></span>

- <span data-ttu-id="2bc0a-130">İmzalayan tarafından kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-130">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="2bc0a-131"><xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> Sınıfı tarafından imzalanan bir imzayı doğrulamak için <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-131">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="2bc0a-132"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Sınıf, imzalayanın ortak anahtarı sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-132">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="2bc0a-133">Ortak anahtarı belirtmek için mod ve üs değerlerinin değerlerine ihtiyacınız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-133">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="2bc0a-134">(Ortak/özel anahtar çiftini oluşturan tarafın bu değerleri sağlaması gerekir.) İlk olarak, <xref:System.Security.Cryptography.RSACryptoServiceProvider> imzayı doğrulayacak ortak anahtarı tutacak bir nesne oluşturun ve sonra ortak anahtarı belirten mod ve üs <xref:System.Security.Cryptography.RSAParameters> değerlerine bir yapı başlatın.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-134">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="2bc0a-135">Aşağıdaki kod, bir <xref:System.Security.Cryptography.RSAParameters> yapının oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-135">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="2bc0a-136">Özelliği adlı `modulusData` bir bayt dizisinin değerine ayarlanır ve `Exponent` özelliği adlı `exponentData`bir bayt dizisinin değerine ayarlanır. `Modulus`</span><span class="sxs-lookup"><span data-stu-id="2bc0a-136">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="2bc0a-137">Nesneyi oluşturduktan sonra, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfının yeni bir örneğini ' de <xref:System.Security.Cryptography.RSAParameters>belirtilen değerlere başlatabilirsiniz. <xref:System.Security.Cryptography.RSAParameters></span><span class="sxs-lookup"><span data-stu-id="2bc0a-137">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="2bc0a-138">, Buna karşılık, anahtarı aktarmak için bir <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> öğesinin oluşturucusuna geçirilir. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="2bc0a-138">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="2bc0a-139">Aşağıdaki örnek bu süreci göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-139">The following example illustrates this process.</span></span> <span data-ttu-id="2bc0a-140">Bu örnekte, `hashValue` ve `signedHashValue` bir uzak tarafın sağladığı bayt dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-140">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="2bc0a-141">Uzak taraf, dijital imzayı `hashValue` `signedHashValue`üreten SHA1 algoritmasını kullanan imzalı.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-141">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="2bc0a-142">Yöntemi, dijital imzanın geçerli olduğunu ve `hashValue`imzalamak için kullanıldığını doğrular. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2bc0a-142">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

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

<span data-ttu-id="2bc0a-143">Bu kod parçası, imza geçerliyse`The signature is valid`""`The signature is not valid`ve değilse "" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-143">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bc0a-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bc0a-144">See also</span></span>

- [<span data-ttu-id="2bc0a-145">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="2bc0a-145">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

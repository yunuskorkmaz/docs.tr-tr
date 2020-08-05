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
# <a name="cryptographic-signatures"></a><span data-ttu-id="f98f7-102">Şifreleme İmzası</span><span class="sxs-lookup"><span data-stu-id="f98f7-102">Cryptographic Signatures</span></span>

<span data-ttu-id="f98f7-103">Şifreleme dijital imzaları, veri bütünlüğü sağlamak için ortak anahtar algoritmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f98f7-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="f98f7-104">Verileri dijital imzayla imzaladığınızda, başka biri imzayı doğrulayabilirler ve verilerin sizi imzaladıktan sonra değiştirilmediğini kanıtlayabilirler.</span><span class="sxs-lookup"><span data-stu-id="f98f7-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="f98f7-105">Dijital imzalar hakkında daha fazla bilgi için bkz. [Şifreleme Hizmetleri](cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="f98f7-105">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="f98f7-106">Bu konu, ad alanındaki sınıfları kullanarak dijital imzaların nasıl oluşturulacağını ve doğrulandığını açıklamaktadır <xref:System.Security.Cryptography> .</span><span class="sxs-lookup"><span data-stu-id="f98f7-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="f98f7-107">Imza oluşturma</span><span class="sxs-lookup"><span data-stu-id="f98f7-107">Generating Signatures</span></span>

<span data-ttu-id="f98f7-108">Dijital imzalar genellikle daha büyük verileri temsil eden karma değerlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f98f7-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="f98f7-109">Aşağıdaki örnek bir karma değere dijital imza uygular.</span><span class="sxs-lookup"><span data-stu-id="f98f7-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="f98f7-110">İlk olarak, <xref:System.Security.Cryptography.RSA> ortak/özel anahtar çifti oluşturmak için sınıfının yeni bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f98f7-110">First, a new instance of the <xref:System.Security.Cryptography.RSA> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="f98f7-111">Ardından,, <xref:System.Security.Cryptography.RSA> sınıfının yeni bir örneğine geçirilir <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> .</span><span class="sxs-lookup"><span data-stu-id="f98f7-111">Next, the <xref:System.Security.Cryptography.RSA> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="f98f7-112">Bu, özel anahtarı <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> aslında dijital imzalamayı gerçekleştirecek olan öğesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="f98f7-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="f98f7-113">Karma kodu imzalayabilmeniz için önce kullanmak üzere bir karma algoritması belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f98f7-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="f98f7-114">Bu örnek, SHA1 algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f98f7-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="f98f7-115">Son olarak, <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> yöntemi imzalamayı gerçekleştirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f98f7-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="f98f7-116">SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneririz.</span><span class="sxs-lookup"><span data-stu-id="f98f7-116">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>

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

## <a name="verifying-signatures"></a><span data-ttu-id="f98f7-117">Imzalar doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="f98f7-117">Verifying Signatures</span></span>

<span data-ttu-id="f98f7-118">Verilerin belirli bir taraflarca imzalandığını doğrulamak için aşağıdaki bilgilere sahip olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="f98f7-118">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="f98f7-119">Verileri imzalayan tarafın ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f98f7-119">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="f98f7-120">Dijital imza.</span><span class="sxs-lookup"><span data-stu-id="f98f7-120">The digital signature.</span></span>

- <span data-ttu-id="f98f7-121">İmzalanmış veriler.</span><span class="sxs-lookup"><span data-stu-id="f98f7-121">The data that was signed.</span></span>

- <span data-ttu-id="f98f7-122">İmzalayan tarafından kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="f98f7-122">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="f98f7-123">Sınıfı tarafından imzalanan bir imzayı doğrulamak için <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f98f7-123">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="f98f7-124"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>Sınıf, imzalayanın ortak anahtarı sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f98f7-124">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="f98f7-125">RSA için, genel anahtarı belirtmek üzere mod ve üs değerlerinin değerlerini kullanmanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="f98f7-125">For RSA, you will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="f98f7-126">(Ortak/özel anahtar çiftini oluşturan tarafın bu değerleri sağlaması gerekir.) İlk olarak, <xref:System.Security.Cryptography.RSA> imzayı doğrulayacak ortak anahtarı tutacak bir nesne oluşturun ve sonra <xref:System.Security.Cryptography.RSAParameters> ortak anahtarı belirten mod ve üs değerlerine bir yapı başlatın.</span><span class="sxs-lookup"><span data-stu-id="f98f7-126">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSA> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="f98f7-127">Aşağıdaki kod, bir yapının oluşturulmasını gösterir <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="f98f7-127">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="f98f7-128">`Modulus`Özelliği adlı bir bayt dizisinin değerine ayarlanır `modulusData` ve `Exponent` özelliği adlı bir bayt dizisinin değerine ayarlanır `exponentData` .</span><span class="sxs-lookup"><span data-stu-id="f98f7-128">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="f98f7-129">Nesneyi oluşturduktan sonra <xref:System.Security.Cryptography.RSAParameters> , uygulama sınıfının yeni bir örneğini <xref:System.Security.Cryptography.RSA> ' de belirtilen değerlere başlatabilirsiniz <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="f98f7-129">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSA> implementation class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="f98f7-130"><xref:System.Security.Cryptography.RSA>Örnek, <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> anahtarı aktarmak için öğesinin oluşturucuya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="f98f7-130">The <xref:System.Security.Cryptography.RSA> instance is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="f98f7-131">Aşağıdaki örnek bu süreci göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f98f7-131">The following example illustrates this process.</span></span> <span data-ttu-id="f98f7-132">Bu örnekte, `hashValue` ve `signedHashValue` bir uzak tarafın sağladığı bayt dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="f98f7-132">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="f98f7-133">Uzak taraf, `hashValue` dijital imzayı üreten SHA1 algoritmasını kullanan imzalı `signedHashValue` .</span><span class="sxs-lookup"><span data-stu-id="f98f7-133">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="f98f7-134"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>Yöntemi, dijital imzanın geçerli olduğunu ve imzalamak için kullanıldığını doğrular `hashValue` .</span><span class="sxs-lookup"><span data-stu-id="f98f7-134">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

<span data-ttu-id="f98f7-135">SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneririz.</span><span class="sxs-lookup"><span data-stu-id="f98f7-135">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>  <span data-ttu-id="f98f7-136">Ancak, imzayı oluşturmak için SHA1 kullanılmışsa, imzayı doğrulamak için SHA1 kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f98f7-136">However, if SHA1 was used to create the signature, you have to use SHA1 to verify the signature.</span></span>

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

<span data-ttu-id="f98f7-137">Bu kod parçası, imza geçerliyse "" ve değilse "" görüntülenir `The signature is valid` `The signature is not valid` .</span><span class="sxs-lookup"><span data-stu-id="f98f7-137">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="f98f7-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f98f7-138">See also</span></span>

- [<span data-ttu-id="f98f7-139">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="f98f7-139">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="f98f7-140">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="f98f7-140">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="f98f7-141">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="f98f7-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="f98f7-142">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="f98f7-142">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

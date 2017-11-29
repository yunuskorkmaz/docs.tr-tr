---
title: "Şifreleme İmzası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0651ae0fbc85b01d3e02354c06a9796804c8516e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="8d989-102">Şifreleme İmzası</span><span class="sxs-lookup"><span data-stu-id="8d989-102">Cryptographic Signatures</span></span>
<span data-ttu-id="8d989-103"><a name="top"></a>Şifreleme Dijital imzalar, veri bütünlüğünü sağlamak için ortak anahtar algoritmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d989-103"><a name="top"></a> Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="8d989-104">Veri bir dijital imza ile oturum açtığınızda başka birinin imzasını doğrular ve verileri sizden geldiğini ve siz imzaladıktan sonra değiştirilmiş değil kanıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d989-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="8d989-105">Dijital imzalar hakkında daha fazla bilgi için bkz: [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="8d989-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>  
  
 <span data-ttu-id="8d989-106">Bu konuda oluşturmak ve sınıflarda kullanarak dijital imzaları doğrulamak açıklanmaktadır <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8d989-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
-   [<span data-ttu-id="8d989-107">İmzalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d989-107">Generating Signatures</span></span>](#generate)  
  
-   [<span data-ttu-id="8d989-108">İmzaları doğrulama</span><span class="sxs-lookup"><span data-stu-id="8d989-108">Verifying Signatures</span></span>](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a><span data-ttu-id="8d989-109">İmzalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d989-109">Generating Signatures</span></span>  
 <span data-ttu-id="8d989-110">Dijital imzalar genellikle daha büyük veri temsil eden karma değerlerini uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8d989-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="8d989-111">Aşağıdaki örnek, bir karma değer bir dijital imza uygular.</span><span class="sxs-lookup"><span data-stu-id="8d989-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="8d989-112">İlk olarak, yeni bir örneğini <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı, bir ortak/özel anahtar çifti oluşturmak için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8d989-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="8d989-113">Ardından, <xref:System.Security.Cryptography.RSACryptoServiceProvider> için yeni bir örneği olarak geçirilmiş <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8d989-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="8d989-114">Bu özel anahtara aktarır <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, aslında gerçekleştirir dijital imza.</span><span class="sxs-lookup"><span data-stu-id="8d989-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="8d989-115">Karma kod oturum önce kullanmak için bir karma algoritması belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d989-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="8d989-116">Bu örnek SHA1 algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d989-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="8d989-117">Son olarak, <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> yöntemi imzalama gerçekleştirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8d989-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
        'The hash value to sign.  
        Dim HashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}  
  
        'The value to hold the signed value.  
        Dim SignedHashValue() As Byte  
  
        'Generate a public/private key pair.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create an RSAPKCS1SignatureFormatter object and pass it   
        'the RSACryptoServiceProvider to transfer the private key.  
        Dim RSAFormatter As New RSAPKCS1SignatureFormatter(RSA)  
  
        'Set the hash algorithm to SHA1.  
        RSAFormatter.SetHashAlgorithm("SHA1")  
  
        'Create a signature for HashValue and assign it to   
        'SignedHashValue.  
        SignedHashValue = RSAFormatter.CreateSignature(HashValue)  
    End Sub  
End Module  
  
using System;  
using System.Security.Cryptography;  
```  
  
```csharp  
class Class1  
{  
   static void Main()  
   {  
      //The hash value to sign.  
      byte[] HashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};  
  
      //The value to hold the signed value.  
      byte[] SignedHashValue;  
  
      //Generate a public/private key pair.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create an RSAPKCS1SignatureFormatter object and pass it the   
      //RSACryptoServiceProvider to transfer the private key.  
      RSAPKCS1SignatureFormatter RSAFormatter = new RSAPKCS1SignatureFormatter(RSA);  
  
      //Set the hash algorithm to SHA1.  
      RSAFormatter.SetHashAlgorithm("SHA1");  
  
      //Create a signature for HashValue and assign it to   
      //SignedHashValue.  
      SignedHashValue = RSAFormatter.CreateSignature(HashValue);  
   }  
}  
```  
  
### <a name="signing-xml-files"></a><span data-ttu-id="8d989-118">XML dosyaları imzalama</span><span class="sxs-lookup"><span data-stu-id="8d989-118">Signing XML Files</span></span>  
 <span data-ttu-id="8d989-119">.NET Framework sağlar <xref:System.Security.Cryptography.Xml> oturum XML ad alanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d989-119">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="8d989-120">XML imzalama XML belirli bir kaynaktan kaynaklandığı doğrulamak istediğinizde önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8d989-120">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="8d989-121">Örneğin, XML kullanan bir hisse senedi hizmet kullanıyorsanız, bunu kaydolduysanız XML kaynağını doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d989-121">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>  
  
 <span data-ttu-id="8d989-122">Bu ad alanındaki sınıflar izleyin [XML imzası sözdizimi ve işleme öneri](http://go.microsoft.com/fwlink/?LinkId=136777) World Wide Web Konsorsiyumu gelen.</span><span class="sxs-lookup"><span data-stu-id="8d989-122">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](http://go.microsoft.com/fwlink/?LinkId=136777) from the World Wide Web Consortium.</span></span>  
  
 [<span data-ttu-id="8d989-123">Başa dön</span><span class="sxs-lookup"><span data-stu-id="8d989-123">Back to top</span></span>](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a><span data-ttu-id="8d989-124">İmzaları doğrulama</span><span class="sxs-lookup"><span data-stu-id="8d989-124">Verifying Signatures</span></span>  
 <span data-ttu-id="8d989-125">Verileri belirli bir şahıs tarafından imzalandığı doğrulamak için aşağıdaki bilgileri olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="8d989-125">To verify that data was signed by a particular party, you must have the following information:</span></span>  
  
-   <span data-ttu-id="8d989-126">Veri imzalı taraf ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="8d989-126">The public key of the party that signed the data.</span></span>  
  
-   <span data-ttu-id="8d989-127">Dijital imza.</span><span class="sxs-lookup"><span data-stu-id="8d989-127">The digital signature.</span></span>  
  
-   <span data-ttu-id="8d989-128">İmzalandığı veriler.</span><span class="sxs-lookup"><span data-stu-id="8d989-128">The data that was signed.</span></span>  
  
-   <span data-ttu-id="8d989-129">İmzalayan tarafından kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="8d989-129">The hash algorithm used by the signer.</span></span>  
  
 <span data-ttu-id="8d989-130">Tarafından imzalanmış bir imzayı doğrulamak için <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfı, kullanın <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8d989-130">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="8d989-131"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Sınıfı olmalıdır imzalayan ortak anahtarını sağlanan.</span><span class="sxs-lookup"><span data-stu-id="8d989-131">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="8d989-132">Modulus ve ortak anahtarı belirtmek için üs değerlerini gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d989-132">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="8d989-133">(Genel/özel anahtar çifti oluşturulan taraf bu değerler sağlaması gerekir.) İlk oluşturma bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> imzasını doğrular ve ardından başlatma ortak anahtarı tutmak için nesne bir <xref:System.Security.Cryptography.RSAParameters> ortak anahtar belirtmesi mod ve üs değerlere yapısı.</span><span class="sxs-lookup"><span data-stu-id="8d989-133">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>  
  
 <span data-ttu-id="8d989-134">Aşağıdaki kod oluşturulmasını gösterir bir <xref:System.Security.Cryptography.RSAParameters> yapısı.</span><span class="sxs-lookup"><span data-stu-id="8d989-134">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="8d989-135">`Modulus` Özelliği olarak adlandırılan bir bayt dizisi değerine ayarlanmış `ModulusData` ve `Exponent` özelliği olarak adlandırılan bir bayt dizisi değerine ayarlanmış `ExponentData`.</span><span class="sxs-lookup"><span data-stu-id="8d989-135">The `Modulus` property is set to the value of a byte array called `ModulusData` and the `Exponent` property is set to the value of a byte array called `ExponentData`.</span></span>  
  
```vb  
Dim RSAKeyInfo As RSAParameters  
RSAKeyInfo.Modulus = ModulusData  
RSAKeyInfo.Exponent = ExponentData  
```  
  
```csharp  
RSAParameters RSAKeyInfo;  
RSAKeyInfo.Modulus = ModulusData;  
RSAKeyInfo.Exponent = ExponentData;  
```  
  
 <span data-ttu-id="8d989-136">Oluşturduktan sonra <xref:System.Security.Cryptography.RSAParameters> nesne, yeni bir örneğini başlatma <xref:System.Security.Cryptography.RSACryptoServiceProvider> belirtilen değerleri sınıfına <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="8d989-136">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="8d989-137"><xref:System.Security.Cryptography.RSACryptoServiceProvider> Sırayla oluşturucusuna geçirilen bir <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> anahtarı aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="8d989-137">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>  
  
 <span data-ttu-id="8d989-138">Aşağıdaki örnek, bu işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d989-138">The following example illustrates this process.</span></span> <span data-ttu-id="8d989-139">Bu örnekte, `HashValue` ve `SignedHashValue` uzak bir şirket tarafından sağlanan bayt dizidir.</span><span class="sxs-lookup"><span data-stu-id="8d989-139">In this example, `HashValue` and `SignedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="8d989-140">Uzak tarafı imzaladığı `HashValue` dijital imza oluşturan SHA1 algoritması kullanılarak `SignedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="8d989-140">The remote party has signed the `HashValue` using the SHA1 algorithm, producing the digital signature `SignedHashValue`.</span></span> <span data-ttu-id="8d989-141">Bu</span><span class="sxs-lookup"><span data-stu-id="8d989-141">The</span></span>  
  
 <span data-ttu-id="8d989-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>dijital imza geçerli olduğundan ve imzalamak için kullanılan yöntem doğrular `HashValue`.</span><span class="sxs-lookup"><span data-stu-id="8d989-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `HashValue`.</span></span>  
  
```vb  
Dim RSA As New RSACryptoServiceProvider()  
RSA.ImportParameters(RSAKeyInfo)  
Dim RSADeformatter As New RSAPKCS1SignatureDeformatter(RSA)  
RSADeformatter.SetHashAlgorithm("SHA1")  
If RSADeformatter.VerifySignature(HashValue, SignedHashValue) Then  
   Console.WriteLine("The signature is valid.")  
Else  
   Console.WriteLine("The signture is not valid.")  
End If  
```  
  
```csharp  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
RSA.ImportParameters(RSAKeyInfo);  
RSAPKCS1SignatureDeformatter RSADeformatter = new RSAPKCS1SignatureDeformatter(RSA);  
RSADeformatter.SetHashAlgorithm("SHA1");  
if(RSADeformatter.VerifySignature(HashValue, SignedHashValue))  
{  
   Console.WriteLine("The signature is valid.");  
}  
else  
{  
   Console.WriteLine("The signature is not valid.");  
}  
```  
  
 <span data-ttu-id="8d989-143">Bu kod parçası görüntüler "`The signature is valid`" imza geçerli olup olmadığını ve "`The signature is not valid`" değilse.</span><span class="sxs-lookup"><span data-stu-id="8d989-143">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d989-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d989-144">See Also</span></span>  
 [<span data-ttu-id="8d989-145">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="8d989-145">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

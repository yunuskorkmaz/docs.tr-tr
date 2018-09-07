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
ms.openlocfilehash: 3f9d83a0edb6dc2261931e422b0ae4c735d2e0d1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086102"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="082f4-102">Şifreleme İmzası</span><span class="sxs-lookup"><span data-stu-id="082f4-102">Cryptographic Signatures</span></span>
<a name="top"></a> <span data-ttu-id="082f4-103">Şifreleme Dijital imzalar, veri bütünlüğünü sağlamak için ortak anahtar algoritmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="082f4-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="082f4-104">Verileri bir dijital imza ile oturum açtığınızda başka birisi imzasını doğrulayabilir ve verileri sizin tarafınızdan oluşturulan ve siz imzaladıktan sonra değiştirilmiş değil kanıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="082f4-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="082f4-105">Dijital imzalar hakkında daha fazla bilgi için bkz: [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="082f4-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>  
  
 <span data-ttu-id="082f4-106">Bu konu başlığında, oluşturmak ve sınıfları kullanarak dijital imzaları doğrulamak açıklanmaktadır <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="082f4-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
-   [<span data-ttu-id="082f4-107">İmzalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="082f4-107">Generating Signatures</span></span>](#generate)  
  
-   [<span data-ttu-id="082f4-108">İmzaları doğrulama</span><span class="sxs-lookup"><span data-stu-id="082f4-108">Verifying Signatures</span></span>](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a><span data-ttu-id="082f4-109">İmzalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="082f4-109">Generating Signatures</span></span>  
 <span data-ttu-id="082f4-110">Dijital imzalar, genellikle daha büyük verileri temsil eden karma değerlerini uygulanır.</span><span class="sxs-lookup"><span data-stu-id="082f4-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="082f4-111">Aşağıdaki örnek, bir dijital imza için bir karma değer geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="082f4-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="082f4-112">İlk olarak, yeni bir örneğini <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı, bir ortak/özel anahtar çifti oluşturmak için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="082f4-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="082f4-113">Ardından, <xref:System.Security.Cryptography.RSACryptoServiceProvider> için yeni bir örneği olarak geçirilmiş olup <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="082f4-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="082f4-114">Bu özel anahtarı aktarır <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, aslında gerçekleştiren bir dijital imza.</span><span class="sxs-lookup"><span data-stu-id="082f4-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="082f4-115">Karma kod oturum açabilmesi için önce kullanmak için bir karma algoritmasını belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="082f4-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="082f4-116">Bu örnekte, SHA1 algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="082f4-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="082f4-117">Son olarak, <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> imzalamayı yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="082f4-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>  
  
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
  
### <a name="signing-xml-files"></a><span data-ttu-id="082f4-118">XML dosyaları imzalama</span><span class="sxs-lookup"><span data-stu-id="082f4-118">Signing XML Files</span></span>  
 <span data-ttu-id="082f4-119">.NET Framework sağlar <xref:System.Security.Cryptography.Xml> oturum XML ad alanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="082f4-119">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="082f4-120">XML imzalama XML belirli bir kaynaktan kaynaklanan doğrulamak istediğiniz durumlarda önemlidir.</span><span class="sxs-lookup"><span data-stu-id="082f4-120">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="082f4-121">Örneğin, XML kullanan bir hisse senedi hizmet kullanıyorsanız, imzalanmış olup olmadığını XML kaynağını doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="082f4-121">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>  
  
 <span data-ttu-id="082f4-122">Bu ad alanındaki sınıflar izleyin [Podpisu XML sözdizimi ve işleme öneri](https://www.w3.org/TR/xmldsig-core/) World Wide Web Consortium öğesinden.</span><span class="sxs-lookup"><span data-stu-id="082f4-122">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>  
  
 [<span data-ttu-id="082f4-123">Başa dön</span><span class="sxs-lookup"><span data-stu-id="082f4-123">Back to top</span></span>](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a><span data-ttu-id="082f4-124">İmzaları doğrulama</span><span class="sxs-lookup"><span data-stu-id="082f4-124">Verifying Signatures</span></span>  
 <span data-ttu-id="082f4-125">Verileri belirli bir şahıs tarafından imzalandığı doğrulamak için aşağıdaki bilgilere sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="082f4-125">To verify that data was signed by a particular party, you must have the following information:</span></span>  
  
-   <span data-ttu-id="082f4-126">Veri imzalı taraf ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="082f4-126">The public key of the party that signed the data.</span></span>  
  
-   <span data-ttu-id="082f4-127">Dijital imza.</span><span class="sxs-lookup"><span data-stu-id="082f4-127">The digital signature.</span></span>  
  
-   <span data-ttu-id="082f4-128">İmzalanmış olan veriler.</span><span class="sxs-lookup"><span data-stu-id="082f4-128">The data that was signed.</span></span>  
  
-   <span data-ttu-id="082f4-129">İmzalayan tarafından kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="082f4-129">The hash algorithm used by the signer.</span></span>  
  
 <span data-ttu-id="082f4-130">Tarafından imzalanmış bir imzayı doğrulamak için <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfı, kullanın <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="082f4-130">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="082f4-131"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Sınıfı olmalıdır sağlanan imzalayan ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="082f4-131">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="082f4-132">Modulus ve ortak anahtarı belirtmek için üs değerini gerekir.</span><span class="sxs-lookup"><span data-stu-id="082f4-132">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="082f4-133">(Ortak/özel anahtar çifti oluşturan taraf bu değerler sağlamanız gerekir.) İlk oluşturmak bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> ortak anahtar imzasını doğrular ve ardından başlatmak tutacak nesne bir <xref:System.Security.Cryptography.RSAParameters> ortak anahtar belirtmesi modulus ve üs değerlere yapısı.</span><span class="sxs-lookup"><span data-stu-id="082f4-133">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>  
  
 <span data-ttu-id="082f4-134">Aşağıdaki kod oluşturma işlemini gösterir. bir <xref:System.Security.Cryptography.RSAParameters> yapısı.</span><span class="sxs-lookup"><span data-stu-id="082f4-134">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="082f4-135">`Modulus` Özellik değeri olarak adlandırılan bir bayt dizisi olarak ayarlandığından `ModulusData` ve `Exponent` özellik değeri olarak adlandırılan bir bayt dizisi olarak ayarlandığından `ExponentData`.</span><span class="sxs-lookup"><span data-stu-id="082f4-135">The `Modulus` property is set to the value of a byte array called `ModulusData` and the `Exponent` property is set to the value of a byte array called `ExponentData`.</span></span>  
  
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
  
 <span data-ttu-id="082f4-136">Oluşturduktan sonra <xref:System.Security.Cryptography.RSAParameters> nesnesine yeni bir örneğini başlatmak <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı belirtilen değerlere <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="082f4-136">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="082f4-137"><xref:System.Security.Cryptography.RSACryptoServiceProvider> Buna karşılık oluşturucuya geçirilen olan bir <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> anahtarını aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="082f4-137">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>  
  
 <span data-ttu-id="082f4-138">Aşağıdaki örnek, bu işlemi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="082f4-138">The following example illustrates this process.</span></span> <span data-ttu-id="082f4-139">Bu örnekte, `HashValue` ve `SignedHashValue` uzak bir şirket tarafından sağlanan bayt dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="082f4-139">In this example, `HashValue` and `SignedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="082f4-140">Uzak tarafı oturum açtığını `HashValue` dijital imza üreten SHA1 algoritması kullanılarak `SignedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="082f4-140">The remote party has signed the `HashValue` using the SHA1 algorithm, producing the digital signature `SignedHashValue`.</span></span> <span data-ttu-id="082f4-141">Bu</span><span class="sxs-lookup"><span data-stu-id="082f4-141">The</span></span>  
  
 <span data-ttu-id="082f4-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> dijital imza geçerli olduğundan ve imzalamak için kullanılan yöntem doğrular `HashValue`.</span><span class="sxs-lookup"><span data-stu-id="082f4-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `HashValue`.</span></span>  
  
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
  
 <span data-ttu-id="082f4-143">Bu kod parçasını görüntüler "`The signature is valid`" imzası geçerli olup olmadığını ve "`The signature is not valid`", değilse.</span><span class="sxs-lookup"><span data-stu-id="082f4-143">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="082f4-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="082f4-144">See also</span></span>

- [<span data-ttu-id="082f4-145">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="082f4-145">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

---
title: Şifreleme İmzası
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
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
caps.latest.revision: 17
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 596625f229c4031b681755d538bf0a3d7b6674c8
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="cryptographic-signatures"></a>Şifreleme İmzası
<a name="top"></a> Şifreleme Dijital imzalar, veri bütünlüğünü sağlamak için ortak anahtar algoritmaları kullanır. Veri bir dijital imza ile oturum açtığınızda başka birinin imzasını doğrular ve verileri sizden geldiğini ve siz imzaladıktan sonra değiştirilmiş değil kanıtlayabilirsiniz. Dijital imzalar hakkında daha fazla bilgi için bkz: [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md).  
  
 Bu konuda oluşturmak ve sınıflarda kullanarak dijital imzaları doğrulamak açıklanmaktadır <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanı.  
  
-   [İmzalar oluşturma](#generate)  
  
-   [İmzaları doğrulama](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a>İmzalar oluşturma  
 Dijital imzalar genellikle daha büyük veri temsil eden karma değerlerini uygulanır. Aşağıdaki örnek, bir karma değer bir dijital imza uygular. İlk olarak, yeni bir örneğini <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı, bir ortak/özel anahtar çifti oluşturmak için oluşturulur. Ardından, <xref:System.Security.Cryptography.RSACryptoServiceProvider> için yeni bir örneği olarak geçirilmiş <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfı. Bu özel anahtara aktarır <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, aslında gerçekleştirir dijital imza. Karma kod oturum önce kullanmak için bir karma algoritması belirtmeniz gerekir. Bu örnek SHA1 algoritması kullanır. Son olarak, <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> yöntemi imzalama gerçekleştirmek için çağrılır.  
  
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
  
### <a name="signing-xml-files"></a>XML dosyaları imzalama  
 .NET Framework sağlar <xref:System.Security.Cryptography.Xml> oturum XML ad alanı sağlar. XML imzalama XML belirli bir kaynaktan kaynaklandığı doğrulamak istediğinizde önemlidir. Örneğin, XML kullanan bir hisse senedi hizmet kullanıyorsanız, bunu kaydolduysanız XML kaynağını doğrulayabilirsiniz.  
  
 Bu ad alanındaki sınıflar izleyin [XML imzası sözdizimi ve işleme öneri](https://www.w3.org/TR/xmldsig-core/) World Wide Web Konsorsiyumu gelen.  
  
 [Başa dön](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a>İmzaları doğrulama  
 Verileri belirli bir şahıs tarafından imzalandığı doğrulamak için aşağıdaki bilgileri olması gerekir:  
  
-   Veri imzalı taraf ortak anahtarı.  
  
-   Dijital imza.  
  
-   İmzalandığı veriler.  
  
-   İmzalayan tarafından kullanılan karma algoritması.  
  
 Tarafından imzalanmış bir imzayı doğrulamak için <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfı, kullanın <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfı. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Sınıfı olmalıdır imzalayan ortak anahtarını sağlanan. Modulus ve ortak anahtarı belirtmek için üs değerlerini gerekir. (Genel/özel anahtar çifti oluşturulan taraf bu değerler sağlaması gerekir.) İlk oluşturma bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> imzasını doğrular ve ardından başlatma ortak anahtarı tutmak için nesne bir <xref:System.Security.Cryptography.RSAParameters> ortak anahtar belirtmesi mod ve üs değerlere yapısı.  
  
 Aşağıdaki kod oluşturulmasını gösterir bir <xref:System.Security.Cryptography.RSAParameters> yapısı. `Modulus` Özelliği olarak adlandırılan bir bayt dizisi değerine ayarlanmış `ModulusData` ve `Exponent` özelliği olarak adlandırılan bir bayt dizisi değerine ayarlanmış `ExponentData`.  
  
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
  
 Oluşturduktan sonra <xref:System.Security.Cryptography.RSAParameters> nesne, yeni bir örneğini başlatma <xref:System.Security.Cryptography.RSACryptoServiceProvider> belirtilen değerleri sınıfına <xref:System.Security.Cryptography.RSAParameters>. <xref:System.Security.Cryptography.RSACryptoServiceProvider> Sırayla oluşturucusuna geçirilen bir <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> anahtarı aktarmak için.  
  
 Aşağıdaki örnek, bu işlemi gösterilmektedir. Bu örnekte, `HashValue` ve `SignedHashValue` uzak bir şirket tarafından sağlanan bayt dizidir. Uzak tarafı imzaladığı `HashValue` dijital imza oluşturan SHA1 algoritması kullanılarak `SignedHashValue`. Bu  
  
 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> dijital imza geçerli olduğundan ve imzalamak için kullanılan yöntem doğrular `HashValue`.  
  
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
  
 Bu kod parçası görüntüler "`The signature is valid`" imza geçerli olup olmadığını ve "`The signature is not valid`" değilse.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)

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
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869999"
---
# <a name="cryptographic-signatures"></a>Şifreleme İmzası
<a name="top"></a> Şifreleme Dijital imzalar, veri bütünlüğünü sağlamak için ortak anahtar algoritmaları kullanır. Verileri bir dijital imza ile oturum açtığınızda başka birisi imzasını doğrulayabilir ve verileri sizin tarafınızdan oluşturulan ve siz imzaladıktan sonra değiştirilmiş değil kanıtlayabilirsiniz. Dijital imzalar hakkında daha fazla bilgi için bkz: [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md).  
  
 Bu konu başlığında, oluşturmak ve sınıfları kullanarak dijital imzaları doğrulamak açıklanmaktadır <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanı.  
  
-   [İmzalar oluşturma](#generate)  
  
-   [İmzaları doğrulama](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a>İmzalar oluşturma  
 Dijital imzalar, genellikle daha büyük verileri temsil eden karma değerlerini uygulanır. Aşağıdaki örnek, bir dijital imza için bir karma değer geçerlidir. İlk olarak, yeni bir örneğini <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı, bir ortak/özel anahtar çifti oluşturmak için oluşturulur. Ardından, <xref:System.Security.Cryptography.RSACryptoServiceProvider> için yeni bir örneği olarak geçirilmiş olup <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfı. Bu özel anahtarı aktarır <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, aslında gerçekleştiren bir dijital imza. Karma kod oturum açabilmesi için önce kullanmak için bir karma algoritmasını belirtmelisiniz. Bu örnekte, SHA1 algoritması kullanır. Son olarak, <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> imzalamayı yöntemi çağrılır.  
  
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
 .NET Framework sağlar <xref:System.Security.Cryptography.Xml> oturum XML ad alanı sağlar. XML imzalama XML belirli bir kaynaktan kaynaklanan doğrulamak istediğiniz durumlarda önemlidir. Örneğin, XML kullanan bir hisse senedi hizmet kullanıyorsanız, imzalanmış olup olmadığını XML kaynağını doğrulayabilirsiniz.  
  
 Bu ad alanındaki sınıflar izleyin [Podpisu XML sözdizimi ve işleme öneri](https://www.w3.org/TR/xmldsig-core/) World Wide Web Consortium öğesinden.  
  
 [Başa dön](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a>İmzaları doğrulama  
 Verileri belirli bir şahıs tarafından imzalandığı doğrulamak için aşağıdaki bilgilere sahip olmalıdır:  
  
-   Veri imzalı taraf ortak anahtarı.  
  
-   Dijital imza.  
  
-   İmzalanmış olan veriler.  
  
-   İmzalayan tarafından kullanılan karma algoritması.  
  
 Tarafından imzalanmış bir imzayı doğrulamak için <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> sınıfı, kullanın <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> sınıfı. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Sınıfı olmalıdır sağlanan imzalayan ortak anahtarı. Modulus ve ortak anahtarı belirtmek için üs değerini gerekir. (Ortak/özel anahtar çifti oluşturan taraf bu değerler sağlamanız gerekir.) İlk oluşturmak bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> ortak anahtar imzasını doğrular ve ardından başlatmak tutacak nesne bir <xref:System.Security.Cryptography.RSAParameters> ortak anahtar belirtmesi modulus ve üs değerlere yapısı.  
  
 Aşağıdaki kod oluşturma işlemini gösterir. bir <xref:System.Security.Cryptography.RSAParameters> yapısı. `Modulus` Özellik değeri olarak adlandırılan bir bayt dizisi olarak ayarlandığından `ModulusData` ve `Exponent` özellik değeri olarak adlandırılan bir bayt dizisi olarak ayarlandığından `ExponentData`.  
  
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
  
 Oluşturduktan sonra <xref:System.Security.Cryptography.RSAParameters> nesnesine yeni bir örneğini başlatmak <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı belirtilen değerlere <xref:System.Security.Cryptography.RSAParameters>. <xref:System.Security.Cryptography.RSACryptoServiceProvider> Buna karşılık oluşturucuya geçirilen olan bir <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> anahtarını aktarmak için.  
  
 Aşağıdaki örnek, bu işlemi göstermektedir. Bu örnekte, `HashValue` ve `SignedHashValue` uzak bir şirket tarafından sağlanan bayt dizilerdir. Uzak tarafı oturum açtığını `HashValue` dijital imza üreten SHA1 algoritması kullanılarak `SignedHashValue`. Bu  
  
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
  
 Bu kod parçasını görüntüler "`The signature is valid`" imzası geçerli olup olmadığını ve "`The signature is not valid`", değilse.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)

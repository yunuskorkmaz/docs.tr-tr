---
title: "Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama"
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
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8835bd09e041ce8bb36c09951ea5526d42ff0c3c
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="43e2c-102">Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama</span><span class="sxs-lookup"><span data-stu-id="43e2c-102">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="43e2c-103">Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi veya bir XML belgesi bir dijital imza ile parçası imzalamak için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="43e2c-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="43e2c-104">XML dijital imzaları (XMLDSIG) imzalandığından sonra veri değiştirildiği değil olduğunu doğrulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="43e2c-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="43e2c-105">World Wide Web Konsorsiyumu (W3C) öneri XMLDSIG standart hakkında daha fazla bilgi için bkz: [XML imza sözdizimi ve işleme](https://www.w3.org/TR/xmldsig-core/).</span><span class="sxs-lookup"><span data-stu-id="43e2c-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="43e2c-106">Bu yordamı kod örneğinde dijital olarak tüm XML belgesi imzalamak ve imza belgede ekleme gösterilmiştir bir <`Signature`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="43e2c-106">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="43e2c-107">Örnek bir RSA imzalama anahtarı oluşturur, güvenli bir anahtar kapsayıcısı anahtar ekler ve bir XML belgesi dijital olarak imzalamak için anahtar kullanır.</span><span class="sxs-lookup"><span data-stu-id="43e2c-107">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="43e2c-108">Anahtarı XML dijital imzayı doğrulamak alınabilir veya başka bir XML belgesi imzalamak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="43e2c-108">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="43e2c-109">Bu yordam kullanılarak oluşturulmuş bir XML dijital imzası doğrulama hakkında daha fazla bilgi için bkz: [nasıl yapılır: dijital imzalar, XML belgelerinin doğrulayın](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="43e2c-109">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="43e2c-110">Bir XML belgesi dijital olarak imzalamak için</span><span class="sxs-lookup"><span data-stu-id="43e2c-110">To digitally sign an XML document</span></span>  
  
1.  <span data-ttu-id="43e2c-111">Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve anahtar kapsayıcı adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="43e2c-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="43e2c-112">Bir asimetrik anahtar kullanarak Oluştur <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="43e2c-112">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="43e2c-113">Geçirdiğiniz zaman anahtar için anahtar kapsayıcısını otomatik olarak kaydedilir <xref:System.Security.Cryptography.CspParameters> oluşturucusunun nesnesine <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="43e2c-113">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="43e2c-114">Bu anahtar, XML belgesi imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="43e2c-114">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="43e2c-115">Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.</span><span class="sxs-lookup"><span data-stu-id="43e2c-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="43e2c-116"><xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="43e2c-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="43e2c-117">Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesne ve geçirin <xref:System.Xml.XmlDocument> nesnesiyle.</span><span class="sxs-lookup"><span data-stu-id="43e2c-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="43e2c-118">İmzalama RSA anahtarı eklemek <xref:System.Security.Cryptography.Xml.SignedXml> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="43e2c-118">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="43e2c-119">Oluşturma bir <xref:System.Security.Cryptography.Xml.Reference> imzalamak açıklanmaktadır nesnesi.</span><span class="sxs-lookup"><span data-stu-id="43e2c-119">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="43e2c-120">Tüm belgeyi imzalamak için ayarlanmış <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> özelliğine `""`.</span><span class="sxs-lookup"><span data-stu-id="43e2c-120">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="43e2c-121">Ekleme bir <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> nesnesini <xref:System.Security.Cryptography.Xml.Reference> nesne.</span><span class="sxs-lookup"><span data-stu-id="43e2c-121">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="43e2c-122">Bir dönüşüm XML verileri imzalayan kullanılan aynı şekilde temsil etmek Doğrulayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="43e2c-122">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="43e2c-123">Bu doğrulama için önemli bir adımdır şekilde XML verileri farklı şekillerde temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="43e2c-123">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="43e2c-124">Ekleme <xref:System.Security.Cryptography.Xml.Reference> nesnesini <xref:System.Security.Cryptography.Xml.SignedXml> nesne.</span><span class="sxs-lookup"><span data-stu-id="43e2c-124">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="43e2c-125">İmza çağırarak işlem <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="43e2c-125">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="43e2c-126">İmza XML gösterimini almak (bir <`Signature`> öğesi) ve yeni bir kaydetme <xref:System.Xml.XmlElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="43e2c-126">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="43e2c-127">Öğesine ekleme <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="43e2c-127">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="43e2c-128">Belgeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="43e2c-128">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="43e2c-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="43e2c-129">Example</span></span>  
 <span data-ttu-id="43e2c-130">Bu örnek, bir dosya adlı varsayar `test.xml` derlenmiş programın aynı dizinde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43e2c-130">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="43e2c-131">Aşağıdaki XML adlı bir dosyaya yerleştirebilirsiniz `test.xml` ve bu örnek ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="43e2c-131">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43e2c-132">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="43e2c-132">Compiling the Code</span></span>  
  
-   <span data-ttu-id="43e2c-133">Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="43e2c-133">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="43e2c-134">Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="43e2c-134">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="43e2c-135">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="43e2c-135">.NET Framework Security</span></span>  
 <span data-ttu-id="43e2c-136">Hiçbir zaman depolamak veya asimetrik anahtar çifti düz metin olarak özel anahtarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="43e2c-136">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="43e2c-137">Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz: [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="43e2c-137">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="43e2c-138">Hiçbir zaman bir özel anahtar kaynak kodunuza doğrudan ekleyin.</span><span class="sxs-lookup"><span data-stu-id="43e2c-138">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="43e2c-139">Katıştırılmış anahtarları kullanarak bir derlemeye ait kolayca da okunabilir [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.</span><span class="sxs-lookup"><span data-stu-id="43e2c-139">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e2c-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43e2c-140">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="43e2c-141">Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="43e2c-141">How to: Verify the Digital Signatures of XML Documents</span></span>](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)

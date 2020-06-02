---
title: 'Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: fa5e13e4a84a7d5d5c07c63df9079f4a07aebc62
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277147"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="82e59-102">Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="82e59-102">How to: Verify the Digital Signatures of XML Documents</span></span>
<span data-ttu-id="82e59-103"><xref:System.Security.Cryptography.Xml>Dijital imzayla IMZALANMıŞ XML verilerini doğrulamak için ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82e59-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span> <span data-ttu-id="82e59-104">XML dijital imzaları (XMLDSIG), imzalandıktan sonra verilerin değiştirilmediğini doğrulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="82e59-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span> <span data-ttu-id="82e59-105">XMLDSIG standardı hakkında daha fazla bilgi için, bkz. World Wide Web Konsorsiyumu (W3C) belirtimi <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="82e59-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at <https://www.w3.org/TR/xmldsig-core/>.</span></span>
  
 <span data-ttu-id="82e59-106">Bu yordamdaki kod örneği, bir <> öğesinde bulunan bir XML dijital imzasının nasıl doğrulandığını gösterir `Signature` .</span><span class="sxs-lookup"><span data-stu-id="82e59-106">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="82e59-107">Örnek, anahtar kapsayıcısından bir RSA ortak anahtarı alır ve ardından imzayı doğrulamak için anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="82e59-107">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
 <span data-ttu-id="82e59-108">Bu tekniği kullanarak doğrulanabilen dijital imza oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML belgelerini dijital Imzalarla imzalama](how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="82e59-108">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="82e59-109">Bir XML belgesinin dijital imzasını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="82e59-109">To verify the digital signature of an XML document</span></span>  
  
1. <span data-ttu-id="82e59-110">Belgeyi doğrulamak için, imzalama için kullanılan asimetrik anahtarı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="82e59-110">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="82e59-111">Bir <xref:System.Security.Cryptography.CspParameters> nesne oluşturun ve imzalanmak üzere kullanılan anahtar kapsayıcısının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="82e59-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="82e59-112">Sınıfını kullanarak ortak anahtarı alın <xref:System.Security.Cryptography.RSACryptoServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="82e59-112">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="82e59-113">Bu anahtar, nesneyi sınıfının oluşturucusuna geçirdiğinizde anahtar kapsayıcısından ada göre otomatik olarak yüklenir <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="82e59-113">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="82e59-114"><xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82e59-114">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="82e59-115"><xref:System.Xml.XmlDocument>Nesne doğrulanacak olan IMZALANMıŞ XML belgesini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="82e59-115">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="82e59-116">Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesne oluşturun ve <xref:System.Xml.XmlDocument> nesneyi buna geçirin.</span><span class="sxs-lookup"><span data-stu-id="82e59-116">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="82e59-117"><`signature`> öğesini bulun ve yeni bir nesne oluşturun <xref:System.Xml.XmlNodeList> .</span><span class="sxs-lookup"><span data-stu-id="82e59-117">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="82e59-118">İlk <`signature`> ÖĞESININ XML 'sini <xref:System.Security.Cryptography.Xml.SignedXml> nesnesine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="82e59-118">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="82e59-119"><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A>Yöntemi ve RSA ortak anahtarını kullanarak imzayı denetleyin.</span><span class="sxs-lookup"><span data-stu-id="82e59-119">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="82e59-120">Bu yöntem, başarılı veya başarısız olduğunu belirten bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="82e59-120">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="82e59-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="82e59-121">Example</span></span>  
 <span data-ttu-id="82e59-122">Bu örnek, adlı bir dosyanın `"test.xml"` derlenen programla aynı dizinde bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="82e59-122">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="82e59-123">Bu `"test.xml"` Dosya, [nasıl yapılır: XML belgelerini dijital Imzalarla imzalama](how-to-sign-xml-documents-with-digital-signatures.md)bölümünde açıklanan teknikler kullanılarak imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82e59-123">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="82e59-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="82e59-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="82e59-125">Bu örneği derlemek için, öğesine bir başvuru eklemeniz gerekir `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="82e59-125">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="82e59-126">Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="82e59-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="82e59-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="82e59-127">.NET Framework Security</span></span>  
 <span data-ttu-id="82e59-128">Asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="82e59-128">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="82e59-129">Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="82e59-129">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="82e59-130">Özel anahtarı hiçbir şekilde doğrudan kaynak kodunuza gömmeyin.</span><span class="sxs-lookup"><span data-stu-id="82e59-130">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="82e59-131">Gömülü anahtarlar [ıldadsm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.</span><span class="sxs-lookup"><span data-stu-id="82e59-131">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e59-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82e59-132">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="82e59-133">Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama</span><span class="sxs-lookup"><span data-stu-id="82e59-133">How to: Sign XML Documents with Digital Signatures</span></span>](how-to-sign-xml-documents-with-digital-signatures.md)

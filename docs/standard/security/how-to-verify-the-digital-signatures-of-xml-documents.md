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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19537fa3e3e27c3446d22f1f1a8cf2faf472158e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307775"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="00b41-102">Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="00b41-102">How to: Verify the Digital Signatures of XML Documents</span></span>
<span data-ttu-id="00b41-103">Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> XML verileri doğrulamak için ad alanı bir dijital imza ile imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="00b41-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span> <span data-ttu-id="00b41-104">XML dijital imzaları (XMLDSIG) imzalandıktan sonra veri değiştirilmiş değil olduğunu doğrulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="00b41-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span> <span data-ttu-id="00b41-105">World Wide Web Consortium (W3C) belirtimi, XMLDSIG standart hakkında daha fazla bilgi için bkz <https://www.w3.org/TR/xmldsig-core/>.</span><span class="sxs-lookup"><span data-stu-id="00b41-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at <https://www.w3.org/TR/xmldsig-core/>.</span></span>
  
 <span data-ttu-id="00b41-106">Bu yordam kod örneğinde yer alan bir XML dijital imzayı doğrulamak gösterilmiştir bir <`Signature`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="00b41-106">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="00b41-107">Örnek, RSA ortak anahtarı bir anahtar kapsayıcısından alır ve ardından imzayı doğrulamak için anahtar kullanır.</span><span class="sxs-lookup"><span data-stu-id="00b41-107">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
 <span data-ttu-id="00b41-108">Bu teknik kullanılarak doğrulanabilir bir dijital imza oluşturma hakkında bilgi için bkz: [nasıl yapılır: XML belgelerini dijital imzalarla imzalama](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="00b41-108">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="00b41-109">Bir XML belgesinin dijital imzasını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="00b41-109">To verify the digital signature of an XML document</span></span>  
  
1. <span data-ttu-id="00b41-110">Belgeyi doğrulamak için imzalama için kullanılan aynı asimetrik anahtar kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="00b41-110">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="00b41-111">Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve imzalama için kullanılan anahtar kapsayıcısı adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="00b41-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="00b41-112">Ortak anahtarınızı kullanarak almak <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00b41-112">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="00b41-113">Geçirdiğiniz anahtarı otomatik olarak anahtar kapsayıcısından adına göre yüklenir <xref:System.Security.Cryptography.CspParameters> nesnesi oluşturucusuna <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00b41-113">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="00b41-114">Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.</span><span class="sxs-lookup"><span data-stu-id="00b41-114">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="00b41-115"><xref:System.Xml.XmlDocument> Doğrulamak için imzalı XML belge nesne içerir.</span><span class="sxs-lookup"><span data-stu-id="00b41-115">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="00b41-116">Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesne ve geçirin <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="00b41-116">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="00b41-117">Bulma <`signature`> öğesi ve yeni bir <xref:System.Xml.XmlNodeList> nesne.</span><span class="sxs-lookup"><span data-stu-id="00b41-117">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="00b41-118">İlk XML Yükleme <`signature`> öğesine <xref:System.Security.Cryptography.Xml.SignedXml> nesne.</span><span class="sxs-lookup"><span data-stu-id="00b41-118">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="00b41-119">Kullanarak imza denetimi <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> yöntemi ve RSA ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="00b41-119">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="00b41-120">Bu yöntem, başarı veya başarısızlık durumu gösteren bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="00b41-120">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="00b41-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="00b41-121">Example</span></span>  
 <span data-ttu-id="00b41-122">Bu örnek adlı bir dosya olduğunu varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00b41-122">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="00b41-123">`"test.xml"` Açıklanan teknikleri kullanarak dosya imzalanmalıdır [nasıl yapılır: XML belgelerini dijital imzalarla imzalama](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="00b41-123">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="00b41-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="00b41-124">Compiling the Code</span></span>  
  
-   <span data-ttu-id="00b41-125">Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="00b41-125">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="00b41-126">Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="00b41-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="00b41-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="00b41-127">.NET Framework Security</span></span>  
 <span data-ttu-id="00b41-128">Hiçbir zaman depolayabilen veya asimetrik anahtar çifti düz metin olarak özel anahtarı.</span><span class="sxs-lookup"><span data-stu-id="00b41-128">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="00b41-129">Simetrik hem de asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="00b41-129">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="00b41-130">Hiçbir zaman bir özel anahtar doğrudan sizin kaynak kodunuza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="00b41-130">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="00b41-131">Katıştırılmış anahtarları kullanarak bir derlemeden kolayca da okunabilir [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.</span><span class="sxs-lookup"><span data-stu-id="00b41-131">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b41-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00b41-132">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="00b41-133">Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama</span><span class="sxs-lookup"><span data-stu-id="00b41-133">How to: Sign XML Documents with Digital Signatures</span></span>](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)

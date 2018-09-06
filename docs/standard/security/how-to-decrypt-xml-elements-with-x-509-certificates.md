---
title: 'Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25a2fb441269508402263e103a6c6e1be2635406
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869538"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="819d6-102">Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme</span><span class="sxs-lookup"><span data-stu-id="819d6-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="819d6-103">Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> şifreleme ve şifre çözme bir XML belgesi içindeki bir öğe için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="819d6-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="819d6-104">XML şifreleme, exchange veya bir kolayca okunan verilerin hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="819d6-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="819d6-105">XML şifreleme konumundaki XML şifreleme standardı hakkında daha fazla bilgi için World Wide Web Consortium (W3C) belirtimi bakın http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="819d6-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="819d6-106">Bu örnekte açıklanan yöntemleri kullanılarak şifrelenmiş bir XML öğesi şifresini çözer: [nasıl yapılır: XML öğelerini X.509 sertifikalarıyla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="819d6-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="819d6-107">Bulduğu bir <`EncryptedData`> öğesi, öğenin şifresini çözer ve daha sonra öğenin özgün düz metin XML öğesi ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="819d6-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="819d6-108">Kod örneği, bu yordamı geçerli kullanıcı hesabı yerel sertifika deposundan bir X.509 sertifikası kullanarak bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="819d6-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="819d6-109">Örnekte <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> otomatik olarak X.509 sertifika almak ve bir oturum anahtarı depolanan şifresini çözmek için gereken yöntemini <`EncryptedKey`> öğesi <`EncryptedData`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="819d6-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="819d6-110"><xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> Yöntemi ardından otomatik olarak oturum anahtarı XML öğesinin şifresini çözmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="819d6-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="819d6-111">Bu örnek, birden çok uygulama şifrelenmiş veri paylaşımı gereken yere veya uygulamanın çalıştığı zamanları arasında şifrelenmiş verileri kaydetmek gereken yere durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="819d6-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="819d6-112">X.509 sertifikası olan bir XML öğesinin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="819d6-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="819d6-113">Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.</span><span class="sxs-lookup"><span data-stu-id="819d6-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="819d6-114"><xref:System.Xml.XmlDocument> Nesne şifresini çözmek için XML öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="819d6-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="819d6-115">Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> geçirerek nesne <xref:System.Xml.XmlDocument> oluşturucusuna.</span><span class="sxs-lookup"><span data-stu-id="819d6-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="819d6-116">XML kullanarak belgenin şifresini <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="819d6-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="819d6-117">Kaydet <xref:System.Xml.XmlDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="819d6-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="819d6-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="819d6-118">Example</span></span>  
 <span data-ttu-id="819d6-119">Bu örnek adlı bir dosya olduğunu varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="819d6-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="819d6-120">Ayrıca varsayılmaktadır `"test.xml"` içeren bir `"creditcard"` öğesi.</span><span class="sxs-lookup"><span data-stu-id="819d6-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="819d6-121">Aşağıdaki XML adlı bir dosyaya yerleştirebilirsiniz `test.xml` ve bu örneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="819d6-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="819d6-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="819d6-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="819d6-123">Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="819d6-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="819d6-124">Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="819d6-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="819d6-125">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="819d6-125">.NET Framework Security</span></span>  
 <span data-ttu-id="819d6-126">Bu örnekte kullanılan X.509 sertifikası, yalnızca test amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="819d6-126">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="819d6-127">Uygulamaları, bir güvenilen sertifika yetkilisi tarafından oluşturulan bir X.509 sertifikası kullanın veya Microsoft Windows sertifika sunucusu tarafından oluşturulan bir sertifika kullanın.</span><span class="sxs-lookup"><span data-stu-id="819d6-127">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="819d6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="819d6-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>  
- [<span data-ttu-id="819d6-129">Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="819d6-129">How to: Encrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)

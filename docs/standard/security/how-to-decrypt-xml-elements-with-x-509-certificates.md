---
title: 'Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme'
ms.date: 07/14/2020
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
ms.openlocfilehash: f60947a3b722f33c88b696d47c6a4000a1cb076b
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555740"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="b4ad3-102">Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme</span><span class="sxs-lookup"><span data-stu-id="b4ad3-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>

<span data-ttu-id="b4ad3-103"><xref:System.Security.Cryptography.Xml>BIR XML belgesi içindeki bir öğeyi şifrelemek ve şifrelerini çözmek için ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="b4ad3-104">XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="b4ad3-105">XML şifreleme standardı hakkında daha fazla bilgi için bkz. konumundaki XML şifrelemesi için World Wide Web Konsorsiyumu (W3C) belirtimi <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="b4ad3-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="b4ad3-106">Bu örnek,: [nasıl yapılır: XML öğelerini X. 509.440 sertifikalarıyla şifreleme](how-to-encrypt-xml-elements-with-x-509-certificates.md)bölümünde açıklanan yöntemler kullanılarak ŞIFRELENMIŞ bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="b4ad3-107">Bir <`EncryptedData`> öğesi bulur, öğenin şifresini çözer ve sonra öğeyi özgün düz metın XML öğesiyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="b4ad3-108">Bu yordamdaki kod örneği, geçerli kullanıcı hesabının yerel sertifika deposundan bir X. 509.440 sertifikası kullanarak bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="b4ad3-109">Örnek, <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> X. 509.952 sertifikasını otomatik olarak almak ve `EncryptedKey` <> öğesinin <> öğesinde depolanan bir oturum anahtarının şifresini çözmek için yöntemini kullanır `EncryptedData` .</span><span class="sxs-lookup"><span data-stu-id="b4ad3-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="b4ad3-110"><xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>Daha sonra yöntemi, XML öğesinin şifresini çözmek için oturum anahtarını otomatik olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="b4ad3-111">Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, kaç kez şifrelenmiş verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="b4ad3-112">X.509 sertifikası olan bir XML öğesinin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="b4ad3-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="b4ad3-113"><xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="b4ad3-114"><xref:System.Xml.XmlDocument>Nesnesi, şifresinin çözülmesi IÇIN XML öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. <span data-ttu-id="b4ad3-115"><xref:System.Security.Cryptography.Xml.EncryptedXml>Nesneyi oluşturucuya geçirerek yeni bir nesne oluşturun <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="b4ad3-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. <span data-ttu-id="b4ad3-116">Yöntemini kullanarak XML belgesinin şifresini çözün <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> .</span><span class="sxs-lookup"><span data-stu-id="b4ad3-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. <span data-ttu-id="b4ad3-117">Nesneyi kaydedin <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="b4ad3-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="b4ad3-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4ad3-118">Example</span></span>

<span data-ttu-id="b4ad3-119">Bu örnek, adlı bir dosyanın `"test.xml"` derlenen programla aynı dizinde bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="b4ad3-120">Ayrıca `"test.xml"` bir öğesi içerdiğini varsayar `"creditcard"` .</span><span class="sxs-lookup"><span data-stu-id="b4ad3-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="b4ad3-121">Aşağıdaki XML 'i adlı bir dosyaya yerleştirebilir `test.xml` ve bu örnekle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b4ad3-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b4ad3-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="b4ad3-123">.NET Framework hedefleyen bir projede, öğesine bir başvuru ekleyin `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="b4ad3-123">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="b4ad3-124">.NET Core veya .NET 5 ' i hedefleyen bir projede NuGet paketi [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)' yi yükler.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-124">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>

- <span data-ttu-id="b4ad3-125">Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="b4ad3-125">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="b4ad3-126">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="b4ad3-126">.NET Security</span></span>

<span data-ttu-id="b4ad3-127">Bu örnekte kullanılan X. 509.440 sertifikası yalnızca test amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-127">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="b4ad3-128">Uygulamalar, güvenilir bir sertifika yetkilisi tarafından oluşturulan bir X. 509.440 sertifikası kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-128">Applications should use an X.509 certificate generated by a trusted certificate authority.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ad3-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4ad3-129">See also</span></span>

- [<span data-ttu-id="b4ad3-130">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="b4ad3-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="b4ad3-131">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="b4ad3-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="b4ad3-132">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="b4ad3-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="b4ad3-133">Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="b4ad3-133">How to: Encrypt XML Elements with X.509 Certificates</span></span>](how-to-encrypt-xml-elements-with-x-509-certificates.md)
- [<span data-ttu-id="b4ad3-134">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="b4ad3-134">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

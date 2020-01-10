---
title: 'Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], X.509 certificates
- cryptography [.NET Framework], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
ms.openlocfilehash: 7f74e4e46ba760b7a943b2e2728e487ee87ae204
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706077"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="6ea59-102">Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="6ea59-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="6ea59-103">Bir XML belgesi içindeki bir öğeyi şifrelemek için <xref:System.Security.Cryptography.Xml> ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ea59-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="6ea59-104">XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="6ea59-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="6ea59-105">XML şifreleme standardı hakkında daha fazla bilgi için, <https://www.w3.org/TR/xmldsig-core/>konumundaki XML şifrelemesi için World Wide Web Konsorsiyumu (W3C) belirtimine bakın.</span><span class="sxs-lookup"><span data-stu-id="6ea59-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="6ea59-106">XML şifrelemesini, şifrelenmiş XML verilerini içeren bir <`EncryptedData`> öğesiyle herhangi bir XML öğesini veya belgeyi değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ea59-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="6ea59-107"><`EncryptedData`> öğesi, şifreleme sırasında kullanılan anahtarlar ve süreçler hakkında bilgiler içeren alt öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6ea59-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="6ea59-108">XML şifrelemesi, bir belgenin birden çok şifrelenmiş öğe içermesini sağlar ve bir öğenin birden çok kez şifrelenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ea59-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="6ea59-109">Bu yordamdaki kod örneği, daha sonra şifre çözme sırasında kullanabileceğiniz birkaç diğer alt öğe ile birlikte <`EncryptedData`> öğesi oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ea59-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="6ea59-110">Bu örnek, iki anahtar kullanarak bir XML öğesini şifreler.</span><span class="sxs-lookup"><span data-stu-id="6ea59-110">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="6ea59-111">[Sertifika oluşturma aracı 'nı (Makecert. exe)](/windows/desktop/SecCrypto/makecert) kullanarak bir test X. 509.440 sertifikası oluşturur ve sertifikayı bir sertifika deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6ea59-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) and saves the certificate to a certificate store.</span></span> <span data-ttu-id="6ea59-112">Örnek daha sonra sertifikayı program aracılığıyla alır ve <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi kullanarak bir XML öğesini şifrelemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="6ea59-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="6ea59-113">Dahili olarak, <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi ayrı bir oturum anahtarı oluşturur ve XML belgesini şifrelemek için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="6ea59-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="6ea59-114">Bu yöntem, oturum anahtarını şifreler ve şifreli XML ile birlikte yeni bir <`EncryptedData`> öğesi içinde kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6ea59-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="6ea59-115">XML öğesinin şifresini çözmek için, mağazadan X. 509.440 sertifikasını otomatik olarak alan <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> yöntemini çağırmanız ve gerekli şifre çözmeyi gerçekleştirmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="6ea59-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="6ea59-116">Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözme hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerinin şifresini X. 509.440 sertifikalarıyla çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6ea59-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="6ea59-117">Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, kaç kez şifrelenmiş verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="6ea59-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="6ea59-118">Bir XML öğesini X.509 sertifikası ile şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="6ea59-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="6ea59-119">[Sertifika oluşturma aracı 'nı (Makecert. exe)](/windows/desktop/SecCrypto/makecert) kullanarak bir test X. 509.952 sertifikası oluşturun ve bunu yerel kullanıcı deposuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6ea59-119">Use the [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="6ea59-120">Bir Exchange anahtarı oluşturmanız gerekir ve anahtarı dışa aktarılabilir yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ea59-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="6ea59-121">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="6ea59-121">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="6ea59-122"><xref:System.Security.Cryptography.X509Certificates.X509Store> nesnesi oluşturun ve geçerli kullanıcı deposunu açmak için başlatın.</span><span class="sxs-lookup"><span data-stu-id="6ea59-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="6ea59-123">Depoyu salt okuma modunda açın.</span><span class="sxs-lookup"><span data-stu-id="6ea59-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="6ea59-124">Depodaki tüm sertifikalarla bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> başlatın.</span><span class="sxs-lookup"><span data-stu-id="6ea59-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="6ea59-125">Depodaki sertifikaları numaralandırın ve uygun ada sahip sertifikayı bulun.</span><span class="sxs-lookup"><span data-stu-id="6ea59-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="6ea59-126">Bu örnekte, sertifika `"CN=XML_ENC_TEST_CERT"`olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6ea59-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="6ea59-127">Sertifika oluşturulduktan sonra mağazayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="6ea59-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="6ea59-128">Diskten bir XML dosyası yükleyerek <xref:System.Xml.XmlDocument> nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6ea59-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="6ea59-129"><xref:System.Xml.XmlDocument> nesnesi şifrelenecek XML öğesini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6ea59-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="6ea59-130"><xref:System.Xml.XmlDocument> nesnesinde belirtilen öğeyi bulun ve şifrelemek istediğiniz öğeyi temsil eden yeni bir <xref:System.Xml.XmlElement> nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6ea59-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="6ea59-131">Bu örnekte `"creditcard"` öğesi şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="6ea59-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="6ea59-132"><xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfının yeni bir örneğini oluşturun ve X. 509.440 sertifikasını kullanarak belirtilen öğeyi şifrelemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="6ea59-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="6ea59-133"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi, şifrelenmiş öğeyi bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="6ea59-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="6ea59-134">Öğeyi özgün <xref:System.Xml.XmlDocument> nesnesinden <xref:System.Security.Cryptography.Xml.EncryptedData> öğesiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6ea59-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="6ea59-135"><xref:System.Xml.XmlDocument> nesnesini kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6ea59-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="6ea59-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ea59-136">Example</span></span>  
 <span data-ttu-id="6ea59-137">Bu örnek, `"test.xml"` adlı bir dosyanın derlenen programla aynı dizinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="6ea59-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="6ea59-138">Ayrıca, `"test.xml"` bir `"creditcard"` öğesi içerdiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="6ea59-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="6ea59-139">Aşağıdaki XML 'i `test.xml` adlı bir dosyaya yerleştirebilir ve bu örnekle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ea59-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6ea59-140">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="6ea59-140">Compiling the Code</span></span>  
  
- <span data-ttu-id="6ea59-141">Bu örneği derlemek için `System.Security.dll`bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ea59-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="6ea59-142">Şu ad alanlarını ekleyin: <xref:System.Xml>, <xref:System.Security.Cryptography>ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="6ea59-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6ea59-143">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="6ea59-143">.NET Framework Security</span></span>  
 <span data-ttu-id="6ea59-144">Bu örnekte kullanılan X. 509.440 sertifikası yalnızca test amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="6ea59-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="6ea59-145">Uygulamalar, güvenilir bir sertifika yetkilisi tarafından oluşturulan bir X. 509.440 sertifikası kullanmalı veya Microsoft Windows sertifika sunucusu tarafından oluşturulan bir sertifikayı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ea59-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea59-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ea59-146">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="6ea59-147">Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme</span><span class="sxs-lookup"><span data-stu-id="6ea59-147">How to: Decrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)

---
description: 'Daha fazla bilgi edinin: nasıl yapılır: XML öğelerini X. 509.440 sertifikalarıyla şifreleme'
title: 'Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], X.509 certificates
- cryptography [.NET], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
ms.openlocfilehash: f815d253b15823070e074c5d922d3024da602a0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685107"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="745c5-103">Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="745c5-103">How to: Encrypt XML Elements with X.509 Certificates</span></span>

<span data-ttu-id="745c5-104"><xref:System.Security.Cryptography.Xml>BIR XML belgesi içindeki bir öğeyi şifrelemek için ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="745c5-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="745c5-105">XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="745c5-105">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="745c5-106">XML şifreleme standardı hakkında daha fazla bilgi için bkz. konumundaki XML şifrelemesi için World Wide Web Konsorsiyumu (W3C) belirtimi <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="745c5-106">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="745c5-107">XML şifrelemesini, `EncryptedData` ŞIFRELENMIŞ XML verilerini içeren bir <> öğesiyle herhangi BIR XML öğesini veya belgeyi değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="745c5-107">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="745c5-108"><`EncryptedData`> öğesi, şifreleme sırasında kullanılan anahtarlar ve süreçler hakkında bilgi içeren alt öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="745c5-108">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="745c5-109">XML şifrelemesi, bir belgenin birden çok şifrelenmiş öğe içermesini sağlar ve bir öğenin birden çok kez şifrelenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="745c5-109">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="745c5-110">Bu yordamdaki kod örneği, `EncryptedData` daha sonra şifre çözme sırasında kullanabileceğiniz diğer birkaç alt öğe ile birlikte <> bir öğe oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="745c5-110">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
<span data-ttu-id="745c5-111">Bu örnek, iki anahtar kullanarak bir XML öğesini şifreler.</span><span class="sxs-lookup"><span data-stu-id="745c5-111">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="745c5-112">Örnek program aracılığıyla bir sertifikayı alır ve bu yöntemi kullanarak bir XML öğesini şifrelemek için kullanır <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> .</span><span class="sxs-lookup"><span data-stu-id="745c5-112">The example programmatically retrieves a certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="745c5-113">Dahili olarak, <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Yöntem ayrı bir oturum anahtarı oluşturur ve XML belgesini şifrelemek için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="745c5-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="745c5-114">Bu yöntem, oturum anahtarını şifreler ve şifreli XML ile birlikte yeni bir <> öğesi içinde kaydeder `EncryptedData` .</span><span class="sxs-lookup"><span data-stu-id="745c5-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  

<span data-ttu-id="745c5-115">XML öğesinin şifresini çözmek için, <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> mağazadan X. 509.952 sertifikasını otomatik olarak alan ve gerekli şifre çözme işlemini gerçekleştiren yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="745c5-115">To decrypt the XML element, call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="745c5-116">Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözme hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerinin şifresini X. 509.440 sertifikalarıyla çözme](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="745c5-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
<span data-ttu-id="745c5-117">Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, kaç kez şifrelenmiş verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="745c5-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="745c5-118">Bir XML öğesini X.509 sertifikası ile şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="745c5-118">To encrypt an XML element with an X.509 certificate</span></span>  

<span data-ttu-id="745c5-119">Bu örneği çalıştırmak için bir test sertifikası oluşturmanız ve onu bir sertifika deposuna kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="745c5-119">To run this example, you need to create a test certificate and save it in a certificate store.</span></span> <span data-ttu-id="745c5-120">Bu görev için yönergeler yalnızca Windows [sertifika oluşturma aracı (Makecert.exe)](/windows/desktop/SecCrypto/makecert)için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="745c5-120">Instructions for that task are provided only for the Windows [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert).</span></span>

1. <span data-ttu-id="745c5-121">Bir test X. 509.952 sertifikası oluşturmak ve bunu yerel kullanıcı deposuna yerleştirmek için [Makecert.exe](/windows/desktop/SecCrypto/makecert) kullanın.</span><span class="sxs-lookup"><span data-stu-id="745c5-121">Use [Makecert.exe](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="745c5-122">Bir Exchange anahtarı oluşturmanız gerekir ve anahtarı dışa aktarılabilir yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="745c5-122">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="745c5-123">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="745c5-123">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2020 -e 01/01/2025 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="745c5-124">Bir <xref:System.Security.Cryptography.X509Certificates.X509Store> nesne oluşturun ve geçerli kullanıcı deposunu açmak için başlatın.</span><span class="sxs-lookup"><span data-stu-id="745c5-124">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="745c5-125">Depoyu salt okuma modunda açın.</span><span class="sxs-lookup"><span data-stu-id="745c5-125">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="745c5-126"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection>Mağazadaki tüm sertifikalarla bir ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="745c5-126">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="745c5-127">Depodaki sertifikaları numaralandırın ve uygun ada sahip sertifikayı bulun.</span><span class="sxs-lookup"><span data-stu-id="745c5-127">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="745c5-128">Bu örnekte, sertifika adlandırılır `"CN=XML_ENC_TEST_CERT"` .</span><span class="sxs-lookup"><span data-stu-id="745c5-128">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="745c5-129">Sertifika oluşturulduktan sonra mağazayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="745c5-129">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="745c5-130"><xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="745c5-130">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="745c5-131"><xref:System.Xml.XmlDocument>Nesne ŞIFRELENECEK XML öğesini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="745c5-131">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="745c5-132">Nesnede belirtilen öğeyi bulun <xref:System.Xml.XmlDocument> ve <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="745c5-132">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="745c5-133">Bu örnekte, `"creditcard"` öğesi şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="745c5-133">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="745c5-134">Sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.Xml.EncryptedXml> ve X. 509.440 sertifikasını kullanarak belirtilen öğeyi şifrelemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="745c5-134">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="745c5-135"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A>Yöntemi, şifreli öğeyi bir nesne olarak döndürür <xref:System.Security.Cryptography.Xml.EncryptedData> .</span><span class="sxs-lookup"><span data-stu-id="745c5-135">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="745c5-136">Öğeyi özgün <xref:System.Xml.XmlDocument> nesnesinden öğesi ile değiştirin <xref:System.Security.Cryptography.Xml.EncryptedData> .</span><span class="sxs-lookup"><span data-stu-id="745c5-136">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="745c5-137">Nesneyi kaydedin <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="745c5-137">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="745c5-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="745c5-138">Example</span></span>  

 <span data-ttu-id="745c5-139">Bu örnek, adlı bir dosyanın `"test.xml"` derlenen programla aynı dizinde bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="745c5-139">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="745c5-140">Ayrıca `"test.xml"` bir öğesi içerdiğini varsayar `"creditcard"` .</span><span class="sxs-lookup"><span data-stu-id="745c5-140">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="745c5-141">Aşağıdaki XML 'i adlı bir dosyaya yerleştirebilir `test.xml` ve bu örnekle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="745c5-141">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="745c5-142">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="745c5-142">Compiling the Code</span></span>  
  
- <span data-ttu-id="745c5-143">.NET Framework hedefleyen bir projede, öğesine bir başvuru ekleyin `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="745c5-143">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="745c5-144">.NET Core veya .NET 5 ' i hedefleyen bir projede NuGet paketi [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)' yi yükler.</span><span class="sxs-lookup"><span data-stu-id="745c5-144">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="745c5-145">Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="745c5-145">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="745c5-146">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="745c5-146">.NET Security</span></span>
  
<span data-ttu-id="745c5-147">Bu örnekte kullanılan X. 509.440 sertifikası yalnızca test amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="745c5-147">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="745c5-148">Uygulamalar, güvenilir bir sertifika yetkilisi tarafından oluşturulan bir X. 509.440 sertifikası kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="745c5-148">Applications should use an X.509 certificate generated by a trusted certificate authority.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="745c5-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="745c5-149">See also</span></span>

- [<span data-ttu-id="745c5-150">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="745c5-150">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="745c5-151">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="745c5-151">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="745c5-152">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="745c5-152">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="745c5-153">Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme</span><span class="sxs-lookup"><span data-stu-id="745c5-153">How to: Decrypt XML Elements with X.509 Certificates</span></span>](how-to-decrypt-xml-elements-with-x-509-certificates.md)
- [<span data-ttu-id="745c5-154">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="745c5-154">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

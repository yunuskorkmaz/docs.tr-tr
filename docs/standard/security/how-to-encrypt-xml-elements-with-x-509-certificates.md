---
title: "Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme"
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
- encryption [.NET Framework], X.509 certificates
- cryptography [.NET Framework], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 108a07a818adaec6734637da2c95aed42e837847
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="26bec-102">Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="26bec-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="26bec-103">Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi içindeki bir öğe şifrelemek için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="26bec-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="26bec-104">XML şifrelemesi, exchange veya kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="26bec-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="26bec-105">XML şifrelemesi için World Wide Web Konsorsiyumu (W3C) belirtimi http://www.w3.org/TR/xmldsig-core/ bulunan standart XML şifreleme hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="26bec-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="26bec-106">XML şifrelemesi herhangi bir XML öğesi değiştirin veya ile belge için kullanabileceğiniz bir <`EncryptedData`> şifrelenmiş XML verileri içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="26bec-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="26bec-107"><`EncryptedData`> Öğesi, anahtarlar ve şifreleme sırasında kullanılan işlemler hakkında bilgi içeren alt öğelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="26bec-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="26bec-108">XML şifrelemesi şifrelenmiş birden çok öğe içeren bir belge ve birden çok kez şifrelenmesi için bir öğe olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="26bec-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="26bec-109">Bu yordamı kod örneğinde nasıl oluşturulacağını gösterir bir <`EncryptedData`> öğesi, daha sonra şifre çözme sırasında kullanabileceğiniz diğer alt öğelerini birlikte.</span><span class="sxs-lookup"><span data-stu-id="26bec-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="26bec-110">Bu örnek iki anahtarlar kullanılarak bir XML öğesi şifreler.</span><span class="sxs-lookup"><span data-stu-id="26bec-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="26bec-111">Bir X.509 sertifikası kullanarak test oluşturur [sertifika oluşturma Aracı (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) ve sertifikayı sertifika deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="26bec-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) and saves the certificate to a certificate store.</span></span>  <span data-ttu-id="26bec-112">Örnek ardından program aracılığıyla sertifikayı alır ve bir XML öğesi kullanarak şifrelemek için kullandığı <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="26bec-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span>  <span data-ttu-id="26bec-113">Dahili olarak, <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi ayrı oturum anahtarı oluşturur ve XML belgesi şifrelemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="26bec-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="26bec-114">Bu yöntem, oturum anahtarı şifreler ve şifrelenmiş XML yanı sıra içinde yeni bir kaydeder <`EncryptedData`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="26bec-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="26bec-115">XML öğesi şifresini çözmek için yalnızca çağrı <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> otomatik olarak X.509 Sertifika depodan alır ve gerekli şifre çözme gerçekleştiren yöntemi.</span><span class="sxs-lookup"><span data-stu-id="26bec-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="26bec-116">Bu yordam kullanılarak şifrelenmiş bir XML öğesi şifresini hakkında daha fazla bilgi için bkz: [nasıl yapılır: XML öğelerini X.509 sertifikalarıyla şifresini](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="26bec-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="26bec-117">Bu örnek birden çok uygulama şifrelenmiş verileri paylaşmak gereken yeri veya burada çalıştırdığı zamanları arasında şifrelenmiş verileri kaydetmek bir uygulama gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="26bec-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="26bec-118">Bir XML öğesini X.509 sertifikası ile şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="26bec-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="26bec-119">Kullanım [sertifika oluşturma Aracı (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) bir test X.509 sertifikası oluşturup yerel kullanıcı deposunda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="26bec-119">Use the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) to generate a test X.509 certificate and place it in the local user store.</span></span>  <span data-ttu-id="26bec-120">Değişim anahtarı oluşturmanız gerekir ve anahtarı dışa aktarılabilir duruma getir.</span><span class="sxs-lookup"><span data-stu-id="26bec-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="26bec-121">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="26bec-121">Run the following command:</span></span>  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  <span data-ttu-id="26bec-122">Oluşturma bir <xref:System.Security.Cryptography.X509Certificates.X509Store> nesne ve geçerli kullanıcı deposunda açmak için Başlat.</span><span class="sxs-lookup"><span data-stu-id="26bec-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  <span data-ttu-id="26bec-123">Deposu salt okunur modunda açın.</span><span class="sxs-lookup"><span data-stu-id="26bec-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  <span data-ttu-id="26bec-124">Başlatma bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> tüm deposundaki sertifikalar.</span><span class="sxs-lookup"><span data-stu-id="26bec-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  <span data-ttu-id="26bec-125">Deposundaki sertifikalar aracılığıyla numaralandırır ve uygun bir ad ile sertifikayı bulun.</span><span class="sxs-lookup"><span data-stu-id="26bec-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="26bec-126">Bu örnekte, sertifika adlı `"CN=XML_ENC_TEST_CERT"`.</span><span class="sxs-lookup"><span data-stu-id="26bec-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  <span data-ttu-id="26bec-127">Sertifika bulunduktan sonra mağaza kapatın.</span><span class="sxs-lookup"><span data-stu-id="26bec-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  <span data-ttu-id="26bec-128">Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.</span><span class="sxs-lookup"><span data-stu-id="26bec-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="26bec-129"><xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="26bec-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  <span data-ttu-id="26bec-130">Belirtilen öğe Bul <xref:System.Xml.XmlDocument> nesne ve yeni bir <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="26bec-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="26bec-131">Bu örnekte, `"creditcard"` öğesi şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="26bec-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="26bec-132">Yeni bir örneğini oluşturmak <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfı ve X.509 sertifikası kullanarak belirtilen öğe şifrelemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26bec-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="26bec-133"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Yöntem şifrelenmiş öğesi olarak bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="26bec-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="26bec-134">Özgün öğeyi değiştirin <xref:System.Xml.XmlDocument> nesnesi ile <xref:System.Security.Cryptography.Xml.EncryptedData> öğesi.</span><span class="sxs-lookup"><span data-stu-id="26bec-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="26bec-135">Kaydet <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="26bec-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="26bec-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="26bec-136">Example</span></span>  
 <span data-ttu-id="26bec-137">Bu örnek, bir dosya adlı varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="26bec-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="26bec-138">Ayrıca varsayılmaktadır `"test.xml"` içeren bir `"creditcard"` öğesi.</span><span class="sxs-lookup"><span data-stu-id="26bec-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="26bec-139">Aşağıdaki XML adlı bir dosyaya yerleştirebilirsiniz `test.xml` ve bu örnek ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="26bec-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="26bec-140">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="26bec-140">Compiling the Code</span></span>  
  
-   <span data-ttu-id="26bec-141">Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="26bec-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="26bec-142">Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="26bec-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="26bec-143">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="26bec-143">.NET Framework Security</span></span>  
 <span data-ttu-id="26bec-144">Bu örnekte kullanılan X.509 sertifikası yalnızca sınama amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="26bec-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="26bec-145">Uygulamaları, güvenilen bir sertifika yetkilisi tarafından oluşturulan bir X.509 sertifikası kullanın veya Microsoft Windows sertifika sunucusu tarafından oluşturulan bir sertifika kullanın.</span><span class="sxs-lookup"><span data-stu-id="26bec-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26bec-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26bec-146">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="26bec-147">Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme</span><span class="sxs-lookup"><span data-stu-id="26bec-147">How to: Decrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)

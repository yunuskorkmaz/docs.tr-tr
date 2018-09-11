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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 674a4c917df20f58a509e92465e756c4615118ca
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353888"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="cb642-102">Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="cb642-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="cb642-103">Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi bir öğesinde şifrelemek için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cb642-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="cb642-104">XML şifreleme, exchange veya bir kolayca okunan verilerin hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="cb642-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="cb642-105">XML şifreleme konumundaki XML şifreleme standardı hakkında daha fazla bilgi için World Wide Web Consortium (W3C) belirtimi bakın http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="cb642-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="cb642-106">XML şifreleme herhangi bir XML öğesini değiştirin veya ile belge için kullanabileceğiniz bir <`EncryptedData`> şifrelenmiş XML verilerini içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="cb642-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="cb642-107"><`EncryptedData`> Öğesi, anahtarları ve şifreleme sırasında kullanılan işlemler hakkında bilgi içeren alt öğelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="cb642-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="cb642-108">XML şifreleme şifrelenmiş birden çok öğe içeren bir belge sağlar ve bir öğe birden çok kez şifrelenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb642-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="cb642-109">Bu yordam kod örneğinde nasıl oluşturulacağını gösterir bir <`EncryptedData`> öğesi birlikte, daha sonra şifre çözme sırasında kullanabileceğiniz diğer alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="cb642-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="cb642-110">Bu örnekte, iki anahtar kullanarak bir XML öğesi şifreler.</span><span class="sxs-lookup"><span data-stu-id="cb642-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="cb642-111">Bir test X.509 sertifikası kullanarak oluşturur [sertifika oluşturma Aracı (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) ve sertifikayı sertifika deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cb642-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) and saves the certificate to a certificate store.</span></span>  <span data-ttu-id="cb642-112">Örnek daha sonra program aracılığıyla sertifikayı alır ve bir XML öğesini kullanarak şifrelemek için kullandığı <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cb642-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span>  <span data-ttu-id="cb642-113">Dahili olarak <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi ayrı oturum anahtarı oluşturur ve XML belgesi şifrelemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="cb642-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="cb642-114">Bu yöntem oturum anahtarı şifreler ve şifrelenmiş XML yanı sıra içinde yeni bir kaydeder <`EncryptedData`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb642-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="cb642-115">XML öğesinin şifresini çözmek için basitçe çağrı <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> yöntemi otomatik olarak X.509 sertifika deposundan alır ve gerekli şifre çözme işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="cb642-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="cb642-116">Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözmek hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerini X.509 sertifikalarıyla şifresini](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="cb642-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="cb642-117">Bu örnek, birden çok uygulama şifrelenmiş veri paylaşımı gereken yere veya uygulamanın çalıştığı zamanları arasında şifrelenmiş verileri kaydetmek gereken yere durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="cb642-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="cb642-118">Bir XML öğesini X.509 sertifikası ile şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="cb642-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="cb642-119">Kullanım [sertifika oluşturma Aracı (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) test X.509 sertifikası oluşturma ve yerel kullanıcı depolama alanına yerleştir.</span><span class="sxs-lookup"><span data-stu-id="cb642-119">Use the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) to generate a test X.509 certificate and place it in the local user store.</span></span>  <span data-ttu-id="cb642-120">Değişim anahtarı oluşturmanız gerekir ve anahtar dışarı aktarılabilir yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb642-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="cb642-121">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cb642-121">Run the following command:</span></span>  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  <span data-ttu-id="cb642-122">Oluşturma bir <xref:System.Security.Cryptography.X509Certificates.X509Store> nesne ve geçerli kullanıcı deposu açmak için Başlat.</span><span class="sxs-lookup"><span data-stu-id="cb642-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  <span data-ttu-id="cb642-123">Deponun yalnızca Okuma modunda açın.</span><span class="sxs-lookup"><span data-stu-id="cb642-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  <span data-ttu-id="cb642-124">Başlatma bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> tüm sertifikaları aşağıdaki depolama.</span><span class="sxs-lookup"><span data-stu-id="cb642-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  <span data-ttu-id="cb642-125">Deposundaki sertifikalar aracılığıyla listeleme ve uygun ad sahip sertifika bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="cb642-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="cb642-126">Bu örnekte, sertifika adlı `"CN=XML_ENC_TEST_CERT"`.</span><span class="sxs-lookup"><span data-stu-id="cb642-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  <span data-ttu-id="cb642-127">Sertifika bulunduktan sonra deponun kapatın.</span><span class="sxs-lookup"><span data-stu-id="cb642-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  <span data-ttu-id="cb642-128">Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.</span><span class="sxs-lookup"><span data-stu-id="cb642-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="cb642-129"><xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="cb642-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  <span data-ttu-id="cb642-130">Belirtilen öğe Bul <xref:System.Xml.XmlDocument> nesne ve yeni bir <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="cb642-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="cb642-131">Bu örnekte, `"creditcard"` öğesi şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="cb642-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="cb642-132">Yeni bir örneğini oluşturma <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfı ve X.509 sertifikası kullanarak belirtilen öğeyi şifrelemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb642-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="cb642-133"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Yöntemi döndürür şifrelenmiş öğesi olarak bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne.</span><span class="sxs-lookup"><span data-stu-id="cb642-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="cb642-134">Özgün öğeden değiştirin <xref:System.Xml.XmlDocument> nesnesi ile <xref:System.Security.Cryptography.Xml.EncryptedData> öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb642-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="cb642-135">Kaydet <xref:System.Xml.XmlDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="cb642-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="cb642-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb642-136">Example</span></span>  
 <span data-ttu-id="cb642-137">Bu örnek adlı bir dosya olduğunu varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb642-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="cb642-138">Ayrıca varsayılmaktadır `"test.xml"` içeren bir `"creditcard"` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb642-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="cb642-139">Aşağıdaki XML adlı bir dosyaya yerleştirebilirsiniz `test.xml` ve bu örneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb642-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb642-140">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cb642-140">Compiling the Code</span></span>  
  
-   <span data-ttu-id="cb642-141">Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="cb642-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="cb642-142">Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="cb642-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cb642-143">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="cb642-143">.NET Framework Security</span></span>  
 <span data-ttu-id="cb642-144">Bu örnekte kullanılan X.509 sertifikası, yalnızca test amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="cb642-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="cb642-145">Uygulamaları, bir güvenilen sertifika yetkilisi tarafından oluşturulan bir X.509 sertifikası kullanın veya Microsoft Windows sertifika sunucusu tarafından oluşturulan bir sertifika kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb642-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb642-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb642-146">See also</span></span>

- <xref:System.Security.Cryptography.Xml>  
- [<span data-ttu-id="cb642-147">Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme</span><span class="sxs-lookup"><span data-stu-id="cb642-147">How to: Decrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)

---
title: 'Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
ms.openlocfilehash: 475446f6206676e93ea72d16e01bcf1067c24e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277381"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="d3101-102">Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="d3101-102">How to: Encrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="d3101-103"><xref:System.Security.Cryptography.Xml>BIR XML belgesi içindeki bir öğeyi şifrelemek için ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3101-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="d3101-104">XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="d3101-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="d3101-105">XML şifreleme standardı hakkında daha fazla bilgi için bkz. konumundaki XML şifrelemesi için World Wide Web Konsorsiyumu (W3C) belirtimi <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="d3101-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="d3101-106">XML şifrelemesini, `EncryptedData` ŞIFRELENMIŞ XML verilerini içeren bir <> öğesiyle herhangi BIR XML öğesini veya belgeyi değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3101-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="d3101-107"><`EncryptedData`> öğesi, şifreleme sırasında kullanılan anahtarlar ve süreçler hakkında bilgiler içeren alt öğeleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d3101-107">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="d3101-108">XML şifrelemesi, bir belgenin birden çok şifrelenmiş öğe içermesini sağlar ve bir öğenin birden çok kez şifrelenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3101-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="d3101-109">Bu yordamdaki kod örneği, `EncryptedData` daha sonra şifre çözme sırasında kullanabileceğiniz diğer birkaç alt öğe ile birlikte bir <> öğesinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3101-109">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="d3101-110">Bu örnek, iki anahtar kullanarak bir XML öğesini şifreler.</span><span class="sxs-lookup"><span data-stu-id="d3101-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="d3101-111">Bir RSA ortak/özel anahtar çifti oluşturur ve anahtar çiftini güvenli anahtar kapsayıcısına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d3101-111">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="d3101-112">Örnek daha sonra, Rijnbael algoritması olarak da bilinen Gelişmiş Şifreleme Standardı (AES) algoritmasını kullanarak ayrı bir oturum anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3101-112">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm, also called the Rijndael algorithm.</span></span>  <span data-ttu-id="d3101-113">Örnek, XML belgesini şifrelemek için AES oturum anahtarını kullanır ve ardından AES oturum anahtarını şifrelemek için RSA ortak anahtarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3101-113">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="d3101-114">Son olarak, örnek, şifreli AES oturum anahtarını ve şifrelenmiş XML verilerini yeni bir <> öğesi içindeki XML belgesine kaydeder `EncryptedData` .</span><span class="sxs-lookup"><span data-stu-id="d3101-114">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="d3101-115">XML öğesinin şifresini çözmek için, anahtar kapsayıcısından RSA özel anahtarını alır, oturum anahtarının şifresini çözmek için onu kullanın ve ardından belgenin şifresini çözmek için oturum anahtarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3101-115">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="d3101-116">Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözme hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerinin şifresini Asimetrik Anahtarlarla çözme](how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="d3101-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="d3101-117">Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, kaç kez şifrelenmiş verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d3101-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="d3101-118">Asimetrik anahtarla bir XML öğesini şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="d3101-118">To encrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="d3101-119">Bir <xref:System.Security.Cryptography.CspParameters> nesne oluşturun ve anahtar kapsayıcısının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d3101-119">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="d3101-120">Sınıfını kullanarak bir simetrik anahtar oluşturun <xref:System.Security.Cryptography.RSACryptoServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="d3101-120">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="d3101-121">Anahtar, nesneyi sınıfının oluşturucusuna geçirdiğinizde anahtar kapsayıcıya otomatik olarak kaydedilir <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="d3101-121">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="d3101-122">Bu anahtar, AES oturum anahtarını şifrelemek için kullanılacaktır ve daha sonra bu dosyanın şifresini çözmek için elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d3101-122">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="d3101-123"><xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3101-123">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="d3101-124"><xref:System.Xml.XmlDocument>Nesne ŞIFRELENECEK XML öğesini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d3101-124">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="d3101-125">Nesnede belirtilen öğeyi bulun <xref:System.Xml.XmlDocument> ve <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3101-125">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="d3101-126">Bu örnekte, `"creditcard"` öğesi şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="d3101-126">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="d3101-127">Sınıfını kullanarak yeni bir oturum anahtarı oluşturun <xref:System.Security.Cryptography.RijndaelManaged> .</span><span class="sxs-lookup"><span data-stu-id="d3101-127">Create a new session key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="d3101-128">Bu anahtar, XML öğesini şifreler ve sonra, bir XML belgesine yerleştirilir ve bu öğe şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="d3101-128">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="d3101-129">Sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.Xml.EncryptedXml> ve oturum anahtarını kullanarak belirtilen öğeyi şifrelemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3101-129">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="d3101-130">Yöntemi, şifreli <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> bir öğe olarak şifrelenmiş bir bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3101-130">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="d3101-131">Bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne oluşturun ve ŞIFRELENMIŞ XML ÖĞESININ URL tanımlayıcısıyla doldurun.</span><span class="sxs-lookup"><span data-stu-id="d3101-131">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="d3101-132">Bu URL tanımlayıcısı, şifre çözme tarafına XML 'in şifreli bir öğe içerdiğini bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3101-132">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="d3101-133"><xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>URL tanımlayıcısını belirtmek için alanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3101-133">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="d3101-134">Düz metin XML öğesi, `EncryptedData` Bu nesne tarafından kapsüllenmiş bir <> öğesi ile değiştirilmeyecektir <xref:System.Security.Cryptography.Xml.EncryptedData> .</span><span class="sxs-lookup"><span data-stu-id="d3101-134">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="d3101-135"><xref:System.Security.Cryptography.Xml.EncryptionMethod>Oturum anahtarını oluşturmak için kullanılan şifreleme ALGORITMASıNıN URL tanımlayıcısı için başlatılan bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3101-135">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="d3101-136"><xref:System.Security.Cryptography.Xml.EncryptionMethod>Nesneyi <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliğe geçirin.</span><span class="sxs-lookup"><span data-stu-id="d3101-136">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="d3101-137"><xref:System.Security.Cryptography.Xml.EncryptedKey>Şifrelenmiş oturum anahtarını içerecek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3101-137">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="d3101-138">Oturum anahtarını şifreleyin, <xref:System.Security.Cryptography.Xml.EncryptedKey> nesnesine ekleyin ve oturum anahtarı adı ile anahtar tanımlayıcı URL 'si girin.</span><span class="sxs-lookup"><span data-stu-id="d3101-138">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="d3101-139"><xref:System.Security.Cryptography.Xml.DataReference>Şifrelenmiş verileri belirli bir oturum anahtarıyla eşleyen yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3101-139">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="d3101-140">Bu isteğe bağlı adım, bir XML belgesinin birden çok bölümünün tek bir anahtarla şifrelendiğini kolayca belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3101-140">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="d3101-141">Şifrelenen anahtarı <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3101-141">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="d3101-142"><xref:System.Security.Cryptography.Xml.KeyInfo>RSA anahtarının adını belirtmek için yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3101-142">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="d3101-143"><xref:System.Security.Cryptography.Xml.EncryptedData>Nesnesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3101-143">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="d3101-144">Bu, şifre çözme tarafına, oturum anahtarının şifresini çözerken kullanılacak doğru asimetrik anahtarı belirlemesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d3101-144">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="d3101-145">Şifrelenen öğe verilerini <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3101-145">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="d3101-146">Öğeyi özgün <xref:System.Xml.XmlDocument> nesnesinden öğesi ile değiştirin <xref:System.Security.Cryptography.Xml.EncryptedData> .</span><span class="sxs-lookup"><span data-stu-id="d3101-146">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="d3101-147">Nesneyi kaydedin <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="d3101-147">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="d3101-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3101-148">Example</span></span>  
 <span data-ttu-id="d3101-149">Bu örnek, adlı bir dosyanın `"test.xml"` derlenen programla aynı dizinde bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="d3101-149">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="d3101-150">Ayrıca `"test.xml"` bir öğesi içerdiğini varsayar `"creditcard"` .</span><span class="sxs-lookup"><span data-stu-id="d3101-150">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="d3101-151">Aşağıdaki XML 'i adlı bir dosyaya yerleştirebilir `test.xml` ve bu örnekle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3101-151">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d3101-152">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d3101-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="d3101-153">Bu örneği derlemek için, öğesine bir başvuru eklemeniz gerekir `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="d3101-153">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="d3101-154">Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="d3101-154">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d3101-155">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d3101-155">.NET Framework Security</span></span>  
 <span data-ttu-id="d3101-156">Simetrik bir şifreleme anahtarını düz metin olarak depolamayın veya bir simetrik anahtarı makineler arasında düz metin olarak aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="d3101-156">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="d3101-157">Bunlara ek olarak, asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="d3101-157">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="d3101-158">Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="d3101-158">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="d3101-159">Doğrudan kaynak kodunuza bir anahtar gömmeyin.</span><span class="sxs-lookup"><span data-stu-id="d3101-159">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="d3101-160">Gömülü anahtarlar [ıldadsm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.</span><span class="sxs-lookup"><span data-stu-id="d3101-160">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="d3101-161">Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemini çağırarak bellekten kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d3101-161">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="d3101-162">Şifreleme anahtarları bazen bir hata ayıklayıcı tarafından bellekten okunabilir veya bellek konumu diske disk belleğine alınmış ise sabit sürücüden okuyabilirler.</span><span class="sxs-lookup"><span data-stu-id="d3101-162">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3101-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3101-163">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="d3101-164">Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="d3101-164">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](how-to-decrypt-xml-elements-with-asymmetric-keys.md)

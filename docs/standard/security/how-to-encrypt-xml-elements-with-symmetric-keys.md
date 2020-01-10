---
title: 'Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
ms.openlocfilehash: cda5a32e9a7421cd65b2046b403fde9e05230493
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706090"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="9dc1f-102">Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="9dc1f-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="9dc1f-103">Bir XML belgesi içindeki bir öğeyi şifrelemek için <xref:System.Security.Cryptography.Xml> ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="9dc1f-104">XML şifrelemesi, gizli XML 'yi kolayca okuyamakta olan veriler hakkında endişelenmenize gerek kalmadan depolamanıza veya taşıetmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="9dc1f-105">Bu yordam, Rijnbael olarak da bilinen Gelişmiş Şifreleme Standardı (AES) algoritmasını kullanarak bir XML öğesini şifreler.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-105">This procedure encrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="9dc1f-106">Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözme hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerinin şifresini simetrik anahtarlarla çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="9dc1f-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="9dc1f-107">XML verilerini şifrelemek için AES gibi simetrik bir algoritma kullandığınızda, XML verilerini şifrelemek ve şifrelerini çözmek için aynı anahtarı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="9dc1f-108">Bu yordamdaki örnek, şifrelenmiş XML 'in aynı anahtar kullanılarak şifresinin çözülemediğini ve şifreleme ve şifre çözme tarafların kullanılacak algoritmayı ve anahtarı kabul etmiş olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="9dc1f-109">Bu örnek, şifreli XML içinde AES anahtarını depolamaz veya şifrelemez.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="9dc1f-110">Bu örnek, tek bir uygulamanın bellekte depolanan bir oturum anahtarını temel alarak veya bir paroladan türetilmiş şifreli olmayan bir güçlü anahtara göre verileri şifrelemek için gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="9dc1f-111">İki veya daha fazla uygulamanın şifrelenmiş XML verilerini paylaşması gereken durumlarda, asimetrik algoritmayı veya X. 509.440 sertifikasını temel alan bir şifreleme düzeni kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="9dc1f-112">XML öğesini bir simetrik anahtarla şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="9dc1f-112">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="9dc1f-113"><xref:System.Security.Cryptography.RijndaelManaged> sınıfını kullanarak bir simetrik anahtar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="9dc1f-114">Bu anahtar, XML öğesini şifrelemek için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="9dc1f-115">Diskten bir XML dosyası yükleyerek <xref:System.Xml.XmlDocument> nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="9dc1f-116"><xref:System.Xml.XmlDocument> nesnesi şifrelenecek XML öğesini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="9dc1f-117"><xref:System.Xml.XmlDocument> nesnesinde belirtilen öğeyi bulun ve şifrelemek istediğiniz öğeyi temsil eden yeni bir <xref:System.Xml.XmlElement> nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="9dc1f-118">Bu örnekte `"creditcard"` öğesi şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="9dc1f-119"><xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfının yeni bir örneğini oluşturun ve bunu simetrik anahtarla <xref:System.Xml.XmlElement> şifrelemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="9dc1f-120"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> yöntemi, şifrelenen bir bayt dizisi olarak şifrelenmiş öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="9dc1f-121">Bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi oluşturun ve bunu XML şifreleme öğesinin URL tanımlayıcısıyla doldurun.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="9dc1f-122">Bu URL tanımlayıcısı, şifre çözme tarafına XML 'in şifreli bir öğe içerdiğini bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="9dc1f-123">URL tanımlayıcısını belirtmek için <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> alanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="9dc1f-124">Anahtarı oluşturmak için kullanılan şifreleme algoritmasının URL tanımlayıcısı için başlatılan bir <xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="9dc1f-125"><xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesini <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliğine geçirin.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="9dc1f-126">Şifrelenmiş öğe verilerini <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="9dc1f-127">Öğeyi özgün <xref:System.Xml.XmlDocument> nesnesinden <xref:System.Security.Cryptography.Xml.EncryptedData> öğesiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="9dc1f-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="9dc1f-128">Example</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9dc1f-129">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="9dc1f-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="9dc1f-130">Bu örneği derlemek için `System.Security.dll`bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="9dc1f-131">Şu ad alanlarını ekleyin: <xref:System.Xml>, <xref:System.Security.Cryptography>ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9dc1f-132">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9dc1f-132">.NET Framework Security</span></span>  
 <span data-ttu-id="9dc1f-133">Bir şifreleme anahtarını düz metin olarak depolamayın veya bir anahtar düz metin olarak makineler arasında aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="9dc1f-134">Bunun yerine, şifreleme anahtarlarını depolamak için güvenli anahtar kapsayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="9dc1f-135">Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya yönetilen şifreleme sınıfının <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yöntemini çağırarak bellekten kaldırın.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc1f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dc1f-136">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="9dc1f-137">Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="9dc1f-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)

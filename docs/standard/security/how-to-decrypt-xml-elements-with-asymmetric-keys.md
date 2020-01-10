---
title: 'Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: 5ed1e2eb2518366da0a57655d7a8691e23f725d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706142"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="f6745-102">Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="f6745-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="f6745-103">Bir XML belgesi içindeki bir öğeyi şifrelemek ve şifrelerini çözmek için <xref:System.Security.Cryptography.Xml> ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6745-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="f6745-104">XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="f6745-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="f6745-105">XML şifreleme standardı hakkında daha fazla bilgi için bkz. World Wide Web Konsorsiyumu (W3C) önerisi [XML Imzası sözdizimi ve işleme](https://www.w3.org/TR/xmldsig-core/).</span><span class="sxs-lookup"><span data-stu-id="f6745-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="f6745-106">Bu yordamdaki örnek, [nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)bölümünde açıklanan yöntemler kullanılarak ŞIFRELENMIŞ bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="f6745-106">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="f6745-107">Bir <`EncryptedData`> öğesi bulur, öğenin şifresini çözer ve sonra öğeyi özgün düz metin XML öğesiyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f6745-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="f6745-108">Bu örnek, iki anahtar kullanarak bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="f6745-108">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="f6745-109">Daha önce oluşturulmuş bir RSA özel anahtarını anahtar kapsayıcısından alır ve ardından RSA anahtarını, <`EncryptedData`> öğesinin <`EncryptedKey`> öğesinde depolanan bir oturum anahtarının şifresini çözmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6745-109">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="f6745-110">Daha sonra örnek, XML öğesinin şifresini çözmek için oturum anahtarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6745-110">The example then uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="f6745-111">Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, şifrelenen verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="f6745-111">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="f6745-112">Asimetrik anahtarla bir XML öğesinin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="f6745-112">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="f6745-113"><xref:System.Security.Cryptography.CspParameters> nesnesi oluşturun ve anahtar kapsayıcısının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f6745-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="f6745-114"><xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesini kullanarak kapsayıcıdan daha önce üretilmiş bir asimetrik anahtar alın.</span><span class="sxs-lookup"><span data-stu-id="f6745-114">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="f6745-115"><xref:System.Security.Cryptography.CspParameters> nesnesini <xref:System.Security.Cryptography.RSACryptoServiceProvider> oluşturucusuna geçirdiğinizde anahtar kapsayıcısından anahtar otomatik olarak alınır.</span><span class="sxs-lookup"><span data-stu-id="f6745-115">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="f6745-116">Belgenin şifresini çözmek için yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f6745-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="f6745-117">RSA anahtarını, şifresi çözülmesi gereken belge içindeki öğeyle ilişkilendirmek için bir anahtar/ad eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6745-117">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="f6745-118">Belgeyi şifrelediyseniz kullandığınız anahtar için aynı adı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6745-118">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="f6745-119">Bu adın, 1. adımda belirtilen anahtar kapsayıcısında anahtarı tanımlamak için kullanılan adından ayrı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f6745-119">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="f6745-120">`EncryptedData`> öğesinin şifresini çözmek için <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="f6745-120">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="f6745-121">Bu yöntem, oturum anahtarının şifresini çözmek için RSA anahtarını kullanır ve XML öğesinin şifresini çözmek için oturum anahtarını otomatik olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6745-121">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="f6745-122">Ayrıca, <`EncryptedData`> öğesini özgün düz metin ile otomatik olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f6745-122">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="f6745-123">XML belgesini kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f6745-123">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="f6745-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6745-124">Example</span></span>  
 <span data-ttu-id="f6745-125">Bu örnek, `test.xml` adlı bir dosyanın derlenen programla aynı dizinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="f6745-125">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="f6745-126">Ayrıca, `test.xml` [nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)bölümünde açıklanan teknikler kullanılarak ŞIFRELENMIŞ bir XML öğesi içerdiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="f6745-126">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6745-127">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="f6745-127">Compiling the Code</span></span>  
  
- <span data-ttu-id="f6745-128">Bu örneği derlemek için `System.Security.dll`bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6745-128">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="f6745-129">Şu ad alanlarını ekleyin: <xref:System.Xml>, <xref:System.Security.Cryptography>ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="f6745-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f6745-130">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f6745-130">.NET Framework Security</span></span>  
 <span data-ttu-id="f6745-131">Simetrik bir şifreleme anahtarını düz metin olarak depolamayın veya bir simetrik anahtarı makineler arasında düz metin olarak aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="f6745-131">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="f6745-132">Bunlara ek olarak, asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="f6745-132">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="f6745-133">Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="f6745-133">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="f6745-134">Doğrudan kaynak kodunuza bir anahtar gömmeyin.</span><span class="sxs-lookup"><span data-stu-id="f6745-134">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="f6745-135">Gömülü anahtarlar [ıldadsm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.</span><span class="sxs-lookup"><span data-stu-id="f6745-135">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="f6745-136">Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya yönetilen şifreleme sınıfının <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yöntemini çağırarak bellekten kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f6745-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="f6745-137">Şifreleme anahtarları bazen bir hata ayıklayıcı tarafından bellekten okunabilir veya bellek konumu diske disk belleğine alınmış ise sabit sürücüden okuyabilirler.</span><span class="sxs-lookup"><span data-stu-id="f6745-137">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6745-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6745-138">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="f6745-139">Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="f6745-139">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)

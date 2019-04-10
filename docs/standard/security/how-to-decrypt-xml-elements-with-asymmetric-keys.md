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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 303c7db984b682d24a8f0e00160eb2d0827a84e6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314431"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="b7b4b-102">Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="b7b4b-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="b7b4b-103">Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> şifreleme ve şifre çözme bir XML belgesi içindeki bir öğe için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="b7b4b-104">XML şifreleme, exchange veya bir kolayca okunan verilerin hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="b7b4b-105">XML şifreleme standardı hakkında daha fazla bilgi için bkz. World Wide Web Consortium (W3C) öneri [XML imza söz dizimi ve işleme](https://www.w3.org/TR/xmldsig-core/).</span><span class="sxs-lookup"><span data-stu-id="b7b4b-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="b7b4b-106">Bu yordamdaki örnek da açıklanmış yöntemleri kullanılarak şifrelenmiş bir XML öğesi şifresini çözer [nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="b7b4b-106">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="b7b4b-107">Bulduğu bir <`EncryptedData`> öğesi, öğenin şifresini çözer ve daha sonra öğenin özgün düz metin XML öğesi ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="b7b4b-108">Bu örnekte, iki anahtar kullanarak bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-108">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="b7b4b-109">Daha önce oluşturulan bir RSA özel anahtarı bir anahtar kapsayıcısından alır ve ardından bir oturum anahtarı şifresini çözmek için RSA anahtarı içinde depolanan kullanır <`EncryptedKey`> öğesi <`EncryptedData`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-109">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="b7b4b-110">Örnek, XML öğesinin şifresini çözmek için daha sonra oturum anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-110">The example then uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="b7b4b-111">Bu örnek, birden çok uygulama şifrelenmiş veri paylaşımı sahip olduğu veya bir uygulamanın çalıştığı zamanları arasında şifrelenmiş verileri kaydetmek sahip olduğu durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-111">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="b7b4b-112">Asimetrik anahtar ile bir XML öğesinin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="b7b4b-112">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="b7b4b-113">Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve anahtar kapsayıcısı adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="b7b4b-114">Daha önce oluşturulan bir asimetrik anahtar kullanarak kapsayıcıdaki almak <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesne.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-114">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="b7b4b-115">Anahtar, başarılı olduğunda otomatik olarak anahtar kapsayıcısından alındığı <xref:System.Security.Cryptography.CspParameters> nesnesini <xref:System.Security.Cryptography.RSACryptoServiceProvider> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-115">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="b7b4b-116">Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> belgenin şifresini çözmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="b7b4b-117">Öğe çözülmeli belge içinde RSA anahtarı ilişkilendirmek için bir anahtar/ad eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-117">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="b7b4b-118">Belge şifreli kullandığınız anahtarı için aynı adı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-118">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="b7b4b-119">Bu ad, 1. adımda belirtilen anahtar kapsayıcısında anahtarını tanımlamak üzere kullanılan ad ayrıdır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-119">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="b7b4b-120">Çağrı <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> şifresini çözmek için gereken yöntemini <`EncryptedData`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-120">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="b7b4b-121">Bu yöntem, oturum anahtarının şifresini çözmek için RSA anahtarını kullanır ve otomatik olarak XML öğesinin şifresini çözmek için oturum anahtarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-121">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="b7b4b-122">Ayrıca otomatik olarak değiştirir <`EncryptedData`> öğesi ile özgün düz metin.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-122">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="b7b4b-123">XML belgesi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-123">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="b7b4b-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7b4b-124">Example</span></span>  
 <span data-ttu-id="b7b4b-125">Bu örnek adlı bir dosya olduğunu varsayar `test.xml` derlenmiş programın aynı dizinde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-125">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="b7b4b-126">Ayrıca varsayılmaktadır `test.xml` açıklanan teknikleri kullanılarak şifrelenmiş bir XML öğesi içeren [nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="b7b4b-126">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b7b4b-127">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b7b4b-127">Compiling the Code</span></span>  
  
-   <span data-ttu-id="b7b4b-128">Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-128">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="b7b4b-129">Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b7b4b-130">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b7b4b-130">.NET Framework Security</span></span>  
 <span data-ttu-id="b7b4b-131">Hiçbir zaman düz metin olarak bir simetrik şifreleme anahtarı depolamak veya makine düz metin arasında bir simetrik anahtar aktarın.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-131">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="b7b4b-132">Buna ek olarak, hiçbir zaman depolayabilen veya asimetrik anahtar çifti düz metin olarak özel anahtarı.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-132">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="b7b4b-133">Simetrik hem de asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="b7b4b-133">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="b7b4b-134">Hiçbir zaman doğrudan sizin kaynak kodunuza bir anahtar ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-134">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="b7b4b-135">Katıştırılmış anahtarları kolayca okunabilir bir derlemeden kullanarak [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-135">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="b7b4b-136">İşiniz bittiğinde bir şifreleme anahtarı kullanarak temizleyin, bellekten her byte sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="b7b4b-137">Şifreleme anahtarlarını bazen bellekten bir hata ayıklayıcı tarafından okunabilir veya disk belleğine alınan bellek konumunda bir sabit diskten okunur diske.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-137">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b4b-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7b4b-138">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="b7b4b-139">Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="b7b4b-139">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)

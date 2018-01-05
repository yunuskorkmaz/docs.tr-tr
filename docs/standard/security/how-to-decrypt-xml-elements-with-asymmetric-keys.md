---
title: "Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme"
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
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 099937fe113c39c717b4c9fcba2042115b9105e6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="47886-102">Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="47886-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="47886-103">Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> şifrelemek ve şifresini çözmek bir XML belgesi içindeki bir öğe için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="47886-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="47886-104">XML şifrelemesi, exchange veya kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="47886-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="47886-105">World Wide Web Konsorsiyumu (W3C) öneri XML şifreleme standardı hakkında daha fazla bilgi için bkz: [XML imza sözdizimi ve işleme](http://go.microsoft.com/fwlink/?LinkID=136777).</span><span class="sxs-lookup"><span data-stu-id="47886-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](http://go.microsoft.com/fwlink/?LinkID=136777).</span></span>  
  
 <span data-ttu-id="47886-106">Bu yordamı örnekte açıklanan yöntemleri kullanılarak şifrelenmiş bir XML öğesi şifresini çözer [nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="47886-106">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="47886-107">Bulduğu bir <`EncryptedData`> öğesi, öğenin şifresini çözer ve özgün düz metin XML öğesi ile öğenin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="47886-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="47886-108">Bu örnek iki anahtarlar kullanılarak bir XML öğesi şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="47886-108">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="47886-109">Bir anahtar kapsayıcı önceden oluşturulan bir RSA özel anahtarı alır ve ardından kullanan bir oturum anahtarı şifresini çözmek için RSA anahtarı depolanan <`EncryptedKey`> öğesi <`EncryptedData`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="47886-109">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="47886-110">Örnek sonra XML öğesi şifresini çözmek için oturum anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="47886-110">The example then uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="47886-111">Bu örnek, şifrelenmiş veriler paylaşmak birden çok uygulamalara sahip olduğu ya da uygulamanın çalıştığı zamanları arasında şifrelenmiş verileri kaydetmek sahip olduğu durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="47886-111">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="47886-112">Bir XML öğesi bir asimetrik anahtar şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="47886-112">To decrypt an XML element with an asymmetric key</span></span>  
  
1.  <span data-ttu-id="47886-113">Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve anahtar kapsayıcı adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="47886-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="47886-114">Kapsayıcı kullanmaktan daha önce oluşturulan bir asimetrik anahtar almak <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="47886-114">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="47886-115">Geçirdiğiniz anahtarı otomatik olarak anahtar kapsayıcıdan alınır <xref:System.Security.Cryptography.CspParameters> nesnesine <xref:System.Security.Cryptography.RSACryptoServiceProvider> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="47886-115">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="47886-116">Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> belgenin şifresini çözmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="47886-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  <span data-ttu-id="47886-117">RSA anahtar şifresi belge içindeki öğe ilişkilendirmek için bir anahtar/ad eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="47886-117">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="47886-118">Bu belge şifreli olduğunda, kullanılan anahtar için aynı adı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47886-118">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="47886-119">Bu ad 1. adımda belirtilen anahtar kapsayıcısı anahtarında tanımlamak için kullanılan ad ayrı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="47886-119">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  <span data-ttu-id="47886-120">Çağrı <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> şifresini çözmek için yöntemi <`EncryptedData`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="47886-120">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="47886-121">Bu yöntem, oturum anahtarının şifresini çözmek için RSA anahtarı kullanan ve otomatik olarak XML öğesi şifresini çözmek için oturum anahtarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="47886-121">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="47886-122">Ayrıca otomatik olarak değiştirir <`EncryptedData`> öğesi özgün düz metin ile.</span><span class="sxs-lookup"><span data-stu-id="47886-122">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  <span data-ttu-id="47886-123">XML belgesi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="47886-123">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="47886-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="47886-124">Example</span></span>  
 <span data-ttu-id="47886-125">Bu örnek, bir dosya adlı varsayar `test.xml` derlenmiş programın aynı dizinde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47886-125">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="47886-126">Ayrıca varsayılmaktadır `test.xml` açıklanan teknikleri kullanılarak şifrelenmiş bir XML öğesi içeren [nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="47886-126">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47886-127">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="47886-127">Compiling the Code</span></span>  
  
-   <span data-ttu-id="47886-128">Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="47886-128">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="47886-129">Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="47886-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="47886-130">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="47886-130">.NET Framework Security</span></span>  
 <span data-ttu-id="47886-131">Düz metin olarak hiçbir zaman bir simetrik şifreleme anahtarı depolamak veya düz metin olarak makineler arasında bir simetrik anahtar aktarın.</span><span class="sxs-lookup"><span data-stu-id="47886-131">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="47886-132">Buna ek olarak, hiçbir zaman depolamak veya asimetrik anahtar çifti düz metin olarak özel anahtarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="47886-132">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="47886-133">Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz: [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="47886-133">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="47886-134">Hiç kaynak kodunuza doğrudan bir anahtar ekleyin.</span><span class="sxs-lookup"><span data-stu-id="47886-134">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="47886-135">Katıştırılmış anahtarları kolay okunabilir bir derlemeye ait kullanarak [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.</span><span class="sxs-lookup"><span data-stu-id="47886-135">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="47886-136">İşiniz bittiğinde şifreleme anahtarını kullanarak temizleyin, bellekten her bayt sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="47886-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="47886-137">Şifreleme anahtarları bazen bellekten bir hata ayıklayıcı tarafından okunabilir veya bellek konumuna disk belleği, bir sabit diskten okuma diske.</span><span class="sxs-lookup"><span data-stu-id="47886-137">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47886-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47886-138">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="47886-139">Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="47886-139">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)

---
title: "Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme"
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
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6bacdb47d1107f6a800d9beec2578c0f7085a894
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="cd4f5-102">Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="cd4f5-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="cd4f5-103">Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi içindeki bir öğe şifrelemek için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="cd4f5-104">XML şifrelemesi, saklamak veya hassas XML kolayca okunan veriler hakkında endişelenmeden aktarım olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="cd4f5-105">Bu kod örneği olarak da bilinen Rijndael Gelişmiş Şifreleme Standardı (AES) algoritması kullanılarak bir XML öğesi şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="cd4f5-106">Bu yordamı kullanarak bir XML öğesi şifreleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="cd4f5-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="cd4f5-107">XML verileri şifrelemek için simetrik algoritması AES gibi kullandığınızda, şifrelemek ve XML verilerin şifresini çözmek için aynı anahtarı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="cd4f5-108">Bu yordamdaki örneğin varsayar şifrelenmiş XML aynı anahtar kullanılarak şifrelenmiş ve şifreleme ve tarafların şifre çözme algoritması ve anahtarı kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="cd4f5-109">Bu örnek depolamaz veya şifrelenmiş XML içindeki AES anahtarını şifrelemek.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="cd4f5-110">Bu örnek, burada bellekte ya da bir parolasından türetilen şifreleme açısından güçlü bir anahtarı temel alan bir oturum anahtarı temel alan verileri şifrelemek için tek bir uygulama gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="cd4f5-111">Burada şifrelenmiş XML verileri paylaşmak için iki veya daha fazla uygulama gereken durumlar için asimetrik algoritma veya bir X.509 sertifikası göre bir şifreleme şeması kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="cd4f5-112">XML öğesinin şifresini bir simetrik anahtarla çözmek için</span><span class="sxs-lookup"><span data-stu-id="cd4f5-112">To decrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="cd4f5-113">Bir XML öğesi içinde açıklanan teknikleri kullanarak daha önce oluşturulan anahtar ile şifreleme [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="cd4f5-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="cd4f5-114">Bul <`EncryptedData`> (XML şifreleme standardı tarafından tanımlanan) öğesinde bir <xref:System.Xml.XmlDocument> şifrelenmiş XML içeren nesne ve yeni bir <xref:System.Xml.XmlElement> bu öğeyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  <span data-ttu-id="cd4f5-115">Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptedData> ham XML verilerini önceden oluşturulan yükleme nesne <xref:System.Xml.XmlElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  <span data-ttu-id="cd4f5-116">Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> nesne ve şifreleme için kullanılan aynı anahtarı kullanarak XML verileri şifrelemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  <span data-ttu-id="cd4f5-117">XML belgesi içindeki yeni şifresi çözülmüş düz metin öğesiyle şifrelenmiş öğeyi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="cd4f5-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd4f5-118">Example</span></span>  
 <span data-ttu-id="cd4f5-119">Bu örnek, bir dosya adlı varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="cd4f5-120">Ayrıca varsayılmaktadır `"test.xml"` içeren bir `"creditcard"` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="cd4f5-121">Aşağıdaki XML adlı bir dosyaya yerleştirebilirsiniz `test.xml` ve bu örnek ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd4f5-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cd4f5-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="cd4f5-123">Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="cd4f5-124">Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cd4f5-125">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="cd4f5-125">.NET Framework Security</span></span>  
 <span data-ttu-id="cd4f5-126">Düz metin olarak hiçbir zaman bir şifreleme anahtarı depolamak veya düz metin olarak makineler arasında bir anahtar aktarın.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-126">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
 <span data-ttu-id="cd4f5-127">İşiniz bittiğinde simetrik şifreleme anahtarını kullanarak temizleyin, bellekten her bayt sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-127">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd4f5-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd4f5-128">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="cd4f5-129">Nasıl yapılır: XML öğelerini simetrik anahtarlarla şifreleme</span><span class="sxs-lookup"><span data-stu-id="cd4f5-129">How to: Encrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)

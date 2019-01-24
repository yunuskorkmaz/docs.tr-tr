---
title: 'Nasıl yapılır: XML öğelerini simetrik anahtarlarla şifre çözme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19ee0e3244d9a9bf7d7eddc9be4eb7c50b467cf5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502630"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="7b7a3-102">Nasıl yapılır: XML öğelerini simetrik anahtarlarla şifre çözme</span><span class="sxs-lookup"><span data-stu-id="7b7a3-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="7b7a3-103">Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi bir öğesinde şifrelemek için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="7b7a3-104">XML şifreleme depolamak veya hassas XML kolay okunan verilerin hakkında endişelenmeden taşıma sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="7b7a3-105">Bu kod örneği, Gelişmiş Şifreleme Standardı (AES) olarak da bilinen Rijndael algoritmasını kullanarak bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="7b7a3-106">Bu yordamı kullanarak bir XML öğesi şifreleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="7b7a3-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="7b7a3-107">XML verileri şifrelemek için Simetrik algoritma AES gibi kullandığınızda, aynı anahtar şifreleme ve şifre çözme XML verileri için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="7b7a3-108">Bu yordamdaki örnek olduğunu varsayar aynı anahtar kullanılarak şifrelenmiş XML şifrelenmiş ve şifreleme ve taraflar şifre çözme algoritması ve anahtar kullanmayı kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="7b7a3-109">Bu örnekte depolamak veya şifrelenmiş XML içinde AES anahtarını şifrelemek desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="7b7a3-110">Bu örnek, tek bir uygulama bellekte veya bir parolasından türetilen şifreleme açısından güçlü bir anahtara göre bir oturum anahtarı temel alan verileri şifrelemek için gereken yere durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="7b7a3-111">İki veya daha fazla uygulama şifrelenmiş XML veri paylaşımı için gereken yere durumlarda, asimetrik algoritma veya bir X.509 sertifikası tabanlı bir şifreleme şeması kullanılarak göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="7b7a3-112">XML öğesinin şifresini bir simetrik anahtarla çözmek için</span><span class="sxs-lookup"><span data-stu-id="7b7a3-112">To decrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="7b7a3-113">Bir XML öğesi içinde açıklanan teknikleri kullanarak daha önce oluşturulmuş anahtarla şifrelemek [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="7b7a3-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="7b7a3-114">Bulma <`EncryptedData`> (XML şifreleme standardı tarafından tanımlanan) öğesinde bir <xref:System.Xml.XmlDocument> şifrelenmiş XML içeren nesne ve yeni bir <xref:System.Xml.XmlElement> o öğenin temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  <span data-ttu-id="7b7a3-115">Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptedData> ham XML verileri daha önce oluşturulan yüklerken nesne <xref:System.Xml.XmlElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  <span data-ttu-id="7b7a3-116">Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> nesne ve şifreleme için kullanılan aynı anahtarı kullanarak XML verileri şifrelemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  <span data-ttu-id="7b7a3-117">XML belgesi içindeki yeni şifresi düz metin öğesi ile şifrelenmiş öğeyi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="7b7a3-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b7a3-118">Example</span></span>  
 <span data-ttu-id="7b7a3-119">Bu örnek adlı bir dosya olduğunu varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="7b7a3-120">Ayrıca varsayılmaktadır `"test.xml"` içeren bir `"creditcard"` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="7b7a3-121">Aşağıdaki XML adlı bir dosyaya yerleştirebilirsiniz `test.xml` ve bu örneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="7b7a3-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7b7a3-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="7b7a3-123">Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="7b7a3-124">Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7b7a3-125">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="7b7a3-125">.NET Framework Security</span></span>  
 <span data-ttu-id="7b7a3-126">Hiçbir zaman düz metin olarak bir şifreleme anahtarı depolamak veya düz metin makineler arasında bir anahtar aktarımı.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-126">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
 <span data-ttu-id="7b7a3-127">İşiniz bittiğinde bir simetrik şifreleme anahtarını kullanarak temizleyin, bellekten her byte sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-127">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7a3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b7a3-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="7b7a3-129">Nasıl yapılır: XML öğelerini simetrik anahtarlarla şifreleme</span><span class="sxs-lookup"><span data-stu-id="7b7a3-129">How to: Encrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)

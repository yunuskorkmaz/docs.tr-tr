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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d9fa06ed0befd82a3efdd46deaa2362b1f10fa35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586081"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="08f3d-102">Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="08f3d-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="08f3d-103">Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi içindeki bir öğe şifrelemek için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="08f3d-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="08f3d-104">XML şifrelemesi, saklamak veya hassas XML kolayca okunan veriler hakkında endişelenmeden aktarım olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="08f3d-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="08f3d-105">Bu yordam, Gelişmiş Şifreleme Standardı (AES) algoritması, olarak da bilinen Rijndael kullanarak bir XML öğesi şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="08f3d-105">This procedure decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="08f3d-106">Bu yordam kullanılarak şifrelenmiş bir XML öğesi şifresini çözme hakkında daha fazla bilgi için bkz: [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifresini](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="08f3d-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="08f3d-107">XML verileri şifrelemek için simetrik algoritması AES gibi kullandığınızda, şifrelemek ve XML verilerin şifresini çözmek için aynı anahtarı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08f3d-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="08f3d-108">Bu yordamdaki örneğin şifrelenmiş XML aynı anahtarı kullanarak şifresi çözülmüş olacağını ve şifreleme ve tarafların şifre çözme algoritması ve anahtarı kabul varsayar.</span><span class="sxs-lookup"><span data-stu-id="08f3d-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="08f3d-109">Bu örnek depolamaz veya şifrelenmiş XML içindeki AES anahtarını şifrelemek.</span><span class="sxs-lookup"><span data-stu-id="08f3d-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="08f3d-110">Bu örnek, burada bellekte ya da bir parolasından türetilen şifreleme açısından güçlü bir anahtarı temel alan bir oturum anahtarı temel alan verileri şifrelemek için tek bir uygulama gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="08f3d-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="08f3d-111">Burada şifrelenmiş XML verileri paylaşmak için iki veya daha fazla uygulama gereken durumlar için asimetrik algoritma veya bir X.509 sertifikası göre bir şifreleme şeması kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="08f3d-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="08f3d-112">XML öğesini bir simetrik anahtarla şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="08f3d-112">To encrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="08f3d-113">Bir simetrik anahtar kullanarak Oluştur <xref:System.Security.Cryptography.RijndaelManaged> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="08f3d-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="08f3d-114">Bu anahtar, XML öğesi şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08f3d-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="08f3d-115">Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.</span><span class="sxs-lookup"><span data-stu-id="08f3d-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="08f3d-116"><xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="08f3d-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="08f3d-117">Belirtilen öğe Bul <xref:System.Xml.XmlDocument> nesne ve yeni bir <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="08f3d-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="08f3d-118">Bu örnekte, `"creditcard"` öğesi şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="08f3d-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="08f3d-119">Yeni bir örneğini oluşturmak <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfı ve şifrelemek için kullandığınız <xref:System.Xml.XmlElement> simetrik anahtara sahip.</span><span class="sxs-lookup"><span data-stu-id="08f3d-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="08f3d-120"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Yöntem şifrelenmiş bir bayt dizisi şifrelenmiş öğesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="08f3d-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="08f3d-121">Oluşturmak bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne ve XML şifrelemesi öğesi URL tanıtıcısı ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="08f3d-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="08f3d-122">Bu URL tanımlayıcı XML şifrelenmiş bir öğe içeriyor bilmeniz şifresi çözme bir taraf sağlar.</span><span class="sxs-lookup"><span data-stu-id="08f3d-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="08f3d-123">Kullanabileceğiniz <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> alan URL tanımlayıcısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="08f3d-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="08f3d-124">Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptionMethod> anahtarı oluşturmak için kullanılan şifreleme algoritması URL tanıtıcısı başlatılmamış nesne.</span><span class="sxs-lookup"><span data-stu-id="08f3d-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="08f3d-125">Geçirmek <xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesinin <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="08f3d-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="08f3d-126">Şifreli öğe verileri eklediğinizde <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="08f3d-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="08f3d-127">Özgün öğeyi değiştirin <xref:System.Xml.XmlDocument> nesnesi ile <xref:System.Security.Cryptography.Xml.EncryptedData> öğesi.</span><span class="sxs-lookup"><span data-stu-id="08f3d-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="08f3d-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="08f3d-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="08f3d-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="08f3d-129">Compiling the Code</span></span>  
  
-   <span data-ttu-id="08f3d-130">Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="08f3d-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="08f3d-131">Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="08f3d-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="08f3d-132">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="08f3d-132">.NET Framework Security</span></span>  
 <span data-ttu-id="08f3d-133">Düz metin olarak hiçbir zaman bir şifreleme anahtarı depolamak veya düz metin olarak makineler arasında bir anahtar aktarın.</span><span class="sxs-lookup"><span data-stu-id="08f3d-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="08f3d-134">Bunun yerine, şifreleme anahtarlarını depolamak için güvenli bir anahtar kapsayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="08f3d-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="08f3d-135">İşiniz bittiğinde şifreleme anahtarını kullanarak temizleyin, bellekten her bayt sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="08f3d-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f3d-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08f3d-136">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="08f3d-137">Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="08f3d-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)

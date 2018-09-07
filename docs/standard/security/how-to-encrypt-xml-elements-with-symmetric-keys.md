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
ms.openlocfilehash: f5c221dc05787c6d76d998977069ad327a3dfa83
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097518"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="b6ef0-102">Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="b6ef0-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="b6ef0-103">Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi bir öğesinde şifrelemek için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="b6ef0-104">XML şifreleme depolamak veya hassas XML kolay okunan verilerin hakkında endişelenmeden taşıma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="b6ef0-105">Bu yordam olarak da bilinen Rijndael Gelişmiş Şifreleme Standardı (AES) algoritması kullanılarak bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-105">This procedure decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="b6ef0-106">Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözmek hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifre çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="b6ef0-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="b6ef0-107">XML verileri şifrelemek için Simetrik algoritma AES gibi kullandığınızda, aynı anahtar şifreleme ve şifre çözme XML verileri için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="b6ef0-108">Bu yordamdaki örnek, şifrelenmiş XML aynı anahtar ile şifresi çözülmüş olacaktır ve şifreleme ve taraflar şifre çözme algoritması ve kullanılacak anahtarı kabul varsayar.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="b6ef0-109">Bu örnekte depolamak veya şifrelenmiş XML içinde AES anahtarını şifrelemek desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="b6ef0-110">Bu örnek, tek bir uygulama bellekte veya bir parolasından türetilen şifreleme açısından güçlü bir anahtara göre bir oturum anahtarı temel alan verileri şifrelemek için gereken yere durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="b6ef0-111">İki veya daha fazla uygulama şifrelenmiş XML veri paylaşımı için gereken yere durumlarda, asimetrik algoritma veya bir X.509 sertifikası tabanlı bir şifreleme şeması kullanılarak göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="b6ef0-112">XML öğesini bir simetrik anahtarla şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="b6ef0-112">To encrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="b6ef0-113">Bir simetrik anahtar kullanarak Oluştur <xref:System.Security.Cryptography.RijndaelManaged> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="b6ef0-114">Bu anahtar, XML öğesi şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="b6ef0-115">Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="b6ef0-116"><xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="b6ef0-117">Belirtilen öğe Bul <xref:System.Xml.XmlDocument> nesne ve yeni bir <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="b6ef0-118">Bu örnekte, `"creditcard"` öğesi şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="b6ef0-119">Yeni bir örneğini oluşturma <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfı ve şifrelemek üzere kullanmak <xref:System.Xml.XmlElement> simetrik anahtara sahip.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="b6ef0-120"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Yöntem şifrelenmiş öğesi şifrelenmiş bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="b6ef0-121">Oluşturmak bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne ve XML şifreleme öğesinin URL tanımlayıcısı ile doldurun.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="b6ef0-122">Bu URL tanımlayıcısı XML şifrelenmiş bir öğe içerdiğini bildiğiniz öğesinin şifresini çözerken bir taraf sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="b6ef0-123">Kullanabileceğiniz <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> alanını URL tanımlayıcısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="b6ef0-124">Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptionMethod> şifreleme algoritması anahtarı oluşturmak için kullanılan URL tanımlayıcısı için başlatılmış olan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="b6ef0-125">Geçirmek <xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesini <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="b6ef0-126">Şifreli öğe verileri eklediğinizde <xref:System.Security.Cryptography.Xml.EncryptedData> nesne.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="b6ef0-127">Özgün öğeden değiştirin <xref:System.Xml.XmlDocument> nesnesi ile <xref:System.Security.Cryptography.Xml.EncryptedData> öğesi.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="b6ef0-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6ef0-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b6ef0-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b6ef0-129">Compiling the Code</span></span>  
  
-   <span data-ttu-id="b6ef0-130">Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="b6ef0-131">Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b6ef0-132">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b6ef0-132">.NET Framework Security</span></span>  
 <span data-ttu-id="b6ef0-133">Hiçbir zaman düz metin olarak bir şifreleme anahtarı depolamak veya düz metin makineler arasında bir anahtar aktarımı.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="b6ef0-134">Bunun yerine, şifreleme anahtarlarını depolamak için güvenli bir anahtar kapsayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="b6ef0-135">İşiniz bittiğinde bir şifreleme anahtarı kullanarak temizleyin, bellekten her byte sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ef0-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6ef0-136">See also</span></span>

- <xref:System.Security.Cryptography.Xml>  
- [<span data-ttu-id="b6ef0-137">Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="b6ef0-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)

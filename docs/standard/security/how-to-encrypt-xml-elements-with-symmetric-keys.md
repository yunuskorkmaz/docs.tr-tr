---
description: 'Daha fazla bilgi edinin: nasıl yapılır: XML öğelerini Simetrik Anahtarlarla Şifreleme'
title: 'Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET], symmetric keys
- encryption [.NET], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- Advanced Encryption Standard algorithm
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
ms.openlocfilehash: 137e1592a73ff9eb25fd6a5ba29b92c839f44575
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685120"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="4f274-103">Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="4f274-103">How to: Encrypt XML Elements with Symmetric Keys</span></span>

<span data-ttu-id="4f274-104"><xref:System.Security.Cryptography.Xml>BIR XML belgesi içindeki bir öğeyi şifrelemek için ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f274-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="4f274-105">XML şifrelemesi, gizli XML 'yi kolayca okuyamakta olan veriler hakkında endişelenmenize gerek kalmadan depolamanıza veya taşıetmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4f274-105">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="4f274-106">Bu yordam, Gelişmiş Şifreleme Standardı (AES) algoritmasını kullanarak bir XML öğesini şifreler.</span><span class="sxs-lookup"><span data-stu-id="4f274-106">This procedure encrypts an XML element using the Advanced Encryption Standard (AES) algorithm.</span></span>  
  
 <span data-ttu-id="4f274-107">Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözme hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerinin şifresini simetrik anahtarlarla çözme](how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="4f274-107">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="4f274-108">XML verilerini şifrelemek için AES gibi simetrik bir algoritma kullandığınızda, XML verilerini şifrelemek ve şifrelerini çözmek için aynı anahtarı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f274-108">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="4f274-109">Bu yordamdaki örnek, şifrelenmiş XML 'in aynı anahtar kullanılarak şifresinin çözülemediğini ve şifreleme ve şifre çözme tarafların kullanılacak algoritmayı ve anahtarı kabul etmiş olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="4f274-109">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="4f274-110">Bu örnek, şifreli XML içinde AES anahtarını depolamaz veya şifrelemez.</span><span class="sxs-lookup"><span data-stu-id="4f274-110">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="4f274-111">Bu örnek, tek bir uygulamanın bellekte depolanan bir oturum anahtarını temel alarak veya bir paroladan türetilmiş şifreli olmayan bir güçlü anahtara göre verileri şifrelemek için gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="4f274-111">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="4f274-112">İki veya daha fazla uygulamanın şifrelenmiş XML verilerini paylaşması gereken durumlarda, asimetrik algoritmayı veya X. 509.440 sertifikasını temel alan bir şifreleme düzeni kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="4f274-112">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="4f274-113">XML öğesini bir simetrik anahtarla şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="4f274-113">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="4f274-114">Sınıfını kullanarak bir simetrik anahtar oluşturun <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="4f274-114">Generate a symmetric key using the <xref:System.Security.Cryptography.Aes> class.</span></span>  <span data-ttu-id="4f274-115">Bu anahtar, XML öğesini şifrelemek için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="4f274-115">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="4f274-116"><xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4f274-116">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="4f274-117"><xref:System.Xml.XmlDocument>Nesne ŞIFRELENECEK XML öğesini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="4f274-117">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="4f274-118">Nesnede belirtilen öğeyi bulun <xref:System.Xml.XmlDocument> ve <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4f274-118">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="4f274-119">Bu örnekte, `"creditcard"` öğesi şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="4f274-119">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="4f274-120">Sınıfının yeni bir örneğini oluşturun <xref:System.Security.Cryptography.Xml.EncryptedXml> ve bunu simetrik anahtarla şifrelemek için kullanın <xref:System.Xml.XmlElement> .</span><span class="sxs-lookup"><span data-stu-id="4f274-120">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="4f274-121">Yöntemi, şifreli <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> bir öğe olarak şifrelenmiş bir bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f274-121">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="4f274-122">Bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne oluşturun ve bunu XML şifreleme ÖĞESININ URL tanımlayıcısıyla doldurun.</span><span class="sxs-lookup"><span data-stu-id="4f274-122">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="4f274-123">Bu URL tanımlayıcısı, şifre çözme tarafına XML 'in şifreli bir öğe içerdiğini bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f274-123">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="4f274-124"><xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>URL tanımlayıcısını belirtmek için alanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f274-124">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="4f274-125"><xref:System.Security.Cryptography.Xml.EncryptionMethod>Anahtarı oluşturmak için kullanılan şifreleme ALGORITMASıNıN URL tanımlayıcısı için başlatılan bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4f274-125">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="4f274-126"><xref:System.Security.Cryptography.Xml.EncryptionMethod>Nesneyi <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliğe geçirin.</span><span class="sxs-lookup"><span data-stu-id="4f274-126">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="4f274-127">Şifrelenen öğe verilerini <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4f274-127">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="4f274-128">Öğeyi özgün <xref:System.Xml.XmlDocument> nesnesinden öğesi ile değiştirin <xref:System.Security.Cryptography.Xml.EncryptedData> .</span><span class="sxs-lookup"><span data-stu-id="4f274-128">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="4f274-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f274-129">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f274-130">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4f274-130">Compiling the Code</span></span>  
  
- <span data-ttu-id="4f274-131">.NET Framework hedefleyen bir projede, öğesine bir başvuru ekleyin `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="4f274-131">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="4f274-132">.NET Core veya .NET 5 ' i hedefleyen bir projede NuGet paketi [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)' yi yükler.</span><span class="sxs-lookup"><span data-stu-id="4f274-132">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="4f274-133">Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="4f274-133">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="4f274-134">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="4f274-134">.NET Security</span></span>

<span data-ttu-id="4f274-135">Bir şifreleme anahtarını düz metin olarak depolamayın veya bir anahtar düz metin olarak makineler arasında aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="4f274-135">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="4f274-136">Bunun yerine, şifreleme anahtarlarını depolamak için güvenli anahtar kapsayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4f274-136">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
<span data-ttu-id="4f274-137">Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemini çağırarak bellekten kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4f274-137">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f274-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f274-138">See also</span></span>

- <span data-ttu-id="4f274-139">[Şifreleme modeli](cryptography-model.md) -şifrelemenin temel sınıf kitaplığında nasıl uygulandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f274-139">[Cryptography Model](cryptography-model.md) - Describes how cryptography is implemented in the base class library.</span></span>
- [<span data-ttu-id="4f274-140">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="4f274-140">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="4f274-141">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="4f274-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="4f274-142">Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="4f274-142">How to: Decrypt XML Elements with Symmetric Keys</span></span>](how-to-decrypt-xml-elements-with-symmetric-keys.md)
- [<span data-ttu-id="4f274-143">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="4f274-143">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

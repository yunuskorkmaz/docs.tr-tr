---
description: 'Daha fazla bilgi edinin: nasıl yapılır: XML öğelerinin şifresini simetrik anahtarlarla çözme'
title: 'Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
ms.openlocfilehash: 894b202143daf2af767fd9877266e2323e0057e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685185"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="9fa3c-103">Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="9fa3c-103">How to: Decrypt XML Elements with Symmetric Keys</span></span>

<span data-ttu-id="9fa3c-104"><xref:System.Security.Cryptography.Xml>BIR XML belgesi içindeki bir öğeyi şifrelemek için ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="9fa3c-105">XML şifrelemesi, gizli XML 'yi kolayca okuyamakta olan veriler hakkında endişelenmenize gerek kalmadan depolamanıza veya taşıetmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-105">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="9fa3c-106">Bu kod örneği, Gelişmiş Şifreleme Standardı (AES) algoritmasını kullanarak bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-106">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm.</span></span>
  
 <span data-ttu-id="9fa3c-107">Bu yordamı kullanarak bir XML öğesinin nasıl şifreleneceği hakkında bilgi için bkz. [nasıl yapılır: XML öğelerini Simetrik Anahtarlarla Şifreleme](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="9fa3c-107">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="9fa3c-108">XML verilerini şifrelemek için AES gibi simetrik bir algoritma kullandığınızda, XML verilerini şifrelemek ve şifrelerini çözmek için aynı anahtarı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-108">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="9fa3c-109">Bu yordamdaki örnek, şifrelenmiş XML 'in aynı anahtar kullanılarak şifrelendiğini ve şifreleme ve şifre çözme tarafların kullanılacak algoritmayı ve anahtarı kabul etmiş olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-109">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="9fa3c-110">Bu örnek, şifreli XML içinde AES anahtarını depolamaz veya şifrelemez.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-110">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="9fa3c-111">Bu örnek, tek bir uygulamanın bellekte depolanan bir oturum anahtarını temel alarak veya bir paroladan türetilmiş şifreli olmayan bir güçlü anahtara göre verileri şifrelemek için gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-111">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="9fa3c-112">İki veya daha fazla uygulamanın şifrelenmiş XML verilerini paylaşması gereken durumlarda, asimetrik algoritmayı veya X. 509.440 sertifikasını temel alan bir şifreleme düzeni kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-112">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="9fa3c-113">XML öğesinin şifresini bir simetrik anahtarla çözmek için</span><span class="sxs-lookup"><span data-stu-id="9fa3c-113">To decrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="9fa3c-114">[Nasıl yapılır: XML öğelerini Simetrik Anahtarlarla Şifreleme](how-to-encrypt-xml-elements-with-symmetric-keys.md)bölümünde açıklanan teknikleri kullanarak, önceden oluşturulan ANAHTARLA bir XML öğesini şifreleyin.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-114">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2. <span data-ttu-id="9fa3c-115">`EncryptedData`ŞIFRELENMIŞ XML içeren bir nesne içinde <> öğesini (XML şifreleme standardı tarafından tanımlanır) bulun <xref:System.Xml.XmlDocument> ve <xref:System.Xml.XmlElement> Bu öğeyi temsil eden yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-115">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. <span data-ttu-id="9fa3c-116"><xref:System.Security.Cryptography.Xml.EncryptedData>Daha önce oluşturulan nesneden ham xml verilerini yükleyerek bir nesne oluşturun <xref:System.Xml.XmlElement> .</span><span class="sxs-lookup"><span data-stu-id="9fa3c-116">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. <span data-ttu-id="9fa3c-117"><xref:System.Security.Cryptography.Xml.EncryptedXml>Şifreleme için kullanılan anahtarı kullanarak XML verilerinin şifresini çözmek için yeni bir nesne oluşturun ve onu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-117">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. <span data-ttu-id="9fa3c-118">Şifrelenmiş öğeyi XML belgesi içindeki yeni şifresi çözülmüş düz metin öğesiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-118">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="9fa3c-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fa3c-119">Example</span></span>  

 <span data-ttu-id="9fa3c-120">Bu örnek, adlı bir dosyanın `"test.xml"` derlenen programla aynı dizinde bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-120">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="9fa3c-121">Ayrıca `"test.xml"` bir öğesi içerdiğini varsayar `"creditcard"` .</span><span class="sxs-lookup"><span data-stu-id="9fa3c-121">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="9fa3c-122">Aşağıdaki XML 'i adlı bir dosyaya yerleştirebilir `test.xml` ve bu örnekle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-122">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="9fa3c-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9fa3c-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="9fa3c-124">.NET Framework hedefleyen bir projede, öğesine bir başvuru ekleyin `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="9fa3c-124">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="9fa3c-125">.NET Core veya .NET 5 ' i hedefleyen bir projede NuGet paketi [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)' yi yükler.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-125">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="9fa3c-126">Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="9fa3c-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="9fa3c-127">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="9fa3c-127">.NET Security</span></span>
  
<span data-ttu-id="9fa3c-128">Bir şifreleme anahtarını düz metin olarak depolamayın veya bir anahtar düz metin olarak makineler arasında aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-128">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
<span data-ttu-id="9fa3c-129">Bir simetrik şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemini çağırarak bellekten kaldırın.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-129">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa3c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fa3c-130">See also</span></span>

- [<span data-ttu-id="9fa3c-131">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="9fa3c-131">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="9fa3c-132">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="9fa3c-132">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="9fa3c-133">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="9fa3c-133">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="9fa3c-134">Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="9fa3c-134">How to: Encrypt XML Elements with Symmetric Keys</span></span>](how-to-encrypt-xml-elements-with-symmetric-keys.md)
- [<span data-ttu-id="9fa3c-135">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="9fa3c-135">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

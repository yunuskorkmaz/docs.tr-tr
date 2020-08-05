---
title: 'Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
ms.openlocfilehash: f60947a3b722f33c88b696d47c6a4000a1cb076b
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555740"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme

<xref:System.Security.Cryptography.Xml>BIR XML belgesi içindeki bir öğeyi şifrelemek ve şifrelerini çözmek için ad alanındaki sınıfları kullanabilirsiniz.  XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.  XML şifreleme standardı hakkında daha fazla bilgi için bkz. konumundaki XML şifrelemesi için World Wide Web Konsorsiyumu (W3C) belirtimi <https://www.w3.org/TR/xmldsig-core/> .  
  
 Bu örnek,: [nasıl yapılır: XML öğelerini X. 509.440 sertifikalarıyla şifreleme](how-to-encrypt-xml-elements-with-x-509-certificates.md)bölümünde açıklanan yöntemler kullanılarak ŞIFRELENMIŞ bir XML öğesinin şifresini çözer.  Bir <`EncryptedData`> öğesi bulur, öğenin şifresini çözer ve sonra öğeyi özgün düz metın XML öğesiyle değiştirir.  
  
Bu yordamdaki kod örneği, geçerli kullanıcı hesabının yerel sertifika deposundan bir X. 509.440 sertifikası kullanarak bir XML öğesinin şifresini çözer.  Örnek, <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> X. 509.952 sertifikasını otomatik olarak almak ve `EncryptedKey` <> öğesinin <> öğesinde depolanan bir oturum anahtarının şifresini çözmek için yöntemini kullanır `EncryptedData` .  <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>Daha sonra yöntemi, XML öğesinin şifresini çözmek için oturum anahtarını otomatik olarak kullanır.  
  
Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, kaç kez şifrelenmiş verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>X.509 sertifikası olan bir XML öğesinin şifresini çözmek için  
  
1. <xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.  <xref:System.Xml.XmlDocument>Nesnesi, şifresinin çözülmesi IÇIN XML öğesini içerir.  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. <xref:System.Security.Cryptography.Xml.EncryptedXml>Nesneyi oluşturucuya geçirerek yeni bir nesne oluşturun <xref:System.Xml.XmlDocument> .  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. Yöntemini kullanarak XML belgesinin şifresini çözün <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> .  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. Nesneyi kaydedin <xref:System.Xml.XmlDocument> .  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a>Örnek

Bu örnek, adlı bir dosyanın `"test.xml"` derlenen programla aynı dizinde bulunduğunu varsayar.  Ayrıca `"test.xml"` bir öğesi içerdiğini varsayar `"creditcard"` .  Aşağıdaki XML 'i adlı bir dosyaya yerleştirebilir `test.xml` ve bu örnekle birlikte kullanabilirsiniz.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
[!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- .NET Framework hedefleyen bir projede, öğesine bir başvuru ekleyin `System.Security.dll` .

- .NET Core veya .NET 5 ' i hedefleyen bir projede NuGet paketi [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)' yi yükler.

- Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-security"></a>.NET güvenliği

Bu örnekte kullanılan X. 509.440 sertifikası yalnızca test amaçlıdır.  Uygulamalar, güvenilir bir sertifika yetkilisi tarafından oluşturulan bir X. 509.440 sertifikası kullanmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Modeli](cryptography-model.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme](how-to-encrypt-xml-elements-with-x-509-certificates.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)

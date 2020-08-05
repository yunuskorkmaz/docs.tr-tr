---
title: 'Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme'
ms.date: 07/14/2020
ms.technology: dotnet-standard
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
ms.openlocfilehash: dd69ec6a5317f7f6f800cd225d920a1934c77a0c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555819"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme

<xref:System.Security.Cryptography.Xml>BIR XML belgesi içindeki bir öğeyi şifrelemek için ad alanındaki sınıfları kullanabilirsiniz.  XML şifrelemesi, gizli XML 'yi kolayca okuyamakta olan veriler hakkında endişelenmenize gerek kalmadan depolamanıza veya taşıetmenize olanak tanır.  Bu yordam, Gelişmiş Şifreleme Standardı (AES) algoritmasını kullanarak bir XML öğesini şifreler.  
  
 Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözme hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerinin şifresini simetrik anahtarlarla çözme](how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 XML verilerini şifrelemek için AES gibi simetrik bir algoritma kullandığınızda, XML verilerini şifrelemek ve şifrelerini çözmek için aynı anahtarı kullanmanız gerekir.  Bu yordamdaki örnek, şifrelenmiş XML 'in aynı anahtar kullanılarak şifresinin çözülemediğini ve şifreleme ve şifre çözme tarafların kullanılacak algoritmayı ve anahtarı kabul etmiş olduğunu varsayar.  Bu örnek, şifreli XML içinde AES anahtarını depolamaz veya şifrelemez.  
  
 Bu örnek, tek bir uygulamanın bellekte depolanan bir oturum anahtarını temel alarak veya bir paroladan türetilmiş şifreli olmayan bir güçlü anahtara göre verileri şifrelemek için gereken durumlar için uygundur.  İki veya daha fazla uygulamanın şifrelenmiş XML verilerini paylaşması gereken durumlarda, asimetrik algoritmayı veya X. 509.440 sertifikasını temel alan bir şifreleme düzeni kullanmayı düşünün.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>XML öğesini bir simetrik anahtarla şifrelemek için  
  
1. Sınıfını kullanarak bir simetrik anahtar oluşturun <xref:System.Security.Cryptography.Aes> .  Bu anahtar, XML öğesini şifrelemek için kullanılacaktır.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.  <xref:System.Xml.XmlDocument>Nesne ŞIFRELENECEK XML öğesini içeriyor.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. Nesnede belirtilen öğeyi bulun <xref:System.Xml.XmlDocument> ve <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden yeni bir nesne oluşturun.  Bu örnekte, `"creditcard"` öğesi şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. Sınıfının yeni bir örneğini oluşturun <xref:System.Security.Cryptography.Xml.EncryptedXml> ve bunu simetrik anahtarla şifrelemek için kullanın <xref:System.Xml.XmlElement> .  Yöntemi, şifreli <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> bir öğe olarak şifrelenmiş bir bayt dizisi döndürür.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. Bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne oluşturun ve bunu XML şifreleme ÖĞESININ URL tanımlayıcısıyla doldurun.  Bu URL tanımlayıcısı, şifre çözme tarafına XML 'in şifreli bir öğe içerdiğini bilmesini sağlar.  <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>URL tanımlayıcısını belirtmek için alanını kullanabilirsiniz.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <xref:System.Security.Cryptography.Xml.EncryptionMethod>Anahtarı oluşturmak için kullanılan şifreleme ALGORITMASıNıN URL tanımlayıcısı için başlatılan bir nesne oluşturun.  <xref:System.Security.Cryptography.Xml.EncryptionMethod>Nesneyi <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliğe geçirin.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. Şifrelenen öğe verilerini <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. Öğeyi özgün <xref:System.Xml.XmlDocument> nesnesinden öğesi ile değiştirin <xref:System.Security.Cryptography.Xml.EncryptedData> .  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a>Örnek  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- .NET Framework hedefleyen bir projede, öğesine bir başvuru ekleyin `System.Security.dll` .

- .NET Core veya .NET 5 ' i hedefleyen bir projede NuGet paketi [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)' yi yükler.
  
- Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-security"></a>.NET güvenliği

Bir şifreleme anahtarını düz metin olarak depolamayın veya bir anahtar düz metin olarak makineler arasında aktarmayın.  Bunun yerine, şifreleme anahtarlarını depolamak için güvenli anahtar kapsayıcısı kullanın.  
  
Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemini çağırarak bellekten kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme modeli](cryptography-model.md) -şifrelemenin temel sınıf kitaplığında nasıl uygulandığını açıklar.
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme](how-to-decrypt-xml-elements-with-symmetric-keys.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)

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
ms.openlocfilehash: b792fd6eea0a33b0143fafa03641a78947d7e127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458064"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme
Bir XML belgesi içindeki bir öğeyi şifrelemek için <xref:System.Security.Cryptography.Xml> ad alanındaki sınıfları kullanabilirsiniz.  XML şifrelemesi, gizli XML 'yi kolayca okuyamakta olan veriler hakkında endişelenmenize gerek kalmadan depolamanıza veya taşıetmenize olanak tanır.  Bu yordam, Rijnbael olarak da bilinen Gelişmiş Şifreleme Standardı (AES) algoritmasını kullanarak bir XML öğesini şifreler.  
  
 Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözme hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerinin şifresini simetrik anahtarlarla çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 XML verilerini şifrelemek için AES gibi simetrik bir algoritma kullandığınızda, XML verilerini şifrelemek ve şifrelerini çözmek için aynı anahtarı kullanmanız gerekir.  Bu yordamdaki örnek, şifrelenmiş XML 'in aynı anahtar kullanılarak şifresinin çözülemediğini ve şifreleme ve şifre çözme tarafların kullanılacak algoritmayı ve anahtarı kabul etmiş olduğunu varsayar.  Bu örnek, şifreli XML içinde AES anahtarını depolamaz veya şifrelemez.  
  
 Bu örnek, tek bir uygulamanın bellekte depolanan bir oturum anahtarını temel alarak veya bir paroladan türetilmiş şifreli olmayan bir güçlü anahtara göre verileri şifrelemek için gereken durumlar için uygundur.  İki veya daha fazla uygulamanın şifrelenmiş XML verilerini paylaşması gereken durumlarda, asimetrik algoritmayı veya X. 509.440 sertifikasını temel alan bir şifreleme düzeni kullanmayı düşünün.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>XML öğesini bir simetrik anahtarla şifrelemek için  
  
1. <xref:System.Security.Cryptography.RijndaelManaged> sınıfını kullanarak bir simetrik anahtar oluşturun.  Bu anahtar, XML öğesini şifrelemek için kullanılacaktır.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. Diskten bir XML dosyası yükleyerek <xref:System.Xml.XmlDocument> nesnesi oluşturun.  <xref:System.Xml.XmlDocument> nesnesi şifrelenecek XML öğesini içeriyor.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <xref:System.Xml.XmlDocument> nesnesinde belirtilen öğeyi bulun ve şifrelemek istediğiniz öğeyi temsil eden yeni bir <xref:System.Xml.XmlElement> nesnesi oluşturun.  Bu örnekte `"creditcard"` öğesi şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfının yeni bir örneğini oluşturun ve bunu simetrik anahtarla <xref:System.Xml.XmlElement> şifrelemek için kullanın.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> yöntemi, şifrelenen bir bayt dizisi olarak şifrelenmiş öğeyi döndürür.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. Bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi oluşturun ve bunu XML şifreleme öğesinin URL tanımlayıcısıyla doldurun.  Bu URL tanımlayıcısı, şifre çözme tarafına XML 'in şifreli bir öğe içerdiğini bilmesini sağlar.  URL tanımlayıcısını belirtmek için <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> alanını kullanabilirsiniz.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. Anahtarı oluşturmak için kullanılan şifreleme algoritmasının URL tanımlayıcısı için başlatılan bir <xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesi oluşturun.  <xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesini <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliğine geçirin.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. Şifrelenmiş öğe verilerini <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. Öğeyi özgün <xref:System.Xml.XmlDocument> nesnesinden <xref:System.Security.Cryptography.Xml.EncryptedData> öğesiyle değiştirin.  
  
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
  
- Bu örneği derlemek için `System.Security.dll`bir başvuru eklemeniz gerekir.  
  
- Şu ad alanlarını ekleyin: <xref:System.Xml>, <xref:System.Security.Cryptography>ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bir şifreleme anahtarını düz metin olarak depolamayın veya bir anahtar düz metin olarak makineler arasında aktarmayın.  Bunun yerine, şifreleme anahtarlarını depolamak için güvenli anahtar kapsayıcısı kullanın.  
  
 Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya yönetilen şifreleme sınıfının <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yöntemini çağırarak bellekten kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)

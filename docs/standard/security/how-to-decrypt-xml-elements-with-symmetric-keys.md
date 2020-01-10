---
title: 'Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme'
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
ms.openlocfilehash: fd377cd470d361f5a46c662ab37780713a2d3804
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706129"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme
Bir XML belgesi içindeki bir öğeyi şifrelemek için <xref:System.Security.Cryptography.Xml> ad alanındaki sınıfları kullanabilirsiniz.  XML şifrelemesi, gizli XML 'yi kolayca okuyamakta olan veriler hakkında endişelenmenize gerek kalmadan depolamanıza veya taşıetmenize olanak tanır.  Bu kod örneği, Rijnbael olarak da bilinen Gelişmiş Şifreleme Standardı (AES) algoritmasını kullanarak bir XML öğesinin şifresini çözer.  
  
 Bu yordamı kullanarak bir XML öğesinin nasıl şifreleneceği hakkında bilgi için bkz. [nasıl yapılır: XML öğelerini Simetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 XML verilerini şifrelemek için AES gibi simetrik bir algoritma kullandığınızda, XML verilerini şifrelemek ve şifrelerini çözmek için aynı anahtarı kullanmanız gerekir.  Bu yordamdaki örnek, şifrelenmiş XML 'in aynı anahtar kullanılarak şifrelendiğini ve şifreleme ve şifre çözme tarafların kullanılacak algoritmayı ve anahtarı kabul etmiş olduğunu varsayar.  Bu örnek, şifreli XML içinde AES anahtarını depolamaz veya şifrelemez.  
  
 Bu örnek, tek bir uygulamanın bellekte depolanan bir oturum anahtarını temel alarak veya bir paroladan türetilmiş şifreli olmayan bir güçlü anahtara göre verileri şifrelemek için gereken durumlar için uygundur.  İki veya daha fazla uygulamanın şifrelenmiş XML verilerini paylaşması gereken durumlarda, asimetrik algoritmayı veya X. 509.440 sertifikasını temel alan bir şifreleme düzeni kullanmayı düşünün.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>XML öğesinin şifresini bir simetrik anahtarla çözmek için  
  
1. [Nasıl yapılır: XML öğelerini Simetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)bölümünde açıklanan teknikleri kullanarak, önceden oluşturulan ANAHTARLA bir XML öğesini şifreleyin.  
  
2. Şifrelenmiş XML içeren bir <xref:System.Xml.XmlDocument> nesnesindeki <`EncryptedData`> öğesini (XML şifreleme standardı tarafından tanımlanır) bulun ve bu öğeyi temsil eden yeni bir <xref:System.Xml.XmlElement> nesnesi oluşturun.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. Daha önce oluşturulan <xref:System.Xml.XmlElement> nesnesinden ham XML verilerini yükleyerek bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi oluşturun.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> nesnesi oluşturun ve şifreleme için kullanılan anahtarı kullanarak XML verilerinin şifresini çözmek için kullanın.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. Şifrelenmiş öğeyi XML belgesi içindeki yeni şifresi çözülmüş düz metin öğesiyle değiştirin.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, `"test.xml"` adlı bir dosyanın derlenen programla aynı dizinde olduğunu varsayar.  Ayrıca, `"test.xml"` bir `"creditcard"` öğesi içerdiğini varsayar.  Aşağıdaki XML 'i `test.xml` adlı bir dosyaya yerleştirebilir ve bu örnekle birlikte kullanabilirsiniz.  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- Bu örneği derlemek için `System.Security.dll`bir başvuru eklemeniz gerekir.  
  
- Şu ad alanlarını ekleyin: <xref:System.Xml>, <xref:System.Security.Cryptography>ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bir şifreleme anahtarını düz metin olarak depolamayın veya bir anahtar düz metin olarak makineler arasında aktarmayın.  
  
 Bir simetrik şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya yönetilen şifreleme sınıfının <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yöntemini çağırarak bellekten kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)

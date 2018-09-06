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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38bb22de14ecef618d45f54cced32af57542d3df
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866851"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme
Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi bir öğesinde şifrelemek için ad alanı.  XML şifreleme depolamak veya hassas XML kolay okunan verilerin hakkında endişelenmeden taşıma sağlar.  Bu kod örneği, Gelişmiş Şifreleme Standardı (AES) olarak da bilinen Rijndael algoritmasını kullanarak bir XML öğesinin şifresini çözer.  
  
 Bu yordamı kullanarak bir XML öğesi şifreleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 XML verileri şifrelemek için Simetrik algoritma AES gibi kullandığınızda, aynı anahtar şifreleme ve şifre çözme XML verileri için kullanmanız gerekir.  Bu yordamdaki örnek olduğunu varsayar aynı anahtar kullanılarak şifrelenmiş XML şifrelenmiş ve şifreleme ve taraflar şifre çözme algoritması ve anahtar kullanmayı kabul etmiş olursunuz.  Bu örnekte depolamak veya şifrelenmiş XML içinde AES anahtarını şifrelemek desteklemez.  
  
 Bu örnek, tek bir uygulama bellekte veya bir parolasından türetilen şifreleme açısından güçlü bir anahtara göre bir oturum anahtarı temel alan verileri şifrelemek için gereken yere durumlar için uygundur.  İki veya daha fazla uygulama şifrelenmiş XML veri paylaşımı için gereken yere durumlarda, asimetrik algoritma veya bir X.509 sertifikası tabanlı bir şifreleme şeması kullanılarak göz önünde bulundurun.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>XML öğesinin şifresini bir simetrik anahtarla çözmek için  
  
1.  Bir XML öğesi içinde açıklanan teknikleri kullanarak daha önce oluşturulmuş anahtarla şifrelemek [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2.  Bulma <`EncryptedData`> (XML şifreleme standardı tarafından tanımlanan) öğesinde bir <xref:System.Xml.XmlDocument> şifrelenmiş XML içeren nesne ve yeni bir <xref:System.Xml.XmlElement> o öğenin temsil eden nesne.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptedData> ham XML verileri daha önce oluşturulan yüklerken nesne <xref:System.Xml.XmlElement> nesne.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> nesne ve şifreleme için kullanılan aynı anahtarı kullanarak XML verileri şifrelemek için kullanabilirsiniz.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  XML belgesi içindeki yeni şifresi düz metin öğesi ile şifrelenmiş öğeyi değiştirin.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir dosya olduğunu varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.  Ayrıca varsayılmaktadır `"test.xml"` içeren bir `"creditcard"` öğesi.  Aşağıdaki XML adlı bir dosyaya yerleştirebilirsiniz `test.xml` ve bu örneği kullanın.  
  
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
  
-   Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.  
  
-   Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Hiçbir zaman düz metin olarak bir şifreleme anahtarı depolamak veya düz metin makineler arasında bir anahtar aktarımı.  
  
 İşiniz bittiğinde bir simetrik şifreleme anahtarını kullanarak temizleyin, bellekten her byte sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>  
- [Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)

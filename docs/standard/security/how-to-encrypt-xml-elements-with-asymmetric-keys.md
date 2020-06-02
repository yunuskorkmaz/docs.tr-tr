---
title: 'Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
ms.openlocfilehash: 475446f6206676e93ea72d16e01bcf1067c24e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277381"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme
<xref:System.Security.Cryptography.Xml>BIR XML belgesi içindeki bir öğeyi şifrelemek için ad alanındaki sınıfları kullanabilirsiniz.  XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.  XML şifreleme standardı hakkında daha fazla bilgi için bkz. konumundaki XML şifrelemesi için World Wide Web Konsorsiyumu (W3C) belirtimi <https://www.w3.org/TR/xmldsig-core/> .  
  
 XML şifrelemesini, `EncryptedData` ŞIFRELENMIŞ XML verilerini içeren bir <> öğesiyle herhangi BIR XML öğesini veya belgeyi değiştirmek için kullanabilirsiniz.  <`EncryptedData`> öğesi, şifreleme sırasında kullanılan anahtarlar ve süreçler hakkında bilgiler içeren alt öğeleri de içerebilir.  XML şifrelemesi, bir belgenin birden çok şifrelenmiş öğe içermesini sağlar ve bir öğenin birden çok kez şifrelenmesini sağlar.  Bu yordamdaki kod örneği, `EncryptedData` daha sonra şifre çözme sırasında kullanabileceğiniz diğer birkaç alt öğe ile birlikte bir <> öğesinin nasıl oluşturulacağını gösterir.  
  
 Bu örnek, iki anahtar kullanarak bir XML öğesini şifreler.  Bir RSA ortak/özel anahtar çifti oluşturur ve anahtar çiftini güvenli anahtar kapsayıcısına kaydeder.  Örnek daha sonra, Rijnbael algoritması olarak da bilinen Gelişmiş Şifreleme Standardı (AES) algoritmasını kullanarak ayrı bir oturum anahtarı oluşturur.  Örnek, XML belgesini şifrelemek için AES oturum anahtarını kullanır ve ardından AES oturum anahtarını şifrelemek için RSA ortak anahtarını kullanır.  Son olarak, örnek, şifreli AES oturum anahtarını ve şifrelenmiş XML verilerini yeni bir <> öğesi içindeki XML belgesine kaydeder `EncryptedData` .  
  
 XML öğesinin şifresini çözmek için, anahtar kapsayıcısından RSA özel anahtarını alır, oturum anahtarının şifresini çözmek için onu kullanın ve ardından belgenin şifresini çözmek için oturum anahtarını kullanın.  Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözme hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerinin şifresini Asimetrik Anahtarlarla çözme](how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, kaç kez şifrelenmiş verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>Asimetrik anahtarla bir XML öğesini şifrelemek için  
  
1. Bir <xref:System.Security.Cryptography.CspParameters> nesne oluşturun ve anahtar kapsayıcısının adını belirtin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Sınıfını kullanarak bir simetrik anahtar oluşturun <xref:System.Security.Cryptography.RSACryptoServiceProvider> .  Anahtar, nesneyi sınıfının oluşturucusuna geçirdiğinizde anahtar kapsayıcıya otomatik olarak kaydedilir <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> .  Bu anahtar, AES oturum anahtarını şifrelemek için kullanılacaktır ve daha sonra bu dosyanın şifresini çözmek için elde edilebilir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.  <xref:System.Xml.XmlDocument>Nesne ŞIFRELENECEK XML öğesini içeriyor.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. Nesnede belirtilen öğeyi bulun <xref:System.Xml.XmlDocument> ve <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden yeni bir nesne oluşturun. Bu örnekte, `"creditcard"` öğesi şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. Sınıfını kullanarak yeni bir oturum anahtarı oluşturun <xref:System.Security.Cryptography.RijndaelManaged> .  Bu anahtar, XML öğesini şifreler ve sonra, bir XML belgesine yerleştirilir ve bu öğe şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. Sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.Xml.EncryptedXml> ve oturum anahtarını kullanarak belirtilen öğeyi şifrelemek için kullanın.  Yöntemi, şifreli <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> bir öğe olarak şifrelenmiş bir bayt dizisi döndürür.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. Bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne oluşturun ve ŞIFRELENMIŞ XML ÖĞESININ URL tanımlayıcısıyla doldurun.  Bu URL tanımlayıcısı, şifre çözme tarafına XML 'in şifreli bir öğe içerdiğini bilmesini sağlar.  <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>URL tanımlayıcısını belirtmek için alanını kullanabilirsiniz.  Düz metin XML öğesi, `EncryptedData` Bu nesne tarafından kapsüllenmiş bir <> öğesi ile değiştirilmeyecektir <xref:System.Security.Cryptography.Xml.EncryptedData> .  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. <xref:System.Security.Cryptography.Xml.EncryptionMethod>Oturum anahtarını oluşturmak için kullanılan şifreleme ALGORITMASıNıN URL tanımlayıcısı için başlatılan bir nesne oluşturun.  <xref:System.Security.Cryptography.Xml.EncryptionMethod>Nesneyi <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliğe geçirin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <xref:System.Security.Cryptography.Xml.EncryptedKey>Şifrelenmiş oturum anahtarını içerecek bir nesne oluşturun.  Oturum anahtarını şifreleyin, <xref:System.Security.Cryptography.Xml.EncryptedKey> nesnesine ekleyin ve oturum anahtarı adı ile anahtar tanımlayıcı URL 'si girin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <xref:System.Security.Cryptography.Xml.DataReference>Şifrelenmiş verileri belirli bir oturum anahtarıyla eşleyen yeni bir nesne oluşturun.  Bu isteğe bağlı adım, bir XML belgesinin birden çok bölümünün tek bir anahtarla şifrelendiğini kolayca belirtmenizi sağlar.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Şifrelenen anahtarı <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <xref:System.Security.Cryptography.Xml.KeyInfo>RSA anahtarının adını belirtmek için yeni bir nesne oluşturun.  <xref:System.Security.Cryptography.Xml.EncryptedData>Nesnesine ekleyin. Bu, şifre çözme tarafına, oturum anahtarının şifresini çözerken kullanılacak doğru asimetrik anahtarı belirlemesine yardımcı olur.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Şifrelenen öğe verilerini <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Öğeyi özgün <xref:System.Xml.XmlDocument> nesnesinden öğesi ile değiştirin <xref:System.Security.Cryptography.Xml.EncryptedData> .  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Nesneyi kaydedin <xref:System.Xml.XmlDocument> .  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bu örneği derlemek için, öğesine bir başvuru eklemeniz gerekir `System.Security.dll` .  
  
- Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Simetrik bir şifreleme anahtarını düz metin olarak depolamayın veya bir simetrik anahtarı makineler arasında düz metin olarak aktarmayın.  Bunlara ek olarak, asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.  Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](generating-keys-for-encryption-and-decryption.md).  
  
 Doğrudan kaynak kodunuza bir anahtar gömmeyin.  Gömülü anahtarlar [ıldadsm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.  
  
 Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemini çağırarak bellekten kaldırın.  Şifreleme anahtarları bazen bir hata ayıklayıcı tarafından bellekten okunabilir veya bellek konumu diske disk belleğine alınmış ise sabit sürücüden okuyabilirler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme](how-to-decrypt-xml-elements-with-asymmetric-keys.md)

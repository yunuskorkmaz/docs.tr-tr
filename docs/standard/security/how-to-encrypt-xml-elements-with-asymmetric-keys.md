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
ms.openlocfilehash: 2ebf3f86ac550c0179b2e26879a7df128fd529e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706103"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme
Bir XML belgesi içindeki bir öğeyi şifrelemek için <xref:System.Security.Cryptography.Xml> ad alanındaki sınıfları kullanabilirsiniz.  XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.  XML şifreleme standardı hakkında daha fazla bilgi için, <https://www.w3.org/TR/xmldsig-core/>konumundaki XML şifrelemesi için World Wide Web Konsorsiyumu (W3C) belirtimine bakın.  
  
 XML şifrelemesini, şifrelenmiş XML verilerini içeren bir <`EncryptedData`> öğesiyle herhangi bir XML öğesini veya belgeyi değiştirmek için kullanabilirsiniz.  <`EncryptedData`> öğesi, şifreleme sırasında kullanılan anahtarlar ve süreçler hakkında bilgi içeren alt öğeleri de içerebilir.  XML şifrelemesi, bir belgenin birden çok şifrelenmiş öğe içermesini sağlar ve bir öğenin birden çok kez şifrelenmesini sağlar.  Bu yordamdaki kod örneği, daha sonra şifre çözme sırasında kullanabileceğiniz birkaç diğer alt öğe ile birlikte <`EncryptedData`> öğesinin nasıl oluşturulacağını gösterir.  
  
 Bu örnek, iki anahtar kullanarak bir XML öğesini şifreler.  Bir RSA ortak/özel anahtar çifti oluşturur ve anahtar çiftini güvenli anahtar kapsayıcısına kaydeder.  Örnek daha sonra, Rijnbael algoritması olarak da bilinen Gelişmiş Şifreleme Standardı (AES) algoritmasını kullanarak ayrı bir oturum anahtarı oluşturur.  Örnek, XML belgesini şifrelemek için AES oturum anahtarını kullanır ve ardından AES oturum anahtarını şifrelemek için RSA ortak anahtarını kullanır.  Son olarak, örnek, şifreli AES oturum anahtarını ve şifrelenmiş XML verilerini yeni bir <`EncryptedData`> öğesi içindeki XML belgesine kaydeder.  
  
 XML öğesinin şifresini çözmek için, anahtar kapsayıcısından RSA özel anahtarını alır, oturum anahtarının şifresini çözmek için onu kullanın ve ardından belgenin şifresini çözmek için oturum anahtarını kullanın.  Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözme hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerinin şifresini Asimetrik Anahtarlarla çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, kaç kez şifrelenmiş verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>Asimetrik anahtarla bir XML öğesini şifrelemek için  
  
1. <xref:System.Security.Cryptography.CspParameters> nesnesi oluşturun ve anahtar kapsayıcısının adını belirtin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfını kullanarak bir simetrik anahtar oluşturun.  <xref:System.Security.Cryptography.CspParameters> nesnesini <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfının oluşturucusuna geçirdiğinizde anahtar otomatik olarak anahtar kapsayıcısına kaydedilir.  Bu anahtar, AES oturum anahtarını şifrelemek için kullanılacaktır ve daha sonra bu dosyanın şifresini çözmek için elde edilebilir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Diskten bir XML dosyası yükleyerek <xref:System.Xml.XmlDocument> nesnesi oluşturun.  <xref:System.Xml.XmlDocument> nesnesi şifrelenecek XML öğesini içeriyor.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. <xref:System.Xml.XmlDocument> nesnesinde belirtilen öğeyi bulun ve şifrelemek istediğiniz öğeyi temsil eden yeni bir <xref:System.Xml.XmlElement> nesnesi oluşturun. Bu örnekte `"creditcard"` öğesi şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. <xref:System.Security.Cryptography.RijndaelManaged> sınıfını kullanarak yeni bir oturum anahtarı oluşturun.  Bu anahtar, XML öğesini şifreler ve sonra, bir XML belgesine yerleştirilir ve bu öğe şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfının yeni bir örneğini oluşturun ve oturum anahtarını kullanarak belirtilen öğeyi şifrelemek için kullanın.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> yöntemi, şifrelenen bir bayt dizisi olarak şifrelenmiş öğeyi döndürür.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi oluşturun ve şifrelenmiş XML öğesinin URL tanımlayıcısıyla doldurun.  Bu URL tanımlayıcısı, şifre çözme tarafına XML 'in şifreli bir öğe içerdiğini bilmesini sağlar.  URL tanımlayıcısını belirtmek için <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> alanını kullanabilirsiniz.  Düz metin XML öğesi, bu <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi tarafından kapsüllenmiş bir <`EncryptedData`> öğesi ile değiştirilmeyecektir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. Oturum anahtarını oluşturmak için kullanılan şifreleme algoritmasının URL tanımlayıcısı için başlatılan bir <xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesi oluşturun.  <xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesini <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliğine geçirin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Şifrelenmiş oturum anahtarını içerecek bir <xref:System.Security.Cryptography.Xml.EncryptedKey> nesnesi oluşturun.  Oturum anahtarını şifreleyin, <xref:System.Security.Cryptography.Xml.EncryptedKey> nesnesine ekleyin ve oturum anahtarı adı ile anahtar tanımlayıcı URL 'SI girin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Şifrelenmiş verileri belirli bir oturum anahtarıyla eşleyen yeni bir <xref:System.Security.Cryptography.Xml.DataReference> nesnesi oluşturun.  Bu isteğe bağlı adım, bir XML belgesinin birden çok bölümünün tek bir anahtarla şifrelendiğini kolayca belirtmenizi sağlar.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Şifrelenmiş anahtarı <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. RSA anahtarının adını belirtmek için yeni bir <xref:System.Security.Cryptography.Xml.KeyInfo> nesnesi oluşturun.  <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin. Bu, şifre çözme tarafına, oturum anahtarının şifresini çözerken kullanılacak doğru asimetrik anahtarı belirlemesine yardımcı olur.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Şifrelenmiş öğe verilerini <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesine ekleyin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Öğeyi özgün <xref:System.Xml.XmlDocument> nesnesinden <xref:System.Security.Cryptography.Xml.EncryptedData> öğesiyle değiştirin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <xref:System.Xml.XmlDocument> nesnesini kaydedin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- Bu örneği derlemek için `System.Security.dll`bir başvuru eklemeniz gerekir.  
  
- Şu ad alanlarını ekleyin: <xref:System.Xml>, <xref:System.Security.Cryptography>ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Simetrik bir şifreleme anahtarını düz metin olarak depolamayın veya bir simetrik anahtarı makineler arasında düz metin olarak aktarmayın.  Bunlara ek olarak, asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.  Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Doğrudan kaynak kodunuza bir anahtar gömmeyin.  Gömülü anahtarlar [ıldadsm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.  
  
 Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya yönetilen şifreleme sınıfının <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yöntemini çağırarak bellekten kaldırın.  Şifreleme anahtarları bazen bir hata ayıklayıcı tarafından bellekten okunabilir veya bellek konumu diske disk belleğine alınmış ise sabit sürücüden okuyabilirler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)

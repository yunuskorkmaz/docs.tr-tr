---
title: 'Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: 5ed1e2eb2518366da0a57655d7a8691e23f725d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706142"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme
Bir XML belgesi içindeki bir öğeyi şifrelemek ve şifrelerini çözmek için <xref:System.Security.Cryptography.Xml> ad alanındaki sınıfları kullanabilirsiniz.  XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.  XML şifreleme standardı hakkında daha fazla bilgi için bkz. World Wide Web Konsorsiyumu (W3C) önerisi [XML Imzası sözdizimi ve işleme](https://www.w3.org/TR/xmldsig-core/).  
  
 Bu yordamdaki örnek, [nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)bölümünde açıklanan yöntemler kullanılarak ŞIFRELENMIŞ bir XML öğesinin şifresini çözer.  Bir <`EncryptedData`> öğesi bulur, öğenin şifresini çözer ve sonra öğeyi özgün düz metin XML öğesiyle değiştirir.  
  
 Bu örnek, iki anahtar kullanarak bir XML öğesinin şifresini çözer.  Daha önce oluşturulmuş bir RSA özel anahtarını anahtar kapsayıcısından alır ve ardından RSA anahtarını, <`EncryptedData`> öğesinin <`EncryptedKey`> öğesinde depolanan bir oturum anahtarının şifresini çözmek için kullanır.  Daha sonra örnek, XML öğesinin şifresini çözmek için oturum anahtarını kullanır.  
  
 Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, şifrelenen verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Asimetrik anahtarla bir XML öğesinin şifresini çözmek için  
  
1. <xref:System.Security.Cryptography.CspParameters> nesnesi oluşturun ve anahtar kapsayıcısının adını belirtin.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesini kullanarak kapsayıcıdan daha önce üretilmiş bir asimetrik anahtar alın.  <xref:System.Security.Cryptography.CspParameters> nesnesini <xref:System.Security.Cryptography.RSACryptoServiceProvider> oluşturucusuna geçirdiğinizde anahtar kapsayıcısından anahtar otomatik olarak alınır.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Belgenin şifresini çözmek için yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> nesnesi oluşturun.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. RSA anahtarını, şifresi çözülmesi gereken belge içindeki öğeyle ilişkilendirmek için bir anahtar/ad eşlemesi ekleyin.  Belgeyi şifrelediyseniz kullandığınız anahtar için aynı adı kullanmanız gerekir.  Bu adın, 1. adımda belirtilen anahtar kapsayıcısında anahtarı tanımlamak için kullanılan adından ayrı olduğunu unutmayın.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. `EncryptedData`> öğesinin şifresini çözmek için <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> yöntemi çağırın.  Bu yöntem, oturum anahtarının şifresini çözmek için RSA anahtarını kullanır ve XML öğesinin şifresini çözmek için oturum anahtarını otomatik olarak kullanır.  Ayrıca, <`EncryptedData`> öğesini özgün düz metin ile otomatik olarak değiştirir.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. XML belgesini kaydedin.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, `test.xml` adlı bir dosyanın derlenen programla aynı dizinde olduğunu varsayar.  Ayrıca, `test.xml` [nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)bölümünde açıklanan teknikler kullanılarak ŞIFRELENMIŞ bir XML öğesi içerdiğini varsayar.  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- Bu örneği derlemek için `System.Security.dll`bir başvuru eklemeniz gerekir.  
  
- Şu ad alanlarını ekleyin: <xref:System.Xml>, <xref:System.Security.Cryptography>ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Simetrik bir şifreleme anahtarını düz metin olarak depolamayın veya bir simetrik anahtarı makineler arasında düz metin olarak aktarmayın.  Bunlara ek olarak, asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.  Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Doğrudan kaynak kodunuza bir anahtar gömmeyin.  Gömülü anahtarlar [ıldadsm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.  
  
 Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya yönetilen şifreleme sınıfının <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yöntemini çağırarak bellekten kaldırın.  Şifreleme anahtarları bazen bir hata ayıklayıcı tarafından bellekten okunabilir veya bellek konumu diske disk belleğine alınmış ise sabit sürücüden okuyabilirler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)

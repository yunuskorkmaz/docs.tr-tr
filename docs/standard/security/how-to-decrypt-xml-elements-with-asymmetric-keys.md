---
title: 'Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSA class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: 4a06628ddde0920133bfd74568786fbca6d5cf09
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556780"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme

<xref:System.Security.Cryptography.Xml>BIR XML belgesi içindeki bir öğeyi şifrelemek ve şifrelerini çözmek için ad alanındaki sınıfları kullanabilirsiniz.  XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.  XML şifreleme standardı hakkında daha fazla bilgi için bkz. World Wide Web Konsorsiyumu (W3C) önerisi [XML Imzası sözdizimi ve işleme](https://www.w3.org/TR/xmldsig-core/).  

> [!NOTE]
> Bu makaledeki kod Windows için geçerlidir.

Bu yordamdaki örnek, [nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](how-to-encrypt-xml-elements-with-asymmetric-keys.md)bölümünde açıklanan yöntemler kullanılarak ŞIFRELENMIŞ bir XML öğesinin şifresini çözer.  Bir <`EncryptedData`> öğesi bulur, öğenin şifresini çözer ve sonra öğeyi özgün düz metın XML öğesiyle değiştirir.  
  
Bu örnek, iki anahtar kullanarak bir XML öğesinin şifresini çözer.  Daha önce oluşturulmuş bir RSA özel anahtarını anahtar kapsayıcısından alır ve ardından RSA anahtarını kullanarak `EncryptedKey` <> öğesinin <> öğesinde depolanan bir oturum anahtarının şifresini çözer `EncryptedData` .  Daha sonra örnek, XML öğesinin şifresini çözmek için oturum anahtarını kullanır.  
  
Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, şifrelenen verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Asimetrik anahtarla bir XML öğesinin şifresini çözmek için  
  
1. Bir <xref:System.Security.Cryptography.CspParameters> nesne oluşturun ve anahtar kapsayıcısının adını belirtin.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Nesneyi kullanarak kapsayıcıdan daha önce oluşturulmuş bir asimetrik anahtar alın <xref:System.Security.Cryptography.RSACryptoServiceProvider> .  Bu anahtar, nesneyi oluşturucuya geçirdiğinizde anahtar kapsayıcısından otomatik olarak alınır <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> .  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <xref:System.Security.Cryptography.Xml.EncryptedXml>Belgenin şifresini çözmek için yeni bir nesne oluşturun.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. RSA anahtarını, şifresi çözülmesi gereken belge içindeki öğeyle ilişkilendirmek için bir anahtar/ad eşlemesi ekleyin.  Belgeyi şifrelediyseniz kullandığınız anahtar için aynı adı kullanmanız gerekir.  Bu adın, 1. adımda belirtilen anahtar kapsayıcısında anahtarı tanımlamak için kullanılan adından ayrı olduğunu unutmayın.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A><> öğesinin şifresini çözmek için yöntemini çağırın `EncryptedData` .  Bu yöntem, oturum anahtarının şifresini çözmek için RSA anahtarını kullanır ve XML öğesinin şifresini çözmek için oturum anahtarını otomatik olarak kullanır.  Ayrıca, <`EncryptedData`> öğesini özgün düz metin ile otomatik olarak değiştirir.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. XML belgesini kaydedin.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Örnek

Bu örnek, adlı bir dosyanın `test.xml` derlenen programla aynı dizinde bulunduğunu varsayar.  Ayrıca, `test.xml` [nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](how-to-encrypt-xml-elements-with-asymmetric-keys.md)bölümünde açıklanan teknikler KULLANıLARAK şifrelenmiş bir XML öğesi içerdiğini varsayar.  
  
[!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- .NET Framework hedefleyen bir projede, öğesine bir başvuru ekleyin `System.Security.dll` .

- .NET Core veya .NET 5 ' i hedefleyen bir projede NuGet paketi [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)' yi yükler.
  
- Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-security"></a>.NET güvenliği  

Simetrik bir şifreleme anahtarını düz metin olarak depolamayın veya bir simetrik anahtarı makineler arasında düz metin olarak aktarmayın.  Bunlara ek olarak, asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.  Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](generating-keys-for-encryption-and-decryption.md).  
  
 Doğrudan kaynak kodunuza bir anahtar gömmeyin.  Katıştırılmış anahtarlar [Ildasm.exe (Il ayrıştırma)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.  
  
 Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemini çağırarak bellekten kaldırın.  Şifreleme anahtarları bazen bir hata ayıklayıcı tarafından bellekten okunabilir veya bellek konumu diske disk belleğine alınmış ise sabit sürücüden okuyabilirler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Modeli](cryptography-model.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](how-to-encrypt-xml-elements-with-asymmetric-keys.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)

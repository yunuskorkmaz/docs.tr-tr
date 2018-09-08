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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96bee90c7cb3847f9c7059e1a0b1d737209b924f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186012"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme
Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> şifreleme ve şifre çözme bir XML belgesi içindeki bir öğe için ad alanı.  XML şifreleme, exchange veya bir kolayca okunan verilerin hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.  XML şifreleme standardı hakkında daha fazla bilgi için bkz. World Wide Web Consortium (W3C) öneri [XML imza söz dizimi ve işleme](https://www.w3.org/TR/xmldsig-core/).  
  
 Bu yordamdaki örnek da açıklanmış yöntemleri kullanılarak şifrelenmiş bir XML öğesi şifresini çözer [nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Bulduğu bir <`EncryptedData`> öğesi, öğenin şifresini çözer ve daha sonra öğenin özgün düz metin XML öğesi ile değiştirir.  
  
 Bu örnekte, iki anahtar kullanarak bir XML öğesinin şifresini çözer.  Daha önce oluşturulan bir RSA özel anahtarı bir anahtar kapsayıcısından alır ve ardından bir oturum anahtarı şifresini çözmek için RSA anahtarı içinde depolanan kullanır <`EncryptedKey`> öğesi <`EncryptedData`> öğesi.  Örnek, XML öğesinin şifresini çözmek için daha sonra oturum anahtarı kullanır.  
  
 Bu örnek, birden çok uygulama şifrelenmiş veri paylaşımı sahip olduğu veya bir uygulamanın çalıştığı zamanları arasında şifrelenmiş verileri kaydetmek sahip olduğu durumlar için uygundur.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Asimetrik anahtar ile bir XML öğesinin şifresini çözmek için  
  
1.  Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve anahtar kapsayıcısı adını belirtin.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Daha önce oluşturulan bir asimetrik anahtar kullanarak kapsayıcıdaki almak <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesne.  Anahtar, başarılı olduğunda otomatik olarak anahtar kapsayıcısından alındığı <xref:System.Security.Cryptography.CspParameters> nesnesini <xref:System.Security.Cryptography.RSACryptoServiceProvider> Oluşturucusu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> belgenin şifresini çözmek için nesne.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  Öğe çözülmeli belge içinde RSA anahtarı ilişkilendirmek için bir anahtar/ad eşlemesi ekleyin.  Belge şifreli kullandığınız anahtarı için aynı adı kullanmanız gerekir.  Bu ad, 1. adımda belirtilen anahtar kapsayıcısında anahtarını tanımlamak üzere kullanılan ad ayrıdır unutmayın.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  Çağrı <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> şifresini çözmek için gereken yöntemini <`EncryptedData`> öğesi.  Bu yöntem, oturum anahtarının şifresini çözmek için RSA anahtarını kullanır ve otomatik olarak XML öğesinin şifresini çözmek için oturum anahtarını kullanır.  Ayrıca otomatik olarak değiştirir <`EncryptedData`> öğesi ile özgün düz metin.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  XML belgesi kaydedin.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir dosya olduğunu varsayar `test.xml` derlenmiş programın aynı dizinde bulunmaktadır.  Ayrıca varsayılmaktadır `test.xml` açıklanan teknikleri kullanılarak şifrelenmiş bir XML öğesi içeren [nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.  
  
-   Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Hiçbir zaman düz metin olarak bir simetrik şifreleme anahtarı depolamak veya makine düz metin arasında bir simetrik anahtar aktarın.  Buna ek olarak, hiçbir zaman depolayabilen veya asimetrik anahtar çifti düz metin olarak özel anahtarı.  Simetrik hem de asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Hiçbir zaman doğrudan sizin kaynak kodunuza bir anahtar ekleyin.  Katıştırılmış anahtarları kolayca okunabilir bir derlemeden kullanarak [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.  
  
 İşiniz bittiğinde bir şifreleme anahtarı kullanarak temizleyin, bellekten her byte sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.  Şifreleme anahtarlarını bazen bellekten bir hata ayıklayıcı tarafından okunabilir veya disk belleğine alınan bellek konumunda bir sabit diskten okunur diske.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>  
- [Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)

---
title: "Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 698a542765cf8599a2f07e747669893502b75045
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme
Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> şifrelemek ve şifresini çözmek bir XML belgesi içindeki bir öğe için ad alanı.  XML şifrelemesi, exchange veya kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.  World Wide Web Konsorsiyumu (W3C) öneri XML şifreleme standardı hakkında daha fazla bilgi için bkz: [XML imza sözdizimi ve işleme](https://www.w3.org/TR/xmldsig-core/).  
  
 Bu yordamı örnekte açıklanan yöntemleri kullanılarak şifrelenmiş bir XML öğesi şifresini çözer [nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Bulduğu bir <`EncryptedData`> öğesi, öğenin şifresini çözer ve özgün düz metin XML öğesi ile öğenin yerini alır.  
  
 Bu örnek iki anahtarlar kullanılarak bir XML öğesi şifresini çözer.  Bir anahtar kapsayıcı önceden oluşturulan bir RSA özel anahtarı alır ve ardından kullanan bir oturum anahtarı şifresini çözmek için RSA anahtarı depolanan <`EncryptedKey`> öğesi <`EncryptedData`> öğesi.  Örnek sonra XML öğesi şifresini çözmek için oturum anahtarı kullanır.  
  
 Bu örnek, şifrelenmiş veriler paylaşmak birden çok uygulamalara sahip olduğu ya da uygulamanın çalıştığı zamanları arasında şifrelenmiş verileri kaydetmek sahip olduğu durumlar için uygundur.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Bir XML öğesi bir asimetrik anahtar şifresini çözmek için  
  
1.  Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve anahtar kapsayıcı adını belirtin.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Kapsayıcı kullanmaktan daha önce oluşturulan bir asimetrik anahtar almak <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesi.  Geçirdiğiniz anahtarı otomatik olarak anahtar kapsayıcıdan alınır <xref:System.Security.Cryptography.CspParameters> nesnesine <xref:System.Security.Cryptography.RSACryptoServiceProvider> Oluşturucusu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> belgenin şifresini çözmek için nesne.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  RSA anahtar şifresi belge içindeki öğe ilişkilendirmek için bir anahtar/ad eşlemesi ekleyin.  Bu belge şifreli olduğunda, kullanılan anahtar için aynı adı kullanmanız gerekir.  Bu ad 1. adımda belirtilen anahtar kapsayıcısı anahtarında tanımlamak için kullanılan ad ayrı olduğuna dikkat edin.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  Çağrı <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> şifresini çözmek için yöntemi <`EncryptedData`> öğesi.  Bu yöntem, oturum anahtarının şifresini çözmek için RSA anahtarı kullanan ve otomatik olarak XML öğesi şifresini çözmek için oturum anahtarını kullanır.  Ayrıca otomatik olarak değiştirir <`EncryptedData`> öğesi özgün düz metin ile.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  XML belgesi kaydedin.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dosya adlı varsayar `test.xml` derlenmiş programın aynı dizinde bulunmaktadır.  Ayrıca varsayılmaktadır `test.xml` açıklanan teknikleri kullanılarak şifrelenmiş bir XML öğesi içeren [nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.  
  
-   Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Düz metin olarak hiçbir zaman bir simetrik şifreleme anahtarı depolamak veya düz metin olarak makineler arasında bir simetrik anahtar aktarın.  Buna ek olarak, hiçbir zaman depolamak veya asimetrik anahtar çifti düz metin olarak özel anahtarı aktarın.  Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz: [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Hiç kaynak kodunuza doğrudan bir anahtar ekleyin.  Katıştırılmış anahtarları kolay okunabilir bir derlemeye ait kullanarak [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.  
  
 İşiniz bittiğinde şifreleme anahtarını kullanarak temizleyin, bellekten her bayt sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.  Şifreleme anahtarları bazen bellekten bir hata ayıklayıcı tarafından okunabilir veya bellek konumuna disk belleği, bir sabit diskten okuma diske.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Cryptography.Xml>  
 [Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)

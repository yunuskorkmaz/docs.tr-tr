---
title: "Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme"
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
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ac84956e8b80dbc91fa59af3ae0f33d18112a9a2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme
Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi içindeki bir öğe şifrelemek için ad alanı.  XML şifrelemesi, saklamak veya hassas XML kolayca okunan veriler hakkında endişelenmeden aktarım olanak sağlar.  Bu kod örneği olarak da bilinen Rijndael Gelişmiş Şifreleme Standardı (AES) algoritması kullanılarak bir XML öğesi şifresini çözer.  
  
 Bu yordamı kullanarak bir XML öğesi şifreleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 XML verileri şifrelemek için simetrik algoritması AES gibi kullandığınızda, şifrelemek ve XML verilerin şifresini çözmek için aynı anahtarı kullanmanız gerekir.  Bu yordamdaki örneğin varsayar şifrelenmiş XML aynı anahtar kullanılarak şifrelenmiş ve şifreleme ve tarafların şifre çözme algoritması ve anahtarı kabul etmiş olursunuz.  Bu örnek depolamaz veya şifrelenmiş XML içindeki AES anahtarını şifrelemek.  
  
 Bu örnek, burada bellekte ya da bir parolasından türetilen şifreleme açısından güçlü bir anahtarı temel alan bir oturum anahtarı temel alan verileri şifrelemek için tek bir uygulama gereken durumlar için uygundur.  Burada şifrelenmiş XML verileri paylaşmak için iki veya daha fazla uygulama gereken durumlar için asimetrik algoritma veya bir X.509 sertifikası göre bir şifreleme şeması kullanmayı düşünün.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>XML öğesinin şifresini bir simetrik anahtarla çözmek için  
  
1.  Bir XML öğesi içinde açıklanan teknikleri kullanarak daha önce oluşturulan anahtar ile şifreleme [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2.  Bul <`EncryptedData`> (XML şifreleme standardı tarafından tanımlanan) öğesinde bir <xref:System.Xml.XmlDocument> şifrelenmiş XML içeren nesne ve yeni bir <xref:System.Xml.XmlElement> bu öğeyi temsil eden nesne.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptedData> ham XML verilerini önceden oluşturulan yükleme nesne <xref:System.Xml.XmlElement> nesne.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> nesne ve şifreleme için kullanılan aynı anahtarı kullanarak XML verileri şifrelemek için kullanın.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  XML belgesi içindeki yeni şifresi çözülmüş düz metin öğesiyle şifrelenmiş öğeyi değiştirin.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dosya adlı varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.  Ayrıca varsayılmaktadır `"test.xml"` içeren bir `"creditcard"` öğesi.  Aşağıdaki XML adlı bir dosyaya yerleştirebilirsiniz `test.xml` ve bu örnek ile kullanın.  
  
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
  
-   Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.  
  
-   Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Düz metin olarak hiçbir zaman bir şifreleme anahtarı depolamak veya düz metin olarak makineler arasında bir anahtar aktarın.  
  
 İşiniz bittiğinde simetrik şifreleme anahtarını kullanarak temizleyin, bellekten her bayt sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Cryptography.Xml>  
 [Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)

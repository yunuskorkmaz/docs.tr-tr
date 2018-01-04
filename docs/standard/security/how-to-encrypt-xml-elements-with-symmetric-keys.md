---
title: "Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme"
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2130a8c615faefeb49219b9df7e5765f77f4fac8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Nasıl yapılır: XML Öğelerini Simetrik Anahtarlarla Şifreleme
Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi içindeki bir öğe şifrelemek için ad alanı.  XML şifrelemesi, saklamak veya hassas XML kolayca okunan veriler hakkında endişelenmeden aktarım olanak sağlar.  Bu yordam, Gelişmiş Şifreleme Standardı (AES) algoritması, olarak da bilinen Rijndael kullanarak bir XML öğesi şifresini çözer.  
  
 Bu yordam kullanılarak şifrelenmiş bir XML öğesi şifresini çözme hakkında daha fazla bilgi için bkz: [nasıl yapılır: XML öğelerini simetrik anahtarlarla şifresini](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 XML verileri şifrelemek için simetrik algoritması AES gibi kullandığınızda, şifrelemek ve XML verilerin şifresini çözmek için aynı anahtarı kullanmanız gerekir.  Bu yordamdaki örneğin şifrelenmiş XML aynı anahtarı kullanarak şifresi çözülmüş olacağını ve şifreleme ve tarafların şifre çözme algoritması ve anahtarı kabul varsayar.  Bu örnek depolamaz veya şifrelenmiş XML içindeki AES anahtarını şifrelemek.  
  
 Bu örnek, burada bellekte ya da bir parolasından türetilen şifreleme açısından güçlü bir anahtarı temel alan bir oturum anahtarı temel alan verileri şifrelemek için tek bir uygulama gereken durumlar için uygundur.  Burada şifrelenmiş XML verileri paylaşmak için iki veya daha fazla uygulama gereken durumlar için asimetrik algoritma veya bir X.509 sertifikası göre bir şifreleme şeması kullanmayı düşünün.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>XML öğesini bir simetrik anahtarla şifrelemek için  
  
1.  Bir simetrik anahtar kullanarak Oluştur <xref:System.Security.Cryptography.RijndaelManaged> sınıfı.  Bu anahtar, XML öğesi şifrelemek için kullanılır.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2.  Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.  <xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3.  Belirtilen öğe Bul <xref:System.Xml.XmlDocument> nesne ve yeni bir <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden nesne.  Bu örnekte, `"creditcard"` öğesi şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4.  Yeni bir örneğini oluşturmak <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfı ve şifrelemek için kullandığınız <xref:System.Xml.XmlElement> simetrik anahtara sahip.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Yöntem şifrelenmiş bir bayt dizisi şifrelenmiş öğesi döndürür.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5.  Oluşturmak bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne ve XML şifrelemesi öğesi URL tanıtıcısı ile doldurur.  Bu URL tanımlayıcı XML şifrelenmiş bir öğe içeriyor bilmeniz şifresi çözme bir taraf sağlar.  Kullanabileceğiniz <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> alan URL tanımlayıcısını belirtin.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6.  Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptionMethod> anahtarı oluşturmak için kullanılan şifreleme algoritması URL tanıtıcısı başlatılmamış nesne.  Geçirmek <xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesinin <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliği.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7.  Şifreli öğe verileri eklediğinizde <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8.  Özgün öğeyi değiştirin <xref:System.Xml.XmlDocument> nesnesi ile <xref:System.Security.Cryptography.Xml.EncryptedData> öğesi.  
  
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
  
-   Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.  
  
-   Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Düz metin olarak hiçbir zaman bir şifreleme anahtarı depolamak veya düz metin olarak makineler arasında bir anahtar aktarın.  Bunun yerine, şifreleme anahtarlarını depolamak için güvenli bir anahtar kapsayıcısı kullanın.  
  
 İşiniz bittiğinde şifreleme anahtarını kullanarak temizleyin, bellekten her bayt sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Cryptography.Xml>  
 [Nasıl yapılır: XML Öğelerinin Şifresini Simetrik Anahtarlarla Çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)

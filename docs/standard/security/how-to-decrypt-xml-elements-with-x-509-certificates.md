---
title: 'Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0064aaf2e67eb3fb40e4c58995ce8678321d21aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583337"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme
Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> şifrelemek ve şifresini çözmek bir XML belgesi içindeki bir öğe için ad alanı.  XML şifrelemesi, exchange veya kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.  XML şifrelemesi konumunda bulunan için XML şifreleme standardı hakkında daha fazla bilgi için bkz: World Wide Web Konsorsiyumu (W3C) belirtimi http://www.w3.org/TR/xmldsig-core/.  
  
 Bu örnekte açıklanan yöntemleri kullanılarak şifrelenmiş bir XML öğesi şifresini çözer: [nasıl yapılır: XML öğelerini X.509 sertifikalarıyla şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).  Bulduğu bir <`EncryptedData`> öğesi, öğenin şifresini çözer ve özgün düz metin XML öğesi ile öğenin yerini alır.  
  
 Bu yordamı kod örneğinde geçerli kullanıcı hesabının yerel sertifika deposundan bir X.509 sertifikası kullanarak bir XML öğesi şifresini çözer.  Örnek kullanır <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> otomatik olarak X.509 sertifika almak ve bir oturum anahtarı depolanır şifresini çözmek için yöntem <`EncryptedKey`> öğesi <`EncryptedData`> öğesi.  <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> Yöntemi sonra otomatik olarak oturum anahtarı XML öğesi şifresini çözmek için kullanır.  
  
 Bu örnek birden çok uygulama şifrelenmiş verileri paylaşmak gereken yeri veya burada çalıştırdığı zamanları arasında şifrelenmiş verileri kaydetmek bir uygulama gereken durumlar için uygundur.  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>X.509 sertifikası olan bir XML öğesinin şifresini çözmek için  
  
1.  Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.  <xref:System.Xml.XmlDocument> Nesne şifresini çözmek için XML öğesi içerir.  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  Yeni bir <xref:System.Security.Cryptography.Xml.EncryptedXml> geçirerek nesne <xref:System.Xml.XmlDocument> oluşturucuya nesnesi.  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  XML kullanarak belgenin şifresini <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> yöntemi.  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  Kaydet <xref:System.Xml.XmlDocument> nesnesi.  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
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
  
 [!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.  
  
-   Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu örnekte kullanılan X.509 sertifikası yalnızca sınama amaçlıdır.  Uygulamaları, güvenilen bir sertifika yetkilisi tarafından oluşturulan bir X.509 sertifikası kullanın veya Microsoft Windows sertifika sunucusu tarafından oluşturulan bir sertifika kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Cryptography.Xml>  
 [Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)

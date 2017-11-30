---
title: "Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme"
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
- encryption [.NET Framework], X.509 certificates
- cryptography [.NET Framework], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6690c87bb7a632a783fc89341d405bf81166470c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme
Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi içindeki bir öğe şifrelemek için ad alanı.  XML şifrelemesi, exchange veya kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.  XML şifrelemesi için World Wide Web Konsorsiyumu (W3C) belirtimi http://www.w3.org/TR/xmldsig-core/ bulunan standart XML şifreleme hakkında daha fazla bilgi için bkz.  
  
 XML şifrelemesi herhangi bir XML öğesi değiştirin veya ile belge için kullanabileceğiniz bir <`EncryptedData`> şifrelenmiş XML verileri içeren öğe. <`EncryptedData`> Öğesi, anahtarlar ve şifreleme sırasında kullanılan işlemler hakkında bilgi içeren alt öğelerini içerebilir.  XML şifrelemesi şifrelenmiş birden çok öğe içeren bir belge ve birden çok kez şifrelenmesi için bir öğe olanak sağlar.  Bu yordamı kod örneğinde nasıl oluşturulacağını gösterir bir <`EncryptedData`> öğesi, daha sonra şifre çözme sırasında kullanabileceğiniz diğer alt öğelerini birlikte.  
  
 Bu örnek iki anahtarlar kullanılarak bir XML öğesi şifreler.  Bir X.509 sertifikası kullanarak test oluşturur [sertifika oluşturma Aracı (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) ve sertifikayı sertifika deposuna kaydeder.  Örnek ardından program aracılığıyla sertifikayı alır ve bir XML öğesi kullanarak şifrelemek için kullandığı <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi.  Dahili olarak, <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi ayrı oturum anahtarı oluşturur ve XML belgesi şifrelemek için kullanır. Bu yöntem, oturum anahtarı şifreler ve şifrelenmiş XML yanı sıra içinde yeni bir kaydeder <`EncryptedData`> öğesi.  
  
 XML öğesi şifresini çözmek için yalnızca çağrı <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> otomatik olarak X.509 Sertifika depodan alır ve gerekli şifre çözme gerçekleştiren yöntemi.  Bu yordam kullanılarak şifrelenmiş bir XML öğesi şifresini hakkında daha fazla bilgi için bkz: [nasıl yapılır: XML öğelerini X.509 sertifikalarıyla şifresini](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
 Bu örnek birden çok uygulama şifrelenmiş verileri paylaşmak gereken yeri veya burada çalıştırdığı zamanları arasında şifrelenmiş verileri kaydetmek bir uygulama gereken durumlar için uygundur.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Bir XML öğesini X.509 sertifikası ile şifrelemek için  
  
1.  Kullanım [sertifika oluşturma Aracı (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) bir test X.509 sertifikası oluşturup yerel kullanıcı deposunda yerleştirin.  Değişim anahtarı oluşturmanız gerekir ve anahtarı dışa aktarılabilir duruma getir. Şu komutu çalıştırın:  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  Oluşturma bir <xref:System.Security.Cryptography.X509Certificates.X509Store> nesne ve geçerli kullanıcı deposunda açmak için Başlat.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  Deposu salt okunur modunda açın.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  Başlatma bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> tüm deposundaki sertifikalar.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  Deposundaki sertifikalar aracılığıyla numaralandırır ve uygun bir ad ile sertifikayı bulun.  Bu örnekte, sertifika adlı `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  Sertifika bulunduktan sonra mağaza kapatın.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.  <xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  Belirtilen öğe Bul <xref:System.Xml.XmlDocument> nesne ve yeni bir <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden nesne.  Bu örnekte, `"creditcard"` öğesi şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Yeni bir örneğini oluşturmak <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfı ve X.509 sertifikası kullanarak belirtilen öğe şifrelemek için kullanabilirsiniz.  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Yöntem şifrelenmiş öğesi olarak bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Özgün öğeyi değiştirin <xref:System.Xml.XmlDocument> nesnesi ile <xref:System.Security.Cryptography.Xml.EncryptedData> öğesi.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Kaydet <xref:System.Xml.XmlDocument> nesnesi.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.  
  
-   Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu örnekte kullanılan X.509 sertifikası yalnızca sınama amaçlıdır.  Uygulamaları, güvenilen bir sertifika yetkilisi tarafından oluşturulan bir X.509 sertifikası kullanın veya Microsoft Windows sertifika sunucusu tarafından oluşturulan bir sertifika kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Cryptography.Xml>  
 [Nasıl yapılır: X.509 sertifikalarıyla XML öğelerinin şifresini çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)

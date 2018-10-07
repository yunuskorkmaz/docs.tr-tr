---
title: 'Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3d61fcbab4c905ba675e08346ea7cb28b0e710c
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845520"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme
Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi bir öğesinde şifrelemek için ad alanı.  XML şifreleme, exchange veya bir kolayca okunan verilerin hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.  XML şifreleme konumundaki XML şifreleme standardı hakkında daha fazla bilgi için World Wide Web Consortium (W3C) belirtimi bakın <https://www.w3.org/TR/xmldsig-core/>.  
  
 XML şifreleme herhangi bir XML öğesini değiştirin veya ile belge için kullanabileceğiniz bir <`EncryptedData`> şifrelenmiş XML verilerini içeren öğe. <`EncryptedData`> Öğesi, anahtarları ve şifreleme sırasında kullanılan işlemler hakkında bilgi içeren alt öğelerini içerebilir.  XML şifreleme şifrelenmiş birden çok öğe içeren bir belge sağlar ve bir öğe birden çok kez şifrelenmesini sağlar.  Bu yordam kod örneğinde nasıl oluşturulacağını gösterir bir <`EncryptedData`> öğesi birlikte, daha sonra şifre çözme sırasında kullanabileceğiniz diğer alt öğeleri.  
  
 Bu örnekte, iki anahtar kullanarak bir XML öğesi şifreler.  Bir test X.509 sertifikası kullanarak oluşturur [sertifika oluşturma Aracı (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) ve sertifikayı sertifika deposuna kaydeder.  Örnek daha sonra program aracılığıyla sertifikayı alır ve bir XML öğesini kullanarak şifrelemek için kullandığı <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi.  Dahili olarak <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi ayrı oturum anahtarı oluşturur ve XML belgesi şifrelemek için kullanır. Bu yöntem oturum anahtarı şifreler ve şifrelenmiş XML yanı sıra içinde yeni bir kaydeder <`EncryptedData`> öğesi.  
  
 XML öğesinin şifresini çözmek için basitçe çağrı <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> yöntemi otomatik olarak X.509 sertifika deposundan alır ve gerekli şifre çözme işlemleri gerçekleştirir.  Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözmek hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerini X.509 sertifikalarıyla şifresini](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
 Bu örnek, birden çok uygulama şifrelenmiş veri paylaşımı gereken yere veya uygulamanın çalıştığı zamanları arasında şifrelenmiş verileri kaydetmek gereken yere durumlar için uygundur.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Bir XML öğesini X.509 sertifikası ile şifrelemek için  
  
1.  Kullanım [sertifika oluşturma Aracı (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) test X.509 sertifikası oluşturma ve yerel kullanıcı depolama alanına yerleştir.  Değişim anahtarı oluşturmanız gerekir ve anahtar dışarı aktarılabilir yapmanız gerekir. Şu komutu çalıştırın:  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  Oluşturma bir <xref:System.Security.Cryptography.X509Certificates.X509Store> nesne ve geçerli kullanıcı deposu açmak için Başlat.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  Deponun yalnızca Okuma modunda açın.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  Başlatma bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> tüm sertifikaları aşağıdaki depolama.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  Deposundaki sertifikalar aracılığıyla listeleme ve uygun ad sahip sertifika bulunamadı.  Bu örnekte, sertifika adlı `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  Sertifika bulunduktan sonra deponun kapatın.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.  <xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  Belirtilen öğe Bul <xref:System.Xml.XmlDocument> nesne ve yeni bir <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden nesne.  Bu örnekte, `"creditcard"` öğesi şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Yeni bir örneğini oluşturma <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfı ve X.509 sertifikası kullanarak belirtilen öğeyi şifrelemek için kullanabilirsiniz.  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Yöntemi döndürür şifrelenmiş öğesi olarak bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Özgün öğeden değiştirin <xref:System.Xml.XmlDocument> nesnesi ile <xref:System.Security.Cryptography.Xml.EncryptedData> öğesi.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Kaydet <xref:System.Xml.XmlDocument> nesne.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir dosya olduğunu varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.  Ayrıca varsayılmaktadır `"test.xml"` içeren bir `"creditcard"` öğesi.  Aşağıdaki XML adlı bir dosyaya yerleştirebilirsiniz `test.xml` ve bu örneği kullanın.  
  
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
  
-   Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.  
  
-   Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu örnekte kullanılan X.509 sertifikası, yalnızca test amaçlıdır.  Uygulamaları, bir güvenilen sertifika yetkilisi tarafından oluşturulan bir X.509 sertifikası kullanın veya Microsoft Windows sertifika sunucusu tarafından oluşturulan bir sertifika kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>  
- [Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)

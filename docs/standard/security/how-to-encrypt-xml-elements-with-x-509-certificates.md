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
ms.openlocfilehash: 7f74e4e46ba760b7a943b2e2728e487ee87ae204
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706077"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Nasıl yapılır: XML Öğelerini X.509 Sertifikalarıyla Şifreleme
Bir XML belgesi içindeki bir öğeyi şifrelemek için <xref:System.Security.Cryptography.Xml> ad alanındaki sınıfları kullanabilirsiniz.  XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.  XML şifreleme standardı hakkında daha fazla bilgi için, <https://www.w3.org/TR/xmldsig-core/>konumundaki XML şifrelemesi için World Wide Web Konsorsiyumu (W3C) belirtimine bakın.  
  
 XML şifrelemesini, şifrelenmiş XML verilerini içeren bir <`EncryptedData`> öğesiyle herhangi bir XML öğesini veya belgeyi değiştirmek için kullanabilirsiniz. <`EncryptedData`> öğesi, şifreleme sırasında kullanılan anahtarlar ve süreçler hakkında bilgiler içeren alt öğeleri içerebilir.  XML şifrelemesi, bir belgenin birden çok şifrelenmiş öğe içermesini sağlar ve bir öğenin birden çok kez şifrelenmesini sağlar.  Bu yordamdaki kod örneği, daha sonra şifre çözme sırasında kullanabileceğiniz birkaç diğer alt öğe ile birlikte <`EncryptedData`> öğesi oluşturma işlemini gösterir.  
  
 Bu örnek, iki anahtar kullanarak bir XML öğesini şifreler. [Sertifika oluşturma aracı 'nı (Makecert. exe)](/windows/desktop/SecCrypto/makecert) kullanarak bir test X. 509.440 sertifikası oluşturur ve sertifikayı bir sertifika deposuna kaydeder. Örnek daha sonra sertifikayı program aracılığıyla alır ve <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi kullanarak bir XML öğesini şifrelemek için kullanır. Dahili olarak, <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi ayrı bir oturum anahtarı oluşturur ve XML belgesini şifrelemek için onu kullanır. Bu yöntem, oturum anahtarını şifreler ve şifreli XML ile birlikte yeni bir <`EncryptedData`> öğesi içinde kaydeder.  
  
 XML öğesinin şifresini çözmek için, mağazadan X. 509.440 sertifikasını otomatik olarak alan <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> yöntemini çağırmanız ve gerekli şifre çözmeyi gerçekleştirmeniz yeterlidir.  Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözme hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerinin şifresini X. 509.440 sertifikalarıyla çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
 Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, kaç kez şifrelenmiş verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Bir XML öğesini X.509 sertifikası ile şifrelemek için  
  
1. [Sertifika oluşturma aracı 'nı (Makecert. exe)](/windows/desktop/SecCrypto/makecert) kullanarak bir test X. 509.952 sertifikası oluşturun ve bunu yerel kullanıcı deposuna yerleştirin. Bir Exchange anahtarı oluşturmanız gerekir ve anahtarı dışa aktarılabilir yapmanız gerekir. Şu komutu çalıştırın:  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2. <xref:System.Security.Cryptography.X509Certificates.X509Store> nesnesi oluşturun ve geçerli kullanıcı deposunu açmak için başlatın.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. Depoyu salt okuma modunda açın.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. Depodaki tüm sertifikalarla bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> başlatın.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. Depodaki sertifikaları numaralandırın ve uygun ada sahip sertifikayı bulun.  Bu örnekte, sertifika `"CN=XML_ENC_TEST_CERT"`olarak adlandırılmıştır.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. Sertifika oluşturulduktan sonra mağazayı kapatın.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. Diskten bir XML dosyası yükleyerek <xref:System.Xml.XmlDocument> nesnesi oluşturun.  <xref:System.Xml.XmlDocument> nesnesi şifrelenecek XML öğesini içeriyor.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <xref:System.Xml.XmlDocument> nesnesinde belirtilen öğeyi bulun ve şifrelemek istediğiniz öğeyi temsil eden yeni bir <xref:System.Xml.XmlElement> nesnesi oluşturun.  Bu örnekte `"creditcard"` öğesi şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfının yeni bir örneğini oluşturun ve X. 509.440 sertifikasını kullanarak belirtilen öğeyi şifrelemek için kullanın.  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> yöntemi, şifrelenmiş öğeyi bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi olarak döndürür.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Öğeyi özgün <xref:System.Xml.XmlDocument> nesnesinden <xref:System.Security.Cryptography.Xml.EncryptedData> öğesiyle değiştirin.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <xref:System.Xml.XmlDocument> nesnesini kaydedin.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- Bu örneği derlemek için `System.Security.dll`bir başvuru eklemeniz gerekir.  
  
- Şu ad alanlarını ekleyin: <xref:System.Xml>, <xref:System.Security.Cryptography>ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu örnekte kullanılan X. 509.440 sertifikası yalnızca test amaçlıdır.  Uygulamalar, güvenilir bir sertifika yetkilisi tarafından oluşturulan bir X. 509.440 sertifikası kullanmalı veya Microsoft Windows sertifika sunucusu tarafından oluşturulan bir sertifikayı kullanmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Öğelerinin Şifresini X.509 Sertifikalarıyla Çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)

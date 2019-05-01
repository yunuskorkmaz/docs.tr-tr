---
title: 'Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec5d42bd003f6fb6a79bbd71beb8c88efa4e84c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795115"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme
Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi bir öğesinde şifrelemek için ad alanı.  XML şifreleme, exchange veya bir kolayca okunan verilerin hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.  XML şifreleme konumundaki XML şifreleme standardı hakkında daha fazla bilgi için World Wide Web Consortium (W3C) belirtimi bakın <https://www.w3.org/TR/xmldsig-core/>.  
  
 XML şifreleme herhangi bir XML öğesini değiştirin veya ile belge için kullanabileceğiniz bir <`EncryptedData`> şifrelenmiş XML verilerini içeren öğe.  <`EncryptedData`> Öğesi anahtarları ve şifreleme sırasında kullanılan işlemler hakkında bilgi içeren alt öğelerini içerebilir.  XML şifreleme şifrelenmiş birden çok öğe içeren bir belge sağlar ve bir öğe birden çok kez şifrelenmesini sağlar.  Bu yordam kod örneğinde nasıl oluşturulacağını gösterir. bir <`EncryptedData`> öğesi birlikte, daha sonra şifre çözme sırasında kullanabileceğiniz diğer alt öğeleri.  
  
 Bu örnekte, iki anahtar kullanarak bir XML öğesi şifreler.  Bu, bir RSA ortak/özel anahtar çifti oluşturur ve güvenli bir anahtar kapsayıcısı için bir anahtar çifti kaydeder.  Bu örnek, ardından Rijndael algoritma olarak da bilinir Gelişmiş Şifreleme Standardı (AES) algoritması kullanılarak ayrı bir oturum anahtarı oluşturur.  Örnek XML belgesi şifreleme için AES oturum anahtarı kullanır ve ardından AES oturum anahtarı şifrelemek için RSA ortak anahtarı kullanır.  Son olarak, örnek şifrelenmiş AES oturum anahtarı ve şifrelenmiş XML verileri için XML belgesi içinde yeni bir kaydeder <`EncryptedData`> öğesi.  
  
 XML öğesinin şifresini çözmek için anahtar kapsayıcısından RSA özel anahtarını alamazsa, oturum anahtarının şifresini çözmek için kullanın ve sonra belgenin şifresini çözmek için oturum anahtarını kullanır.  Bu yordam kullanılarak şifrelenmiş bir XML öğesinin şifresini çözmek hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifre çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Bu örnek, birden çok uygulama şifrelenmiş veri paylaşımı gereken yere veya uygulamanın çalıştığı zamanları arasında şifrelenmiş verileri kaydetmek gereken yere durumlar için uygundur.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>Bir XML öğesi bir asimetrik anahtarla şifrelemek için  
  
1. Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve anahtar kapsayıcısı adını belirtin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Bir simetrik anahtar kullanarak Oluştur <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.  Geçirdiğinizde anahtarı için anahtar kapsayıcısını otomatik olarak kaydedilir <xref:System.Security.Cryptography.CspParameters> nesnesi oluşturucusuna <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.  Bu anahtar, AES oturum anahtarı şifrelemek için kullanılan ve daha sonra şifresini alınabilir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.  <xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. Belirtilen öğe Bul <xref:System.Xml.XmlDocument> nesne ve yeni bir <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden nesne. Bu örnekte, `"creditcard"` öğesi şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. Kullanarak bir yeni bir oturum anahtarı oluşturun <xref:System.Security.Cryptography.RijndaelManaged> sınıfı.  Bu anahtar XML öğesi şifrelemek ve ardından kendisini şifrelenir ve XML belgesinde yerleştirilir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. Yeni bir örneğini oluşturma <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfı ve oturum anahtarı kullanarak belirtilen öğeyi şifrelemek için kullanabilirsiniz.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Yöntem şifrelenmiş öğesi şifrelenmiş bayt dizisi döndürür.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. Oluşturmak bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne ve şifrelenmiş XML öğesi URL'si tanıtıcısı ile doldurun.  Bu URL tanımlayıcısı XML şifrelenmiş bir öğe içerdiğini bildiğiniz öğesinin şifresini çözerken bir taraf sağlar.  Kullanabileceğiniz <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> alanını URL tanımlayıcısını belirtin.  Düz metin XML öğesi yerine bir <`EncryptedData`> öğesi tarafından bu kapsüllenmiş <xref:System.Security.Cryptography.Xml.EncryptedData> nesne.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptionMethod> oturum anahtarı oluşturmak için kullanılan şifreleme algoritması URL tanımlayıcısı için başlatılmış olan bir nesne.  Geçirmek <xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesini <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliği.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptedKey> şifrelenmiş oturum anahtarı içeren nesne.  Oturum anahtarı şifrelemek, ekleyin <xref:System.Security.Cryptography.Xml.EncryptedKey> nesnesinin ve oturum anahtarı adı ve anahtar tanımlayıcı URL'sini girin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Yeni bir <xref:System.Security.Cryptography.Xml.DataReference> belirli oturum anahtarı şifreli verilere eşleyen nesne.  Bu isteğe bağlı bir adım, bir XML belgesi birden fazla bölümü tek bir anahtarla şifrelenmiş kolayca belirtmenizi sağlar.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Şifrelenmiş anahtarı ekleme <xref:System.Security.Cryptography.Xml.EncryptedData> nesne.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Yeni bir <xref:System.Security.Cryptography.Xml.KeyInfo> RSA anahtarı adını belirtmek için nesne.  Ekleyin <xref:System.Security.Cryptography.Xml.EncryptedData> nesne. Bu oturum anahtarının şifresini çözerken doğru asimetrik anahtar tanımlamak şifresini çözmeyi taraf yardımcı olur.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Şifreli öğe verileri eklediğinizde <xref:System.Security.Cryptography.Xml.EncryptedData> nesne.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Özgün öğeden değiştirin <xref:System.Xml.XmlDocument> nesnesi ile <xref:System.Security.Cryptography.Xml.EncryptedData> öğesi.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Kaydet <xref:System.Xml.XmlDocument> nesne.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.  
  
- Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Hiçbir zaman düz metin olarak bir simetrik şifreleme anahtarı depolamak veya makine düz metin arasında bir simetrik anahtar aktarın.  Buna ek olarak, hiçbir zaman depolayabilen veya asimetrik anahtar çifti düz metin olarak özel anahtarı.  Simetrik hem de asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Hiçbir zaman doğrudan sizin kaynak kodunuza bir anahtar ekleyin.  Katıştırılmış anahtarları kullanarak bir derlemeden kolayca da okunabilir [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.  
  
 İşiniz bittiğinde bir şifreleme anahtarı kullanarak temizleyin, bellekten her byte sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.  Şifreleme anahtarlarını bazen bellekten bir hata ayıklayıcı tarafından okunabilir veya disk belleğine alınan bellek konumunda bir sabit diskten okunur diske.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifre çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)

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
ms.openlocfilehash: b6840a9005aaca4805252298e1ceaf7e51f38971
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme
Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi içindeki bir öğe şifrelemek için ad alanı.  XML şifrelemesi, exchange veya kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verileri depolamak için standart bir yoludur.  XML şifrelemesi konumunda bulunan için XML şifreleme standardı hakkında daha fazla bilgi için bkz: World Wide Web Konsorsiyumu (W3C) belirtimi http://www.w3.org/TR/xmldsig-core/.  
  
 XML şifrelemesi herhangi bir XML öğesi değiştirin veya ile belge için kullanabileceğiniz bir <`EncryptedData`> şifrelenmiş XML verileri içeren öğe.  <`EncryptedData`> Öğesi anahtarları ve şifreleme sırasında kullanılan işlemler hakkında bilgi içeren alt öğeleri de içerebilir.  XML şifrelemesi şifrelenmiş birden çok öğe içeren bir belge ve birden çok kez şifrelenmesi için bir öğe olanak sağlar.  Bu yordamı kod örneğinde nasıl oluşturulacağını gösterir bir <`EncryptedData`> öğesi, daha sonra şifre çözme sırasında kullanabileceğiniz diğer alt öğelerini birlikte.  
  
 Bu örnek iki anahtarlar kullanılarak bir XML öğesi şifreler.  Bir RSA ortak/özel anahtar çifti oluşturur ve güvenli bir anahtar kapsayıcısı için anahtar çifti kaydeder.  Bu örnek daha sonra Rijndael algoritması olarak da bilinir Gelişmiş Şifreleme Standardı (AES) algoritması kullanılarak ayrı oturum anahtarı oluşturur.  Örnek XML belgesi şifrelemek için AES oturum anahtarı kullanır ve AES oturum anahtarı şifrelemek için RSA ortak anahtarı kullanır.  Son olarak, örnek şifrelenmiş AES oturum anahtarı ve şifrelenmiş XML verileri XML belgesi içinde yeni bir kaydeder <`EncryptedData`> öğesi.  
  
 XML öğesi şifresini çözmek için anahtar kapsayıcıdan RSA özel anahtarı almak, oturum anahtarının şifresini çözmek için kullanın ve sonra belgenin şifresini çözmek için oturum anahtarını kullanır.  Bu yordam kullanılarak şifrelenmiş bir XML öğesi şifresini hakkında daha fazla bilgi için bkz: [nasıl yapılır: XML öğelerini asimetrik anahtarlarla şifresini](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Bu örnek birden çok uygulama şifrelenmiş verileri paylaşmak gereken yeri veya burada çalıştırdığı zamanları arasında şifrelenmiş verileri kaydetmek bir uygulama gereken durumlar için uygundur.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>Bir XML öğesi bir asimetrik anahtar şifrelemek için  
  
1.  Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve anahtar kapsayıcı adını belirtin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Bir simetrik anahtar kullanarak Oluştur <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.  Geçirdiğiniz zaman anahtar için anahtar kapsayıcısını otomatik olarak kaydedilir <xref:System.Security.Cryptography.CspParameters> oluşturucusunun nesnesine <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.  Bu anahtar, AES oturum anahtarı şifrelemek için kullanılan ve daha sonra şifresini alınabilir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.  <xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  Belirtilen öğe Bul <xref:System.Xml.XmlDocument> nesne ve yeni bir <xref:System.Xml.XmlElement> şifrelemek istediğiniz öğeyi temsil eden nesne. Bu örnekte, `"creditcard"` öğesi şifrelenir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  Kullanarak bir yeni bir oturum anahtarı oluşturun <xref:System.Security.Cryptography.RijndaelManaged> sınıfı.  Bu anahtar XML öğesi şifrelemek ve ardından kendisini şifrelenir ve XML belgesinde yerleştirilir.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  Yeni bir örneğini oluşturmak <xref:System.Security.Cryptography.Xml.EncryptedXml> sınıfı ve oturum anahtarı kullanarak belirtilen öğe şifrelemek için kullanabilirsiniz.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Yöntem şifrelenmiş bir bayt dizisi şifrelenmiş öğesi döndürür.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  Oluşturmak bir <xref:System.Security.Cryptography.Xml.EncryptedData> nesne ve şifrelenmiş XML öğesi URL tanıtıcısı ile doldurur.  Bu URL tanımlayıcı XML şifrelenmiş bir öğe içeriyor bilmeniz şifresi çözme bir taraf sağlar.  Kullanabileceğiniz <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> alan URL tanımlayıcısını belirtin.  Düz metin XML öğesi yerine bir <`EncryptedData`> öğesi tarafından bu kapsüllenmiş <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptionMethod> oturum anahtarı oluşturmak için kullanılan şifreleme algoritması URL tanıtıcısı başlatılmamış nesne.  Geçirmek <xref:System.Security.Cryptography.Xml.EncryptionMethod> nesnesinin <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> özelliği.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Oluşturma bir <xref:System.Security.Cryptography.Xml.EncryptedKey> şifreli oturum anahtarı içeren nesne.  Oturum anahtarını şifrelemek, ekleyin <xref:System.Security.Cryptography.Xml.EncryptedKey> nesne ve bir oturum anahtarı adı ve anahtar tanımlayıcı URL'sini girin.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Yeni bir <xref:System.Security.Cryptography.Xml.DataReference> belirli oturum anahtarı için şifrelenmiş veriler eşlemeleri nesnesi.  Bu isteğe bağlı adım, bir XML belgesi birden fazla bölümü tek bir anahtarla şifrelenmiş kolayca belirtmenizi sağlar.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Şifrelenmiş anahtar ekler <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Yeni bir <xref:System.Security.Cryptography.Xml.KeyInfo> nesne RSA anahtar adını belirtin.  Ekleyin <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi. Bu, oturum anahtarının şifresini çözme sırasında kullanmak için doğru asimetrik anahtar tanımlamak şifresi çözme taraf yardımcı olur.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Şifreli öğe verileri eklediğinizde <xref:System.Security.Cryptography.Xml.EncryptedData> nesnesi.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Özgün öğeyi değiştirin <xref:System.Xml.XmlDocument> nesnesi ile <xref:System.Security.Cryptography.Xml.EncryptedData> öğesi.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Kaydet <xref:System.Xml.XmlDocument> nesnesi.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.  
  
-   Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Düz metin olarak hiçbir zaman bir simetrik şifreleme anahtarı depolamak veya düz metin olarak makineler arasında bir simetrik anahtar aktarın.  Buna ek olarak, hiçbir zaman depolamak veya asimetrik anahtar çifti düz metin olarak özel anahtarı aktarın.  Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz: [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Hiç kaynak kodunuza doğrudan bir anahtar ekleyin.  Katıştırılmış anahtarları kullanarak bir derlemeye ait kolayca da okunabilir [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.  
  
 İşiniz bittiğinde şifreleme anahtarını kullanarak temizleyin, bellekten her bayt sıfır olarak ayarlayarak veya çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemi.  Şifreleme anahtarları bazen bellekten bir hata ayıklayıcı tarafından okunabilir veya bellek konumuna disk belleği, bir sabit diskten okuma diske.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Cryptography.Xml>  
 [Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)

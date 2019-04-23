---
title: 'Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39e053ea9ca0b2fdc548a4b9447d34e852816a61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324506"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a>Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama
Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> bir XML belgesi ya da bir dijital imzaya sahip bir XML belgesi bir parçası olarak imzalamak için ad alanı.  XML dijital imzaları (XMLDSIG) imzalandıktan sonra veri değiştirilmiş değil olduğunu doğrulamanızı sağlar.  World Wide Web Consortium (W3C) öneri XMLDSIG standart hakkında daha fazla bilgi için bkz. [XML imza söz dizimi ve işleme](https://www.w3.org/TR/xmldsig-core/).  
  
 Kod örneği, bu yordamı dijital olarak tüm bir XML belgesi oturum ve imza belgede ekleme yapmayı gösteren bir <`Signature`> öğesi.  Örnek, RSA imzalama anahtarı oluşturur, anahtarı güvenli bir anahtar kapsayıcısına ekler ve ardından bir XML belgesinin dijital olarak imzalamak için anahtar kullanır.  Anahtar XML dijital imzasını alınabilir veya başka bir XML belgesi imzalamak için kullanılabilir.  
  
 Bu yordamı kullanılarak oluşturulan bir XML dijital imza doğrulama hakkında daha fazla bilgi için bkz: [nasıl yapılır: XML belgelerinin dijital imzalarını doğrulama](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).  
  
### <a name="to-digitally-sign-an-xml-document"></a>Bir XML belgesinin dijital olarak imzalamak için  
  
1. Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve anahtar kapsayıcısı adını belirtin.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Bir asimetrik anahtar kullanarak Oluştur <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.  Geçirdiğinizde anahtarı için anahtar kapsayıcısını otomatik olarak kaydedilir <xref:System.Security.Cryptography.CspParameters> nesnesi oluşturucusuna <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.  Bu anahtar, XML belgesi imzalamak için kullanılır.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.  <xref:System.Xml.XmlDocument> Nesne şifrelemek için XML öğesi içerir.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesne ve geçirin <xref:System.Xml.XmlDocument> nesnesi.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. İmzalama RSA anahtarı ekleme <xref:System.Security.Cryptography.Xml.SignedXml> nesne.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. Oluşturma bir <xref:System.Security.Cryptography.Xml.Reference> oturum gerekenler tanımlayan nesne.  Tüm belgeyi imzalamak için ayarlanmış <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> özelliğini `""`.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. Ekleme bir <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> nesnesini <xref:System.Security.Cryptography.Xml.Reference> nesnesi.  Bir dönüştürme imzalayan kullanılan aynı şekilde XML verileri temsil etmek Doğrulayıcı sağlar.  Bu doğrulama için önemli bir adımdır şekilde XML verileri farklı şekillerde temsil edilebilir.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. Ekleme <xref:System.Security.Cryptography.Xml.Reference> nesnesini <xref:System.Security.Cryptography.Xml.SignedXml> nesnesi.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. İmza çağırarak işlem <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> yöntemi.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. İmza XML gösterimini almak (bir <`Signature`> öğesi) ve yeni bir kaydetme <xref:System.Xml.XmlElement> nesne.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. Öğesine ekleme <xref:System.Xml.XmlDocument> nesne.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. Belgeyi kaydedin.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir dosya olduğunu varsayar `test.xml` derlenmiş programın aynı dizinde bulunmaktadır.  Aşağıdaki XML adlı bir dosyaya yerleştirebilirsiniz `test.xml` ve bu örneği kullanın.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.  
  
-   Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Hiçbir zaman depolayabilen veya asimetrik anahtar çifti düz metin olarak özel anahtarı.  Simetrik hem de asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Hiçbir zaman bir özel anahtar doğrudan sizin kaynak kodunuza ekleyin.  Katıştırılmış anahtarları kullanarak bir derlemeden kolayca da okunabilir [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML belgelerinin dijital imzalarını doğrulama](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)

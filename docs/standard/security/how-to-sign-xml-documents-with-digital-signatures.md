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
ms.openlocfilehash: 0df036b3336527f3cc0e48d9a7ec835ab9f1cf4a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706051"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a>Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama
Bir XML belgesini veya bir XML belgesinin bir kısmını dijital imzaya imzalamak için <xref:System.Security.Cryptography.Xml> ad alanındaki sınıfları kullanabilirsiniz.  XML dijital imzaları (XMLDSIG), imzalandıktan sonra verilerin değiştirilmediğini doğrulamanızı sağlar.  XMLDSIG standardı hakkında daha fazla bilgi için, World Wide Web Konsorsiyumu (W3C) önerisi [XML Imzası sözdizimi ve işleme](https://www.w3.org/TR/xmldsig-core/)bölümüne bakın.  
  
 Bu yordamdaki kod örneğinde, bir XML belgesinin tamamını dijital olarak imzalama ve bir <`Signature`> öğesinde imzayı belgeye iliştirme gösterilmektedir.  Örnek, bir RSA imzalama anahtarı oluşturur, anahtarı güvenli bir anahtar kapsayıcısına ekler ve ardından bir XML belgesini dijital olarak imzalamak için anahtarı kullanır.  Anahtar daha sonra XML dijital imzasını doğrulamak için alınabilir veya başka bir XML belgesi imzalamak için kullanılabilir.  
  
 Bu yordam kullanılarak oluşturulan bir XML dijital imzasını doğrulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML belgelerinin dijital Imzalarını doğrulama](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).  
  
### <a name="to-digitally-sign-an-xml-document"></a>Bir XML belgesini dijital olarak imzalamak için  
  
1. <xref:System.Security.Cryptography.CspParameters> nesnesi oluşturun ve anahtar kapsayıcısının adını belirtin.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfını kullanarak asimetrik bir anahtar oluşturun.  <xref:System.Security.Cryptography.CspParameters> nesnesini <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfının oluşturucusuna geçirdiğinizde anahtar otomatik olarak anahtar kapsayıcısına kaydedilir.  Bu anahtar, XML belgesini imzalamak için kullanılacaktır.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Diskten bir XML dosyası yükleyerek <xref:System.Xml.XmlDocument> nesnesi oluşturun.  <xref:System.Xml.XmlDocument> nesnesi şifrelenecek XML öğesini içeriyor.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesnesi oluşturun ve <xref:System.Xml.XmlDocument> nesnesini ona geçirin.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <xref:System.Security.Cryptography.Xml.SignedXml> nesnesine imzalama RSA anahtarını ekleyin.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. İmzalanacak öğeleri açıklayan bir <xref:System.Security.Cryptography.Xml.Reference> nesnesi oluşturun.  Tüm belgeyi imzalamak için <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> özelliğini `""`olarak ayarlayın.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <xref:System.Security.Cryptography.Xml.Reference> nesnesine bir <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> nesnesi ekleyin.  Bir dönüşüm, doğrulayıcının XML verilerini imzalayan tarafından aynı şekilde temsil etmesine olanak tanır.  XML verileri farklı yollarla temsil edilebilir, bu nedenle doğrulama için bu adım önemlidir.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <xref:System.Security.Cryptography.Xml.Reference> nesnesini <xref:System.Security.Cryptography.Xml.SignedXml> nesnesine ekleyin.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> yöntemini çağırarak imzayı hesaplama.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. İmzanın XML temsilini (bir <`Signature`> öğesi) alın ve yeni bir <xref:System.Xml.XmlElement> nesnesine kaydedin.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <xref:System.Xml.XmlDocument> nesnesine öğeyi ekleyin.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. Belgeyi kaydedin.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, `test.xml` adlı bir dosyanın derlenen programla aynı dizinde olduğunu varsayar.  Aşağıdaki XML 'i `test.xml` adlı bir dosyaya yerleştirebilir ve bu örnekle birlikte kullanabilirsiniz.  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- Bu örneği derlemek için `System.Security.dll`bir başvuru eklemeniz gerekir.  
  
- Şu ad alanlarını ekleyin: <xref:System.Xml>, <xref:System.Security.Cryptography>ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.  Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Özel anahtarı hiçbir şekilde doğrudan kaynak kodunuza gömmeyin.  Gömülü anahtarlar [ıldadsm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)

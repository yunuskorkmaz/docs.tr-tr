---
title: 'Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: 5d562c23d3b0fd7eda5dc273932ada77709641a1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706012"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama
Dijital imzayla imzalanmış XML verilerini doğrulamak için <xref:System.Security.Cryptography.Xml> ad alanındaki sınıfları kullanabilirsiniz. XML dijital imzaları (XMLDSIG), imzalandıktan sonra verilerin değiştirilmediğini doğrulamanızı sağlar. XMLDSIG standardı hakkında daha fazla bilgi için <https://www.w3.org/TR/xmldsig-core/>World Wide Web Konsorsiyumu (W3C) belirtimine bakın.
  
 Bu yordamdaki kod örneği, bir <`Signature`> öğesinde bulunan bir XML dijital imzasının nasıl doğrulandığını gösterir.  Örnek, anahtar kapsayıcısından bir RSA ortak anahtarı alır ve ardından imzayı doğrulamak için anahtarı kullanır.  
  
 Bu tekniği kullanarak doğrulanabilen dijital imza oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML belgelerini dijital Imzalarla imzalama](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Bir XML belgesinin dijital imzasını doğrulamak için  
  
1. Belgeyi doğrulamak için, imzalama için kullanılan asimetrik anahtarı kullanmanız gerekir.  <xref:System.Security.Cryptography.CspParameters> nesnesi oluşturun ve imzalanmak üzere kullanılan anahtar kapsayıcısının adını belirtin.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfını kullanarak ortak anahtarı alın.  Anahtar, <xref:System.Security.Cryptography.CspParameters> nesnesini <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfının oluşturucusuna geçirdiğinizde anahtar kapsayıcısından ada göre otomatik olarak yüklenir.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Diskten bir XML dosyası yükleyerek <xref:System.Xml.XmlDocument> nesnesi oluşturun.  <xref:System.Xml.XmlDocument> nesnesi doğrulamak için imzalanmış XML belgesini içerir.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesnesi oluşturun ve <xref:System.Xml.XmlDocument> nesnesini ona geçirin.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. `signature`> öğesini bulun ve yeni bir <xref:System.Xml.XmlNodeList> nesnesi oluşturun.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. İlk <`signature`> öğesinin XML 'sini <xref:System.Security.Cryptography.Xml.SignedXml> nesnesine yükleyin.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> yöntemini ve RSA ortak anahtarını kullanarak imzayı denetleyin.  Bu yöntem, başarılı veya başarısız olduğunu belirten bir Boole değeri döndürür.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, `"test.xml"` adlı bir dosyanın derlenen programla aynı dizinde olduğunu varsayar.  `"test.xml"` dosyası, [nasıl yapılır: XML belgelerini dijital Imzalarla imzalama](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)bölümünde açıklanan teknikler kullanılarak imzalanmalıdır.  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- Bu örneği derlemek için `System.Security.dll`bir başvuru eklemeniz gerekir.  
  
- Şu ad alanlarını ekleyin: <xref:System.Xml>, <xref:System.Security.Cryptography>ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.  Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Özel anahtarı hiçbir şekilde doğrudan kaynak kodunuza gömmeyin.  Gömülü anahtarlar [ıldadsm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)

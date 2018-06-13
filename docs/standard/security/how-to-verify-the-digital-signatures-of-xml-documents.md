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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b2cb61f2cc7129153a71398c6fb219c4e3990a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590656"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama
Sınıflarda kullanabilirsiniz <xref:System.Security.Cryptography.Xml> XML verileri doğrulamak için ad alanı bir dijital imza ile imzalanmış.  XML dijital imzaları (XMLDSIG) imzalandığından sonra veri değiştirildiği değil olduğunu doğrulamanızı sağlar.  World Wide Web Konsorsiyumu (W3C) belirtimi, XMLDSIG standart hakkında daha fazla bilgi için bkz: http://www.w3.org/TR/xmldsig-core/.  
  
 Bu yordamı kod örneğinde yer alan bir XML dijital imzayı doğrulamak gösterilmiştir bir <`Signature`> öğesi.  Örnek bir RSA ortak anahtarı bir anahtar kapsayıcı alır ve imzayı doğrulamak için anahtarı kullanır.  
  
 Bu teknik kullanılarak doğrulanabilir bir dijital imza oluşturma hakkında bilgi için bkz: [nasıl yapılır: oturum XML belgelerini dijital imzalarla](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Bir XML belgesinin dijital imzasını doğrulamak için  
  
1.  Belgeyi doğrulamak için imzalama için kullanılan aynı asimetrik anahtar kullanmanız gerekir.  Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve imzalama için kullanılan anahtar kapsayıcı adını belirtin.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  Ortak anahtar kullanarak almak <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.  Geçirdiğiniz anahtarı otomatik olarak anahtar kapsayıcı adıyla yüklenir <xref:System.Security.Cryptography.CspParameters> oluşturucusunun nesnesine <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.  <xref:System.Xml.XmlDocument> Nesne doğrulamak için imzalanmış XML belgesi içeriyor.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesne ve geçirin <xref:System.Xml.XmlDocument> nesnesiyle.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  Bul <`signature`> öğesi ve yeni bir <xref:System.Xml.XmlNodeList> nesnesi.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  İlk XML yük <`signature`> öğesinin içine <xref:System.Security.Cryptography.Xml.SignedXml> nesnesi.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  Kullanarak imza denetimi <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> yöntemi ve RSA ortak anahtar.  Bu yöntem, başarı veya başarısızlık gösteren bir Boole değeri döndürür.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dosya adlı varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.  `"test.xml"` Açıklanan teknikleri kullanarak dosya imzalanmalıdır [nasıl yapılır: oturum XML belgelerini dijital imzalarla](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örneği derlemek için bir başvuru eklemeniz gerekir `System.Security.dll`.  
  
-   Şu ad alanlarından içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Hiçbir zaman depolamak veya asimetrik anahtar çifti düz metin olarak özel anahtarı aktarın.  Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz: [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Hiçbir zaman bir özel anahtar kaynak kodunuza doğrudan ekleyin.  Katıştırılmış anahtarları kullanarak bir derlemeye ait kolayca da okunabilir [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Cryptography.Xml>  
 [Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)

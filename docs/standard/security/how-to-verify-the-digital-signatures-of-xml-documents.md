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
ms.openlocfilehash: 9ec813e50bb4dca33c8dda8b41914cfa5d5596c2
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537244"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama
Sınıfları kullanabilirsiniz <xref:System.Security.Cryptography.Xml> XML verileri doğrulamak için ad alanı bir dijital imza ile imzalanmış.  XML dijital imzaları (XMLDSIG) imzalandıktan sonra veri değiştirilmiş değil olduğunu doğrulamanızı sağlar.  World Wide Web Consortium (W3C) belirtimi, XMLDSIG standart hakkında daha fazla bilgi için bkz http://www.w3.org/TR/xmldsig-core/.  
  
 Bu yordam kod örneğinde yer alan bir XML dijital imzayı doğrulamak gösterilmiştir bir <`Signature`> öğesi.  Örnek, RSA ortak anahtarı bir anahtar kapsayıcısından alır ve ardından imzayı doğrulamak için anahtar kullanır.  
  
 Bu teknik kullanılarak doğrulanabilir bir dijital imza oluşturma hakkında bilgi için bkz: [nasıl yapılır: oturum XML belgelerini dijital imzalarla](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Bir XML belgesinin dijital imzasını doğrulamak için  
  
1.  Belgeyi doğrulamak için imzalama için kullanılan aynı asimetrik anahtar kullanmanız gerekir.  Oluşturma bir <xref:System.Security.Cryptography.CspParameters> nesne ve imzalama için kullanılan anahtar kapsayıcısı adını belirtin.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  Ortak anahtarınızı kullanarak almak <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.  Geçirdiğiniz anahtarı otomatik olarak anahtar kapsayıcısından adına göre yüklenir <xref:System.Security.Cryptography.CspParameters> nesnesi oluşturucusuna <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  Oluşturma bir <xref:System.Xml.XmlDocument> diskten bir XML dosyası yüklenirken nesne.  <xref:System.Xml.XmlDocument> Doğrulamak için imzalı XML belge nesne içerir.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesne ve geçirin <xref:System.Xml.XmlDocument> nesnesi.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  Bulma <`signature`> öğesi ve yeni bir <xref:System.Xml.XmlNodeList> nesne.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  İlk XML Yükleme <`signature`> öğesine <xref:System.Security.Cryptography.Xml.SignedXml> nesne.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  Kullanarak imza denetimi <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> yöntemi ve RSA ortak anahtarı.  Bu yöntem, başarı veya başarısızlık durumu gösteren bir Boole değeri döndürür.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir dosya olduğunu varsayar `"test.xml"` derlenmiş programın aynı dizinde bulunmaktadır.  `"test.xml"` Açıklanan teknikleri kullanarak dosya imzalanmalıdır [nasıl yapılır: oturum XML belgelerini dijital imzalarla](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örneği derlemeye bir başvuru eklemek gereken `System.Security.dll`.  
  
-   Aşağıdaki ad alanlarını içerir: <xref:System.Xml>, <xref:System.Security.Cryptography>, ve <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Hiçbir zaman depolayabilen veya asimetrik anahtar çifti düz metin olarak özel anahtarı.  Simetrik hem de asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme için anahtarlar oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Hiçbir zaman bir özel anahtar doğrudan sizin kaynak kodunuza ekleyin.  Katıştırılmış anahtarları kullanarak bir derlemeden kolayca da okunabilir [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya Not Defteri gibi bir metin düzenleyicisinde derleme açarak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.Xml>  
- [Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)

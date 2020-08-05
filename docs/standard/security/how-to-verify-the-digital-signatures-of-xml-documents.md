---
title: 'Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSA class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: b9b2dc6a558d1fd6acd2922a7c8ad82ce8776c26
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557053"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama

<xref:System.Security.Cryptography.Xml>Dijital imzayla IMZALANMıŞ XML verilerini doğrulamak için ad alanındaki sınıfları kullanabilirsiniz. XML dijital imzaları (XMLDSIG), imzalandıktan sonra verilerin değiştirilmediğini doğrulamanızı sağlar. XMLDSIG standardı hakkında daha fazla bilgi için, bkz. World Wide Web Konsorsiyumu (W3C) belirtimi <https://www.w3.org/TR/xmldsig-core/> .
  
> [!NOTE]
> Bu makaledeki kod Windows için geçerlidir.

Bu yordamdaki kod örneği, bir <> öğesinde bulunan bir XML dijital imzasının nasıl doğrulandığını gösterir `Signature` .  Örnek, anahtar kapsayıcısından bir RSA ortak anahtarı alır ve ardından imzayı doğrulamak için anahtarı kullanır.  
  
Bu tekniği kullanarak doğrulanabilen dijital imza oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML belgelerini dijital Imzalarla imzalama](how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Bir XML belgesinin dijital imzasını doğrulamak için  
  
1. Belgeyi doğrulamak için, imzalama için kullanılan asimetrik anahtarı kullanmanız gerekir.  Bir <xref:System.Security.Cryptography.CspParameters> nesne oluşturun ve imzalanmak üzere kullanılan anahtar kapsayıcısının adını belirtin.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Sınıfını kullanarak ortak anahtarı alın <xref:System.Security.Cryptography.RSACryptoServiceProvider> .  Bu anahtar, nesneyi sınıfının oluşturucusuna geçirdiğinizde anahtar kapsayıcısından ada göre otomatik olarak yüklenir <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> .  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.  <xref:System.Xml.XmlDocument>Nesne doğrulanacak olan IMZALANMıŞ XML belgesini içeriyor.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesne oluşturun ve <xref:System.Xml.XmlDocument> nesneyi buna geçirin.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <`signature`> öğesini bulun ve yeni bir nesne oluşturun <xref:System.Xml.XmlNodeList> .  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. İlk <`signature`> ÖĞESININ XML 'sini <xref:System.Security.Cryptography.Xml.SignedXml> nesnesine yükleyin.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A>Yöntemi ve RSA ortak anahtarını kullanarak imzayı denetleyin.  Bu yöntem, başarılı veya başarısız olduğunu belirten bir Boole değeri döndürür.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Örnek

Bu örnek, adlı bir dosyanın `"test.xml"` derlenen programla aynı dizinde bulunduğunu varsayar.  Bu `"test.xml"` Dosya, [nasıl yapılır: XML belgelerini dijital Imzalarla imzalama](how-to-sign-xml-documents-with-digital-signatures.md)bölümünde açıklanan teknikler kullanılarak imzalanmalıdır.  
  
[!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
[!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- .NET Framework hedefleyen bir projede, öğesine bir başvuru ekleyin `System.Security.dll` .

- .NET Core veya .NET 5 ' i hedefleyen bir projede NuGet paketi [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)' yi yükler.
  
- Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-security"></a>.NET güvenliği

Asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.  Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](generating-keys-for-encryption-and-decryption.md).  
  
Özel anahtarı hiçbir şekilde doğrudan kaynak kodunuza gömmeyin.  Katıştırılmış anahtarlar [Ildasm.exe (Il ayrıştırma)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Modeli](cryptography-model.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama](how-to-sign-xml-documents-with-digital-signatures.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)

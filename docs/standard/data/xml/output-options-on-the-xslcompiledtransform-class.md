---
title: XslCompiledTransform Sınıfındaki Çıkış Seçenekleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
ms.openlocfilehash: 504057bd5e10498d39b2bce908742fc20b112c52
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710511"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>XslCompiledTransform Sınıfındaki Çıkış Seçenekleri
Bu konu başlığı altında, kullanılabilir XSLT çıkış seçenekleri açıklanmaktadır. Stil sayfasında veya <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yönteminde çıkış seçeneklerini belirtebilirsiniz.  
  
## <a name="xsloutput-element"></a>xsl: output öğesi  
 `xsl:output` öğesi çıkışın seçeneklerini belirtir. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi tarafından belirtilen çıkış türü `xsl:output` seçeneklerinin davranışını belirler.  
  
 Aşağıdaki tabloda, çıkış türü bir Stream veya <xref:System.IO.TextWriter>olduğunda `xsl:output` öğesinde kullanılabilen özniteliklerin her biri için davranış açıklanmaktadır.  
  
|Öznitelik adı|Davranış|  
|--------------------|--------------|  
|{1&gt; yöntemi&lt;1}|Desteklenen.|  
|sürümü|LIP. Sürüm, her zaman için 1,0 for XML ve HTML için 4,0 ' dir.|  
|{1&gt;encoding&lt;1}|Bir <xref:System.IO.TextWriter>çıktısı alırken yok sayılır. Bunun yerine <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> özelliği kullanılır.|  
|{1&gt;atlayın-xml-bildirimi&lt;1}|Desteklenen.|  
|tek başına|Desteklenen.|  
|doctype-genel|Desteklenen.|  
|DOCTYPE-System|Desteklenen.|  
|CDATA-bölüm-öğeler|Desteklenen.|  
|{1&gt;Girinti&lt;1}|Desteklenen.|  
|{1&gt;medya türü&lt;1}|Desteklenen.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Bir XmlWriter 'a çıkış gönderme  
 Stil sayfanızda `xsl:output` öğesi kullanılıyorsa ve çıkış türü bir <xref:System.Xml.XmlWriter> nesnesi ise, <xref:System.Xml.XmlWriter> nesnesini oluştururken <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> özelliğini kullanmanız gerekir. <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> özelliği, derlenmiş bir stil sayfasının `xsl:output` öğesinden türetilmiş bilgiler içeren bir <xref:System.Xml.XmlWriterSettings> nesnesi döndürür. Bu <xref:System.Xml.XmlWriterSettings> nesnesi, doğru ayarlarla bir <xref:System.Xml.XmlWriter> nesnesi oluşturmak için <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> yöntemine geçirilebilir.  
  
## <a name="output-types"></a>Çıkış türleri  
 Aşağıdaki liste <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> komutunda bulunan çıkış türlerini açıklar.  
  
#### <a name="xmlwriter"></a>Işleyemez  
 <xref:System.Xml.XmlWriter> sınıfı, XML akışlarını veya dosyalarını yazar. <xref:System.Xml.XmlWriterSettings> sınıfını kullanarak, çıkış seçenekleri de dahil olmak üzere <xref:System.Xml.XmlWriter> nesnesinde destekedilecek özellikleri belirtebilirsiniz. <xref:System.Xml.XmlWriter> sınıfı, <xref:System.Xml> çerçevesinin ayrılmaz bir parçasıdır. Bu çıktı türünü, çıkış sonuçlarının başka bir XML işlemine göre işlem hattını kullanarak kullanın.  
  
#### <a name="string"></a>Dize  
 Çıkış dosyasının URI 'sini belirtmek için bu çıkış türünü kullanın.  
  
#### <a name="stream"></a>Akış  
 Akış, bir dosya, giriş/çıkış aygıtı, işlem içi iletişim kanalı veya TCP/IP yuvası gibi bir bayt dizisinin soyutlamasıdır. <xref:System.IO.Stream> sınıfı ve onun türetilmiş sınıfları, bu farklı giriş ve çıkış türlerinin genel bir görünümünü sağlar ve bu da programcı 'yı işletim sisteminin ve temel cihazların belirli ayrıntılarından yalılar.  
  
 <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>veya çıkış akışına (`Response.OutputStream`) veri göndermek için bu çıkış türünü kullanın.  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter> sıralı karakterler yazar. Sırasıyla dizelere veya akışlara karakter yazan <xref:System.IO.StringWriter> ve <xref:System.IO.StreamWriter> sınıflarında uygulanır. Bir dizeye çıkış yapmak istediğinizde bu çıkış türünü kullanın.  
  
## <a name="notes"></a>Notlar  
  
- Boş Etiketler yazılırken, öğe adının son karakteri ve ters eğik çizgi arasına bir boşluk yazılır, örneğin `<myElement />`. Bu, daha eski tarayıcıların oluşturulan HTML sayfalarını doğru görüntülemesini sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)

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
 `xsl:output` Öğesi çıktının seçeneklerini belirtir. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Yöntemi tarafından belirtilen çıkış türü, `xsl:output` seçeneklerin davranışını belirler.  
  
 Aşağıdaki tabloda, çıkış türü bir Stream veya a `xsl:output` <xref:System.IO.TextWriter>olduğunda, öğesinde bulunan her bir özniteliklerin davranışı açıklanmaktadır.  
  
|Öznitelik adı|Davranış|  
|--------------------|--------------|  
|method|Destekleniyor.|  
|version|LIP. Sürüm, her zaman için 1,0 for XML ve HTML için 4,0 ' dir.|  
|encoding|Bir <xref:System.IO.TextWriter>öğesine çıktısı oluşturulurken yok sayılır. Bunun <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> yerine özelliği kullanılır.|  
|XML bildirimini atla|Destekleniyor.|  
|bağımsız|Destekleniyor.|  
|doctype-genel|Destekleniyor.|  
|DOCTYPE-System|Destekleniyor.|  
|CDATA-bölüm-öğeler|Destekleniyor.|  
|leyebilirsiniz|Destekleniyor.|  
|medya türü|Destekleniyor.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Bir XmlWriter 'a çıkış gönderme  
 Stil sayfanızda `xsl:output` öğesi kullanılıyorsa ve çıkış türü bir <xref:System.Xml.XmlWriter> nesnedir, <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> <xref:System.Xml.XmlWriter> nesneyi oluştururken özelliğini kullanmanız gerekir. Özelliği <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> , derlenmiş bir <xref:System.Xml.XmlWriterSettings> stil sayfası `xsl:output` öğesinden türetilmiş bilgiler içeren bir nesnesi döndürür. Bu <xref:System.Xml.XmlWriterSettings> nesne, <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> doğru ayarlarla bir <xref:System.Xml.XmlWriter> nesne oluşturmak için yöntemine geçirilebilir.  
  
## <a name="output-types"></a>Çıkış türleri  
 Aşağıdaki listede, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> komutta bulunan çıkış türleri açıklanmaktadır.  
  
#### <a name="xmlwriter"></a>Işleyemez  
 Sınıfı <xref:System.Xml.XmlWriter> , XML akışlarını veya dosyalarını yazar. Sınıfını kullanarak, çıktı seçenekleri de dahil olmak üzere <xref:System.Xml.XmlWriter> , nesne üzerinde destekedilecek özellikleri belirtebilirsiniz. <xref:System.Xml.XmlWriterSettings> <xref:System.Xml.XmlWriter> Sınıfı, <xref:System.Xml> çerçevesinin integral bir parçasıdır. Bu çıktı türünü, çıkış sonuçlarının başka bir XML işlemine göre işlem hattını kullanarak kullanın.  
  
#### <a name="string"></a>Dize  
 Çıkış dosyasının URI 'sini belirtmek için bu çıkış türünü kullanın.  
  
#### <a name="stream"></a>Akış  
 Akış, bir dosya, giriş/çıkış aygıtı, işlem içi iletişim kanalı veya TCP/IP yuvası gibi bir bayt dizisinin soyutlamasıdır. <xref:System.IO.Stream> Sınıfı ve onun türetilmiş sınıfları, bu farklı giriş ve çıkış türlerinin genel bir görünümünü sağlar ve bu da programcı 'yı işletim sisteminin ve temel cihazların belirli ayrıntılarından yalılar.  
  
 Bir <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>veya çıkış akışına (`Response.OutputStream`) veri göndermek için bu çıkış türünü kullanın.  
  
#### <a name="textwriter"></a>TextWriter  
 Sıralı <xref:System.IO.TextWriter> karakterler yazar. Sırasıyla dizelere veya akışlara <xref:System.IO.StringWriter> karakter <xref:System.IO.StreamWriter> yazan ve sınıflarında uygulanır. Bir dizeye çıkış yapmak istediğinizde bu çıkış türünü kullanın.  
  
## <a name="notes"></a>Notlar  
  
- Boş Etiketler yazılırken, öğe adının son karakteri ve ters eğik çizgi `<myElement />` arasına bir boşluk yazılır; örneğin. Bu, daha eski tarayıcıların oluşturulan HTML sayfalarını doğru görüntülemesini sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)

---
title: XslCompiledTransform sınıfındaki çıkış seçenekleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 694d2be51d025ab054caf19e4aa2900216ad5b2e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183492"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>XslCompiledTransform sınıfındaki çıkış seçenekleri
Bu konu başlığı altında kullanılabilir XSLT çıkış seçenekleri açıklanır. Stil sayfası veya üzerinde çıkış seçenekleri belirtebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.  
  
## <a name="xsloutput-element"></a>önceliğiyle öğesi  
 `xsl:output` Öğesi çıktı seçeneklerini belirtir. Çıktı türü tarafından belirtilen <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi davranışını belirler `xsl:output` seçenekleri.  
  
 Aşağıdaki tabloda bulunan özniteliklerin her biri için davranışını tanımlar. `xsl:output` bir akış çıktı türü olduğunda, öğe veya <xref:System.IO.TextWriter>.  
  
|Öznitelik adı|Davranış|  
|--------------------|--------------|  
|yöntemi|Desteklenen.|  
|sürüm|Yoksayıldı. Her zaman 1.0 için XML ve HTML 4.0 sürümüdür.|  
|encoding|İçin alırken dikkate bir <xref:System.IO.TextWriter>. <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> Özelliği bunun yerine kullanılır.|  
|atlayın-xml-bildirimi|Desteklenen.|  
|bağımsız|Desteklenen.|  
|doctype-genel|Desteklenen.|  
|Sistem dışı doctype|Desteklenen.|  
|CDATA bölümü öğeleri|Desteklenen.|  
|Girinti|Desteklenen.|  
|medya türü|Desteklenen.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Çıkış için bir XmlWriter gönderme  
 Stil sayfası kullanıyorsa `xsl:output` öğesi ve çıkış türü bir <xref:System.Xml.XmlWriter> nesne kullanmanız gerektiğini <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> oluşturduğunuzda özelliği <xref:System.Xml.XmlWriter> nesne. <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Xml.XmlWriterSettings> bilgi içeren nesne türetilen `xsl:output` öğesi bir derlenmiş bir stil sayfası. Bu <xref:System.Xml.XmlWriterSettings> nesne geçilebilir <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> yöntemi oluşturmak için bir <xref:System.Xml.XmlWriter> doğru ayarlarla nesne.  
  
## <a name="output-types"></a>Çıktı türleri  
 Aşağıdaki listede bulunan çıktı türleri açıklanmaktadır <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> komutu.  
  
#### <a name="xmlwriter"></a>XmlWriter  
 <xref:System.Xml.XmlWriter> Sınıfı, XML akışlarını veya dosyaları yazar. Destek almak için özellikleri belirtebilirsiniz <xref:System.Xml.XmlWriter> kullanarak çıkış seçenekleri dahil olmak üzere nesne <xref:System.Xml.XmlWriterSettings> sınıfı. <xref:System.Xml.XmlWriter> Sınıfı bir parçası olan <xref:System.Xml> framework. Bu çıkış türü, çıktı sonuçları başka bir XML işleme işlem hattı için kullanın.  
  
#### <a name="string"></a>Dize  
 Çıkış dosyasının URI belirtmek için bu çıktı türünü kullanın.  
  
#### <a name="stream"></a>Akış  
 Bir akış, bir dosya, bir giriş/çıkış cihaz, bir işlemler arası iletişim kanalı ya da bir TCP/IP yuva gibi bir bayt dizisi bir soyutlamadır. <xref:System.IO.Stream> Sınıfı ve türetilmiş sınıflarının girdi ve çıktı, işletim sistemi ve temel alınan cihazlar belirli ayrıntılarından Programcı yalıtma, bu farklı türde genel bir görünümünü sağlar.  
  
 Veri göndermek için bu çıktı türü kullanan bir <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, veya bir çıkış akışı (`Response.OutputStream`).  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter> Sıralı karakterler yazar. İçinde uygulanan <xref:System.IO.StringWriter> ve <xref:System.IO.StreamWriter> sınıfları, karakter dizeleri veya akış, sırasıyla yazma. Bu çıkış türü, bir dizeye çıktı istediğinizde kullanın.  
  
## <a name="notes"></a>Notlar  
  
-   Boş etiketleri yazarken, ters eğik çizgi, öğe adı, son karakter arasında bir boşluk yazılır `<myElement />` örneğin. Bu, oluşturulan HTML sayfalarını düzgün görüntülenmesi eski tarayıcılar olanak tanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)

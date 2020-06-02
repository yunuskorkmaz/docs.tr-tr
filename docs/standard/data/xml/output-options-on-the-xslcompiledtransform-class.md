---
title: XslCompiledTransform Sınıfındaki Çıkış Seçenekleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
ms.openlocfilehash: e9ffdc1377dbf124f042802279e7e7a275222eff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288712"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>XslCompiledTransform Sınıfındaki Çıkış Seçenekleri
Bu konu başlığı altında, kullanılabilir XSLT çıkış seçenekleri açıklanmaktadır. Stil sayfasında veya yönteminde çıkış seçeneklerini belirtebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .  
  
## <a name="xsloutput-element"></a>xsl: output öğesi  
 `xsl:output`Öğesi çıktının seçeneklerini belirtir. Yöntemi tarafından belirtilen çıkış türü, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> seçeneklerin davranışını belirler `xsl:output` .  
  
 Aşağıdaki tabloda, `xsl:output` Çıkış türü bir Stream veya a olduğunda, öğesinde bulunan her bir özniteliklerin davranışı açıklanmaktadır <xref:System.IO.TextWriter> .  
  
|Öznitelik adı|Davranış|  
|--------------------|--------------|  
|method|Destekleniyor.|  
|sürüm|LIP. Sürüm, her zaman için 1,0 for XML ve HTML için 4,0 ' dir.|  
|encoding|Bir öğesine çıktısı oluşturulurken yok sayılır <xref:System.IO.TextWriter> . <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType>Bunun yerine özelliği kullanılır.|  
|XML bildirimini atla|Destekleniyor.|  
|bağımsız|Destekleniyor.|  
|doctype-genel|Destekleniyor.|  
|DOCTYPE-System|Destekleniyor.|  
|CDATA-bölüm-öğeler|Destekleniyor.|  
|leyebilirsiniz|Destekleniyor.|  
|medya türü|Destekleniyor.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Bir XmlWriter 'a çıkış gönderme  
 Stil sayfanızda `xsl:output` öğesi kullanılıyorsa ve çıkış türü bir <xref:System.Xml.XmlWriter> nesnedir, <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> nesneyi oluştururken özelliğini kullanmanız gerekir <xref:System.Xml.XmlWriter> . <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType>Özelliği, <xref:System.Xml.XmlWriterSettings> `xsl:output` derlenmiş bir stil sayfası öğesinden türetilmiş bilgiler içeren bir nesnesi döndürür. Bu <xref:System.Xml.XmlWriterSettings> nesne, <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> doğru ayarlarla bir nesne oluşturmak için yöntemine geçirilebilir <xref:System.Xml.XmlWriter> .  
  
## <a name="output-types"></a>Çıkış türleri  
 Aşağıdaki listede, komutta bulunan çıkış türleri açıklanmaktadır <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .  
  
#### <a name="xmlwriter"></a>Işleyemez  
 <xref:System.Xml.XmlWriter>Sınıfı, XML akışlarını veya dosyalarını yazar. <xref:System.Xml.XmlWriter>Sınıfını kullanarak, çıktı seçenekleri de dahil olmak üzere, nesne üzerinde destekedilecek özellikleri belirtebilirsiniz <xref:System.Xml.XmlWriterSettings> . <xref:System.Xml.XmlWriter>Sınıfı, çerçevesinin integral bir parçasıdır <xref:System.Xml> . Bu çıktı türünü, çıkış sonuçlarının başka bir XML işlemine göre işlem hattını kullanarak kullanın.  
  
#### <a name="string"></a>Dize  
 Çıkış dosyasının URI 'sini belirtmek için bu çıkış türünü kullanın.  
  
#### <a name="stream"></a>Akış  
 Akış, bir dosya, giriş/çıkış aygıtı, işlem içi iletişim kanalı veya TCP/IP yuvası gibi bir bayt dizisinin soyutlamasıdır. <xref:System.IO.Stream>Sınıfı ve onun türetilmiş sınıfları, bu farklı giriş ve çıkış türlerinin genel bir görünümünü sağlar ve bu da programcı 'yı işletim sisteminin ve temel cihazların belirli ayrıntılarından yalılar.  
  
 Bir <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> veya çıkış akışına () veri göndermek için bu çıkış türünü kullanın `Response.OutputStream` .  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter>Sıralı karakterler yazar. <xref:System.IO.StringWriter> <xref:System.IO.StreamWriter> Sırasıyla dizelere veya akışlara karakter yazan ve sınıflarında uygulanır. Bir dizeye çıkış yapmak istediğinizde bu çıkış türünü kullanın.  
  
## <a name="notes"></a>Notlar  
  
- Boş Etiketler yazılırken, öğe adının son karakteri ve ters eğik çizgi arasına bir boşluk yazılır; `<myElement />` Örneğin. Bu, daha eski tarayıcıların oluşturulan HTML sayfalarını doğru görüntülemesini sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](xslt-transformations.md)

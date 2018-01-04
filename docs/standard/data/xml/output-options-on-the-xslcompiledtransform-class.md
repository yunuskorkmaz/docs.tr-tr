---
title: "Çıkış seçenekleri XslCompiledTransform sınıfı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84171c92a56a9970b5ffc16ce8f30c85d61cc678
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>Çıkış seçenekleri XslCompiledTransform sınıfı
Bu konuda kullanılabilir XSLT çıkış seçenekleri açıklanmaktadır. Stil sayfası içinde veya üzerinde çıkış seçenekleri belirtebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.  
  
## <a name="xsloutput-element"></a>önceliğiyle öğesi  
 `xsl:output` Öğesi çıktı seçeneklerini belirtir. Belirtilen çıktı türü <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi davranışını belirler `xsl:output` seçenekleri.  
  
 Aşağıdaki tabloda, her kullanılabilir özniteliklerin davranışını tanımlar. `xsl:output` çıktı türü bir akış olduğunda öğesi veya <xref:System.IO.TextWriter>.  
  
|Öznitelik adı|Davranış|  
|--------------------|--------------|  
|yöntemi|Desteklenen.|  
|sürüm|Yoksayıldı. Her zaman XML 1.0 ve HTML 4.0 sürümüdür.|  
|encoding|İçin alırken göz ardı bir <xref:System.IO.TextWriter>. <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> Özelliğinin yerine kullanılır.|  
|atlayın-xml-bildirimi|Desteklenen.|  
|bağımsız|Desteklenen.|  
|doctype-genel|Desteklenen.|  
|Sistem dışı doctype|Desteklenen.|  
|CDATA bölümü öğeleri|Desteklenen.|  
|Girinti|Desteklenen.|  
|medya türü|Desteklenen.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Çıkış için bir XmlWriter gönderme  
 Stil sayfası kullanıyorsa `xsl:output` öğesi ve çıkış türü bir <xref:System.Xml.XmlWriter> nesnesi, kullanmanız gereken <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> oluşturduğunuzda özelliği <xref:System.Xml.XmlWriter> nesnesi. <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Xml.XmlWriterSettings> bilgi içeren nesne türetilen `xsl:output` derlenmiş stil sayfası öğesidir. Bu <xref:System.Xml.XmlWriterSettings> nesne için geçirilebilir <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> yöntemi oluşturmak için bir <xref:System.Xml.XmlWriter> doğru ayarlarla nesnesi.  
  
## <a name="output-types"></a>Çıktı türleri  
 Kullanılabilir çıktı türleri aşağıdaki listede açıklanmaktadır <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> komutu.  
  
#### <a name="xmlwriter"></a>XmlWriter  
 <xref:System.Xml.XmlWriter> Sınıfı XML akışları veya dosyaları yazar. Destek almak için özellikleri belirtebilirsiniz <xref:System.Xml.XmlWriter> nesnesi kullanarak çıkış seçenekleri de dahil olmak üzere, <xref:System.Xml.XmlWriterSettings> sınıfı. <xref:System.Xml.XmlWriter> Sınıftır bütünleyici <xref:System.Xml> framework. Bu çıktı türü çıkış sonuçları kanalı başka bir XML işlemi için kullanın.  
  
#### <a name="string"></a>Dize  
 Çıktı dosyası URI'sini belirtmek için bu çıktı türü kullanın.  
  
#### <a name="stream"></a>Akış  
 Bir dosya, bir giriş/çıkış cihaz, bir işlemler arası iletişim kanalı ya da bir TCP/IP'yi yuva gibi bayt dizisi için bir Özet akışıdır. <xref:System.IO.Stream> Sınıfı ve türetilmiş sınıflarının giriş ve çıkış, işletim sistemi ve arka plandaki cihazların belirli ayrıntıları Programcı yalıtma farklı bu tür genel bir görünümünü sağlar.  
  
 Veri göndermesini Bu çıktı türü kullanan bir <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, veya bir çıktı akışına (`Response.OutputStream`).  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter> Sıralı karakterleri yazar. Şu uygulanan <xref:System.IO.StringWriter> ve <xref:System.IO.StreamWriter> karakter dizeleri veya akışlar, sırasıyla yazma sınıfları. Bir dizeyi çıktı istediğinizde bu çıktı türü kullanın.  
  
## <a name="notes"></a>Notlar  
  
-   Boş etiketleri yazarken, ters eğik çizgi, öğe adı son karakter arasında bir boşluk yazılır `<myElement />` örneğin. Bu eski tarayıcılar oluşturulan HTML sayfaları doğru görüntülemesini sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)

---
title: Bir belge içine katıştırılmış stil sayfası yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fa671304c611db571b160cd1d960b83bf451c9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Bir belge içine katıştırılmış stil sayfası yönergeleri
Bazen, stil sayfası yönergesinde varolan XML içeriyor `<?xml:stylesheet?>`. Microsoft Internet Explorer alternatif olarak bu kabul `<?xml-stylesheet?>` sözdizimi. XML veri içerdiğinde bir `<?xml:stylesheet?>` yönerge, aşağıdaki veri gösterildiği gibi bu verileri XML belge nesne modeli (DOM) içine yüklemeyi denerken bir özel durum oluşturur.  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 Bu kaynaklanır `<?xml:stylesheet?>` geçersiz olarak kabul **instruction** DOM için Tüm **instruction**, ad alanları XML belirtiminde göre Hayır iki nokta üst üste adları (NCNames) yalnızca olabilir, aksine nitelenmiş adlar (QNames).  
  
 Ad alanı XML belirtiminde sahip etkisini Bölüm 6'dan **yük** ve **LoadXml** yöntemleri uygun belirtimi olan bir belgede:  
  
-   Tüm öğesi türleri ve öznitelik adları sıfır veya bir iki nokta üst üste içerir.  
  
-   Hiçbir varlık adları, instruction hedefler ya da gösterim adları herhangi iki nokta üst üste içerir.  
  
 İle `<?xml:stylesheet?>` bir iki nokta üst üste içeren, artık ikinci madde işareti kuralında ihlal ediyor.  
  
 World Wide Web Konsorsiyumu (W3C) ilişkilendirme stil sayfaları www.w3.org/TR/xml-stylesheet bulunan XML belgeleri sürüm 1.0 öneri ile göre XSLTstilsayfasınıbirXMLbelgesiileilişkilendirmekiçinişlemyönergesiolup`<?xml-stylesheet?>`, iki nokta üst üste değiştirerek bir tire ile.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

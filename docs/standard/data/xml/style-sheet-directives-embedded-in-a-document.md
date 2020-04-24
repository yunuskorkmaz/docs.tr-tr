---
title: Belgeye Katıştırılmış Stil Sayfası Yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 19e25ab7262bb006144eea71e74bd7454066b3f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710160"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Belgeye Katıştırılmış Stil Sayfası Yönergeleri

Bazen varolan XML, öğesinin `<?xml:stylesheet?>`stil sayfası yönergesini içerir. Microsoft Internet Explorer, `<?xml-stylesheet?>` söz dizimini bir alternatif olarak kabul eder. XML verileri aşağıdaki verilerde gösterildiği gibi `<?xml:stylesheet?>` bir yönerge içerdiğinde, bu verileri XML belge nesne modeli yüklemeye ÇALıŞMAK (DOM) bir özel durum oluşturur.

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

Bunun nedeni, `<?xml:stylesheet?>` Dom için geçersiz bir **processingyönergesini** kabul ettiğinden oluşur. XML belirtiminde ad alanlarına göre herhangi bir işlem **yönergesi**, nitelenmiş adların (QNames 'ler) aksine yalnızca iki nokta üst üste olmayan adlar (NCNames) olabilir.

XML belirtiminde ad alanlarının 6. bölümünde, **Load** ve **LoadXml** yöntemlerine sahip olmanın etkisi bir belgede olur:

- Tüm öğe türleri ve öznitelik adları sıfır veya bir iki nokta üst üste içerir.

- Hiçbir varlık adı, Işleme yönergesi hedefi veya gösterim adı herhangi bir iki nokta üst üste içermez.

İki nokta `<?xml:stylesheet?>` üst üste içeren, artık kuralı ikinci madde işaretiyle ihlal edersiniz.

World Wide Web Konsorsiyumu (W3C) [Ile xml belgelerinin sürüm 1,0 önerisi Ile ilişkilendirme](https://www.w3.org/TR/xml-stylesheet/), XSLT stil SAYFASıNı bir XML belgesi `<?xml-stylesheet?>`ile ilişkilendirmek için işleme yönergesi, iki nokta üst üste yerine bir tire ile.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)

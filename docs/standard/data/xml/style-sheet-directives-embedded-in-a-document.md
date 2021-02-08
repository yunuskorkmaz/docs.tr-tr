---
description: 'Daha fazla bilgi edinin: bir belgeye katıştırılmış stil sayfası yönergeleri'
title: Belgeye Katıştırılmış Stil Sayfası Yönergeleri
ms.date: 03/30/2017
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 3585cc2f9e7d931a89c1f81283282712195720f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782942"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Belgeye Katıştırılmış Stil Sayfası Yönergeleri

Bazen varolan XML, öğesinin stil sayfası yönergesini içerir `<?xml:stylesheet?>` . Microsoft Internet Explorer, söz dizimini bir alternatif olarak kabul eder `<?xml-stylesheet?>` . XML verileri `<?xml:stylesheet?>` aşağıdaki verilerde gösterildiği gibi bir yönerge içerdiğinde, bu VERILERI XML belge nesne modeli yüklemeye çalışmak (DOM) bir özel durum oluşturur.

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

`<?xml:stylesheet?>`İki nokta üst üste içeren, artık kuralı ikinci madde işaretiyle ihlal edersiniz.

World Wide Web Konsorsiyumu (W3C) [Ile xml belgelerinin sürüm 1,0 önerisi Ile ilişkilendirme](https://www.w3.org/TR/xml-stylesheet/), XSLT stil SAYFASıNı bir XML belgesi ile ilişkilendirmek için işleme yönergesi, `<?xml-stylesheet?>` iki nokta üst üste yerine bir tire ile.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)

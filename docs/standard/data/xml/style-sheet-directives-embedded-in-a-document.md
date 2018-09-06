---
title: Belgeye katıştırılmış stil sayfası yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65987c5e29d593758b21259d6367202c882df2de
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43882920"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Belgeye katıştırılmış stil sayfası yönergeleri

Bazen, var olan XML stil sayfası yönergesi içeren `<?xml:stylesheet?>`. Microsoft Internet Explorer alternatif olarak bu kabul `<?xml-stylesheet?>` söz dizimi. XML verilerini içerdiğinde bir `<?xml:stylesheet?>` yönerge, aşağıdaki veriler gösterildiği gibi XML belge nesne modeli (DOM) içine bu verileri yüklemeye çalışırken bir özel durum oluşturur.

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

Bu durum oluşur `<?xml:stylesheet?>` geçersiz olarak kabul edilir **instruction** yerli için Tüm **instruction**, ad alanları XML belirtiminde göre no-iki nokta üst üste adları (NCNames) yalnızca olabilir, yerine tam adları (QNames).

Bölüm 6 ad alanları XML belirtiminde olan etkisini **yük** ve **LoadXml** yöntemleri uygun belirtimi bir belgede olmasıdır:

- Tüm öğe türleri ve öznitelik adları sıfır veya bir iki nokta üst üste içerir.

- Herhangi iki nokta üst üste, hiçbir varlık adları, instruction hedefler ya da bildirim adları içeriyor.

İle `<?xml:stylesheet?>` bir iki nokta üst üste içeren, Şimdi ikinci madde işareti kuralı ihlal ediyor.

World Wide Web Consortium (W3C) göre [XML ile ilişkilendirme stil sayfaları, sürüm 1.0 öneri belgeleri](https://www.w3.org/TR/xml-stylesheet/), bir XSLT stil sayfası bir XML belgesi ile ilişkilendirmek için işleme yönergesi `<?xml-stylesheet?>`, ile bir iki nokta üst üste değiştirerek dash.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)

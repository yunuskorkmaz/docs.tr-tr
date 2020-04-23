---
title: XAML'de xml:space İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071439"
---
# <a name="xmlspace-handling-in-xaml"></a>XAML'de xml:space İşleme

Öznitelik, `xml:space` nesne öğesi içindeki önemli beyaz boşluk işleme davranışını bildiren XML tanımlı bir özniteliktir. Bu davranış, bildirilen öğe `xml:space` içinde bulunan tüm içerik (iç metin) için alakalı ve aynı zamanda alt öğeleri kapsamları.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object xml:space="preserve" />
```

 \-veya -

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a>Açıklamalar

XAML'deki iki olası değeri içeren öznitelik `xml:space` tanımı, `xml:space` XML için W3C belirtimleri tarafından "özel öznitelik" olarak tanımlanan tanımdan türetilmiştir.

Özniteliğin `xml:space` varsayılan değeri gerçek değerdir. `"default"` Değer `"default"`için, ya `xml:space` da hiç belirtilmediyse, önemli beyaz boşluk ayrıştırma davranışı, [XAML'de](white-space-processing.md)beyaz alan işleme konusunda tanımlandığı gibi varsayılan işlemedir.

Nesne öğesi içeriğiiçindeki beyaz alanı `xml:space="preserve"` korumak için, bu nesne öğesi üzerinde belirtin.

Çoğu yorumda, `xml:space` öznitelik efektleri ve öznitelik değeri alt öğelere yöneliktir.

XAML'de beyaz alan işleme nin tam bir tartışması için, [XAML'deki Beyaz alan işleme bölümüne](white-space-processing.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML'de Boşluk İşleme](white-space-processing.md)
- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)

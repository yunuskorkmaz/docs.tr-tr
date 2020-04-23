---
title: x:Members Yönergesi
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: c751a4f1cdea8dce7ef5165f5225ab3a825c7344
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071467"
---
# <a name="xmembers-directive"></a>x:Members Yönergesi
Üst öğenin x:Sınıfı için geçerli olan biçimlendirmede tanımlanan bir üye kümesi tutar.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Class="className">
<x:Members>
  oneOrMoreMembers
</x:Members
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`className`|XAML üretimi için destek sınıfının veya kısmi sınıfın adı. Bkz. Açıklamalar.|
|`oneOrMoreMembers`|Üye tanımları temsil eden bir veya daha fazla nesne öğesi. Genellikle, bunlar `x:Property` nesne öğeleridir. Bkz. Açıklamalar.|

## <a name="remarks"></a>Açıklamalar

.NET XAML Hizmetleri uygulamasında, `x:Members`.. `x:Members`herhangi bir türde bir üye olarak var olabilir özel bir XAML üyesidir. Bir XAML düğüm akışında, `x:Members` XAML `Members`dilinden XAML ad alanından bir üye olarak temsil edilir. Üye, `Members` `Member` yalnızca okunan genel nesneler listesini içerir. Tipik biçimlendirmede tek tek `x:Property` üyeler özellik öğeleri olarak belirtilir. `x:Property`türleri özellikleri için özel olarak daha hassas bir `x:Member`türüdür ve atanabilir. Daha fazla bilgi için [bkz: Özellik Yönergesi](xproperty-directive.md).

Biçimlendirmede üye `x:Members` tanımlarını belirtmek için pratik bir kullanım sağlamak için, üyelerin değiştirilebilen bir sınıfla ilişkilendirilmesi gerekir. Amaçlanan model, `x:Members` bir `x:Class`. Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üye tanımları oluşturma mekanizması .NET XAML Hizmetleri düzeyinde desteklenmez. Bu, XAML'den üye tanımlarını destekleyen uygulama modelleri olan tek tek çerçevelere bırakılır. Tipik olarak, MSBUILD, XAML'yi biçimlendirmek ve kod arkası ile tümleştiren veya bu özelliği desteklemek için saf From-XAML derlemeleri üreten eylemler oluşturur.

## <a name="xmembers-for-windows-workflow-foundation"></a>x:Windows İş Akışı Vakfı üyeleri

Windows İş Akışı `x:Members` Temeli için, tamamen XAML veya XAML tanımlı dinamik üyeleri kod arkası olan bir etkinlik tasarımcısı için oluşturulmuş özel bir etkinliğin üyelerini içerir. `x:Class`xaml üretiminin kök elemanı üzerinde de belirtilmelidir. Bu,.NET XAML Hizmetleri düzeyinde bir gereklilik değildir, ancak XAML üretimi MSBUILD yapı eylemleri tarafından yüklendiğinde özel etkinlikleri ve Genel olarak Windows İş Akışı Temeli XAML'yi destekleyen bir gereksinim haline gelir. `x:Members`' yi bildiren nesne öğesinin biçimlendirmesindeki `x:Class`ilk alt öğe olmalıdır.

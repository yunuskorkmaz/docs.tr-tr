---
title: x:Member Yönergesi
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: e82bb6397404ee466a12ab438585ae1898c34d1a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071474"
---
# <a name="xmember-directive"></a>x:Member Yönergesi
Biçimlendirmede bir XAML üyesi bildirir.

## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`className`|XAML üretimi için destek sınıfının veya kısmi sınıfın adı.|
|`memberName`|Tanımlanan özelliğin üye adı.|

## <a name="remarks"></a>Açıklamalar

.NET XAML Hizmetleri uygulamasında, . `x:Member`doğrudan bir tür desteği yoktur, ancak <xref:System.Windows.Markup.MemberDefinition> sınıf tarafından desteklenir. XAML düğümü akışında, `x:Member` xaml dilinden xaml ad alanından bir öğe, xaml adı alan bir `Member`üye olarak temsil edilir. Üye, `Member` biçimlendirme tarafından beyan edildiği gibi öznitelikleri tutar.

.NET `Name` XAML Hizmetleri düzeyinde atanır ve `Type` atanır. Bunlar, daha sonra belirli çerçeveler tarafından empoze edilebilir kurallar altında yorumlanacak, dize değerleri olarak ilk XAML düğüm akışında depolanır. Anlam, xaml adı ve XAML türü anlamı ile hizalanabilir veya uygulamaya bağlı olarak yalnızca bir destek türü sisteminde geçerli olabilir.

Biçimlendirmede üye `x:Members` tanımlarını belirtmek için pratik bir kullanım sağlamak için, üyelerin değiştirilebilen bir sınıfla ilişkilendirilmesi gerekir. Amaçlanan model, `x:Members` bir `x:Class`. Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üye tanımları oluşturma mekanizması .NET XAML Hizmetleri düzeyinde desteklenmez. Bu, XAML'den üye tanımlarını destekleyen uygulama modelleri olan tek tek çerçevelere bırakılır. Tipik olarak, MSBUILD, XAML'yi biçimlendirmek ve kod arkası ile tümleştiren veya bu özelliği desteklemek için saf From-XAML derlemeleri üreten eylemler oluşturur.

## <a name="xproperty-for-windows-workflow-foundation"></a>x:Windows İş Akışı Temeli için özellik

Windows İş Akışı `x:Property` Temeli için, tamamen XAML veya XAML tanımlı dinamik üyeleri kod arkası olan bir etkinlik tasarımcısı için oluşturulan özel bir etkinliğin üyelerini tanımlar. `x:Class`xaml üretiminin kök elemanı üzerinde de belirtilmelidir. Bu,.NET XAML Hizmetleri düzeyinde bir gereklilik değildir, ancak XAML üretimi MSBUILD yapı eylemleri tarafından yüklendiğinde özel etkinlikleri ve Genel olarak Windows İş Akışı Temeli XAML'yi destekleyen bir gereksinim haline gelir. Windows İş Akışı Temeli, öznitelik için `x:Property` `Type` amaçlanan değer olarak saf XAML türü adını kullanmaz ve bunun yerine burada belgelenmemiş bir kuralı kullanır. Daha fazla bilgi için [Dinamik Etkinlik Oluşturma'ya](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100))bakın.

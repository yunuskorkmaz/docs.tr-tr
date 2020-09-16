---
title: x:Property Yönergesi
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: d4294b39ff262198f8082863d23eb6f4edbc7054
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549307"
---
# <a name="xproperty-directive"></a>x:Property Yönergesi

İşaretlemede bir XAML özelliği bildirir.

## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`className`|XAML üretimi için yedekleme sınıfının veya kısmi sınıfın adı.|
|`propertyName`|Tanımlanan özelliğin üye adı.|
|`propertyType`|Bu özelliğin türünü belirten tür adı (veya diğer dize biçimi, çerçeveye özgü).|

## <a name="remarks"></a>Açıklamalar

.NET XAML Hizmetleri uygulamasında,. `x:Property` doğrudan bir tür yedeklemesi yoktur, ancak sınıfı tarafından desteklenir <xref:System.Windows.Markup.PropertyDefinition> . XAML düğüm akışında, bir `x:Property` Öğesı `Property` XAML Language xaml ad alanından adlı bir üye olarak temsil edilir. Üyenin, `Property` biçimlendirme tarafından belirtilen öznitelikleri.

`Name`Ve ' nin anlamı `Type` .net xaml Hizmetleri düzeyinde atanmaz. Bunlar, daha sonra belirli çerçeveler tarafından uygulanabilir kuralların altında yorumlanmak üzere, ilk XAML düğüm akışında dize değerleri olarak depolanır. Anlamı bir XAML adı ve XAML türü anlamını gösterebilir veya uygulamaya bağlı olarak yalnızca bir yedekleme türü sisteminde geçerli olabilir.

' Nin pratik kullanımını, `x:Members` İşaretlemede üye tanımlarının belirtilmesi için bir yol olarak desteklemek amacıyla, üyelerin değiştirilebilen bir sınıfla ilişkilendirilmesi gerekir. Hedeflenen model, `x:Members` bir türü belirten bir üye olarak mevcuttur `x:Class` . Ancak, türlerin ve üyelerin ilişkilendirilmesi veya dinamik üye tanımlarının üretilme mekanizması .NET XAML Hizmetleri düzeyinde desteklenmez. Bu, XAML 'den üye tanımlarını destekleyen uygulama modelleri olan tek tek çerçeveler için bırakılır. Genellikle, XAML 'yi biçimlendirme-derleme ve bu özelliği desteklemeye yönelik saf from-XAML derlemeleri ile tümleştirme sağlayan MSBUILD derleme eylemleri.

## <a name="xproperty-for-windows-workflow-foundation"></a>Windows Workflow Foundation için x:Property

Windows Workflow Foundation için, `x:Property` tamamen XAML 'de oluşturulan özel bir etkinliğin üyelerini ya da arka plan kod içeren bir etkinlik TASARıMCıSıNıN xaml tanımlı dinamik üyelerini tanımlar. `x:Class` Ayrıca XAML üretiminin kök öğesinde de belirtilmelidir. Bu, .NET XAML Hizmetleri düzeyinde bir gereklilik değildir, ancak XAML üretimi özel etkinlikleri destekleyen MSBUILD derleme eylemleri ve genel olarak XAML Windows Workflow Foundation yüklendiğinde bir gereksinim haline gelir. Windows Workflow Foundation, saf XAML tür adını özniteliği için amaçlanan değeri olarak kullanmaz `x:Property` `Type` ve bunun yerine burada belgelenmeyen bir kural kullanır. Daha fazla bilgi için bkz. [DynamicActivity oluşturma](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).

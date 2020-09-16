---
title: x:Member Yönergesi
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: 1c5b26b405e574290af54b29b22fb5e19e4b6b95
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548253"
---
# <a name="xmember-directive"></a>x:Member Yönergesi
İşaretlemede bir XAML üyesi bildirir.

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
|`className`|XAML üretimi için yedekleme sınıfının veya kısmi sınıfın adı.|
|`memberName`|Tanımlanan özelliğin üye adı.|

## <a name="remarks"></a>Açıklamalar

.NET XAML Hizmetleri uygulamasında,. `x:Member` doğrudan bir tür yedeklemesi yoktur, ancak sınıfı tarafından desteklenir <xref:System.Windows.Markup.MemberDefinition> . XAML düğüm akışında, bir `x:Member` Öğesı `Member` XAML Language xaml ad alanından adlı bir üye olarak temsil edilir. Üye, `Member` biçimlendirme tarafından belirtilen öznitelikleri barındırır.

`Name`Ve ' nin anlamı `Type` .net xaml Hizmetleri düzeyinde atanmaz. Bunlar, daha sonra belirli çerçeveler tarafından uygulanabilir kuralların altında yorumlanmak üzere, ilk XAML düğüm akışında dize değerleri olarak depolanır. Anlamı bir XAML adı ve XAML türü anlamını gösterebilir veya uygulamaya bağlı olarak yalnızca bir yedekleme türü sisteminde geçerli olabilir.

' Nin pratik kullanımını, `x:Members` İşaretlemede üye tanımlarının belirtilmesi için bir yol olarak desteklemek amacıyla, üyelerin değiştirilebilen bir sınıfla ilişkilendirilmesi gerekir. Hedeflenen model, `x:Members` bir türü belirten bir üye olarak mevcuttur `x:Class` . Ancak, türlerin ve üyelerin ilişkilendirilmesi veya dinamik üye tanımlarının üretilme mekanizması .NET XAML Hizmetleri düzeyinde desteklenmez. Bu, XAML 'den üye tanımlarını destekleyen uygulama modelleri olan tek tek çerçeveler için bırakılır. Genellikle, XAML 'yi biçimlendirme-derleme ve bu özelliği desteklemeye yönelik saf from-XAML derlemeleri ile tümleştirme sağlayan MSBUILD derleme eylemleri.

## <a name="xproperty-for-windows-workflow-foundation"></a>Windows Workflow Foundation için x:Property

Windows Workflow Foundation için, `x:Property` tamamen XAML 'de oluşturulan özel bir etkinliğin üyelerini ya da arka plan kod içeren bir etkinlik TASARıMCıSıNıN xaml tanımlı dinamik üyelerini tanımlar. `x:Class` Ayrıca XAML üretiminin kök öğesinde de belirtilmelidir. Bu, .NET XAML Hizmetleri düzeyinde bir gereklilik değildir, ancak XAML üretimi özel etkinlikleri destekleyen MSBUILD derleme eylemleri ve genel olarak XAML Windows Workflow Foundation yüklendiğinde bir gereksinim haline gelir. Windows Workflow Foundation, saf XAML tür adını özniteliği için amaçlanan değeri olarak kullanmaz `x:Property` `Type` ve bunun yerine burada belgelenmeyen bir kural kullanır. Daha fazla bilgi için bkz. [DynamicActivity oluşturma](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).

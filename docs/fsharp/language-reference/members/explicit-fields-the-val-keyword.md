---
title: 'Açık Alanlar: val Anahtar Sözcüğü (F#)'
description: "F # hakkında 'val' öğrenin anahtar sözcüğü bir değer türü başlatma olmadan bir sınıf veya yapı türü depolamak için bir konum bildirmek için kullanılır."
ms.date: 05/16/2016
ms.openlocfilehash: 9cd06f7e90192be79490dd0ff67f118cce4339c3
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746405"
---
# <a name="explicit-fields-the-val-keyword"></a>Açık Alanlar: val Anahtar Sözcüğü

`val` Anahtar sözcüğü, bir değer başlatma olmadan bir sınıf veya yapı türü depolamak için bir konum bildirmek için kullanılır. Bu şekilde bildirilen depolama konumları çağrılır *açık alanlar*. Başka bir kullanımını `val` anahtar sözcüğü, birlikte `member` otomatik uygulanan bir özellik bildirmek için anahtar sözcüğü. Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz. [özellikleri](properties.md).

## <a name="syntax"></a>Sözdizimi

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Açıklamalar

Bir sınıf veya yapı türü alanlarını tanımlamak için her zamanki şekilde kullanmaktır bir `let` bağlama. Ancak, `let` bağlamaları her zaman mümkün, gerekli veya arzu değil, sınıf oluşturucusu bir parçası olarak başlatılması gerekir. Kullanabileceğiniz `val` başlatılmamış bir alan istediğinizde anahtar sözcüğü.

Açık alanlar, statik veya statik olmayan olabilir. *Erişim değiştiricisi* olabilir `public`, `private`, veya `internal`. Varsayılan olarak açık alanlar ortaktır. Bu farklıdır `let` her zaman özel sınıflar, bağlarında.

[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) özniteliği, birincil bir oluşturucuya sahip sınıf türleri açık alanları gereklidir. Bu öznitelik alanı sıfır olarak başlatılır belirtir. Sıfır başlatma alanın türünü desteklemesi gerekir. Aşağıdakilerden biri ise sıfır başlatma türü destekler:

- Sıfır değerine sahip bir basit türü.

- Normal bir değer olarak, olağan dışı bir değer olarak veya bir temsili bir değer olarak null değeri destekleyen bir türü. Sınıflar, diziler, kayıtları, İşlevler, arabirimler, .NET başvuru türleri, bu içerir `unit` türü ve ayrılmış birleşim türleri.

- Bir .NET değer türü.

- Tüm alanları varsayılan bir sıfır değeri destekleyen bir yapısı.

Örneğin, sabit bir alan olarak adlandırılan `someField` . NET'te destek alanı gösterimi adı ile derlenmiş olan `someField@`, ve depolanan değeri adlı bir özellik kullanarak erişim `someField`.

Değişebilir bir alan için bir .NET alan derlenmiş .NET gösterimidir.

>[!WARNING]
`Note` .NET Framework ad alanı `System.ComponentModel` aynı ada sahip bir öznitelik içeriyor. Bu özniteliği hakkında daha fazla bilgi için bkz: `System.ComponentModel.DefaultValueAttribute`.

Açık alanlar ve karşılaştırma, kullanımı aşağıdaki kodda gösterildiği bir `let` birincil Oluşturucusu olan bir sınıf içinde bağlama. Unutmayın `let`-ilişkili alan `myInt1` özeldir. Zaman `let`-ilişkili alan `myInt1` bir üye yöntemi, kendi kendine tanımlayıcısı başvurulan `this` gerekli değildir. Ancak, başvuruda açık alanlar `myInt2` ve `myString`, kendi kendine tanımlayıcısı gereklidir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Çıktı aşağıdaki gibidir:

```
11 12 abc
30 def
```

Aşağıdaki kod, birincil bir oluşturucuya sahip değil bir sınıfta açık alanlar kullanımını gösterir. Bu durumda, `DefaultValue` öznitelik gerekli değildir, ancak tüm alanları türü için tanımlanan Yapıcılardaki başlatılması gerekir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Çıktı `35 22`.

Aşağıdaki kod, bir yapıda açık alanlar kullanımını gösterir. Bir yapı bir değer türü olduğundan, otomatik olarak, alanların değerlerini sıfır olarak ayarlayan bir varsayılan oluşturucusu vardır. Bu nedenle, `DefaultValue` öznitelik gerekli değildir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Çıktı `11 xyz`.

Açık alanlar rutin kullanım için tasarlanmamıştır. Genel olarak, mümkün olduğunda kullanmalısınız bir `let` açık bir alanı yerine bir sınıftaki bağlama. Açık alanlar bazı birlikte çalışabilirlik senaryolarında yararlıdır, kullanılacak bir yapı tanımla gerektiğinde gibi bir platform çağırma çağrısı bir yerel API veya COM birlikte çalışma senaryolarda. Daha fazla bilgi için [dış işlevler](../functions/external-functions.md). Hangi birincil Oluşturucu olmadan sınıfları yayan bir F # kodu Oluşturucu ile çalışırken açık bir alan gerekli olabilir başka bir durumdur. Açık alanlar da iş parçacığı statik değişkenler veya benzer yapıları için kullanışlıdır. Daha fazla bilgi için bkz. `System.ThreadStaticAttribute`.

Zaman anahtar sözcükleri `member val` bir arada göründüğünü tür tanımında, otomatik olarak uygulanan bir özellik tanımı öyledir. Daha fazla bilgi için [özellikleri](properties.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](properties.md)
- [Üyeler](index.md)
- [`let` Sınıflardaki bağlamaları](let-bindings-in-classes.md)

---
title: "Açık Alanlar: val Anahtar Sözcüğü (F#)"
description: "F # hakkında 'val' öğrenme anahtar sözcük türü başlatmadan bir sınıf veya yapı türünde bir değer depolamak için bir konum bildirmek için kullanılır."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3bdbc745-436b-407f-bf54-5d11ca829cd0
ms.openlocfilehash: cee53a48f08aec89b0bdd40189ed331cadee877d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="explicit-fields-the-val-keyword"></a>Açık Alanlar: val Anahtar Sözcüğü

`val` Anahtar sözcüğü başlatma olmadan bir sınıf veya yapı tür, bir değeri depolamak için bir konum bildirmek için kullanılır. Bu şekilde bildirilen depolama konumları çağrılır *açık alanlar*. Başka bir kullanımını `val` sözcüktür birlikte `member` otomatik uygulanan özellikler bildirmenize anahtar sözcüğü. Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz: [özellikleri](properties.md).


## <a name="syntax"></a>Sözdizimi

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Açıklamalar
Bir sınıf veya yapı türü alanlarını tanımlamak için her zamanki gibi kullanmaktır bir `let` bağlama. Ancak, `let` bağlamaları her zaman mümkün, gerekli veya istenmediğinde değil sınıfı oluşturucusu bir parçası olarak başlatılmalıdır. Kullanabileceğiniz `val` başlatılmamış olan bir alan istediğinizde anahtar sözcüğü.

Açık alanlar, statik ya da statik olmayan olabilir. *Erişim değiştiricisi* olabilir `public`, `private`, veya `internal`. Varsayılan olarak açık ortak alanlardır. Bu farklıdır `let` her zaman özel sınıflar bağlama.

[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) özniteliği, birincil bir oluşturucuya sahip sınıf türleri, açık alanlar gereklidir. Bu öznitelik alanı sıfır olarak başlatıldığını belirtir. Alanın türü sıfır başlatma desteklemesi gerekir. Aşağıdakilerden biri olması durumunda bir türü sıfır başlatma destekler:

- Sıfır değerine sahip bir basit türü.

- Normal bir değer olarak, normal olmayan bir değer olarak ya da bir gösterimini bir değer olarak null değer destekleyen bir türü. Sınıfları, tanımlama grupları, kayıtları, İşlevler, arabirimler, .NET başvuru türleri, bu içerir `unit` türü ve ayrılmış birleşim türü.

- Bir .NET değer türü.

- Tüm alanları varsayılan sıfır değeri destekleyen bir yapısı.


Örneğin, sabit bir alan adlı `someField` .NET yedekleme alanında adıyla gösterimi hazırladığı `someField@`, ve adlı bir özellik kullanarak depolanan değer erişim `someField`.

Değişebilir bir alan için derlenmiş .NET temsili bir .NET alandır.


>[!WARNING] 
`Note`.NET Framework ad `System.ComponentModel` aynı ada sahip bir öznitelik içeriyor. Bu öznitelik hakkında daha fazla bilgi için bkz: `System.ComponentModel.DefaultValueAttribute`.


Açık alanlar ve karşılaştırma, kullanımı aşağıdaki kod gösterir bir `let` birincil bir oluşturucuya sahip bir sınıfta bağlama. Unutmayın `let`-ilişkili alan `myInt1` özeldir. Zaman `let`-ilişkili alan `myInt1` bir üye yöntemi, kendi kendine tanımlayıcı başvurulan `this` gerekli değildir. Ancak zaman başvuruda açık alanlar `myInt2` ve `myString`, kendi kendine tanımlayıcısı gereklidir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Çıktı aşağıdaki gibidir:

```
11 12 abc
30 def
```

Aşağıdaki kod, birincil bir oluşturucu yok bir sınıfta açık alanlar kullanımını göstermektedir. Bu durumda, `DefaultValue` özniteliği gerekli değildir, ancak tüm alanları türü için tanımlı oluşturucular başlatılması gerekir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Çıktı `35 22`.

Aşağıdaki kod bir yapısında açık alanlar kullanımını göstermektedir. Bir yapı bir değer türü olduğundan, otomatik olarak kendi alanların değerlerini sıfıra ayarlar varsayılan bir oluşturucu yoktur. Bu nedenle, `DefaultValue` özniteliği gerekli değildir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Çıktı `11 xyz`.

Açık alanlar rutin kullanılmak üzere tasarlanmamıştır. Genel olarak, mümkün olduğunda, kullanması gereken bir `let` açık bir alanı yerine bir sınıftaki bağlama. Açık alanlar belirli birlikte çalışabilirlik senaryolarda yararlı olan, kullanılacak bir yapı tanımlamak gerektiğinde gibi bir platform çağırma çağrısı bir yerel API veya COM birlikte çalışma senaryolarda. Daha fazla bilgi için bkz: [dış işlevler](../functions/external-functions.md). Hangi birincil Oluşturucusu olmadan sınıflarını yayar bir F # kod Oluşturucu ile çalışırken açık bir alanı gerekebilir başka bir durumdur. Açık alanlar, ayrıca iş parçacığı statik değişkenler veya benzer yapıları için yararlıdır. Daha fazla bilgi için bkz. `System.ThreadStaticAttribute`.

Zaman anahtar sözcükleri `member val` görünür birlikte bir tür tanımında otomatik olarak uygulanan bir özellik tanımını öyledir. Daha fazla bilgi için bkz: [özellikleri](properties.md).


## <a name="see-also"></a>Ayrıca Bkz.
[Özellikleri](properties.md)

[Üyeleri](index.md)

[`let`Sınıflardaki bağlamaları](let-bindings-in-classes.md)

---
title: 'İmza dosyaları (F #)'
description: 'F # program öğelerine, türleri, ad alanları ve modüller gibi bir dizi ortak imzalarını hakkındaki bilgileri tutmak için F # imza dosyalarını kullanmayı öğrenin.'
ms.date: 06/15/2018
ms.openlocfilehash: f0836aa7f638dc9e2b066b0f46bbb6c086347615
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036489"
---
# <a name="signatures"></a>İmzalar

Bir imza dosyası türleri, ad alanları ve modüller gibi F # program öğelerini, bir dizi ortak imzalarını hakkında bilgiler içerir. Bu program öğelerini erişilebilirliğini belirtmek için kullanılabilir.

## <a name="remarks"></a>Açıklamalar

Her F # kod dosyası için elinizde bir *imza dosyası*, kod dosyası ancak uzantı .fsi .fs yerine ile aynı ada sahip bir dosya olduğu. İmza dosyaları komut satırından doğrudan kullanıyorsanız, komut satırı derleme da eklenebilir. İmza dosyaları kod dosyaları arasında ayrım yapmak için kod dosyaları olarak da adlandırılır *uygulama dosyaları*. Bir projede, ilişkili kod dosyasına imza dosyası gelmelidir.

Ad alanları, modüller, türler ve üyeler uygulama dosyasında karşılık gelen bir imza dosyası açıklar. Hangi bölümlerinin belirtmek için bir imza dosyası bilgileri kullanın karşılık gelen uygulamasında kod dosyasına uygulama dosya dışındaki kod erişebilir ve hangi bölümlerinin uygulama dosyasına iç. Ad alanları, modülleri ve imza dosyasında bulunan türleri ad alanları, modülleri ve uygulama dosyasında bulunan türleri bir alt kümesi olmalıdır. Bu konunun ilerleyen kısımlarında belirtildiği bazı istisnalar v souboru signatury listede yer almayan bu dil öğeleri uygulama dosyanın özel olarak kabul edilir. Varsayılan erişilebilirlik, herhangi bir imza dosyası proje ya da komut satırı bulunursa kullanılır.

Varsayılan erişilebilirlik hakkında daha fazla bilgi için bkz. [erişim denetimi](access-control.md).

Bir imza dosyası içinde türlerinin tanımını ve her yöntem veya işlev uygulamalarını tekrarlamayın. Bunun yerine, her bir yöntemi ve bir modülde veya ad alanı parça tarafından uygulanan işlevleri tam belirtimini görevi gören işlevi için imza kullanın. Tür imzası için söz dizimi, arabirimleri ve soyut sınıflar, soyut yöntem bildirimleri içinde kullanılan aynıdır ve doğru derlenmiş giriş görüntülediğinde, IntelliSense ve F # yorumlayıcısı fsi.exe tarafından da gösterilmektedir.

Tür imzası bir tür korumalı olup olmadığını belirtmek için yeterli bilgi yok ya da bir arabirim türü olmasına bakılmaksızın, bir öznitelik eklemelisiniz derleyiciye tür yapısını gösterir. Bu amaçla kullandığınız öznitelikler aşağıdaki tabloda açıklanmıştır.

|Öznitelik|Açıklama|
|---------|-----------|
|`[<Sealed>]`|Soyut üye bir tür için olan veya olmayan genişletilmesi.|
|`[<Interface>]`|Bir arabirim için bir tür.|
Öznitelikleri imza ve bildirimi uygulama dosyasında arasında tutarlı değilse, derleyici bir hata oluşturur.

Anahtar sözcüğünü kullanın `val` imza için bir değer ya da işlev değer oluşturmak için. Anahtar sözcüğü `type` tür imzası tanıtır.

Bir imza dosyası kullanarak oluşturabileceğiniz `--sig` derleyici seçeneği. Genellikle, .fsi dosyaları el ile yazmanız değil. Bunun yerine, derleyicinin .fsi dosyaları oluşturmak, bir varsa ve yöntem ve erişilebilir olmasını istemediğiniz işlevleri kaldırarak Düzenle bunları projenize ekleyin.

Birkaç kural türü imzalar vardır:

- Tür kısaltmaları bir uygulama dosyasında bir imza dosyası içinde bir kısaltma olmadan bir tür ile aynı olmamalıdır.

- Kayıtlar ve ayrılmış birleşimler tümü veya hiçbiri alanları ve oluşturucular kullanıma açmalıdır ve imza sırayla uygulama dosyasında eşleşmesi gerekir. Sınıflar, bazı, tümü veya hiçbiri alanlar ve yöntemler imzasında ortaya çıkarabilir.

- Sınıf ve yapılardaki oluşturucular olan temel sınıflarının işaretçilerine bildirimlerini kullanıma gerekir ( `inherits` bildirimi). Ayrıca, sınıf ve yapılardaki oluşturucular sahip tüm soyut yöntemler ve arabirimi bildirimleri göstermesi gerekir.

- Tüm yöntemleri ve arabirimleri arabirim türleri açığa çıkar gerekir.

Değer imzaları için kuralları aşağıdaki gibidir:

- Erişilebilirlik değiştiricileri (`public`, `internal`, vb.) ve `inline` ve `mutable` imzasında değiştiriciler bu uygulamada eşleşmesi gerekir.

- Genel tür parametreleri (ya da örtük olarak çıkarılan açıkça bildirildi) sayısı ile eşleşmelidir ve genel tür parametrelerindeki tür kısıtlamaları ve türleri eşleşmelidir.

- Varsa `Literal` özniteliği kullanılır, hem imza hem de uygulama görünmesi gerekir ve her ikisi için aynı değişmez değer kullanılmalıdır.

- Parametreleri desenini (olarak da bilinen *kutup*) imzalar ve uygulamaları tutarlı olmalıdır.

- Parametre adları bir imza dosyası içinde karşılık gelen uygulama dosyasından farklıysa, imza dosyası adı, hata ayıklama veya profil oluşturma sırasında sorunlara neden olabilir bunun yerine kullanılır. Tür uyuşmazlığı, proje dosyanızda 3218 uyarı etkinleştir, bildirim almak istiyorsanız veya derleyicisini çağırma (bkz `--warnon` altında [derleyici seçenekleri](compiler-options.md)).

Aşağıdaki kod örneği, ad alanı, modül, işlevi ve türü imzalarını uygun öznitelikleri ile birlikte sahip bir imza dosyası örneği gösterir. Ayrıca, ilgili uygulama dosyasını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

Aşağıdaki kod uygulama dosyasını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Erişim Denetimi](access-control.md)
- [Derleyici Seçenekleri](compiler-options.md)

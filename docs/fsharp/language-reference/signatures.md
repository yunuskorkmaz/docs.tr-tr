---
title: İmzalar (F#)
description: 'F # programı öğeleri türleri, ad alanları ve modülleri gibi bir dizi ortak imzalar hakkında bilgiyi tutmak için bir F # imza dosyası kullanmayı öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: c98ac6c62fdcee51532a162596e99309a31802ec
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="signatures"></a>İmzalar

Bir imza dosyası türleri, ad alanları ve modülleri gibi F # program öğeleri, bir dizi ortak imzalar hakkında bilgiler içerir. Bu program öğeleri erişilebilirliğini belirtmek için kullanılabilir.


## <a name="remarks"></a>Açıklamalar
Her F # için kod dosyası, elinizde bir *imza dosyası*, kod dosyası olarak ancak .fs yerine uzantısı .fsi ile aynı ada sahip bir dosya değil. İmza dosyaları de komut satırı doğrudan kullanıyorsanız, komut satırı derleme eklenebilir. Kod dosyaları ve imza dosyalarını arasında ayrım yapmak için kod dosyaları olarak da adlandırılır *uygulama dosyaları*. Bir proje ile ilişkili kod dosyası imza dosyası gelmelidir.

Ad alanları, modüller, türleri ve üyeleri karşılık gelen uygulama dosyasındaki bir imza dosyası açıklar. Hangi bölümlerinin belirtmek için bir imza dosyası bilgileri kullanın karşılık gelen uygulamasında kodunun dosya uygulama dosyasını dışındaki koddan erişilebilir ve hangi bölümlerinin uygulama dosyasına iç. Ad alanları, modüller ve uygulama dosyasında bulunan türleri bir alt kümesini ad alanları, modüller ve imza dosyasında bulunan türler olmalıdır. Bu konunun ilerleyen bölümlerinde not ettiğiniz bazı istisnalar imza dosyasında listelenmeyen bu dil öğeleri uygulaması dosyanın özel olarak kabul edilir. Herhangi bir imza dosyası proje veya komut satırı bulunursa, varsayılan erişilebilirlik kullanılır.

Varsayılan erişilebilirlik hakkında daha fazla bilgi için bkz: [erişim denetimi](access-control.md).

Bir imza dosyası türlerinin tanımlarını ve her bir yöntemi veya işlev uygulamaları tekrarlamayın. Bunun yerine, her yöntemi ve tam bir belirtimini bir modül veya ad alanı parça tarafından uygulanan işlevleri gibi davranır işlevi için imza kullanın. Tür imzası sözdizimi Özet yöntem bildirimlerinde arabirimleri ve soyut sınıflar kullanılan aynı ve doğru şekilde derlenmiş giriş görüntülediğinde IntelliSense ve F # Yorumlayıcı fsi.exe tarafından da gösterilmektedir.

Yeterli bilgi türü korumalı olup olmadığını belirtmek için türü imzada değilse veya bir arabirim türü olup olmadığını belirtir, özniteliğin eklemeniz gerekir, derleyici türüne yapısını gösterir. Bu amaçla kullanabileceğiniz öznitelikleri aşağıdaki tabloda açıklanmıştır.



|Öznitelik|Açıklama|
|---------|-----------|
|`[<Sealed>]`|Türü için hiçbir soyut üye olan veya olmayan genişletilmesi.|
|`[<Interface>]`|Bir arabirim için bir türü.|
Derleyici öznitelikleri imza ve uygulama dosyasını bildiriminde arasında tutarlı değilse bir hata oluşturur.

Anahtar sözcüğü kullanmak `val` bir değer veya işlev değeri için imza oluşturma için. Anahtar sözcüğü `type` tür imzası tanıtır.

Kullanarak bir imza dosyası oluşturabilirsiniz `--sig` derleyici seçeneği. Genellikle, .fsi dosyaları el ile yazma. Bunun yerine, derleyici kullanarak .fsi dosyaları oluşturmak, biri varsa ve yöntemleri ve erişilebilir olmasını istiyor musunuz işlevlerini kaldırarak Düzenle bunları, projenize ekleyin.

Türü imzalar çeşitli kurallar şunlardır:


- Tür kısaltmaları uygulama dosyasındaki bir imza dosyasında kısaltma olmadan türü eşleşmesi gerekmez.


- Kayıtlar ve ayrılmış birleşimler tüm ya da kendi alanları ve oluşturucular hiçbiri kullanıma gerekir ve imza sırada uygulama dosyasını sırayla eşleşmelidir. Sınıfları, bazıları, tümü veya hiçbiri kendi alanları ve imza yöntemleri ortaya çıkarabilir.


- Sınıfları ve yapıları oluşturucular sahip temel sınıflarına bildirimlerini kullanıma gerekir ( `inherits` bildirim). Ayrıca, sınıfları ve yapıları oluşturucular sahip tüm kullanıcıların soyut yöntemler ve arabirim bildirimleri kullanıma gerekir.


- Arabirim türleri, yöntemleri ve arabirimleri ortaya gerekir.


Değer imzalar için kurallar aşağıdaki gibidir:


- Erişilebilirlik için değiştiriciler (`public`, `internal`, vb.) ve `inline` ve `mutable` imzada değiştiricileri uygulama de eşleşmesi gerekir.


- Genel tür parametreleri (ya da örtük olarak yapılandırılacağını veya açıkça bildirilen) sayısı eşleşmelidir ve genel tür parametrelerindeki türü kısıtlamaları ve türleri eşleşmelidir.


- Varsa `Literal` özniteliği kullanılır, hem imza hem de uygulama görünmesi gerekir ve her ikisi için aynı sabit değer kullanılmalıdır.


- Parametreleri desenin (olarak da bilinen *parametre*) imzalar ve uygulamaları tutarlı olmalıdır.


Aşağıdaki kod örneğinde, ad alanı, modül, işlevi ve türü imzaları uygun özniteliklerini birlikte sahip bir imza dosyası örneği gösterilmektedir. Ayrıca, karşılık gelen uygulama dosyasını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

Aşağıdaki kod uygulama dosyasını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Erişim Denetimi](access-control.md)

[Derleyici Seçenekleri](compiler-options.md)

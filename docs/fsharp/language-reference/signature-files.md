---
title: İmza dosyaları
description: Türler, ad alanları F# ve modüller gibi bir F# program öğeleri kümesinin genel imzaları hakkındaki bilgileri tutmak için imza dosyalarını nasıl kullanacağınızı öğrenin.
ms.date: 06/15/2018
ms.openlocfilehash: c04ac8bf4ee360a2caa15be8f2bbea41105bd160
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627160"
---
# <a name="signatures"></a>İmzalar

İmza dosyası türler, ad alanları ve modüller gibi bir F# program öğeleri kümesinin genel imzaları hakkında bilgiler içerir. Bu program öğelerinin erişilebilirliğini belirtmek için kullanılabilir.

## <a name="remarks"></a>Açıklamalar

Her F# kod dosyası için, kod dosyasıyla aynı ada sahip ancak. FS yerine. fsi uzantılı bir dosya olan bir *imza dosyasına*sahip olabilirsiniz. Komut satırını doğrudan kullanıyorsanız, imza dosyaları da derleme komut satırına eklenebilir. Kod dosyalarını ve imza dosyalarını ayırt etmek için, kod dosyaları bazen *uygulama dosyaları*olarak adlandırılır. Bir projede, imza dosyası ilişkili kod dosyasından önce gelmelidir.

İmza dosyası, ilgili uygulama dosyasındaki ad alanlarını, modülleri, türleri ve üyeleri açıklar. İlgili uygulama dosyasındaki kodun hangi bölümlerinin uygulama dosyası dışındaki koddan erişilebilir olduğunu ve uygulama dosyasına hangi parçaların dahili olduğunu belirtmek için bir imza dosyasındaki bilgileri kullanırsınız. İmza dosyasına dahil edilen ad alanları, modüller ve türler, uygulama dosyasına dahil edilen ad alanları, modüller ve türlerin bir alt kümesi olmalıdır. Bu konunun ilerleyen kısımlarında belirtilen bazı özel durumlarla birlikte, imza dosyasında listelenmeyen dil öğeleri uygulama dosyası için özel olarak kabul edilir. Projede veya komut satırında imza dosyası bulunmazsa, varsayılan erişilebilirlik kullanılır.

Varsayılan erişilebilirlik hakkında daha fazla bilgi için bkz. [Access Control](access-control.md).

Bir imza dosyasında, türlerin ve her yöntemin veya işlevin uygulamalarının tanımını tekrarlamayın. Bunun yerine, bir modül veya ad alanı parçası tarafından uygulanan işlevselliğin tamamı olarak davranan her bir yöntem ve işlev için imza kullanırsınız. Bir tür imzasının sözdizimi, arabirimler ve soyut sınıflardaki soyut Yöntem bildirimlerinde kullanılan ile aynıdır ve ayrıca, doğru derlenmiş girişi görüntülediğinde, IntelliSense tarafından ve F# Ayrıca, fsi. exe ' de de gösterilir.

Tür imzasında bir türün korumalı olup olmadığını veya bir arabirim türü olup olmadığını belirtmek için yeterli bilgi yoksa, türün yapısını derleyiciye belirten bir öznitelik eklemeniz gerekir. Bu amaçla kullandığınız öznitelikler aşağıdaki tabloda açıklanmıştır.

|Öznitelik|Açıklama|
|---------|-----------|
|`[<Sealed>]`|Soyut üyesi olmayan veya genişletilmemelidir olması gereken bir tür için.|
|`[<Interface>]`|Arabirim olan bir tür için.|

Öznitelikler imza ile uygulama dosyasındaki bildirim arasında tutarlı değilse derleyici bir hata oluşturur.

Bir değer veya `val` işlev değeri için imza oluşturmak için anahtar sözcüğünü kullanın. Anahtar sözcüğü `type` bir tür imzası tanıtır.

`--sig` Derleyici seçeneğini kullanarak bir imza dosyası oluşturabilirsiniz. Genellikle. fsi dosyalarını el ile yazmayın. Bunun yerine, derleyicisini kullanarak. fsi dosyaları oluşturur, varsa bunları projenize ekler ve erişilebilir olmasını istemediğiniz yöntemleri ve işlevleri kaldırarak düzenleyebilirsiniz.

Tür imzaları için çeşitli kurallar mevcuttur:

- Bir uygulama dosyasındaki tür kısaltmaların bir imza dosyasında kısaltması olmadan bir türle eşleşmemesi gerekir.

- Kayıtlar ve ayrılmış birleşimler, kendi alan ve oluşturucularından birini ya da hiçbirini kullanıma sunmalı ve İmzadaki sıranın uygulama dosyasındaki sıralamayla eşleşmesi gerekir. Sınıflar, İmzadaki bazı, hepsi veya hiçbirini ya da bir imzayı hiçbir şekilde gösterebilir.

- Oluşturucuları olan sınıflar ve yapılar kendi temel sınıflarının ( `inherits` bildirim) bildirimlerini kullanıma sunmalıdır. Ayrıca, oluşturucuları olan sınıflar ve yapılar tüm soyut yöntemleri ve arabirim bildirimlerini kullanıma sunmalıdır.

- Arabirim türleri tüm yöntemlerini ve arabirimlerini açığa çıkarmalıdır.

Değer imzalarının kuralları aşağıdaki gibidir:

- Erişilebilirlik (`public`, `internal`, vb. `inline` ) için değiştiriciler ve İmzadaki ve `mutable` değiştiricilerin uygulamadaki olanlarla eşleşmesi gerekir.

- Genel tür parametrelerinin sayısı (örtük olarak çıkarılmış veya açıkça bildirilmiştir) eşleşmelidir ve genel tür parametrelerindeki türler ve tür kısıtlamaları eşleşmelidir.

- `Literal` Özniteliği kullanılırsa, hem imza hem de uygulamada görünmelidir ve her ikisi için de aynı sabit değer kullanılmalıdır.

- İmzaların ve uygulamaların parametrelerinin ( *parametre sayısı*olarak da bilinir) düzeninin tutarlı olması gerekir.

- İmza dosyasındaki parametre adları karşılık gelen uygulama dosyasından farklıysa, bunun yerine imza dosyasındaki ad, hata ayıklama veya profil oluşturma sırasında sorunlara neden olabilecek şekilde kullanılacaktır. Bu tür uyuşmazlıkların bildirilmesini istiyorsanız, proje dosyanızda veya derleyicisini çağırırken uyarı 3218 ' yı etkinleştirin (bkz `--warnon` . [derleyici seçenekleri](compiler-options.md)altında).

Aşağıdaki kod örneğinde, uygun özniteliklerle birlikte ad alanı, modül, işlev değeri ve tür imzaları içeren bir imza dosyası örneği gösterilmektedir. Ayrıca ilgili uygulama dosyasını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9002.fs)]

Aşağıdaki kod, uygulama dosyasını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9001.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Erişim Denetimi](access-control.md)
- [Derleyici Seçenekleri](compiler-options.md)

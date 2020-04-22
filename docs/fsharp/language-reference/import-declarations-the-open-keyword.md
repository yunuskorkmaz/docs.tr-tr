---
title: 'İçeri Aktarma Bildirimleri: open Anahtar Sözcüğü'
description: F# alma bildirimleri ve tam nitelikli bir ad kullanmadan başvuruda bulunabileceğiniz bir modülü veya ad alanını nasıl belirttikleri hakkında bilgi edinin.
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021536"
---
# <a name="import-declarations-the-open-keyword"></a>İthalat Bildirimleri: `open` Anahtar Kelime

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları sizi MSDN'ye götürür.  docs.microsoft.com API başvurusu tamamlanmadı.

*Alma bildirimi,* tam nitelikli bir ad kullanmadan öğelerine başvuruyapabileceğiniz bir modül veya ad alanı belirtir.

## <a name="syntax"></a>Sözdizimi

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Açıklamalar

Kodu, her seferinde tam nitelikli ad alanı veya modül yolunu kullanarak başvurmak, yazması, okunması ve bakımı zor kodlar oluşturabilir. Bunun yerine, sık `open` kullanılan modüller ve ad alanları için anahtar sözcüğü kullanabilirsiniz, böylece bu modülün veya ad alanının bir üyesine başvuruyaptığınızda, tam nitelikli ad yerine adın kısa biçimini kullanabilirsiniz. Bu anahtar kelime C#, `using` `using namespace` Visual C++'daki ve `Imports` Visual Basic'teki anahtar kelimeye benzer.

Sağlanan modül veya ad alanı aynı projede veya başvurulan proje veya derlemede olmalıdır. Değilse, projeye bir başvuru ekleyebilir veya `-reference` komut satırı seçeneğini (veya kısaltmasını) `-r`kullanabilirsiniz. Daha fazla bilgi için [Derleyici Seçenekleri'ne](compiler-options.md)bakın.

Alma bildirimi, adları, çevreleyen ad alanının, modülün veya dosyanın sonuna kadar, bildirimi izleyen kodda kullanılabilir hale getirir.

Birden çok alma bildirimi kullandığınızda, bunlar ayrı satırlarda görünmelidir.

Aşağıdaki kod, kodu basitleştirmek için `open` anahtar kelimenin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F# derleyicisi, aynı ad birden fazla açık modülveya ad alanında oluştuğunda belirsizlikler oluştuğunda bir hata veya uyarı yayar. Belirsizlikler oluştuğunda, F# daha yeni açılan modülü veya ad alanını tercih verir. Örneğin, aşağıdaki kodda, `empty` `Seq.empty`hem `empty` `Seq` modüllerde hem de `List` modüllerde bulunmasına rağmen , anlamına gelir.

```fsharp
open List
open Seq
printfn "%A" empty
```

Bu nedenle, modülleri veya aynı adlara `List` `Seq` sahip üyeler içeren ad alanlarını açtığınızda dikkatli olun; bunun yerine, nitelikli adları kullanmayı düşünün. Kodun alma bildirimlerinin sırasına bağlı olduğu herhangi bir durumdan kaçınmalısınız.

## <a name="namespaces-that-are-open-by-default"></a>Varsayılan Olarak Açık Olan Ad Alanları

Bazı ad alanları F# kodunda o kadar sık kullanılır ki, açık bir alma bildirimine gerek kalmadan örtülü olarak açılırlar. Aşağıdaki tablo, varsayılan olarak açık olan ad alanlarını gösterir.

|Ad Alanı|Açıklama|
|---------|-----------|
|`Microsoft.FSharp.Core`|Dahili türleri için temel F# türü `int` tanımları içerir ve. `float`|
|`Microsoft.FSharp.Core.Operators`|Gibi temel aritmetik `+` işlemleri `*`içerir ve.|
|`Microsoft.FSharp.Collections`|Gibi değişmez toplama sınıfları `List` `Array`içerir ve.|
|`Microsoft.FSharp.Control`|Tembel değerlendirme ve eşzamanlı iş akışları gibi denetim yapıları için türleri içerir.|
|`Microsoft.FSharp.Text`|İşlev gibi biçimlendirilmiş IO `printf` işlevleri içerir.|

## <a name="autoopen-attribute"></a>OtomatikAçık Öznitelik

Derleme başvurulduğunda bir ad alanı veya modülü otomatik olarak açmak istiyorsanız özniteliği bir derlemeye uygulayabilirsiniz. `AutoOpen` Ana modül veya `AutoOpen` ad alanı açıldığında bu modülü otomatik olarak açmak için bir modüle özniteliği de uygulayabilirsiniz. Daha fazla bilgi için [Core.AutoOpenAttribute Class'a](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)bakın.

## <a name="requirequalifiedaccess-attribute"></a>Kalifiye Erişim Özniteliği Gerektirir

Bazı modüller, kayıtlar veya birleşim türleri özniteliği belirtebilir. `RequireQualifiedAccess` Bu modüllerin, kayıtların veya birliş öğelerine başvururken, bir alma bildirimi ekleyip eklemediğinize bakılmaksızın nitelikli bir ad kullanmanız gerekir. Bu özniteliği, yaygın olarak kullanılan adları tanımlayan türler üzerinde stratejik olarak kullanırsanız, ad çakışmalarını önlemeye yardımcı olur ve böylece kodu kitaplıktaki değişikliklere karşı daha esnek hale getirebilirsiniz. Daha fazla bilgi için [Core.RequireQualifiedAccessAttribute Class'a](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dil Referansı](index.md)
- [Ad Alanları](namespaces.md)
- [Modüller](modules.md)

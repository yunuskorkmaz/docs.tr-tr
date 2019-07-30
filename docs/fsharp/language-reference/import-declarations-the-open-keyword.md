---
title: 'Önemli Bildirimler: open Anahtar Sözcüğü'
description: İçeri aktarma F# bildirimleri ve bunların öğelerini tam nitelikli bir ad kullanmadan başvuralabileceğiniz bir modül veya ad alanı belirttikleri hakkında bilgi edinin.
ms.date: 04/04/2019
ms.openlocfilehash: 816bac551692c3397290f64c6267ee22e4ce90fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630580"
---
# <a name="import-declarations-the-open-keyword"></a>Önemli Bildirimler: `open` Anahtar Sözcüğü

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları sizi MSDN 'ye götürür.  Docs.microsoft.com API başvurusu tamamlanmadı.

*İçeri aktarma bildirimi* , öğelerini tam nitelikli bir ad kullanmadan başvuralabileceğiniz bir modül veya ad alanını belirtir.

## <a name="syntax"></a>Sözdizimi

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Açıklamalar

Her seferinde tam nitelikli ad alanı veya modül yolunu kullanarak koda başvurmak, yazmak, okumak ve sürdürmek zor olan kod oluşturabilir. Bunun yerine sık kullanılan modüller ve `open` ad alanları için anahtar sözcüğünü kullanarak bu modülün veya ad alanının bir üyesine başvurduğunuzda, tam ad yerine adın kısa formunu kullanabilirsiniz. Bu anahtar `using` sözcük C#, `using namespace` Visual C++'teki ve `Imports` Visual Basic içindeki anahtar sözcüğe benzerdir.

Belirtilen modül veya ad alanı aynı projede veya başvurulan bir proje ya da derlemede olmalıdır. Yoksa, projeye bir başvuru ekleyebilir veya `-reference` komut`-`satırı seçeneğini `-r`(ya da kısaltmasının) kullanabilirsiniz. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).

İçeri aktarma bildirimi, kapsayan ad alanı, modül veya dosyanın sonuna kadar, bildirimi izleyen koddaki adları kullanılabilir hale getirir.

Çoklu içeri aktarma bildirimleri kullandığınızda, bunlar ayrı satırlarda görünmelidir.

Aşağıdaki kod, kodu basitleştirmek için `open` anahtar sözcüğünün kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

Birden F# fazla açık modülde veya ad alanında aynı ad gerçekleştiğinde, belirsizlikleri gerçekleştiğinde derleyici bir hata veya uyarı göstermez. Belirsizlikleri gerçekleştiğinde, F# daha yeni açılan modüle veya ad alanına tercih verir. Örneğin, `empty` aşağıdaki kodda `Seq.empty` `empty` hem`List`hemde modüllerindebulunur.`Seq`

```fsharp
open List
open Seq
printfn "%A" empty
```

Bu nedenle, `List` ya da gibi özdeş adlara sahip üyeler içeren veya `Seq` gibi modülleri veya ad alanlarını açtığınızda dikkatli olun; bunun yerine nitelikli adları kullanmayı göz önünde bulundurun. Kodun içeri aktarma bildirimlerinin sırasına bağlı olduğu herhangi bir durumu kullanmaktan kaçının.

## <a name="namespaces-that-are-open-by-default"></a>Varsayılan olarak açık olan ad alanları

Bazı ad alanları, genellikle açık bir F# içeri aktarma bildirimine gerek kalmadan örtük olarak açıldıkları kodda kullanılır. Aşağıdaki tabloda varsayılan olarak açık olan ad alanları gösterilmektedir.

|Ad Alanı|Açıklama|
|---------|-----------|
|`Microsoft.FSharp.Core`|`int` F# Ve`float`gibi yerleşik türler için temel tür tanımlarını içerir.|
|`Microsoft.FSharp.Core.Operators`|`+` Ve`*`gibi temel aritmetik işlemleri içerir.|
|`Microsoft.FSharp.Collections`|`List` Ve`Array`gibi sabit koleksiyon sınıflarını içerir.|
|`Microsoft.FSharp.Control`|Yavaş değerlendirme ve zaman uyumsuz iş akışları gibi denetim yapıları için türler içerir.|
|`Microsoft.FSharp.Text`|`printf` İşlev gibi, biçimlendirilen GÇ işlevleri içerir.|

## <a name="autoopen-attribute"></a>Oto aç özniteliği

Derlemeye başvuruluyorsa bir `AutoOpen` ad alanını veya modülü otomatik olarak açmak istiyorsanız, özniteliği bir derlemeye uygulayabilirsiniz. Üst modül veya ad alanı `AutoOpen` açıldığında bu modülü otomatik olarak açmak için bir modüle özniteliği de uygulayabilirsiniz. Daha fazla bilgi için bkz. [Core. oto Openattribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess özniteliği

Bazı modüller, kayıtlar veya birleşim türleri `RequireQualifiedAccess` özniteliği belirtebilir. Bu modüllerin, kayıtların veya birleşimlerin öğelerine başvurduğunuzda, bir içeri aktarma bildirimi eklenip eklenmeyeceğini fark etmeksizin nitelikli bir ad kullanmanız gerekir. Bu özniteliği yaygın olarak kullanılan adları tanımlayan türler üzerinde stratejik olarak kullanırsanız, ad çakışmalarını önlemeyi ve bu sayede kodu kitaplıklarda değişikliklere daha dayanıklı hale getirmenize yardımcı olursunuz. Daha fazla bilgi için bkz. [Core. RequireQualifiedAccessAttribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Ad Alanları](namespaces.md)
- [Modüller](modules.md)

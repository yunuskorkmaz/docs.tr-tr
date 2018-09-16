---
title: Değerler (F#)
description: 'F # değerleri belirli bir tür olan miktarlar nasıl olduğunu öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: f645481ce8395c11ae920aee06cbf07955aeb684
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677831"
---
# <a name="values"></a>Değerler

Belirli bir tür olan miktarlar değerler F #; değerleri tamsayı veya kayan nokta numaralarını, karakter veya metin, listeler, dizileri, diziler, diziler, ayrılmış birleşimler, kayıtları, sınıf türleri veya işlev değerleri olabilir.

## <a name="binding-a-value"></a>Bir değer bağlama

Terim *bağlama* bir adı bir tanımı ile ilişkilendirme anlamına gelir. `let` Anahtar sözcüğü, aşağıdaki örneklerde gösterildiği gibi bir değere bağlar:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Bir değer türü tanımından algılanır. Bir tamsayı veya kayan noktalı sayı gibi basit bir tür için tür sabit değerinin türü belirlenir. Bu nedenle, önceki örnekte, derleyicinin türünü çıkarsar `b` olmasını `unsigned int`derleyici türünü çıkarsar bilgileriyse `a` olmasını `int`. Bir işlevi değer türü, işlev gövdesinde dönüş değerinden belirlenir. İşlev değer türleri hakkında daha fazla bilgi için bkz: [işlevleri](../functions/index.md). Değişmez değer türleri hakkında daha fazla bilgi için bkz: [değişmez değerleri](../literals.md).

Derleyici, varsayılan olarak kullanılmayan bağlamalar hakkında tanılama kesmez. Bu iletileri almayı etkinleştirme derleyici çağrılırken 1182 proje dosyanızdaki veya uyarı (bkz `--warnon` altında [derleyici seçenekleri](../compiler-options.md)).

## <a name="why-immutable"></a>Sabit neden?

Değişmez değerler, program yürütme kurs değiştirilemez değerlerdir. C++, Visual Basic veya C# gibi diller için kullanılıyorsa, F # primacy bir programın yürütülmesi sırasında yeni değerler atanabilir değişkenler yerine sabit değerler üzerinden geçirir, şaşırtıcı bulabilirsiniz. Sabit veri, işlevsel programlama, önemli bir öğesidir. Çok iş parçacıklı bir ortamda yönetmek birçok farklı iş parçacıkları tarafından değiştirilebilecek paylaşılan değişebilir değişkenleri zordur. Ayrıca, değişebilir değişkenleri ile bazen bir değişken başka bir işleve geçirildiğinde değiştirilebilir, bildirmek zor olabilir.

Saf işlevsel dillerde, değişken yok ve İşlevler, kesinlikle matematiksel işlevler olarak davranır. Yordam bir dilde kod, bir değeri değiştirmek için değişken ataması kullanır. Burada, işlevsel bir dildir eşdeğer kodda giriş ve sabit bir işlevi farklı değişmez değerler çıktı olarak bir sabit değer var. Bu matematiksel katılık programın davranışını hakkında akıl sıkı sağlar. Ne derleyicileri daha kesin kodunu kontrol edin ve daha etkili bir şekilde en iyi duruma getirmeyi sağlayan sıkı bu mantık, ve geliştiricilerin anlamak ve doğru kod yazmak için kolaylaştırmak yardımcı olur. Bu nedenle işlev kodu sıradan yordam kodda hata ayıklamak daha kolay olacak şekilde olasıdır.

F # saf işlevsel bir dil değil henüz tam olarak işlevsel programlama destekler. Bunun yapılması bir önemli işlevsel programlama açısından yararlanmak kodunuzu izin verdiğinden değişmez değerleri kullanılarak iyi bir uygulamadır.

## <a name="mutable-variables"></a>Değişebilir değişkenleri

Anahtar sözcüğünü kullanabilirsiniz `mutable` değiştirilebilen bir bağımsız değişken belirtin. F # değişebilir değişkenleri genel olarak, bir türün bir alanı veya yerel bir değer olarak bir sınırlı kapsamı olmalıdır. Kısıtlı bir kapsamla değişebilir değişkenleri denetlemek için daha kolay ve yanlış şekilde değiştirilmesi olasılığı daha düşüktür.

Kullanarak bir başlangıç değeri değişebilir bir değişkene atayabilirsiniz `let` aynı şekilde bir değer tanımlayacağınız anahtar sözcüğü. Ancak, daha sonra yeni değerleri değişebilir değişkenleri kullanarak atayabilirsiniz olduğunu fark `<-` işleci, aşağıdaki örnekte olduğu gibi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]

İşaretli değerleri `mutable` için otomatik olarak yükseltilebilir `'a ref` kapanım tarafından yakalanan, kapanışları, gibi oluşturan formlar dahil `seq` oluşturucular. Bu gerçekleştiğinde bildirim almak istiyorsanız, uyarı etkinleştirin 3180 proje dosyanızdaki veya derleyicisini çağırma.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[let Bağlamaları](../functions/let-bindings.md)|Kullanma hakkında bilgi sağlar `let` adlarını değerleri ve işlevlere bağlamak için anahtar sözcüğü.|
|[İşlevler](../functions/index.md)|F # işlevleri'ne genel bakış sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Null Değerler](null-Values.md)
- [F# Dili Başvurusu](../index.md)

---
title: Değerler (F#)
description: 'F # değerleri belirli bir türe sahip miktarları nasıl olduğunu öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: b40e4a0409a9161a4ef48c8d4ad82b4da346538e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="values"></a>Değerler

F # belirli bir türe sahip miktarları değerler; değerleri tamsayı veya kayan nokta sayıları, karakter veya metin, listeler, dizileri, dizileri, diziler, ayrılmış birleşimler, kayıtları, sınıf türleri veya işlevi değerleri olabilir.


## <a name="binding-a-value"></a>Bir değer bağlama
Terim *bağlama* bir adı bir tanımıyla ilişkilendirme anlamına gelir. `let` Anahtar sözcüğü bağlar aşağıdaki örneklerde olduğu gibi bir değer:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Bir değerin türü tanımı algılanır. Bir tam sayı veya kayan nokta sayısı gibi basit bir tür için türü sabit türünden belirlenir. Bu nedenle, önceki örnekte türü derleyici oluşturur `b` olmasını `unsigned int`, türü derleyici oluşturur ancak `a` olmasını `int`. Bir işlev değerin türü, işlev gövdesi dönüş değerden belirlenir. İşlev değer türleri hakkında daha fazla bilgi için bkz: [işlevler](../functions/index.md). Değişmez değer türleri hakkında daha fazla bilgi için bkz: [değişmez değerleri](../literals.md).


## <a name="why-immutable"></a>Değişmez neden?
Değişmez değerler bir programın yürütme seyri değiştirilemez değerlerdir. C++, Visual Basic veya C# gibi diller için kullandıysanız, şaşırtıcı F # primacy bir program yürütülmesi sırasında yeni değerler atanabilir değişkenleri yerine değişmez değerler üzerinden geçirir olduğunu görebilirsiniz. Sabit veri işlevsel programlama önemli bir öğedir. Birden çok iş parçacıklı bir ortamda, birçok farklı iş parçacıkları tarafından değiştirilebilecek paylaşılan değişebilir yönetmek zor değişkenlerdir. Ayrıca, değişebilir değişkenlerle, bazen başka bir işleve geçirildiğinde bir değişken değişebilir varsa söyleyin zor olabilir.

Saf işlevsel dillerin değişken vardır ve işlevler kesinlikle matematik işlevleri olarak davranır. Yordam bir dil kodu değeri değiştirmek için bir değişken ataması kullandığı yerde, işlevsel bir dilde eşdeğer kod giriş, sabit bir işlev ve farklı değişmez değerler çıktısı olarak bir sabit değere sahip. Bu matematik strictness program davranışı hakkında akıl daha sıkı sağlar. Ne derleyicileri kodu daha kesin denetlemek ve daha etkili bir şekilde en iyi duruma getirmek için sağlayan daha sıkı bu mantığı olan ve geliştiricilerin anlamak ve doğru kod yazmak kolaylaştırmak yardımcı olur. İşlevsel kod bu nedenle daha sıradan yordam kod hatalarını ayıklamak daha kolay olması olasıdır.

F # saf işlevsel bir dil değil henüz tam olarak işlevsel programlama destekler. Bunun yapılması önemli bir işlevsel programlama açısından yararlanmak kodunuzu verdiğinden değişmez değerleri kullanarak iyi bir uygulamadır.


## <a name="mutable-variables"></a>Değişebilir değişkenleri
Anahtar sözcüğünü kullanabilirsiniz `mutable` değiştirilebilir bir değişken olarak belirtmek için. F # değişebilir değişkenleri, genel bir türünde bir alan veya bir yerel değer olarak sınırlı bir kapsam olmalıdır. Sınırlı kapsam değişebilir değişkenlerle denetlemek için daha kolay ve yanlış şekilde değiştirilmiş olasılığı daha düşüktür.

Kullanarak bir başlangıç değeri değişebilir bir değişkene atayabilirsiniz `let` anahtar ile aynı şekilde bir değer tanımlamanız. Ancak, daha sonra yeni değerleri değişebilir değişkenlere kullanarak atayabilirsiniz olduğunu farktır `<-` aşağıdaki örnekteki gibi işleci.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]
    
## <a name="related-topics"></a>İlgili Konular


|Başlık|Açıklama|
|-----|-----------|
|[let Bağlamaları](../functions/let-bindings.md)|Kullanma hakkında bilgi sağlar `let` değerlerin ve işlevlerin adlarını bağlamak için anahtar sözcüğü.|
|[İşlevler](../functions/index.md)|F # işlevleri genel bir bakış sağlar.|

## <a name="see-also"></a>Ayrıca Bkz.
[Null Değerler](null-Values.md)

[F# Dili Başvurusu](../index.md)

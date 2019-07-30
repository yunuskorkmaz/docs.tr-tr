---
title: Değerler
description: İçindeki F# değerlerin belirli bir türe sahip miktarlar olduğunu öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: ed7a5b069a5a47aacf0cce4cfa754ded46f6e84a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630792"
---
# <a name="values"></a>Değerler

İçindeki F# değerler belirli bir türe sahip olan miktarlardır; değerler tamsayı veya kayan nokta sayıları, karakterler veya metin, listeler, sıralar, diziler, tanımlama grupları, ayırt edici birleşimler, kayıtlar, sınıf türleri veya işlev değerleri olabilir.

## <a name="binding-a-value"></a>Değer bağlama

*Bağlama* terimi, bir adı tanımıyla ilişkilendirme anlamına gelir. `let` Anahtar sözcüğü, aşağıdaki örneklerde olduğu gibi bir değeri bağlar:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Bir değerin türü tanımdan algılanır. İntegral veya kayan noktalı sayı gibi temel bir tür için, tür değişmez değer türünden belirlenir. Bu nedenle, `b` önceki örnekte, derleyici `unsigned int`türünü olarak algılar, ancak derleyici türünü `a` `int`olarak algılar. İşlev değerinin türü, işlev gövdesindeki dönüş değerinden belirlenir. İşlev değeri türleri hakkında daha fazla bilgi için bkz. [işlevler](../functions/index.md). Değişmez türler hakkında daha fazla bilgi için bkz. [değişmez değerler](../literals.md).

Derleyici, varsayılan olarak kullanılmayan bağlamalar hakkında tanılama vermiyor. Bu iletileri almak için, proje dosyanızda veya derleyicisini çağırırken uyarı 1182 ' yı etkinleştirin (bkz `--warnon` . [derleyici seçenekleri](../compiler-options.md)altında).

## <a name="why-immutable"></a>Neden sabit?

Sabit değerler, bir programın yürütülmesi sırasında değiştirilemeyen değerlerdir. C++, Visual Basic veya C#gibi dillerde kullandıysanız, bir programın yürütülmesi sırasında yeni değerler atanabileceği değişkenler yerine, sabit değerler üzerinde en fazla değer elde eden değişken olduğunu F# fark edebilirsiniz. Değişmez veriler fonksiyonel Programlamanın önemli bir öğesidir. Çok iş parçacıklı bir ortamda, birçok farklı iş parçacığı tarafından değiştirilebilen paylaşılan kesilebilir değişkenlerin yönetilmesi zordur. Ayrıca, değişebilir değişkenlerle, bazı durumlarda bir değişkenin başka bir işleve geçirildiğinde değiştirilip değiştirilemeyeceğini söylemek zor olabilir.

Saf işlevsel dillerde değişken yoktur ve işlevler kesinlikle matematik işlevleri olarak davranır. Bir yordamsal dildeki kodun bir değeri değiştirmek için değişken atamasını kullanması durumunda, işlevsel dildeki denk kodun girdi, sabit bir işlev ve çıkış olarak farklı sabit değerler olan sabit bir değeri vardır. Bu matematiksel striclük, programın davranışı hakkında daha sıkı bir yaklaşım sağlar. Bu iyileştirme, derleyicilerin kodu daha kolay bir şekilde denetlemesini ve daha etkili bir şekilde iyileştirmesini sağlar ve geliştiricilerin doğru kodu anlamasına ve yazmasını kolaylaştırır. İşlevsel kodun, normal yordamsal koddan hata ayıklamanın daha kolay olması olasıdır.

F#, saf işlevsel bir dil değildir, ancak işlevsel programlamayı tam olarak destekler. Bu işlemin yapılması, kodunuzun işlevsel programlama açısından önemli bir yönden yararlanmasına olanak sağladığından, sabit değerlerin kullanılması iyi bir uygulamadır.

## <a name="mutable-variables"></a>Değişebilir değişkenler

Değiştirilebilecek bir değişken belirtmek için `mutable` anahtar sözcüğünü kullanabilirsiniz. ' Deki F# kesilebilir değişkenlerin, genellikle bir tür alanı veya yerel değer olarak sınırlı bir kapsamı olmalıdır. Sınırlı bir kapsama sahip kesilebilir değişkenlerin denetimi daha kolaydır ve yanlış yollarla değiştirilmesinin daha düşüktür.

`let` Anahtar sözcüğünü bir değer tanımladığınız şekilde kullanarak, değişebilir bir değişkene bir başlangıç değeri atayabilirsiniz. Bununla birlikte, aşağıdaki örnekte olduğu gibi `<-` işleci kullanarak değiştirilebilir değişkenlere daha sonra yeni değerler atayabilmeniz fark olur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet602.fs)]

Oluşturucular gibi `mutable` kapanışları `'a ref` oluşturan formlar da dahil olmak üzere, işaretlenen değerler otomatik olarak bir kapanış tarafından yakalanarak yükseltilir. `seq` Bu gerçekleştiğinde size bildirilmesini istiyorsanız, proje dosyanızda veya derleyicisini çağırırken uyarı 3180 ' yı etkinleştirin.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[let Bağlamaları](../functions/let-bindings.md)|Adları değerlere ve işlevlere bağlamak `let` için anahtar sözcüğünü kullanma hakkında bilgi sağlar.|
|[İşlevler](../functions/index.md)|İçindeki F#işlevlere genel bir bakış sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Null Değerler](null-Values.md)
- [F# Dili Başvurusu](../index.md)

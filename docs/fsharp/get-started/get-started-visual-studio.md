---
title: Visual Studio F# 'da kullanmaya başlayın
description: Visual Studio ile nasıl F# kullanacağınızı öğrenin.
ms.date: 07/03/2018
ms.openlocfilehash: 80b4fc5b7631eace719832fe32003cad578ead27
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552829"
---
# <a name="get-started-with-f-in-visual-studio"></a>Visual Studio F# 'da kullanmaya başlayın

F#Visual Studio IDE F# 'de de görsel araç desteklenir.

Başlamak için [Visual Studio 'nun F#ile yüklü ](install-fsharp.md#install-f-with-visual-studio)olduğundan emin olun.

## <a name="creating-a-console-application"></a>Konsol uygulaması oluşturma

Visual Studio 'daki en temel projelerden biri konsol uygulamasıdır.  Bunun nasıl yapılacağını aşağıda bulabilirsiniz.  Visual Studio açık olduğunda:

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' yi seçin.

2. Yeni proje iletişim kutusunda, **Şablonlar**altında, **görsel F#** ' i görmeniz gerekir.  F# Şablonları göstermek için bunu seçin.

3. **.NET Core konsol uygulaması** ya da **konsol uygulaması**' nı seçin.

4. Projeyi oluşturmak için Tamam düğmesini seçin! F#  Artık Çözüm Gezgini bir F# proje görmeniz gerekir.

## <a name="writing-your-code"></a>Kodunuzu yazma

Önce bazı kodları yazmaya başlayın.  `Program.fs` dosyasının açık olduğundan emin olun ve ardından içeriğini aşağıdakiler ile değiştirin:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Önceki kod örneğinde, `x` adlı bir girişi alan ve kendisini kendisi ile çarparak `square` bir işlev tanımlanmıştır.  F# [Tür çıkarımı](../language-reference/type-inference.md)kullandığından `x` türünün belirtilmesi gerekmez.  F# Derleyici, çarpma 'nın geçerli olduğu türleri anlamıştır ve `square` nasıl çağrıldığını temel alarak `x` bir tür atayacaktır.  `square`üzerine geldiğinizde, aşağıdakileri görmeniz gerekir:

```fsharp
val square: x:int -> int
```

İşlevin tür imzası olarak bilinen budur.  Şu şekilde okunabilir: "kare x adlı bir tamsayı alan ve tamsayı üreten bir işlevdir".  Derleyicinin şu an için `int` türü `square` olduğunu unutmayın. bunun nedeni, çarpma işlemi *Tüm* türler genelinde geneldir, ancak bunun yerine kapalı bir tür kümesinde geneldir.  F# Derleyici bu noktada `int` çekildi, ancak `square` `float`gibi farklı bir giriş türüyle çağırırsanız tür imzasını ayarlar.

`main`başka bir işlev, `EntryPoint` özniteliğiyle birlikte düzenlenmiş ve bu, F# derleyicinin program yürütmesinin burada başlaması gerektiğini söylemelidir.  Komut satırı bağımsız değişkenlerinin bu işleve geçirilebileceği ve bir tamsayı kodunun döndürüldüğü (genellikle `0`) diğer [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)ile aynı kuralı izler.

Bu işlev, `square` işlevini `12`bir bağımsız değişkeniyle çağıracağız.  F# Derleyici daha sonra `int -> int` (bir `int` alan ve bir `int`üreten bir işlev) `square` türünü atar.  `printfn` çağrısı, C stili programlama dillerine benzer bir biçim dizesi, biçim dizesinde belirtilen parametrelere karşılık gelen parametreler ve sonra sonucu ve yeni bir satırı yazdıran biçimli bir yazdırma işlevidir.

## <a name="running-your-code"></a>Kodunuzu çalıştırma

Kodu çalıştırabilir ve **Ctrl**+**F5**tuşlarına basarak sonuçları görebilirsiniz.  Bu, programı hata ayıklamadan çalıştırır ve sonuçları görmenizi sağlar.  Alternatif olarak, Visual Studio 'da **hata ayıklama** üst düzey menü öğesini seçebilir ve **hata ayıklama olmadan Başlat**' ı seçebilirsiniz.

Artık, Visual Studio 'nun bir sonraki konsol penceresinde yazdırılmış olduğunu görmeniz gerekir:

```console
12 squared is 144!
```

Mühendisi!  Visual Studio 'da ilk F# projenizi oluşturdunuz, bu işlevi çağıran sonuçları yazdırılmış F# bir işlev yazdı ve bazı sonuçları görmek için projeyi çalıştırdık.

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, F# dilin bazı temel özelliklerini kapsayan [turuna F# ](../tour.md)göz atın.  Size bazı özelliklerine F#ilişkin bir genel bakış sunar ve Visual Studio 'ya kopyalayabilir ve çalıştırmak için örnek kod örnekleri sağlarsınız.  Ayrıca belgeler F# [ F# giriş sayfasında](../index.yml)belgeler hakkında daha fazla bilgi edinebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Turu](../tour.md)
- [F#dil başvurusu](../language-reference/index.md)
- [Tür çıkarımı](../language-reference/type-inference.md)
- [Sembol ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)

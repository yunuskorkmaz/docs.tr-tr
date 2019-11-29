---
title: Mac için Visual Studio ile F# çalışmaya başlama
description: Mac için Visual Studio ile kullanmayı F# öğrenin.
ms.date: 07/03/2018
ms.openlocfilehash: cd45ab9c59cef76e4bf85a93f39d8e2ee063d200
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552364"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Mac için Visual Studio ile F# çalışmaya başlama

F#Görsel F# araç Mac için Visual Studio IDE 'de desteklenir. [Mac için Visual Studio yüklü](install-fsharp.md#install-f-with-visual-studio-for-mac)olduğundan emin olun.

## <a name="creating-a-console-application"></a>Konsol uygulaması oluşturma

Mac için Visual Studio ' deki en temel projelerden biri konsol uygulamasıdır.  Bunun nasıl yapılacağını aşağıda bulabilirsiniz.  Mac için Visual Studio açıldıktan sonra:

1. **Dosya** menüsünde, **yeni çözüm**' ı işaret edin.

2. Yeni proje iletişim kutusunda, konsol uygulaması için 2 farklı şablon vardır.  .NET Framework hedefleyen diğer > .NET altında bir tane vardır.  Diğer şablon, .NET Core ' u hedefleyen .NET Core-> uygulamasıdır.  Her iki şablon da bu makalenin amacına göre çalışmalıdır.

3. Konsol uygulaması altında, gerekirse C# olarak F# değiştirin.  İleri gitmek için **İleri** düğmesini seçin!  

4. Projenize bir ad verin ve uygulama için istediğiniz seçenekleri belirleyin.  Ekranın yanındaki Önizleme bölmesi, seçilen seçeneklere göre oluşturulacak dizin yapısını gösterecek şekilde görüntülenir.  

5. **Oluştur**'u tıklatın.  Artık Çözüm Gezgini bir F# proje görmeniz gerekir.

## <a name="writing-your-code"></a>Kodunuzu yazma

Önce bazı kodları yazmaya başlayın.  `Program.fs` dosyasının açık olduğundan emin olun ve ardından içeriğini aşağıdakiler ile değiştirin:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Önceki kod örneğinde, `x` adlı bir girişi alan ve kendisini kendisi ile çarparak `square` bir işlev tanımlanmıştır.  F# [Tür çıkarımı](../language-reference/type-inference.md)kullandığından `x` türünün belirtilmesi gerekmez.  F# Derleyici, çarpma 'nın geçerli olduğu türleri anlamıştır ve `square` nasıl çağrıldığını temel alarak `x` bir tür atayacaktır.  `square`üzerine geldiğinizde, aşağıdakileri görmeniz gerekir:

```console
val square: x:int -> int
```

İşlevin tür imzası olarak bilinen budur.  Şu şekilde okunabilir: "kare x adlı bir tamsayı alan ve tamsayı üreten bir işlevdir".  Derleyicinin şu an için `int` türü `square` olduğunu unutmayın. bunun nedeni, çarpma işlemi *Tüm* türler genelinde geneldir, ancak bunun yerine kapalı bir tür kümesinde geneldir.  F# Derleyici bu noktada `int` çekildi, ancak `square` `float`gibi farklı bir giriş türüyle çağırırsanız tür imzasını ayarlar.

`main`başka bir işlev, `EntryPoint` özniteliğiyle birlikte düzenlenmiş ve bu, F# derleyicinin program yürütmesinin burada başlaması gerektiğini söylemelidir.  Komut satırı bağımsız değişkenlerinin bu işleve geçirilebileceği ve bir tamsayı kodunun döndürüldüğü (genellikle `0`) diğer [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)ile aynı kuralı izler.

Bu işlev, `square` işlevini `12`bir bağımsız değişkeniyle çağıracağız.  F# Derleyici daha sonra `int -> int` (bir `int` alan ve bir `int`üreten bir işlev) `square` türünü atar.  `printfn` çağrısı, C stili programlama dillerine benzer bir biçim dizesi, biçim dizesinde belirtilen parametrelere karşılık gelen parametreler ve sonra sonucu ve yeni bir satırı yazdıran biçimli bir yazdırma işlevidir.

## <a name="running-your-code"></a>Kodunuzu çalıştırma

Kodu çalıştırabilir ve en üst düzey menüsünde **Çalıştır** ' a tıklayıp **hata ayıklama olmadan başlatabilirsiniz**.  Bu işlem, programı hata ayıklamadan çalıştırır ve sonuçları görmenizi sağlar.

Şimdi, Mac için Visual Studio oluşan konsol penceresinde yazdırılmış olan aşağıdakileri görmeniz gerekir:

```console
12 squared is 144!
```

Mühendisi!  İlk F# projenizi Mac için Visual Studio oluşturdunuz, bu işlevi çağıran sonuçları yazdırılmış bir F# işlev yazdı ve bazı sonuçları görmek için projeyi çalıştırdık.

## <a name="using-f-interactive"></a>Etkileşimli F# kullanma

Mac için Visual Studio içinde görsel F# araç oluşturma özelliğinin en iyi özelliklerinden biri F# etkileşimli penceresidir.  Bu kodu çağırabileceğiniz ve sonucu etkileşimli olarak görebileceğiniz bir işleme kod göndermenizi sağlar.

Kullanmaya başlamak için kodunuzda tanımlanan `square` işlevini vurgulayın.  Sonra, üst düzey menüsünden **Düzenle** ' ye tıklayın.  Sonra **seçimi etkileşimli olarak F# gönder**' i seçin.  Bu, kodu F# etkileşimli pencerede yürütür.  Alternatif olarak, seçime sağ tıklayıp **seçimi etkileşimli öğesine F# gönder**' i seçebilirsiniz.  F# Etkileşimli pencerenin içinde aşağıdaki gibi göründüğünü görmeniz gerekir:

```console
>

val square : x:int -> int

>
```

Bu, daha önce işlevin üzerine gelindiğinde gördüğünüz `square` işlevi için aynı işlev imzasını gösterir.  `square` artık F# etkileşimli işlemde tanımlandığından, farklı değerlerle çağırabilirsiniz:

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Bu işlevi yürütür, sonucu yeni bir ada `it`bağlar ve `it`türünü ve değerini görüntüler.  `;;`ile her satırı sonlandırabilmeniz gerektiğini unutmayın.  Bu, işlev F# çağrın ne zaman tamamlandığını etkileşimli olarak bilir.  Etkileşimli ' F# de yeni işlevler de tanımlayabilirsiniz:

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Yukarıdaki `isOdd`yeni bir işlevi tanımlar, bu bir `int` alır ve tek olup olmadığını denetler!  Bu işlevi, farklı girişlerle ne döndürdüğünü görmek için çağırabilirsiniz.  İşlev çağrılarının içindeki işlevleri çağırabilirsiniz:

```console
> isOdd (square 15);;
val it : bool = true
```

Ayrıca, değeri iki işlev için ardışık düzen için [Kanal-iletme işlecini](../language-reference/symbol-and-operator-reference/index.md) de kullanabilirsiniz:

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

Kanal iletme operatörü ve daha fazlası sonraki öğreticilerde ele alınmıştır.

Etkileşimli ile F# yapabileceklerinize yalnızca bir göz atmak yeterlidir.  Daha fazla bilgi edinmek için [ F#ile etkileşimli programlamaya ](../tutorials/fsharp-interactive/index.md)göz atın.

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, F# dilin bazı temel özelliklerini kapsayan [turuna F# ](../tour.md)göz atın.  Bu, bazı özelliklerine F#ilişkin bir genel bakış sağlar ve Mac için Visual Studio kopyalayabilir ve çalıştırmak için örnek kod örnekleri sunar.  Ayrıca, [ F# kılavuzda](../index.yml)gösterilen bazı harika dış kaynaklar da mevcuttur.

## <a name="see-also"></a>Ayrıca bkz.

- [F#Rehberi](../index.yml)
- [F# Turu](../tour.md)
- [F#dil başvurusu](../language-reference/index.md)
- [Tür çıkarımı](../language-reference/type-inference.md)
- [Sembol ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)

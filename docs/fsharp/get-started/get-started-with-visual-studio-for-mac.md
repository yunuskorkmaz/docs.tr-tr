---
title: 'Mac için Visual Studio F # ile çalışmaya başlama'
description: "F # ' Mac için Visual Studio nasıl kullanacağınızı öğrenin."
ms.date: 07/03/2018
ms.openlocfilehash: d2ad24ad18bb31419b39508f2cf555c82fbe2e0b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437990"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Mac için Visual Studio F # ile çalışmaya başlama

F # ve Visual F# araçları Mac için Visual Studio IDE 'de desteklenir. [Mac için Visual Studio yüklü](install-fsharp.md#install-f-with-visual-studio-for-mac)olduğundan emin olun.

## <a name="creating-a-console-application"></a>Konsol uygulaması oluşturma

Mac için Visual Studio ' deki en temel projelerden biri konsol uygulamasıdır.  Bunun nasıl yapılacağı aşağıda açıklanmaktadır.  Mac için Visual Studio açıldıktan sonra:

1. **Dosya** menüsünde, **yeni çözüm**' ı işaret edin.

2. Yeni proje iletişim kutusunda, konsol uygulaması için 2 farklı şablon vardır.  .NET Framework hedefleyen diğer > .NET altında bir tane vardır.  Diğer şablon, .NET Core ' u hedefleyen .NET Core-> uygulamasıdır.  Her iki şablon da bu makalenin amacına göre çalışmalıdır.

3. Konsol uygulaması altında, gerekirse C# ' ı F # olarak değiştirin.  İleri gitmek için **İleri** düğmesini seçin!  

4. Projenize bir ad verin ve uygulama için istediğiniz seçenekleri belirleyin.  Ekranın yanındaki Önizleme bölmesi, seçilen seçeneklere göre oluşturulacak dizin yapısını gösterecek şekilde görüntülenir.  

5. **Oluştur**'a tıklayın.  Artık Çözüm Gezgini bir F # projesi görmeniz gerekir.

## <a name="writing-your-code"></a>Kodunuzu yazma

Önce bazı kodları yazmaya başlayın.  Dosyanın açık olduğundan emin olun `Program.fs` ve ardından içeriğini aşağıdakiler ile değiştirin:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Önceki kod örneğinde, `square` adlı bir girişi alan `x` ve kendisiyle çarpar bir işlev tanımlandı.  F # [tür çıkarımı](../language-reference/type-inference.md)kullandığından, türünün `x` belirtilmesi gerekmez.  F # derleyicisi, çarpma 'nın geçerli olduğu türleri anlamıştır ve `x` nasıl çağrıldığını temel alarak bir tür atar `square` .  Üzerine geldiğinizde `square` , aşağıdakileri görmeniz gerekir:

```console
val square: x:int -> int
```

İşlevin tür imzası olarak bilinen budur.  Şu şekilde okunabilir: "kare x adlı bir tamsayı alan ve tamsayı üreten bir işlevdir".  Derleyicinin `square` `int` Şu an için türü vermiştir. bunun nedeni, çarpma 'nın *Tüm* türler genelinde genel olmaması, ancak kapalı bir tür kümesi genelinde genel olması.  F # derleyicisi `int` Bu noktada çekildi, ancak gibi farklı bir giriş türüyle çağırırsanız tür imzasını ayarlar `square` `float` .

Diğer bir işlev olan, `main` `EntryPoint` F # derleyicisine program yürütmenin bu şekilde başlaması gerektiğini bildirmek için özniteliğiyle donatılmış tanımlanmış.  Komut satırı bağımsız değişkenlerinin bu işleve geçirilebileceği ve bir tamsayı kodunun döndürüldüğü (genellikle) diğer [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)ile aynı kuralı izler `0` .

`square`İşlevi bir bağımsız değişkeniyle çağırdığımız bu işlevde `12` .  F # derleyicisi daha sonra türü `square` `int -> int` (diğer bir deyişle, ' ı alan ve üreten bir işlev) olarak atar `int` `int` .  ' A çağrısı, `printfn` C stili programlama dilleri, biçim dizesinde belirtilen parametrelere karşılık gelen parametreler, ancak sonucu ve yeni bir satırı yazdıran biçim dizesi kullanan biçimli bir yazdırma işlevidir.

## <a name="running-your-code"></a>Kodunuzu çalıştırma

Kodu çalıştırabilir ve en üst düzey menüsünde **Çalıştır** ' a tıklayıp **hata ayıklama olmadan başlatabilirsiniz**.  Bu işlem, programı hata ayıklamadan çalıştırır ve sonuçları görmenizi sağlar.

Şimdi, Mac için Visual Studio oluşan konsol penceresinde yazdırılmış olan aşağıdakileri görmeniz gerekir:

```console
12 squared is 144!
```

Tebrikler!  İlk F # projenizi Mac için Visual Studio oluşturdunuz, bir F # işlevi bu işlevi çağırma sonuçlarını yazdırıldı ve bazı sonuçları görmek için projeyi çalıştırmadınız.

## <a name="using-f-interactive"></a>F# Etkileşimli kullanma

Mac için Visual Studio araç Visual F# araçlarının en iyi özelliklerinden biri F# Etkileşimli penceresidir.  Bu kodu çağırabileceğiniz ve sonucu etkileşimli olarak görebileceğiniz bir işleme kod göndermenizi sağlar.

Kullanmaya başlamak için `square` kodunuzda tanımlanan işlevi vurgulayın.  Sonra, üst düzey menüsünden **Düzenle** ' ye tıklayın.  Sonra **seçimi F# Etkileşimli gönder**' i seçin.  Bu, kodu F# Etkileşimli penceresinde yürütür.  Alternatif olarak, seçime sağ tıklayıp **F# Etkileşimli seçim gönder**' i seçebilirsiniz.  F# Etkileşimli penceresinin içinde aşağıdaki gibi göründüğünü görmeniz gerekir:

```console
>

val square : x:int -> int

>
```

Bu, işlevin `square` üzerine gelindiğinde daha önce gördüğünüz işlev için aynı işlev imzasını gösterir.  `square`Artık F# Etkileşimli işleminde tanımlandığından, farklı değerlerle çağırabilirsiniz:

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Bu, işlevi yürütür, sonucu yeni bir ada bağlar `it` ve türünü ve değerini görüntüler `it` .  Her satırı ile birlikte sonlandırabilmeniz gerektiğini unutmayın `;;` .  Bu, işlev çağrın ne zaman tamamlandığını F# Etkileşimli bilir.  Ayrıca, F# Etkileşimli yeni işlevler de tanımlayabilirsiniz:

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Yukarıdaki yeni bir işlevi tanımlar, `isOdd` `int` ve tek bir olup olmadığını denetler.  Bu işlevi, farklı girişlerle ne döndürdüğünü görmek için çağırabilirsiniz.  İşlev çağrılarının içindeki işlevleri çağırabilirsiniz:

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

Bu, F# Etkileşimli ile yapabileceklerinize yalnızca bir göz alabilir.  Daha fazla bilgi edinmek için, [F # Ile etkileşimli programlamaya](../tools/fsharp-interactive/index.md)göz atın.

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, f # dilinin bazı temel özelliklerini kapsayan [f # turuna](../tour.md)göz atın.  Bu, F # ' ın bazı özelliklerine ilişkin bir genel bakış sağlar ve Mac için Visual Studio kopyalayabilir ve çalıştırmak için örnek kod örnekleri sunar.  Ayrıca, [F # kılavuzunda](../index.yml)kullanabileceğiniz bazı harika dış kaynaklar da mevcuttur.

## <a name="see-also"></a>Ayrıca bkz.

- [F# kılavuzu](../index.yml)
- [F# Turu](../tour.md)
- [F# dil başvurusu](../language-reference/index.md)
- [Tür çıkarımı](../language-reference/type-inference.md)
- [Sembol ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)

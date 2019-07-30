---
title: Mac için Visual Studio ile F# çalışmaya başlama
description: Mac için Visual Studio ile kullanmayı F# öğrenin.
ms.date: 07/03/2018
ms.openlocfilehash: 679ed1ea28f5d0e0d910dbd407b38d1d2f0314f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629759"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Mac için Visual Studio ile F# çalışmaya başlama

F#Görsel F# araç Mac için Visual Studio IDE 'de desteklenir. [Mac için Visual Studio yüklü](install-fsharp.md#install-f-with-visual-studio-for-mac)olduğundan emin olun.

## <a name="creating-a-console-application"></a>Konsol uygulaması oluşturma

Mac için Visual Studio ' deki en temel projelerden biri konsol uygulamasıdır.  Bunun nasıl yapılacağını aşağıda bulabilirsiniz.  Mac için Visual Studio açıldıktan sonra:

1. **Dosya** menüsünde, **yeni çözüm**' ı işaret edin.

2. Yeni proje iletişim kutusunda, konsol uygulaması için 2 farklı şablon vardır.  .NET Framework hedefleyen diğer > .NET altında bir tane vardır.  Diğer şablon, .NET Core ' u hedefleyen .NET Core-> uygulamasıdır.  Her iki şablon da bu makalenin amacına göre çalışmalıdır.

3. Konsol uygulaması altında, gerekirse C# olarak F# değiştirin.  İleri gitmek için **İleri** düğmesini seçin!  

4. Projenize bir ad verin ve uygulama için istediğiniz seçenekleri belirleyin.  Ekranın yanındaki Önizleme bölmesi, seçilen seçeneklere göre oluşturulacak dizin yapısını gösterecek şekilde görüntülenir.  

5.           **Oluştur**'a tıklayın.  Artık Çözüm Gezgini bir F# proje görmeniz gerekir.

## <a name="writing-your-code"></a>Kodunuzu yazma

Önce bazı kodları yazmaya başlayın.  `Program.fs` Dosyanın açık olduğundan emin olun ve ardından içeriğini aşağıdakiler ile değiştirin:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Önceki kod örneğinde, adlı `square` `x` bir girişi alan ve kendisiyle çarpar bir işlev tanımlandı.  F# [Tür çıkarımı](../language-reference/type-inference.md)kullandığından, türünün `x` belirtilmesi gerekmez.  F# Derleyici, çarpma 'nın geçerli olduğu türleri anlamıştır ve nasıl `x` `square` çağrılacaktır temel alınarak bir tür atar.  Üzerine `square`geldiğinizde, aşağıdakileri görmeniz gerekir:

```
val square: x:int -> int
```

İşlevin tür imzası olarak bilinen budur.  Bu, şöyle okunabilir: "Kare x adlı bir tamsayı alan ve bir tamsayı üreten bir işlevdir.  Derleyicinin şu an için `square` `int` türü vermiştir. bunun nedeni, çarpma 'nın *Tüm* türler genelinde genel olmaması, ancak kapalı bir tür kümesi genelinde genel olması.  F# Derleyici bu noktada `int` çekildi, ancak gibi `float`farklı bir giriş türüyle çağrdıysanız `square` tür imzasını ayarlar.

Başka bir işlev `main`,, F# derleyicinin program yürütmesinin bu şekilde başlaması `EntryPoint` gerektiğini bildirmek için özniteliğiyle donatılmış, tanımlı.  Komut satırı bağımsız değişkenlerinin bu işleve geçirilebileceği ve bir tamsayı kodunun döndürüldüğü (genellikle `0`) diğer [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)ile aynı kuralı izler.

`square` İşlevi bir`12`bağımsız değişkeniyle çağırdığımız bu işlevde.  F# Derleyici daha sonra türü `square` olarak `int -> int` atar (yani, bir `int` ve üreten bir `int`işlev).  ' A çağrısı `printfn` , C stili programlama dilleri, biçim dizesinde belirtilen parametrelere karşılık gelen parametreler, ancak sonucu ve yeni bir satırı yazdıran biçim dizesi kullanan biçimli bir yazdırma işlevidir.

## <a name="running-your-code"></a>Kodunuzu çalıştırma

Kodu çalıştırabilir ve en üst düzey menüsünde **Çalıştır** ' a tıklayıp **hata ayıklama olmadan başlatabilirsiniz**.  Bu işlem, programı hata ayıklamadan çalıştırır ve sonuçları görmenizi sağlar.

Şimdi, Mac için Visual Studio oluşan konsol penceresinde yazdırılmış olan aşağıdakileri görmeniz gerekir:

```
12 squared is 144!
```

Tebrikler!  İlk F# projenizi Mac için Visual Studio oluşturdunuz, bu işlevi çağıran sonuçları yazdırılmış bir F# işlev yazdı ve bazı sonuçları görmek için projeyi çalıştırdık.

## <a name="using-f-interactive"></a>Etkileşimli F# kullanma

Mac için Visual Studio içinde görsel F# araç oluşturma özelliğinin en iyi özelliklerinden biri F# etkileşimli penceresidir.  Bu kodu çağırabileceğiniz ve sonucu etkileşimli olarak görebileceğiniz bir işleme kod göndermenizi sağlar.

Kullanmaya başlamak için kodunuzda tanımlanan `square` işlevi vurgulayın.  Sonra, üst düzey menüsünden **Düzenle** ' ye tıklayın.  Sonra **seçimi etkileşimli olarak F# gönder**' i seçin.  Bu, kodu F# etkileşimli pencerede yürütür.  Alternatif olarak, seçime sağ tıklayıp **seçimi etkileşimli öğesine F# gönder**' i seçebilirsiniz.  F# Etkileşimli pencerenin içinde aşağıdaki gibi göründüğünü görmeniz gerekir:

```
>

val square : x:int -> int

>
```

Bu, işlevin üzerine gelindiğinde daha önce gördüğünüz `square` işlev için aynı işlev imzasını gösterir.  `square` Artık F# etkileşimli işlemde tanımlandığından, farklı değerlerle çağırabilirsiniz:

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Bu, işlevi yürütür, sonucu yeni bir ada `it`bağlar ve türünü ve `it`değerini görüntüler.  Her satırı ile birlikte `;;`sonlandırabilmeniz gerektiğini unutmayın.  Bu, işlev F# çağrın ne zaman tamamlandığını etkileşimli olarak bilir.  Etkileşimli ' F# de yeni işlevler de tanımlayabilirsiniz:

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Yukarıdaki yeni bir işlevi `isOdd`tanımlar, ve tek bir `int` olup olmadığını denetler.  Bu işlevi, farklı girişlerle ne döndürdüğünü görmek için çağırabilirsiniz.  İşlev çağrılarının içindeki işlevleri çağırabilirsiniz:

```
> isOdd (square 15);;
val it : bool = true
```

Ayrıca, değeri iki işlev için ardışık düzen için [Kanal-iletme işlecini](../language-reference/symbol-and-operator-reference/index.md) de kullanabilirsiniz:

```
> 15 |> square |> isOdd;;
val it : bool = true
```

Kanal iletme operatörü ve daha fazlası sonraki öğreticilerde ele alınmıştır.

Etkileşimli ile F# yapabileceklerinize yalnızca bir göz atmak yeterlidir.  Daha fazla bilgi edinmek için [ F#ile etkileşimli programlamaya ](../tutorials/fsharp-interactive/index.md)göz atın.

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, F# dilin bazı temel özelliklerini kapsayan [turuna F# ](../tour.md)göz atın.  Bu, bazı özelliklerine F#ilişkin bir genel bakış sağlar ve Mac için Visual Studio kopyalayabilir ve çalıştırmak için örnek kod örnekleri sunar.  Ayrıca, [ F# kılavuzda](../index.md)gösterilen bazı harika dış kaynaklar da mevcuttur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual F#](../index.md)
- [F# Turu](../tour.md)
- [F#dil başvurusu](../language-reference/index.md)
- [Tür çıkarımı](../language-reference/type-inference.md)
- [Sembol ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)

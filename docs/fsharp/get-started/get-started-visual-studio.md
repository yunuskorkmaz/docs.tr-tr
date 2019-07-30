---
title: Visual Studio F# 'da kullanmaya başlayın
description: Visual Studio ile nasıl F# kullanacağınızı öğrenin.
ms.date: 07/03/2018
ms.openlocfilehash: 24c9a81cfa61dc904db9b2213224677696d7eb9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629774"
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

Önce bazı kodları yazmaya başlayın.  `Program.fs` Dosyanın açık olduğundan emin olun ve ardından içeriğini aşağıdakiler ile değiştirin:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Önceki kod örneğinde, adlı `square` `x` bir girişi alan ve kendisiyle çarpar bir işlev tanımlandı.  F# [Tür çıkarımı](../language-reference/type-inference.md)kullandığından, türünün `x` belirtilmesi gerekmez.  F# Derleyici, çarpma 'nın geçerli olduğu türleri anlamıştır ve nasıl `x` `square` çağrılacaktır temel alınarak bir tür atar.  Üzerine `square`geldiğinizde, aşağıdakileri görmeniz gerekir:

```fsharp
val square: x:int -> int
```

İşlevin tür imzası olarak bilinen budur.  Bu, şöyle okunabilir: "Kare x adlı bir tamsayı alan ve bir tamsayı üreten bir işlevdir.  Derleyicinin şu an için `square` `int` türü vermiştir. bunun nedeni, çarpma 'nın *Tüm* türler genelinde genel olmaması, ancak kapalı bir tür kümesi genelinde genel olması.  F# Derleyici bu noktada `int` çekildi, ancak gibi `float`farklı bir giriş türüyle çağrdıysanız `square` tür imzasını ayarlar.

Başka bir işlev `main`,, F# derleyicinin program yürütmesinin bu şekilde başlaması `EntryPoint` gerektiğini bildirmek için özniteliğiyle donatılmış, tanımlı.  Komut satırı bağımsız değişkenlerinin bu işleve geçirilebileceği ve bir tamsayı kodunun döndürüldüğü (genellikle `0`) diğer [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)ile aynı kuralı izler.

`square` İşlevi bir`12`bağımsız değişkeniyle çağırdığımız bu işlevde.  F# Derleyici daha sonra türü `square` olarak `int -> int` atar (yani, bir `int` ve üreten bir `int`işlev).  ' A çağrısı `printfn` , C stili programlama dilleri, biçim dizesinde belirtilen parametrelere karşılık gelen parametreler, ancak sonucu ve yeni bir satırı yazdıran biçim dizesi kullanan biçimli bir yazdırma işlevidir.

## <a name="running-your-code"></a>Kodunuzu çalıştırma

Kodu çalıştırıp **CTRL**+**F5**tuşuna basarak sonuçları görebilirsiniz.  Bu, programı hata ayıklamadan çalıştırır ve sonuçları görmenizi sağlar.  Alternatif olarak, Visual Studio 'da **hata ayıklama** üst düzey menü öğesini seçebilir ve **hata ayıklama olmadan Başlat**' ı seçebilirsiniz.

Artık, Visual Studio 'nun bir sonraki konsol penceresinde yazdırılmış olduğunu görmeniz gerekir:

```
12 squared is 144!
```

Tebrikler!  Visual Studio 'da ilk F# projenizi oluşturdunuz, bu işlevi çağıran sonuçları yazdırılmış F# bir işlev yazdı ve bazı sonuçları görmek için projeyi çalıştırdık.

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, F# dilin bazı temel özelliklerini kapsayan [turuna F# ](../tour.md)göz atın.  Size bazı özelliklerine F#ilişkin bir genel bakış sunar ve Visual Studio 'ya kopyalayabilir ve çalıştırmak için örnek kod örnekleri sağlarsınız.  Ayrıca, [ F# kılavuzda](../index.md)gösterilen bazı harika dış kaynaklar da mevcuttur.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Turu](../tour.md)
- [F#dil başvurusu](../language-reference/index.md)
- [Tür çıkarımı](../language-reference/type-inference.md)
- [Sembol ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)

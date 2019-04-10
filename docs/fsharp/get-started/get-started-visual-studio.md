---
title: Kullanmaya başlama F# Visual Studio'da
description: Nasıl kullanacağınızı öğrenin F# Visual Studio ile.
ms.date: 07/03/2018
ms.openlocfilehash: 020e5d32b3aa5d5a2195c19d70d8fe684fbd56ef
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331916"
---
# <a name="get-started-with-f-in-visual-studio"></a>Kullanmaya başlama F# Visual Studio'da

F#ve görsel F# araçları, Visual Studio IDE içinde desteklenir.

Başlamak için sahip olduğunuzdan emin olun [Visual Studio ile yüklenen F# ](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Bir konsol uygulaması oluşturma

Visual Studio'da en temel projelerden birine bir konsol uygulamasıdır.  Nasıl yapılacağı aşağıda verilmiştir.  Visual Studio'yu açtıktan sonra:

1. Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.

2. Yeni iletişim kutusunda, altında proje **şablonları**, görmelisiniz **Visual F#** .  Bu göstermek için F# şablonları.

3. Şunlardan birini seçin **.NET Core konsol uygulaması** veya **konsol uygulaması**.

3. Seçin **Tamam** oluşturmak için düğmeyi F# proje!  Görmelisiniz bir F# Çözüm Gezgini'nde proje.

## <a name="writing-your-code"></a>Kod yazma

Öncelikle bazı kodlar yazarak Haydi başlayalım.  Emin olun `Program.fs` dosya açıksa ve sonra dosyanın içeriğini aşağıdakilerle değiştirin:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

Önceki kod örneğinde, bir işlev `square` adlı girdi aldığı tanımlanan `x` ve kendisi tarafından çarpar.  Çünkü F# kullanan [tür çıkarımı](../language-reference/type-inference.md), türü `x` belirtilmesi gerekmez.  F# Derleyici çarpma olduğu geçerli türlerinin bilincindedir ve bir türe atar `x` bağlı `square` çağrılır.  Üzerine gelin, `square`, aşağıdaki görmeniz gerekir:

```
val square: x:int -> int
```

İşlevin türü imza olarak bilinen budur.  Aşağıdaki gibi okunabilir: "Kare adlı bir tamsayı alan bir işlev, x ve bir tamsayı üretir".  Derleyici verdiğiniz Not `square` `int` türü çarpma arasında genel olmadığından budur şimdilik - *tüm* türleri, ancak yerine kapalı türleri arasında genel kümesidir.  F# Çekilen derleyici `int` şu anda noktası, ancak ayarlamak tür imzası çağırırsanız `square` farklı bir giriş türü gibi bir `float`.

Başka bir işlev `main`, tanımlanır ile donatılmış `EntryPoint` bildirmek için öznitelik F# program yürütmesini derleyici var. başlamalıdır.  Diğer ile aynı kuralı izler [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)burada komut satırı bağımsız değişkenleri için bu işlevi geçirilebilir ve bir tamsayı kodu döndürdü (genellikle `0`).

Dediğimiz Bu işlevde harcanan olan `square` işlevi bağımsız `12`.  F# Derleyici sonra türünü atar `square` olmasını `int -> int` (diğer bir deyişle, alan bir işlev bir `int` ve üreten bir `int`).  Çağrı `printfn` C stili programlama dilleri, Biçim dizesinde belirtilen platformlarla karşılık gelen parametreleri için benzer bir biçim dizesi kullanan biçimlendirilmiş bir yazdırma işlevi ve ardından sonucu ve yeni bir satır yazdırır.

## <a name="running-your-code"></a>Kodunuzu çalıştıran

Kodu çalıştırmak ve sonuçları tuşlarına basarak görmek **Ctrl**+**F5**.  Bu, hata ayıklama olmadan programı çalıştırır ve sonuçları görmenizi sağlar.  Alternatif olarak, seçebileceğiniz **hata ayıklama** üst düzey menü öğesi Visual Studio'da ve seçin **hata ayıklama olmadan Başlat**.

Şimdi Visual Studio açıldığını konsol penceresine yazdırılan aşağıdaki görmeniz gerekir:

```
12 squared is 144!
```

Tebrikler!  İlk oluşturduğunuz F# yazılan Visual Studio projesinde bir F# işlevi, işlev ve bazı sonuçları görmek için projenizi çalıştırarak arama sonuçlarının yazdırılır.

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, kullanıma [Turu F# ](../tour.md), bazı çekirdek özellikleri kapsayan F# dili.  Size bazı özelliklerine genel bir bakış sunacak F#ve Visual Studio'ya kopyalayın ve çalıştırılan bol miktarda kod örnekleri sağlar.  Ayrıca kullanabileceğiniz bazı harika dış kaynaklar verilmiştir büyütmüş içinde [ F# Kılavuzu](../index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# turu](../tour.md)
- [F#Dil Başvurusu](../language-reference/index.md)
- [Tür çıkarımı](../language-reference/type-inference.md)
- [Simge ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)

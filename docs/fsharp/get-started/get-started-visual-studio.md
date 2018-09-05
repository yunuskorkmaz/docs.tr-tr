---
title: "Visual Studio'da F # ile çalışmaya başlama"
description: 'F # ile Visual Studio kullanmayı öğrenin.'
ms.date: 07/03/2018
ms.openlocfilehash: 3dac8466501338873aeb308ceac9274a7934a8a9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563852"
---
# <a name="get-started-with-f-in-visual-studio"></a>Visual Studio'da F # ile çalışmaya başlama

F # ve Visual F # Araçları, Visual Studio IDE içinde desteklenir.

Başlamak için sahip olduğunuzdan emin olun [yüklü F # ile Visual Studio](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Bir konsol uygulaması oluşturma

Visual Studio'da en temel projelerden birine bir konsol uygulamasıdır.  Nasıl yapılacağı aşağıda verilmiştir.  Visual Studio'yu açtıktan sonra:

1. Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.

2.  Yeni iletişim kutusunda, altında proje **şablonları**, görmelisiniz **Visual F #**.  F # şablonları göstermek için bunu seçin.

3. Şunlardan birini seçin **.NET Core konsol uygulaması** veya **konsol uygulaması**.

3. Seçin **Tamam** F # projesi oluşturmak için!  Çözüm Gezgini'nde bir F # projesi görmelisiniz.

## <a name="writing-your-code"></a>Kod yazma

Öncelikle bazı kodlar yazarak Haydi başlayalım.  Emin olun `Program.fs` dosya açıksa ve sonra dosyanın içeriğini aşağıdakilerle değiştirin:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

Önceki kod örneğinde, bir işlev `square` adlı girdi aldığı tanımlanan `x` ve kendisi tarafından çarpar.  F # kullandığından [tür çıkarımı](../language-reference/type-inference.md), türü `x` belirtilmesi gerekmez.  F # derleyicisi çarpma olduğu geçerli türlerinin bilincindedir ve bir türe atar `x` bağlı `square` çağrılır.  Üzerine gelin, `square`, aşağıdaki görmeniz gerekir:

```
val square: x:int -> int
```

İşlevin türü imza olarak bilinen budur.  Bunu aşağıdaki gibi okunabilir: "kare adlı bir tamsayı alan bir işlev, x ve bir tamsayı üretir".  Derleyici verdiğiniz Not `square` `int` türü çarpma arasında genel olmadığından budur şimdilik - *tüm* türleri, ancak yerine kapalı türleri arasında genel kümesidir.  F # derleyicisi çekilen `int` şu anda noktası, ancak ayarlamak tür imzası çağırırsanız `square` farklı bir giriş türü gibi bir `float`.

Başka bir işlev `main`, tanımlanır ile donatılmış `EntryPoint` F # derleyicisi, program yürütme bildirmek için özniteliği var. başlamalıdır.  Diğer ile aynı kuralı izler [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)burada komut satırı bağımsız değişkenleri için bu işlevi geçirilebilir ve bir tamsayı kodu döndürdü (genellikle `0`).

Dediğimiz Bu işlevde harcanan olan `square` işlevi bağımsız `12`.  F # derleyicisi sonra türünü atar `square` olmasını `int -> int` (diğer bir deyişle, alan bir işlev bir `int` ve üreten bir `int`).  Çağrı `printfn` C stili programlama dilleri, Biçim dizesinde belirtilen platformlarla karşılık gelen parametreleri için benzer bir biçim dizesi kullanan biçimlendirilmiş bir yazdırma işlevi ve ardından sonucu ve yeni bir satır yazdırır.

## <a name="running-your-code"></a>Kodunuzu çalıştıran

Kodu çalıştırmak ve sonuçları tuşlarına basarak görmek **Ctrl**+**F5**.  Bu, hata ayıklama olmadan programı çalıştırır ve sonuçları görmenizi sağlar.  Alternatif olarak, seçebileceğiniz **hata ayıklama** üst düzey menü öğesi Visual Studio'da ve seçin **hata ayıklama olmadan Başlat**.

Şimdi Visual Studio açıldığını konsol penceresine yazdırılan aşağıdaki görmeniz gerekir:

```
12 squared is 144!
```

Tebrikler!  İlk F # projenizi Visual Studio'da oluşturulan, F # işlevi, işlev çağırma sonuçları yazdırılan yazılan ve bazı sonuçları görmek için projeyi çalıştırın.

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, kullanıma [turu, F #](../tour.md), F # dilinin temel özelliklerinden bazıları kapsayan.  Bazı F # özelliklerine genel bir bakış sunar ve Visual Studio'ya kopyalayıp çalıştırabilirsiniz bol miktarda kod örnekleri sağlamak.  Ayrıca kullanabileceğiniz bazı harika dış kaynaklar verilmiştir büyütmüş içinde [F # Kılavuzu](../index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Turu](../tour.md)
- [F # dili başvurusu](../language-reference/index.md)
- [Tür çıkarımı](../language-reference/type-inference.md)
- [Simge ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)

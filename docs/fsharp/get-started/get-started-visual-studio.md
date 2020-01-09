---
title: Visual Studio F# 'da kullanmaya başlayın
description: Visual Studio ile nasıl F# kullanacağınızı öğrenin.
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337343"
---
# <a name="get-started-with-f-in-visual-studio"></a>Visual Studio F# 'da kullanmaya başlayın

F#Visual Studio tümleşik F# geliştirme ORTAMıNDA (IDE) Visual araçları desteklenir.

Başlamak için, [Visual Studio 'nun destek F# ile yüklü](install-fsharp.md#install-f-with-visual-studio)olduğundan emin olun.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

Visual Studio 'daki en temel projelerden biri konsol uygulamasıdır. Bunun nasıl oluşturulacağı aşağıda verilmiştir:

1. Visual Studio 2019 ' i açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, dil listesinden öğesini seçin **F#** .

4. **Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

5. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna bir ad girin. Ardından **Oluştur**' u seçin.

   Visual Studio yeni F# projeyi oluşturur. Çözüm Gezgini penceresinde görebilirsiniz.

## <a name="write-the-code"></a>Kodu yazma

Biraz kod yazarak başlayalım. `Program.fs` dosyasının açık olduğundan emin olun ve ardından içeriğini aşağıdakiler ile değiştirin:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Önceki kod örneği, `x` adlı bir girişi alan `square` adlı bir işlevi tanımlar ve kendisiyle çarpar. F# [Tür çıkarımı](../language-reference/type-inference.md)kullandığından `x` türünün belirtilmesi gerekmez. F# Derleyici, çarpma 'nın geçerli olduğu türleri anlamıştır ve `square` nasıl çağrıldığını temel alarak `x` bir tür atar. `square`üzerine geldiğinizde, aşağıdakileri görmeniz gerekir:

```fsharp
val square: x:int -> int
```

İşlevin tür imzası olarak bilinen budur. Şu şekilde okunabilir: "kare x adlı bir tamsayı alan ve tamsayı üreten bir işlevdir". Derleyici, `int` türü `square` verdi; Bunun nedeni, çarpma 'nın *Tüm* türler genelinde genel olmaması, ancak kapalı bir tür kümesidir. `float`F# gibi farklı bir giriş türüyle `square` çağırırsanız derleyici tür imzasını ayarlar.

`main`, `EntryPoint` özniteliğiyle donatılmış başka bir işlev tanımlanmış. Bu öznitelik, F# derleyicinin program yürütmesinin burada başlaması gerektiğini söyler. Komut satırı bağımsız değişkenlerinin bu işleve geçirilebileceği ve bir tamsayı kodunun döndürüldüğü (genellikle `0`) diğer [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)ile aynı kuralı izler.

Bir `12`bağımsız değişkeniyle `square` işlevini çağırdığınız `main`giriş noktası işlevidir. F# Derleyici daha sonra `int -> int` (bir `int` alan ve bir `int`üreten bir işlev) `square` türünü atar. `printfn` çağrısı, biçim dizesi kullanan ve sonucu yazdıran (ve yeni bir satır) biçimli bir yazdırma işlevidir. C stili programlama dillerine benzer biçim dizesinde, kendisine geçirilen bağımsız değişkenlere karşılık gelen parametreler (`%d`) bulunur, bu durumda `12` ve `(square 12)`.

## <a name="run-the-code"></a>Kodu çalıştırma

Kodu çalıştırabilir ve **Ctrl**+**F5**tuşlarına basarak sonuçları görebilirsiniz. Alternatif olarak, üst düzey menü çubuğundan hata **ayıklama** > **Başlat** ' ı seçebilirsiniz. Bu, programı hata ayıklama olmadan çalıştırır.

Aşağıdaki çıktı, Visual Studio 'nun açtığı konsol penceresine yazdırır:

```console
12 squared is: 144!
```

Tebrikler! Visual Studio 'da ilk F# projenizi oluşturdunuz, bir değeri hesaplayan ve yazdıran F# bir işlev yazdı ve sonuçları görmek için projeyi çalıştırdık.

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, F# dilin bazı temel özelliklerini kapsayan [turuna F# ](../tour.md)göz atın. Visual Studio 'ya kopyalayabileceğiniz ve çalıştırmak için kullanabileceğiniz bazı yetenekler F# ve örnek kod örnekleri hakkında genel bir bakış sunar.

> [!div class="nextstepaction"]
> [F# Turu](../tour.md)

## <a name="see-also"></a>Ayrıca bkz.

- [F#dil başvurusu](../language-reference/index.md)
- [Tür çıkarımı](../language-reference/type-inference.md)
- [Sembol ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)

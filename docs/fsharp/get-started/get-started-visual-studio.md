---
title: "F # Visual Studio ile çalışmaya başlama"
description: "F # Visual Studio ile nasıl kullanacağınızı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 944bbbba6a26634ace269d86cbbdde9ef9de7bcd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="get-started-with-f-in-visual-studio"></a>F # Visual Studio ile çalışmaya başlama

F # ve Visual F # Araçları Visual Studio IDE içinde desteklenir.  Başlamak için aşağıdakileri yapmalısınız [Visual Studio indirme](https://www.visualstudio.com/downloads/download-visual-studio-vs), henüz yapmadıysanız.  Bu makalede Visual Studio 2017 Community Edition kullanır, ancak F # tercih ettiğiniz sürümüyle kullanabilirsiniz.

## <a name="installing-f"></a>F # yükleme #

İlk olarak Visual Studio indirme değilse, önce Visual Studio yükleyicisi yükler.  Visual Studio 2017 herhangi bir sürümünü Yükleyiciden yükleyin. Yüklü zaten varsa tıklatın **Değiştir**.

Sonraki iş yüklerinin bir listesini görürsünüz. F # aşağıdaki iş yüklerini kanalıyla yükleyebilirsiniz:

|İş yükü|Eylem|
|--------|------|
| .NET core platformlar arası geliştirme | Hiçbir eylem - F # varsayılan olarak yüklenir |
| ASP.NET ve web geliştirme | Hiçbir eylem - F # varsayılan olarak yüklenir |
| Azure geliştirme | Hiçbir eylem - F # varsayılan olarak yüklenir |
| .NET ile Mobil Geliştirme | Hiçbir eylem - F # varsayılan olarak yüklenir |
| Veri bilimi ve analitik uygulamalar | Hiçbir eylem - F # varsayılan olarak yüklenir |
| .NET masaüstü geliştirme | Seçin **F # Masaüstü dil desteği** sağ taraftaki |
| Veri depolama ve işleme | Seçin **F # Masaüstü dil desteği** sağ taraftaki |

Bundan sonra öğesini **Değiştir** alt sağ tarafındaki.  Bu, seçtiğiniz her şeyi yükler.  Tıklayarak Visual Studio 2017 F # dili desteği ile sonra açabilirsiniz **başlatma**.

## <a name="creating-a-console-application"></a>Bir konsol uygulaması oluşturma

Visual Studio'da en temel projeler konsol uygulaması biridir.  Bunun nasıl yapılacağı aşağıda verilmiştir.  Visual Studio açıldıktan sonra:

1. Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.

2.  Yeni Proje iletişim kutusunda, altında **şablonları**, görmeniz gerekir **Visual F #**.  F # şablonları göstermek için bunu seçin.

3. Şunlardan birini seçin **.NET Core konsol uygulaması** veya **konsol uygulaması**.

3. Seçin **Tamam** F # projesi oluşturmak için düğmesini!  F # projesinde Solution Explorer'da görmelisiniz.

## <a name="writing-your-code"></a>Kod yazma

İlk olarak bazı kodlar yazarak başlayalım.  Olduğundan emin olun `Program.fs` dosya açın ve ardından içeriğini aşağıdakilerle değiştirin:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

Önceki kod örneğinde, bir işlev `square` adlı bir girdi aldığı tanımlanmış `x` ve hizmeti kendi başına çoğaltır.  F # kullandığından [tür çıkarımı](../language-reference/type-inference.md), türü `x` belirtilmesi gerekmez.  F # derleyici çarpma olduğu geçerli türleri anlar ve bir türe atayacaktır `x` hakkında temel `square` olarak adlandırılır.  Üzerine getirirseniz `square`, aşağıdaki görmeniz gerekir:

```
val square: x:int -> int
```

Bu ne işlev türü imza olarak bilinir.  Bunu şu şekilde okunabilir: "kare adlı bir tamsayı alan bir işlevi olduğunu x ve tamsayı üretir".  Derleyici vermiş Not `square` `int` türü çarpma arasında genel olmadığından budur şimdilik - *tüm* türleri, ancak bunun yerine kapalı türleri arasında genel kümesidir.  F # derleyici çekilen `int` şu anda noktası, ancak Ayarla tür imzası çağırırsanız `square` farklı bir giriş türü gibi bir `float`.

Başka bir işlev `main`, tanımlanan ile donatılmış `EntryPoint` Bu program yürütme F # derleyici bildirmek için özniteliği yok başlamalıdır.  Aynısına diğer izleyen [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), burada komut satırı bağımsız değişkenleri bu işleve geçirilebilir ve bir tamsayı kodu döndürdü (genellikle `0`).

Diyoruz Bu işlevde olduğu `square` işlevi bağımsız değişkeninin ile `12`.  F # derleyici sonra türünü atar `square` olmasını `int -> int` (diğer bir deyişle, alan işlevi bir `int` ve üreten bir `int`).  Çağrı `printfn` C stili programlama dilleri, Biçim dizesinde belirtilen karşılık gelen parametreleri için benzer bir biçim dizesi kullanan biçimlendirilmiş bir yazdırma işlevi ve sonuç ve yeni bir satır yazdırır.

## <a name="running-your-code"></a>Kodunuzu çalıştırmaya

Kodu çalıştırmak ve sonuçları tuşlarına basarak görmek **ctrl-f5**.  Bu program hata ayıklama olmadan çalıştırma ve sonuçları görmenizi sağlar.  Alternatif olarak, seçebileceğiniz **hata ayıklama** en üst düzey menü öğesi Visual Studio'da ve seçin **hata ayıklama olmadan Başlat**.

Visual Studio Sil'i yukarı konsol penceresine yazdırılan aşağıdaki görmelisiniz:

```
12 squared is 144!
```

Tebrikler!  Visual Studio'da ilk F # projenize oluşturulan, bu işlev çağırma sonuçları bir F # işlevi yazdırılan yazılır ve bazı sonuçları görmek için projesini çalıştırın.

## <a name="using-f-interactive"></a>F # Etkileşimli kullanma

En iyi özelliklerini Visual F Visual Studio'da tooling # F # Etkileşimli pencere biridir.  Burada bu kodu çağırın ve sonuçları etkileşimli olarak görmek bir işlem kodu üzerinden göndermenize olanak sağlar.

Kullanmaya başlamak için vurgulayın `square` kodunuzda tanımlanan işlevi.  Ardından, tutun **Alt** anahtar ve tuşuna **Enter**.  Bu kod F # Etkileşimli penceresinde yürütür.  F # Etkileşimli aşağıdakileri görünür penceresini görmeniz gerekir:

```
>

val square : x:int -> int

>
```

Bu aynı işlev imzası gösterir `square` işlevi üzerine getirildiği oluşturduğunuzda, daha önce gördüğünüzle işlevi.  Çünkü `square` olduğundan F # Etkileşimli işlemde tanımlanan şimdi farklı değerlerle çağırabilirsiniz:

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Bu işlev çalıştırır, yeni bir ad sonucu bağlar `it`, türünü ve değerini görüntüler `it`.  Her satırın bitmesi Not `;;`.  Nasıl F # Etkileşimli işlev çağrısı bittiği bilir budur.  F # Etkileşimli'de yeni işlevler de tanımlayabilirsiniz:

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Yukarıdaki yeni bir işlev tanımlayan `isOdd`, hangi alır bir `int` ve tek olup olmadığını görmek için denetimleri! Neler farklı girişle döndürür görmek için bu işlevi çağırabilirsiniz.  İşlev çağrıları işlevlerinde çağırabilirsiniz:

```
> isOdd (square 15);;
val it : bool = true
```

De kullanabilirsiniz [kanal İleri işleci](../language-reference/symbol-and-operator-reference/index.md) değeri iki işlevlerini kanalı için:

```
> 15 |> square |> isOdd;;
val it : bool = true
```

Kanal İleri işleci ve daha fazlası sonraki öğreticilerde ele alınmıştır.

F # Etkileşimli ile neler yapabileceğinizi içine yalnızca bir bakışta budur. Daha fazla bilgi için kullanıma [etkileşimli programlama F # ile](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, kullanıma [Tur, F #](../tour.md), hangi kapsayan F # dilinin temel özelliklerden bazıları.  Bu bazı F # özelliklerini genel bakış sağlar ve Visual Studio'ya kopyalama ve çalıştırma geniş kod örnekleri sağlar.  Ayrıca kullanabileceğiniz bazı harika dış kaynaklara vardır, showcased [F # Kılavuzu](../index.md).

## <a name="see-also"></a>Ayrıca bkz.
 [Visual F #](index.md)  
 [F # turu](../tour.md)  
 [F # dili başvurusu](../language-reference/index.md)  
 [Tür çıkarımı](../language-reference/type-inference.md)  
 [Simge ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)  

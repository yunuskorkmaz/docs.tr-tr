---
title: 'F # Visual Studio için Mac kullanmaya başlama'
description: 'F # Visual Studio ile Mac için nasıl kullanacağınızı öğrenin'
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f56d67a7ecb9c68703638cbe05d8531891c132cd
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>F # Visual Studio için Mac kullanmaya başlama

F # ve Visual F # Araçları Visual Studio'da Mac IDE için desteklenir.  Başlamak için aşağıdakileri yapmalısınız [Mac için Visual Studio indirme](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), henüz yapmadıysanız.  Bu makalede, Mac için Visual Studio Community 2017 kullanır, ancak F # tercih ettiğiniz sürümüyle kullanabilirsiniz.

## <a name="installing-f"></a>F # yükleme #

Mac için Visual Studio indirdikten sonra yüklemek istediğiniz seçmenizi ister.  Bu makalede amaçları doğrultusunda biz Varsayılanları bırakarak.  Windows için Visual Studio aksine, özellikle F # desteği yüklemeniz gerekmez.  Devam etmek için "Yükle" tuşlarına basın.

Yükleme tamamlandıktan sonra "Visual Studio Başlat" ı seçin.  Ayrıca, Bulucu üzerinde macOS başlatabilirsiniz.

## <a name="creating-a-console-application"></a>Bir konsol uygulaması oluşturma

Mac için Visual Studio en temel projeler konsol uygulaması biridir.  Bunun nasıl yapılacağı aşağıda verilmiştir.  Mac için Visual Studio açıldıktan sonra:

1. Üzerinde **dosya** menüsündeki **yeni çözüm**.

2.  Yeni Proje iletişim kutusunda, konsol uygulaması için 2 farklı şablonlar vardır.  Bir diğer altında olduğundan, .NET Framework hedefler .NET ->.  Diğer .NET Core altında şablonudur .NET Core hedefler uygulamasını ->.  Bu makalede amacıyla ya da şablon çalışması gerekir.

3. Konsol uygulaması altında C# F # için gerekiyorsa değiştirin.  Seçin **sonraki** ilerlemek için düğmesini!  

4. Projenizi adlandırın ve uygulama için istediğiniz seçenekleri seçin.  Bildirim, oluşturulacak dizin yapısını gösteren ekran tarafına önizleme bölmesinde seçilen seçeneklere dayalı.  

5. **Oluştur**'u tıklatın.  F # projesinde Solution Explorer'da görmelisiniz.

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

Kodu çalıştırmak ve sonuçları tıklayarak görmek **çalıştırmak** en üst düzey menüsünde ve ardından **hata ayıklama olmadan Başlat**.  Bu program hata ayıklama olmadan çalıştırma ve sonuçları görmenizi sağlar.

Mac için Visual Studio Sil'i yukarı konsol penceresine yazdırılan aşağıdaki görmelisiniz:

```
12 squared is 144!
```

Tebrikler!  İlk F # projenizi Visual Studio'da Mac için oluşturulan, bu işlev çağırma sonuçları bir F # işlevi yazdırılan yazılır ve bazı sonuçları görmek için projesini çalıştırın.

## <a name="using-f-interactive"></a>F # Etkileşimli kullanma

En iyi özelliklerini Visual F Mac için Visual Studio Araçları # F # Etkileşimli pencere biridir.  Burada bu kodu çağırın ve sonuçları etkileşimli olarak görmek bir işlem kodu üzerinden göndermenize olanak sağlar.

Kullanmaya başlamak için vurgulayın `square` kodunuzda tanımlanan işlevi.  Ardından, tıklayın **Düzenle** en üst düzey menüsünden.  Ardından **seçimi F # Etkileşimli için Gönder getirin**.  Bu kod F # Etkileşimli penceresinde yürütür.  Alternatif olarak, seçime sağ tıklatın ve seçin **seçimi F # Etkileşimli için Gönder getirin**.  F # Etkileşimli aşağıdakileri görünür penceresini görmeniz gerekir:

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

Yukarıdaki yeni bir işlev tanımlayan `isOdd`, hangi alır bir `int` ve tek olup olmadığını görmek için denetimleri!  Neler farklı girişle döndürür görmek için bu işlevi çağırabilirsiniz.  İşlev çağrıları işlevlerinde çağırabilirsiniz:

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

F # Etkileşimli ile neler yapabileceğinizi içine yalnızca bir bakışta budur.  Daha fazla bilgi için kullanıma [etkileşimli programlama F # ile](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, kullanıma [Tur, F #](../tour.md), hangi kapsayan F # dilinin temel özelliklerden bazıları.  Bunu genel bir bakış bazı F # özelliklerini verin ve Mac için Visual Studio'ya kopyalayıp çalıştırabilirsiniz geniş kod örnekleri sağlayın.  Ayrıca kullanabileceğiniz bazı harika dış kaynaklara vardır, showcased [F # Kılavuzu](../index.md).

## <a name="see-also"></a>Ayrıca bkz.
 [Visual F#](../index.md)  
 [F# Turu](../tour.md)  
 [F # dili başvurusu](../language-reference/index.md)  
 [Tür çıkarımı](../language-reference/type-inference.md)  
 [Simge ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)  

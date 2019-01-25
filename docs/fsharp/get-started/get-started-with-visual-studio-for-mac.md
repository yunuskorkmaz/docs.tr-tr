---
title: Kullanmaya başlama F# Mac için Visual Studio
description: Nasıl kullanacağınızı öğrenin F# Mac için Visual Studio ile
ms.date: 07/03/2018
ms.openlocfilehash: e37600b2ca8f845ec1068a55ff1f9964d2527742
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604177"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Kullanmaya başlama F# Mac için Visual Studio

F#ve görsel F# Mac IDE için Visual Studio Araçları desteklenir. Sahip olduğunuzdan emin olun [yüklü Mac için Visual Studio](install-fsharp.md#install-f-with-visual-studio-for-mac).

## <a name="creating-a-console-application"></a>Bir konsol uygulaması oluşturma

Mac için Visual Studio'daki en temel projelerden birine bir konsol uygulamasıdır.  Nasıl yapılacağı aşağıda verilmiştir.  Mac için Visual Studio açık olduğunda:

1. Üzerinde **dosya** menüsünde **yeni çözüm**.

2.  Yeni Proje iletişim kutusunda, konsol uygulaması için 2 farklı şablonlar vardır.  Bir diğer altında .NET Framework'ü hedefleyen .NET ->.  Diğer .NET Core altında şablonudur hedefleyen .NET Core uygulamasını ->.  Bu makalede amacıyla ya da şablon çalışmalıdır.

3. Konsol uygulaması değiştirme C# için F# gerekirse.  Seçin **sonraki** ilerlemek için düğmeyi!  

4. Projenize bir ad verin ve uygulama için istediğiniz seçenekleri seçin.  Uyarı, Önizleme bölmesi ekranın oluşturulacak dizin yapısını göstermek için seçilen seçeneklere dayalı.  

5. **Oluştur**'u tıklatın.  Görmelisiniz bir F# Çözüm Gezgini'nde proje.

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

Kodu çalıştırmak ve sonuçları tıklayarak görmek **çalıştırma** üst düzey menüsünde ve ardından **hata ayıklama olmadan Başlat**.  Bu, hata ayıklama olmadan programı çalıştırır ve sonuçları görmenizi sağlar.

Artık Mac için Visual Studio açıldığını konsol penceresine yazdırılan aşağıdaki görmeniz gerekir:

```
12 squared is 144!
```

Tebrikler!  İlk oluşturduğunuz F# yazılmış, Mac için Visual Studio projesinde bir F# işlevi, işlev ve bazı sonuçları görmek için projenizi çalıştırarak arama sonuçlarının yazdırılır.

## <a name="using-f-interactive"></a>Kullanarak F# etkileşimli

Görselin en iyi özelliklerinden biri F# Mac için Visual Studio Araçları F# etkileşimli penceresi.  Kod üzerinde bir işlem burada o kod çağırabilir ve sonuçları etkileşimli olarak görmek için göndermenize olanak sağlar.

Hizmeti kullanmaya başlamak için vurgulayın `square` kodunuzda tanımlanan işlev.  Ardından, tıklayarak **Düzenle** üst düzey menüsünde.  Ardından **göndermek için seçimi F# etkileşimli**.  Bu kodu yürütür F# etkileşimli penceresi.  Alternatif olarak, seçime sağ tıklayın ve seçin **göndermek için seçimi F# etkileşimli**.  Görmelisiniz F# da aşağıdaki etkileşimli penceresi görünür:

```
>

val square : x:int -> int

>
```

Bu aynı işlev imzası gösterir `square` işlevin üzerine gelindiğinde, daha önce gördüğünüzle işlevi.  Çünkü `square` artık tanımlanan F# etkileşimli işlem çağırabilirsiniz, farklı değerlere sahip:

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Bu işlevi yürütür, sonuç yeni bir ad ile bağlar `it`, türünü ve değerini görüntüler `it`.  Her satırın erdirmelisiniz Not `;;`.  Bu, nasıl F# etkileşimli, işlev çağrısı tamamlandığında bilir.  Yeni işlevleri de tanımlayabilirsiniz F# etkileşimli:

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Yukarıdaki yeni bir işlev tanımlar `isOdd`, hangi alır bir `int` ve tek sayı olup olmadığını görmek için denetimleri!  Neler farklı girişlerle döndürür görmek için bu işlevi çağırabilirsiniz.  İşlev çağrıları içindeki işlevleri çağırabilirsiniz:

```
> isOdd (square 15);;
val it : bool = true
```

Ayrıca [kanal İleri işleci](../language-reference/symbol-and-operator-reference/index.md) değeri iki işlevlerini işlem hattı için:

```
> 15 |> square |> isOdd;;
val it : bool = true
```

Sonraki öğreticilerde, kanal İleri işleci ve diğer değinilmektedir.

İle yapabilecekleriniz içine yalnızca bir bakışta budur F# etkileşimli.  Daha fazla bilgi için kullanıma [etkileşimli programlama F# ](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, kullanıma [Turu F# ](../tour.md), bazı çekirdek özellikleri kapsayan F# dili.  Size bazı özelliklerine genel bir bakış sunacak F#ve Mac ve çalıştırma için Visual Studio'ya kopyalayabilirsiniz bol miktarda kod örnekleri sağlar.  Ayrıca kullanabileceğiniz bazı harika dış kaynaklar verilmiştir büyütmüş içinde [ F# Kılavuzu](../index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual F#](../index.md)
- [F# Turu](../tour.md)
- [F#Dil Başvurusu](../language-reference/index.md)
- [Tür çıkarımı](../language-reference/type-inference.md)
- [Simge ve işleç başvurusu](../language-reference/symbol-and-operator-reference/index.md)

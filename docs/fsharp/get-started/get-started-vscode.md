---
title: Visual Studio Code’da F# Kullanmaya Başlama
description: Visual Studio Code ve ıonıde eklenti Suite ile nasıl kullanacağınızı F# öğrenin.
ms.date: 12/23/2018
ms.openlocfilehash: 2802438144eb2352c3abeeccfc126b16c6a87d8f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204907"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Visual Studio Code’da F# Kullanmaya Başlama

IntelliSense ve Code F# yeniden düzenlemeler ile harika platformlar arası, hafif tümleşik geliştirme ORTAMı (IDE) deneyimi almak Için [ıonıde eklentisine](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) [Visual Studio Code](https://code.visualstudio.com) yazabilirsiniz. Eklenti hakkında daha fazla bilgi edinmek için [Ionide.io](http://ionide.io) ziyaret edin.

Başlamak için [ F# ve ıonıde eklentisinin doğru yüklendiğinden](install-fsharp.md#install-f-with-visual-studio-code)emin olun.

## <a name="create-your-first-project-with-ionide"></a>Ionıde ile ilk projenizi oluşturma

Yeni F# bir proje oluşturmak için bir komut satırı açın ve .NET Core CLI yeni bir proje oluşturun:

```dotnetcli
dotnet new console -lang F# -o FirstIonideProject
```

Tamamlandıktan sonra, dizini projeye değiştirin ve Visual Studio Code açın:

```console
cd FirstIonideProject
code .
```

Proje Visual Studio Code yüklendikten sonra, pencerenin sol tarafındaki F# Çözüm Gezgini bölmesini görmeniz gerekir. Bu, ıonıde 'nin yeni oluşturduğunuz projeyi başarıyla yüklediği anlamına gelir. Bu noktadan önce düzenleyicide kod yazabilirsiniz, ancak bu durum gerçekleştiğinde her şeyin yüklenmesi tamamlanmıştır.

## <a name="configure-f-interactive"></a>Etkileşimli F# yapılandırma

İlk olarak, .NET Core Scripting 'in varsayılan betik ortamınız olduğundan emin olun:

1. Visual Studio Code ayarlarını açın (**kod** > **tercihleri** > **ayarları**).
1. Terim  **F# betiğini**arayın.
1. **FSharp: SDK betikleri kullan**onay kutusuna tıklayın.

Bu şu anda, .NET Core komut dosyası ile çalışmayan .NET Framework tabanlı betikteki bazı eski davranışlar nedeniyle gereklidir ve ıonıde Şu anda bu geriye dönük uyumluluk için çaba harcar. Gelecekte, .NET Core Scripting varsayılan değer olacaktır.

### <a name="write-your-first-script"></a>İlk komut dosyanızı yazma

.NET Core komut dosyası kullanmak üzere Visual Studio Code yapılandırdıktan sonra, Visual Studio Code gezgin görünümüne gidin ve yeni bir dosya oluşturun. *Myfirstscript. FSX*olarak adlandırın.

Şimdi aşağıdaki kodu buna ekleyin:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Bu işlev, bir kelimeyi bir [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)biçimine dönüştürür. Bir sonraki adım, bunu etkileşimli (FSI F# ) kullanarak değerlendirmelidir.

İşlevin tamamını vurgulayın (11 satır uzunluğunda olmalıdır). Vurgulandıktan sonra, **alt** tuşunu basılı tutun ve **ENTER**tuşuna basın. Ekranın alt kısmında bir Terminal penceresi açılır ve şuna benzer görünmelidir:

![Ionıde ile F# etkileşimli çıkış örneği](./media/getting-started-vscode/vscode-fsi.png)

Bu üç şey oldu:

1. Bu işlem, FSI işlemini başlattı.
2. Bu, FSI işlemi üzerinde vurguladığınız kodu gönderdi.
3. FSI işlemi, üzerinden gönderdiğiniz kodu değerlendirdi.

Üzerinden gönderildikleriniz bir [işleviydi](../language-reference/functions/index.md), artık bu işlevi FSI ile çağırabilirsiniz! Etkileşimli pencerede şunları yazın:

```fsharp
toPigLatin "banana";;
```

Aşağıdaki sonucu görmeniz gerekir:

```fsharp
val it : string = "ananabay"
```

Şimdi ilk harf olarak bir sesli harf deneyelim. Aşağıdakileri girin:

```fsharp
toPigLatin "apple";;
```

Aşağıdaki sonucu görmeniz gerekir:

```fsharp
val it : string = "appleyay"
```

İşlev beklenen şekilde çalışıyor gibi görünüyor. Tebrikler, ilk F# işlevinizi Visual Studio Code YAZMıŞ ve FSI ile değerlendirdiniz!

> [!NOTE]
> Fark etmişsinizdir, FSI içindeki satırlar `;;`ile sonlandırılır. Bunun nedeni, FSI 'in birden çok satır girmenize olanak sağlar. Uçtaki `;;`, kod tamamlandığında FSI 'in bilmesini sağlar.

## <a name="explaining-the-code"></a>Kodu açıklayan

Kodun gerçekten yapmakta olduğu konusunda emin değilseniz, bir adım adım aşağıda verilmiştir.

Gördüğünüz gibi `toPigLatin`, bir sözcüğü giriş olarak alan ve bu sözcüğün Pig-Latin gösterimine dönüştüren bir işlevdir. Bunun kuralları aşağıdaki gibidir:

Bir sözcükteki ilk karakter sesli harf ile başlıyorsa, sözcüğün sonuna "oley" ekleyin. Bir sesli harf ile başlamazsa, ilk karakteri sözcüğün sonuna taşıyın ve buna "ay" ekleyin.

FSI içinde aşağıdakileri fark etmiş olabilirsiniz:

```fsharp
val toPigLatin : word:string -> string
```

Bu `toPigLatin`, giriş olarak bir `string` alan (`word`olarak adlandırılan) ve başka bir `string`döndüren bir işlev olduğunu belirtir. Bu, kodu anlamak F# F# için temel bir parçası olan [işlevin tür imzası](https://fsharpforfunandprofit.com/posts/function-signatures/)olarak bilinir. Ayrıca, Visual Studio Code işlevin üzerine geldiğinizde bunu da fark edeceksiniz.

İşlevin gövdesinde, iki ayrı bölüm fark edeceksiniz:

1. Verilen bir karakterin (`c`), [desen eşleştirme](../language-reference/pattern-matching.md)aracılığıyla sağlanan desenlerden biriyle eşleşip eşleşmediğini denetleyerek, `isVowel`adlı bir iç işlev.

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. İlk karakterin bir sesli harf olup olmadığını denetleyen ve ilk karakterin bir sesli harf mi olduğunu ve giriş karakterlerinden bir dönüş değeri mi olduğunu kontrol eden bir [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) ifadesi:

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

`toPigLatin` akışı bu nedenle:

Giriş sözcüğünün ilk karakterinin sesli harf olup olmadığını denetleyin. Varsa, sözcüğün sonuna "oley" ekleyin. Aksi takdirde, ilk karakteri sözcüğün sonuna taşıyın ve buna "ay" ekleyin.

Bunun hakkında dikkat edilecek bir son şey vardır: başka birçok dilin aksine, işlevden döndürülecek açık yönerge yoktur. Bunun nedeni F# , ifade tabanlıdır ve bir işlevin gövdesindeki son ifade dönüş değeridir. `if..then..else` kendisinin bir ifadesi olduğundan, giriş değerine bağlı olarak, `then` bloğunun veya `else` bloğunun gövdesi döndürülür.

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a>Konsol uygulamasını bir Pig Latin oluşturucusuna dönüştürme

Bu makalenin önceki bölümlerinde kod yazmanın F# yaygın bir ilk adımı gösterilmiştir: ilk işlev YAZıLıYOR ve FSI ile etkileşimli olarak yürütülüyor. Bu, [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 'un "Read-değerlendir-PRINT loop" IÇIN aldığı REPL temelli geliştirme olarak bilinir. Çalışır hale gelene kadar işlevselliği denemek için harika bir yoldur.

REPL temelli geliştirmede bir sonraki adım, çalışma kodunu bir F# uygulama dosyasına taşımadır. Daha sonra, bu, F# derleyici tarafından yürütülebilecek bir derlemeye derlenebilir.

Başlamak için, daha önce .NET Core CLI oluşturduğunuz *program. FS* dosyasını açın. Bazı kodların zaten orada olduğunu fark edeceksiniz.

Sonra, `PigLatin` adlı yeni bir [`module`](../language-reference/modules.md) oluşturun ve daha önce oluşturduğunuz `toPigLatin` işlevini buna benzer şekilde kopyalayın:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Bu modül `main` işlevin üzerinde ve `open System` bildiriminin altında olmalıdır. ' Deki F#bildirimlerin sırası, bu nedenle, bir dosyaya çağrı yapmadan önce işlevi tanımlamanız gerekir.

Şimdi `main` işlevinde, Pig Latin Oluşturucu işlevinizi bağımsız değişkenlerde çağırın:

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

Şimdi, konsol uygulamanızı komut satırından çalıştırabilirsiniz:

```console
dotnet run apple banana
```

Ayrıca, bu kez çalışan bir program olarak, betik dosyanız ile aynı sonucu verir.

## <a name="troubleshooting-ionide"></a>Ionıde sorunlarını giderme

İşte karşılaşabileceğiniz bazı sorunları giderebilmeniz için birkaç yol aşağıda verilmiştir:

1. Ionıde 'nin kod düzenlemesi özelliklerini almak için F# dosyalarınızın diske ve Visual Studio Code çalışma alanında açık olan bir klasörün içine kaydedilmesi gerekir.
1. Sisteminizde değişiklik yaptıysanız veya Visual Studio Code açık olarak ıonıde önkoşulları yüklediyseniz Visual Studio Code yeniden başlatın.
1. Proje dizinlerinizde geçersiz karakterler varsa, ıonıde çalışmayabilir.  Bu durumda proje dizinlerinizi yeniden adlandırın.
1. Ionıde komutlarının hiçbiri çalışmıyorsa, yanlışlıkla geçersiz kılıp kıldığınızı görmek için [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) 'nizi denetleyin.
1. Ionıde makinenizde bozulur ve yukarıdakilerden hiçbiri sorununuzu düzeltmediyse, makinenizde `ionide-fsharp` dizinini kaldırmayı ve eklenti paketini yeniden yüklemeyi deneyin.
1. Bir proje yükleme başarısız olursa ( F# Çözüm Gezgini bunu gösterir), bu projeye sağ tıklayıp **Ayrıntıları gör** ' e tıklayarak daha fazla tanılama bilgisi alın.

Ionıde, F# topluluk üyeleri tarafından oluşturulan ve tutulan açık kaynaklı bir projem. Lütfen sorunları bildirin ve [ıonıde-vscode-FSharp GitHub deposunda](https://github.com/ionide/ionide-vscode-fsharp)katkıda bulunun.

Ayrıca, ıonıde F# [Gitter kanalında](https://gitter.im/ionide/ionide-project)ıonıde geliştiricilerinden ve topluluğundan daha fazla yardım isteyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Ve dilinin özellikleri hakkında F# daha fazla bilgi edinmek Için, [turuna F# ](../tour.md)göz atın.

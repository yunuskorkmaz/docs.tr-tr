---
title: Visual Studio Code ile F# çalışmaya başlama
description: Visual Studio Code ve ıonıde eklenti Suite ile nasıl kullanacağınızı F# öğrenin.
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082995"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Visual Studio Code ile F# çalışmaya başlama

IntelliSense ve Basic F# Code yeniden düzenlemeler ile harika bir platformlar arası, hafif tümleşik geliştirme ORTAMı (IDE) deneyimi almak Için [ıonıde eklentisine](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) [Visual Studio Code](https://code.visualstudio.com) yazabilirsiniz. Eklenti hakkında daha fazla bilgi edinmek için [Ionide.io](http://ionide.io) ziyaret edin.

Başlamak için [ F# ve ıonıde eklentisinin doğru yüklendiğinden](install-fsharp.md#install-f-with-visual-studio-code)emin olun.

> [!NOTE]
> Ionıde, platformlar arası F# uyumluluk sorunlarına sahip olabilen DotNet core olmayan .NET Framework projeler oluşturur. **Linux** veya **OSX**üzerinde çalıştırıyorsanız, kullanmaya başlamak için daha basit bir yol, [komut satırı araçlarını](get-started-command-line.md)kullanmaktır.

## <a name="creating-your-first-project-with-ionide"></a>Ionıde ile ilk projenizi oluşturma

Yeni F# bir proje oluşturmak için Visual Studio Code yeni bir klasörde açın (istediğiniz gibi adlandırabilirsiniz).

Sonra, komut paletini açın ( **> komut paletini görüntüleyin**) ve aşağıdakileri yazın:

```console
> F# new project
```

Bu, [Forge](https://github.com/fsharp-editing/Forge) projesi tarafından desteklenir.

> [!NOTE]
> Şablon seçeneklerini görmüyorsanız, komut paletinde aşağıdaki komutu çalıştırarak şablonları yenilemeyi deneyin: `>F#: Refresh Project Templates`.

Seç "F#: Yeni proje " **ENTER**'a vurarak. Bu, sizi bir proje şablonu seçerken bir sonraki adıma götürür.

Şablonu seçin ve ENTER tuşuna basın. `classlib`

Ardından, projenin oluşturulacağı bir dizin seçin. Boş bırakırsanız, geçerli dizini kullanır.

Son olarak, projenizi son adımda adlandırın. F#proje adları için [Pascal case](http://c2.com/cgi/wiki?PascalCase) kullanır. Bu makale ad `ClassLibraryDemo` olarak kullanır. Projeniz için istediğiniz adı girdikten sonra **ENTER**tuşuna basın.

Önceki adımı izlediyseniz, sol taraftaki Visual Studio Code çalışma alanını, aşağıdaki ile görünmesi için almalısınız:

1. F# Projenin kendisi, `ClassLibraryDemo` klasörün altında.
2. Aracılığıyla [`Paket`](https://fsprojects.github.io/Paket/)paket eklemeye yönelik doğru dizin yapısı.
3. İle [`FAKE`](https://fsharp.github.io/FAKE/)platformlar arası bir derleme betiği.
4. Paketleri alıp sizin için bağımlılıkları çözebilen çalıştırılabilirdosya.`paket.exe`
5. Bu `.gitignore` projeyi git tabanlı kaynak denetimine eklemek isterseniz bir dosya.

## <a name="writing-some-code"></a>Kod yazma

*Classlibrarydemo* klasörünü açın.  Aşağıdaki dosyaları görmeniz gerekir:

1. `ClassLibraryDemo.fs`, bir F# sınıf tanımlı bir uygulama dosyası.
2. `ClassLibraryDemo.fsproj`, bu F# projeyi oluşturmak için kullanılan proje dosyası.
3. `Script.fsx`, kaynak F# dosyayı yükleyen bir betik dosyası.
4. `paket.references`, Proje bağımlılıklarını belirten bir paket dosyası.

Öğesini `Script.fsx`açın ve sonuna aşağıdaki kodu ekleyin:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Bu işlev, bir kelimeyi bir [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)biçimine dönüştürür. Bir sonraki adım, bunu etkileşimli (FSI F# ) kullanarak değerlendirmelidir.

İşlevin tamamını vurgulayın (11 satır uzunluğunda olmalıdır). Vurgulandıktan sonra, **alt** tuşunu basılı tutun ve **ENTER**tuşuna basın. Aşağıda bir pencere açılır ve şuna benzer bir şekilde görünür:

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
> Fark etmeyebilirsiniz, FSI içindeki satırlar ile `;;`sonlandırılır. Bunun nedeni, FSI 'in birden çok satır girmenize olanak sağlar. Son `;;` olarak, kod tamamlandığında FSI 'in bu kodu bilmesini sağlar.

## <a name="explaining-the-code"></a>Kodu açıklayan

Kodun gerçekten yapmakta olduğu konusunda emin değilseniz, bir adım adım aşağıda verilmiştir.

Görebileceğiniz gibi, `toPigLatin` bir sözcüğü giriş olarak alan ve bu sözcüğün Pig-Latin gösterimine dönüştüren bir işlevdir. Bunun kuralları aşağıdaki gibidir:

Bir sözcükteki ilk karakter sesli harf ile başlıyorsa, sözcüğün sonuna "oley" ekleyin. Bir sesli harf ile başlamazsa, ilk karakteri sözcüğün sonuna taşıyın ve buna "ay" ekleyin.

FSI içinde aşağıdakileri fark etmiş olabilirsiniz:

```fsharp
val toPigLatin : word:string -> string
```

Bu durum, `toPigLatin` bir `string` as girişi (olarak adlandırılır `word`) ve diğeri `string`döndüren bir işlev olduğunu belirtir. Bu, kodu anlamak F# F# için temel bir parçası olan [işlevin tür imzası](https://fsharpforfunandprofit.com/posts/function-signatures/)olarak bilinir. Ayrıca, Visual Studio Code işlevin üzerine geldiğinizde bunu da fark edeceksiniz.

İşlevin gövdesinde, iki ayrı bölüm fark edeceksiniz:

1. Verilen bir karakterin ( `isVowel``c`), [desen eşleştirme](../language-reference/pattern-matching.md)aracılığıyla sağlanan desenlerden biriyle eşleşip eşleşmediğini kontrol ederek bir sesli işlevi olarak adlandırılan bir iç işlev.

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. İlk [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) karakterin bir sesli harf olup olmadığını denetleyen ve ilk karakterin bir sesli harf mi olduğunu ve giriş karakterlerinden bir dönüş değeri mi olduğunu kontrol eden bir ifade.

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Flow `toPigLatin` bu nedenle:

Giriş sözcüğünün ilk karakterinin sesli harf olup olmadığını denetleyin. Varsa, sözcüğün sonuna "oley" ekleyin. Aksi takdirde, ilk karakteri sözcüğün sonuna taşıyın ve buna "ay" ekleyin.

Bunun hakkında dikkat edilecek bir son şey vardır: başka birçok dilin aksine, işlevden döndürülecek açık yönerge yoktur. Bunun nedeni F# , ifade tabanlıdır ve bir işlevin gövdesindeki son ifade dönüş değeridir. Kendisinin bir ifadesi `then` `else` olduğu için, blok gövdesi veya bloğunun gövdesi, giriş değerine göre döndürülür. `if..then..else`

## <a name="moving-your-script-code-into-the-implementation-file"></a>Betik kodunuzu uygulama dosyasına taşıma

Bu makalenin önceki bölümlerinde kod yazmanın F# yaygın bir ilk adımı gösterilmiştir: ilk işlev YAZıLıYOR ve FSI ile etkileşimli olarak yürütülüyor. Bu, [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 'un "Read-değerlendir-PRINT loop" IÇIN aldığı REPL temelli geliştirme olarak bilinir. Çalışır hale gelene kadar işlevselliği denemek için harika bir yoldur.

REPL temelli geliştirmede bir sonraki adım, çalışma kodunu bir F# uygulama dosyasına taşımadır. Daha sonra, bu, F# derleyici tarafından yürütülebilecek bir derlemeye derlenebilir.

Başlamak için öğesini açın `ClassLibraryDemo.fs`.  Bazı kodların zaten orada olduğunu fark edeceksiniz. Devam edin ve sınıf tanımını silin, ancak [`namespace`](../language-reference/namespaces.md) bildirimin en üstte ayrıldığınızdan emin olun.

Ardından, yeni [`module`](../language-reference/modules.md) bir adlı `PigLatin` oluşturma oluşturun ve `toPigLatin` işlevi bu şekilde kopyalayın:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Sonra, `Script.fsx` dosyayı yeniden açın ve tüm `toPigLatin` işlevi silin, ancak dosyada aşağıdaki iki satırı kaydettiğinizden emin olun:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

Her iki metin satırını da seçin ve bu satırları FSI içinde yürütmek için alt + ENTER tuşlarına basın. Bu işlem, işlevselliğe erişebilmeniz için Pig Latin kitaplığı içeriğini FSI işlemine ve `open` `ClassLibraryDemo` ad alanına yükler.

Ardından, FSI penceresinde, daha önce tanımladığınız `PigLatin` modülün bulunduğu işlevi çağırın:

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Başarılı! Daha önce olduğu gibi, ancak şimdi bir F# uygulama dosyasından yüklediğiniz sonuçları alırsınız. Buradaki önemli fark, F# kaynak dosyalarının, yalnızca FSI içinde değil, her yerde yürütülebilecek derlemelerde derlendikleri bir farktır.

## <a name="summary"></a>Özet

Bu makalede şunları öğrendiniz:

1. Ionıde ile Visual Studio Code ayarlama.
2. Ionıde ile ilk F# projenizi oluşturma.
3. Komut dosyası kullanarak F# ilk F# Işlevinizi ıonıde 'de yazın ve ardından FSI içinde yürütün.
4. Betik kodunuzu F# kaynağa geçirme ve sonra bu kodu FSI 'dan çağırma.

Artık Visual Studio Code ve ıonıde kullanarak çok F# daha fazla kod yazabilirsiniz.

## <a name="troubleshooting"></a>Sorun giderme

İşte karşılaşabileceğiniz bazı sorunları giderebilmeniz için birkaç yol aşağıda verilmiştir:

1. Ionıde 'nin kod düzenlemesi özelliklerini almak için F# dosyalarınızın diske ve Visual Studio Code çalışma alanında açık olan bir klasörün içine kaydedilmesi gerekir.
2. Sisteminizde değişiklik yaptıysanız veya Visual Studio Code açık olarak ıonıde önkoşulları yüklediyseniz Visual Studio Code yeniden başlatın.
3. Derleyici ve etkileşimli ' i F# F# , tam yol olmadan komut satırından kullanıp kullandığınızı kontrol edin. Bunu, F# derleyici için bir komut `fsc` satırına ve `fsi` ya `fsharpi` da Windows ve mono üzerinde Mac/Linux üzerinde bulunan F# görsel araçlar için yazarak yapabilirsiniz.
4. Proje dizinlerinizde geçersiz karakterler varsa, ıonıde çalışmayabilir.  Bu durumda proje dizinlerinizi yeniden adlandırın.
5. Ionıde komutlarının hiçbiri çalışmıyorsa, yanlışlıkla geçersiz kılıp kıldığınızı görmek için [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) 'nizi denetleyin.
6. Ionıde makinenizde bozulur ve yukarıdakilerden hiçbiri sorununuzu düzeltmediyse, makinenizde `ionide-fsharp` dizini kaldırmayı ve eklenti paketini yeniden yüklemeyi deneyin.

Ionıde, F# topluluk üyeleri tarafından oluşturulan ve tutulan açık kaynaklı bir projem. Lütfen sorunları bildirin ve [ıonıde-vscode 'da katkıda bulunmak için ücretsizdir: FSharp GitHub deposu](https://github.com/ionide/ionide-vscode-fsharp).

Raporlama sorununuz varsa, lütfen [bir sorunu bildirirken kullanılacak günlükleri alma yönergelerini](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)izleyin.

Ayrıca, ıonıde F# [Gitter kanalında](https://gitter.im/ionide/ionide-project)ıonıde geliştiricilerinden ve topluluğundan daha fazla yardım isteyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Ve dilinin özellikleri hakkında F# daha fazla bilgi edinmek Için, [turuna F# ](../tour.md)göz atın.

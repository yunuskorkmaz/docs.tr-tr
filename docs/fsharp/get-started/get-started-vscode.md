---
title: Kullanmaya başlama F# Visual Studio Code
description: Nasıl kullanacağınızı öğrenin F# Visual Studio Code ve Ionide eklenti paketi ile.
ms.date: 05/28/2018
ms.openlocfilehash: 2db587b5614c5a7ca9285cad9b719970d53afd55
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129798"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Kullanmaya başlama F# Visual Studio Code

Yazabileceğiniz F# içinde [Visual Studio Code](https://code.visualstudio.com) ile [Ionide eklentisi](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) IntelliSense ve temel bir kodla harika bir çapraz platform, basit tümleşik geliştirme ortamı (IDE) deneyimi almak için yeniden düzenlemeler. Ziyaret [Ionide.io](http://ionide.io) eklenti hakkında daha fazla bilgi edinmek için.

Başlamak için sahip olduğunuzdan emin olun [ F# ve doğru şekilde yüklenip Ionide eklentisi](install-fsharp.md#install-f-with-visual-studio-code).

## <a name="creating-your-first-project-with-ionide"></a>İlk projenizi Ionide ile oluşturma

Yeni bir F# proje, Visual Studio Code (örneğin adı da istediğiniz gibi) yeni bir klasöre açın.

Ardından, komut paletini açın (**Görüntüle > komut paleti**) ve aşağıdaki komutu yazın:

```
> F# new project
```

Tarafından desteklenen bu [FORGE](https://github.com/fsharp-editing/Forge) proje.

> [!NOTE]
> Şablon seçenekleri görmüyorsanız, komut paletini içinde aşağıdaki komutu çalıştırarak şablonları yenileme deneyin: `>F#: Refresh Project Templates`.

Seçin "F#: Yeni bir proje tarafından ulaşmaktan" **Enter**. Bu, bir proje şablonu seçmek için olan bir sonraki adıma götürür.

Çekme `classlib` şablonu ve isabet **Enter**.

Ardından, projeyi oluşturmak için bir dizin seçin. Bunu boş bırakırsanız, geçerli dizin kullanır.

Son olarak, son adım, projenizi adlandırın. F#kullanan [baş harfleri büyük](http://c2.com/cgi/wiki?PascalCase) proje adları için. Bu makalede `ClassLibraryDemo` adı. Projeniz için istediğiniz ad girdikten sonra isabet **Enter**.

Önceki adımları izlediyseniz, Visual Studio kodu aşağıdakiyle görünmesini çalışma alanı sol taraftaki almanız gerekir:

1. F# Kendisini altındaki proje `ClassLibraryDemo` klasör.
2. Paketler aracılığıyla eklemek için doğru dizin yapısı [ `Paket` ](https://fsprojects.github.io/Paket/).
3. Platformlar arası derleme betiği ile [ `FAKE` ](https://fsharp.github.io/FAKE/).
4. `paket.exe` Fetch paketler ve bağımlılıkları çözümlemeniz için çalıştırılabilir.
5. A `.gitignore` bu proje Git tabanlı kaynak denetimine eklemek isterseniz, dosya.

## <a name="writing-some-code"></a>Bazı kodlar yazma

Açık *ClassLibraryDemo* klasör.  Aşağıdaki dosyaları göreceksiniz:

1. `ClassLibraryDemo.fs`, bir F# uygulama dosyası ile tanımlanmış bir sınıf.
2. `ClassLibraryDemo.fsproj`, bir F# bu projeyi oluşturmak için kullanılan proje dosyası.
3. `Script.fsx`, bir F# kaynak dosyasını yükleyen bir betik dosyası.
4. `paket.references`, proje bağımlılıkları belirten bir Paket dosyası.

Açık `Script.fsx`ve sonunda, aşağıdaki kodu ekleyin:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Bu işlev bir forma bir sözcük dönüştürür [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin). Kullanarak değerlendirmek için sonraki adımdır F# etkileşimli (FSI).

(11 satır uzunluğunda olmalıdır) tüm işlevi vurgulayın. Vurgulanır sonra tutun **Alt** anahtar ve isabet **Enter**. Aşağıdaki açılır penceresi bir pencere görürsünüz ve aşağıdakine benzer göstermelidir:

![Örnek F# etkileşimli Ionide ile çıktı](media/getting-started-vscode/vscode-fsi.png)

Bu üç şey yapar:

1. Bu, FSI işlemi başlatıldı.
2. Vurguladığınız kodun FSI işlem üzerinden gönderilir.
3. FSI işlem üzerinden gönderilen kodu değerlendirilir.

Üzerinden gönderilen olduğundan bir [işlevi](../language-reference/functions/index.md), FSI ile bu işlevi çağırabilirsiniz! Etkileşimli pencerede aşağıdaki komutu yazın:

```fsharp
toPigLatin "banana";;
```

Aşağıdaki sonucu görmeniz gerekir:

```fsharp
val it : string = "ananabay"
```

Artık, bir sesli olarak ilk harfi ile deneyelim. Aşağıdakileri girin:

```fsharp
toPigLatin "apple";;
```

Aşağıdaki sonucu görmeniz gerekir:

```fsharp
val it : string = "appleyay"
```

İşlev beklendiği gibi çalışıyor gibi görünüyor. Tebrikler, yalnızca ilk yazdığınız F# FSI ile değerlendirilir ve işlev Visual Studio Code'da!

> [!NOTE]
> Fark etmiş olabilirsiniz gibi FSI satırları ile sonlandırılır `;;`. Bu durum, FSI birden fazla satır girmenizi sağlar çünkü. `;;` Sonunda kodu tamamlandığında bilmeniz FSI olanak tanır.

## <a name="explaining-the-code"></a>Kod açıklayan

Kod gerçekten yaptığı hakkında emin değilseniz, işte bir adım adım.

Gördüğünüz gibi `toPigLatin` , bir sözcük, girdi olarak alır ve söz konusu sözcüğün bir Pig Latin gösterimine dönüştürür bir işlevdir. Bu kurallar aşağıdaki gibidir:

İlk karakter bir sözcük, bir harfle başlar "yay" kelimenin sonuna ekleyin. Bir harfle başlamazsa, ilk karakterden kelimenin sonuna taşı ve "ay" ekleyin.

FSI aşağıdaki fark etmiş olabilirsiniz:

```fsharp
val toPigLatin : word:string -> string
```

Bu bildiren `toPigLatin` alır bir işlev, bir `string` giriş olarak (adlı `word`) ve başka döndürür `string`. Bu olarak bilinir [işlevin türü imzası](https://fsharpforfunandprofit.com/posts/function-signatures/), temel bir parçasını F# anlamak için anahtarıdır F# kod. Visual Studio code'da işlevi üzerine getirin, ayrıca bu fark edeceksiniz.

İşlevin gövdesinde, iki farklı bölümlerini göreceksiniz:

1. Çağrılan bir iç işlev `isVowel`, belirli bir karakterin belirler (`c`) sağlanan desenlerden biriyle eşleşiyorsa kontrol ederek bir ünlü olduğunu [desen eşleştirme](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Bir [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) veya ilk karakter bir sesli ise ve ilk karakter bir dönüş değeri giriş karakterleri dışında yapıları tabanlı halinde denetleyen bir ifade olan bir sesli:

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Akışı `toPigLatin` böylece:

Giriş kelimenin ilk karakteri bir sesli olup olmadığını denetleyin. İse, "yay" kelimenin sonuna ekleyin. Aksi takdirde, ilk karakterden kelimenin sonuna taşı ve "ay" ekleyin.

Bu konuda fark etmeye son bir şey yoktur: birçok başka dile burada aksine, işlevden döndürülecek hiçbir açık bir yönerge yoktur. Bunun nedeni, F# ifade tabanlı ve bir işlevin gövdesinde son deyim dönüş değeridir. Çünkü `if..then..else` kendisi bir deyim gövdesi olan `then` blok veya gövdesinin `else` blok bağlı olarak giriş değeri döndürülür.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Uygulama dosyasına betik kodunuzu taşıma

Bu makalenin önceki bölümlerinde yazma ortak ilk adımda gösterilen F# kod: bir ilk işlevi yazma ve FSI ile etkileşimli olarak yürütme. Bu REPL odaklı geliştirme bilinir burada [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) "Okuma değerlendirmek yazdırma döngü için" anlamına gelir. Bir sorun çalışma bulunana kadar işlevselliğe sahip denemek için harika bir yoludur.

Sonraki adımda REPL odaklı geliştirme çalışma koduna taşımaktır bir F# uygulama dosyası. Tarafından ardından derlenebilir F# derleyici yürütülebilecek bir derleme içinde.

Başlamak için açık `ClassLibraryDemo.fs`.  Bazı kod zaten kullanımda olduğunu fark edeceksiniz. Devam edin ve sınıf tanımı silin, ancak bıraktığınızdan emin olun [ `namespace` ](../language-reference/namespaces.md) bildiriminin en üstünde.

Ardından, yeni bir oluşturma [ `module` ](../language-reference/modules.md) adlı `PigLatin` ve kopyalama `toPigLatin` işleve, bu nedenle:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Ardından, açık `Script.fsx` dosya yeniden ve tüm silme `toPigLatin` çalışır, ancak aşağıdaki iki satırı dosyasında tutmak olduğundan emin olun:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

İlk satırı yüklemek için betik FSI için gereken `ClassLibraryDemo.fs`. Kolaylık olması açısından ikinci çizgidir: belirlemesini sağlayabilirsiniz isteğe bağlıdır, ancak yazmanız gerekecektir `open ClassLibraryDemo` getirmek istiyorsanız FSI penceresinde `ToPigLatin` kapsama modülü.

Ardından, FSI penceresinde işlevi çağrısı `PigLatin` daha önce tanımladığınız Modülü:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Başarılı! Öğesinden önce ancak artık yüklü aynı sonuçları elde bir F# uygulama dosyası. Burada ana fark F# kaynak dosyaları, yalnızca FSI içinde her yerden yürütülebilecek derlemeleri halinde derlenir.

## <a name="summary"></a>Özet

Bu makalede, öğrendiniz:

1. Visual Studio Code ve Ionide ayarlama yapma.
2. İlk oluşturma F# Ionide projesiyle.
3. Nasıl kullanılacağını F# komut dosyası birinci yazılacak F# işlev içinde Ionide ve ardından içinde FSI yürütün.
4. Betik kodunuzu geçirme F# kaynağı ve ardından FSI kodu çağırın.

Artık çok daha fazlasını yazılacak donatılmış F# Visual Studio Code ve Ionide kullanan kod.

## <a name="troubleshooting"></a>Sorun giderme

Karşılaşabileceğiniz bazı sorunları giderebilir birkaç yolu vardır:

1. Kod düzenleme Ionide, özellikleri almak için F# dosyaları diske ve Visual Studio Code çalışma alanında açık olan bir klasör içinde kaydedilmesi gerekir.
2. Visual Studio Code, sisteme yapılan değişiklikler veya Visual Studio Code ile açık Ionide Önkoşullar yüklendi, yeniden başlatın.
3. Kullanabileceğiniz onay F# derleyici ve F# tam olarak nitelenmiş bir yol olmadan komut satırından etkileşimli. Yazarak bunu yapabilirsiniz `fsc` için komut satırında F# derleyicisi ve `fsi` veya `fsharpi` görsel F# Windows ve Mac/Linux'ta, Mono sırasıyla araçları.
4. Proje dizinlerinizde geçersiz karakterler varsa, Ionide çalışmayabilir.  Bu durumda, proje dizinleri yeniden adlandırın.
5. Ionide komutların hiçbiri çalışıyorsanız, denetle, [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) , bunları yanlışlıkla geçersiz kılma olmadığını görmek için.
6. Yukarıdakilerin hiçbiri sorununuzu düzeltmiştir ve Ionide makinenizde bozuk, uygulamadan yetkilendirmeleri `ionide-fsharp` makinenizde dizin ve eklenti paketini yeniden yükleyin.

Ionide yerleşik ve üyeleri tarafından tutulan bir açık kaynak projesi olan F# topluluğu. Lütfen rapor sorunları ve en katkıda çekinmeyin [Ionide VSCode: FSharp GitHub deposu](https://github.com/ionide/ionide-vscode-fsharp).

Rapor için bir sorun varsa, lütfen izleyin [bir sorun bildirirken kullanmak için günlükleri alma yönergelerini](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Ionide geliştiricilerden Ek Yardım almak için sorabilir ve F# topluluğuna [Ionide Gitter kanal](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Sonraki adımlar

Hakkında daha fazla bilgi edinmek için F# ve dil özelliklerinin kullanıma [Turu F# ](../tour.md).

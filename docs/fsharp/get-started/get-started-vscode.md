---
title: 'F # Visual Studio Code ile çalışmaya başlama'
description: 'F # Visual Studio Code ve Ionide eklentisi paketiyle nasıl kullanacağınızı öğrenin.'
ms.date: 05/28/2018
ms.openlocfilehash: e56274caf36be231338876ded5a6d7c7968906b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728634"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>F # Visual Studio Code ile çalışmaya başlama

F # yazabileceğiniz [Visual Studio Code](https://code.visualstudio.com) ile [Ionide eklentisi](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), IntelliSense ve temel kodla harika bir çapraz platform, basit tümleşik geliştirme ortamı (IDE) deneyim almak için yapan yeniden düzenlemeler. Ziyaret [Ionide.io](http://ionide.io) eklentisi paketi hakkında daha fazla bilgi için.

## <a name="prerequisites"></a>Önkoşullar

Sahip olmanız gerekir [yüklü git](https://git-scm.com/download) ve kullanılabilir yapmak için yolunda Ionide proje şablonlarını kullanabilirsiniz. Bunu doğru şekilde yazarak yüklendiğini doğrulayabilirsiniz `git --version` bir komut istemi ve tuşlarına basarak **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

Ionide kullanan [Mono](http://www.mono-project.com). Homebrew üzerinde macOS Mono yüklemek için en kolay yoludur. Terminalinizde yalnızca aşağıdaki komutu yazın:

```
brew install mono
```

Ayrıca yüklemelisiniz [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

Linux üzerinde Ionide de kullanır [Mono](https://www.mono-project.com). Debian veya Ubuntu değilseniz, aşağıdakileri kullanabilirsiniz:

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Ayrıca yüklemelisiniz [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Windows üzerinde değilseniz, şunları yapmalısınız [F # desteği ile Visual Studio yükleme](get-started-visual-studio.md#installing-f). Bu, yazma, derlemek ve F # kod yürütmek için gerekli tüm bileşenleri yükler.

Ayrıca yüklemelisiniz [.NET Core SDK](https://www.microsoft.com/net/download/).

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a>Visual Studio Code ve Ionide eklentisini yükleme

Visual Studio koddan yükleyebilirsiniz [code.visualstudio.com](https://code.visualstudio.com) Web sitesi.

Ardından, "Ionide" için arama ve uzantıları simgesini tıklatın:

F # Visual Studio Code desteklenmediği için gereken tek eklentisi [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Ancak, aynı zamanda yükleyebilirsiniz [Ionide sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) almak için [sahte](https://fsharp.github.io/FAKE/) desteklemek ve [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) almak için [Paket](https://fsprojects.github.io/Paket/) destekler. SAHTE ve Paket projeleri oluşturmak ve bağımlılıkları, sırasıyla yönetmek için ek F # topluluk araçları.

## <a name="creating-your-first-project-with-ionide"></a>Ionide ile ilk projenizi oluşturma

Yeni bir F # projesi oluşturmak için Visual Studio Code yeni bir klasöre (örneğin, istediğiniz adı verebilirsiniz) açın.

Ardından, komut paletinden açın (**Görünüm > komutu paletinden**) ve aşağıdaki komutu yazın:

```
> F# new project
```

Bu tarafından desteklenmektedir [FORGE](https://github.com/fsharp-editing/Forge) projesi.

> [!NOTE]
Şablon seçenekleri görmüyorsanız, komut Palette aşağıdaki komutu çalıştırarak şablonları yenilemeyi deneyin: `>F#: Refresh Project Templates`.

"F #: Yeni Proje" basarsa tarafından seçin **Enter**. Bu, bir proje şablonu seçmek için olan bir sonraki adıma götürür.

Çekme `classlib` şablonu ve isabet **Enter**.

Ardından, projeyi oluşturmak için bir dizin seçin. Boş bırakırsanız, geçerli dizin kullanır.

Son olarak, son adım projenizde adı. F # kullanan [Pascal durumda](http://c2.com/cgi/wiki?PascalCase) proje adları için. Bu makalede kullanan `ClassLibraryDemo` adı. Projeniz için istediğiniz adı girdikten sonra isabet **Enter**.

Önceki adımda izlediyseniz, Visual Studio kodu aşağıdakilerle görünmesi çalışma alanında sol taraftaki almanız gerekir:

1. F # proje kendisini altındaki `ClassLibraryDemo` klasörü.
2. Paketleri yoluyla eklemek için doğru dizin yapısını [ `Paket` ](https://fsprojects.github.io/Paket/).
3. Çapraz platform komut dosyasıyla yapı [ `FAKE` ](https://fsharp.github.io/FAKE/).
4. `paket.exe` Fetch paketleri ve sizin için bağımlılıklar çözümlenmeye çalıştırılabilir.
5. A `.gitignore` bu proje Git tabanlı bir kaynak denetimine eklemek isterseniz, dosya.

## <a name="writing-some-code"></a>Bazı kod yazma

Açık *ClassLibraryDemo* klasör.  Aşağıdaki dosyalar görmeniz gerekir:

1. `ClassLibraryDemo.fs`, F # uygulaması olan bir dosya tanımlı bir sınıf.
2. `ClassLibraryDemo.fsproj`, bu proje oluşturmak için kullanılan bir F # proje dosyası.
3. `Script.fsx`, kaynak dosya yükleyen bir F # komut dosyası.
4. `paket.references`, proje bağımlılıklarını belirten bir Paket dosyası.

Açık `Script.fsx`ve sonunda, aşağıdaki kodu ekleyin:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Bu işlev bir sözcük bir forma dönüştürür [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin). F # Etkileşimli (FSI) kullanarak değerlendirmek için sonraki adımda kullanılır.

(11 satır uzunluğundaki olmalıdır) tüm işlevi vurgulayın. Vurgulanır sonra tutun **Alt** anahtarı ve isabet **Enter**. Aşağıdaki açılır pencere görürsünüz ve şöyle bir şey göstermesi gerekir:

![F # Etkileşimli çıktı Ionide ile örneği](media/getting-started-vscode/vscode-fsi.png)

Üçünü yapar:

1. FSI işlemi başlatıldı.
2. Bu vurguladığınız kodun FSI işlemi gönderilir.
3. FSI işlemi üzerinden gönderilen kodu değerlendirilir.

Üzerinden gönderilen olduğundan bir [işlevi](../language-reference/functions/index.md), o FSI işleviyle çağırabilirsiniz! Etkileşimli penceresinde aşağıdaki komutu yazın:

```fsharp
toPigLatin "banana";;
```

Aşağıdaki sonucu görmeniz gerekir:

```fsharp
val it : string = "ananabay"
```

Şimdi, ilk harfi olarak sesli bir ile deneyelim. Aşağıdakileri girin:

```fsharp
toPigLatin "apple";;
```

Aşağıdaki sonucu görmeniz gerekir:

```fsharp
val it : string = "appleyay"
```

İşlev beklendiği gibi çalıştığını görünüyor. Tebrikler, yalnızca Visual Studio kodda ilk F # işlevinizi yazdı ve FSI ile değerlendirilir.

>[!NOTE]
Fark etmiş olabilirsiniz gibi FSI satırları ile sona erdirilir `;;`. FSI birden fazla satır girmenizi sağlayan olmasıdır. `;;` Sonunda kodu bittiği bilmeniz FSI olanak sağlar.

## <a name="explaining-the-code"></a>Kod açıklayan

Kod gerçekte yaptıklarını hakkında emin değilseniz, işte bir adım adım.

Gördüğünüz gibi `toPigLatin` bir sözcük, girdi olarak alır ve bu word'ün bir Pig Latin gösterimine dönüştürür bir işlevdir. Bu kurallar aşağıdaki gibidir:

İlk karakter bir sözcük, sesli bir harfle başlarsa, "yay" sözcüğü sonuna ekleyin. Sesli bir harfle başlamazsa, bu ilk karakteri sözcüğün sonuna taşıyın ve "ay" ekleyin.

FSI aşağıdakileri fark etmiş olabilirsiniz:

```fsharp
val toPigLatin : word:string -> string
```

Bu bildiren `toPigLatin` alır, bir işlev değil bir `string` giriş olarak (adlı `word`) ve başka döndürür `string`. Bu olarak bilinir [işlevinin türü imzası](https://fsharpforfunandprofit.com/posts/function-signatures/), temel bir F #'ın, F # kodunu anlamanın anahtarıdır. Visual Studio Code işlevinde üzerine getirirseniz de bu fark edeceksiniz.

İşlev gövdesine iki ayrı bölümlere görürsünüz:

1. Adlı bir iç işlevi `isVowel`, belirli bir karakter varsa belirler (`c`) sağlanan desenleri biriyle eşleşiyorsa denetleyerek bir sesli olup [desen eşleştirme](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Bir [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) ilk karakteri bir sesli bir dönüş değeri dışında giriş karakter yapıları ise ilk karakter tabanlı olmadığını denetler ve ifadesi veya bir sesli oluştu:

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Akışını `toPigLatin` böylece:

Giriş word ilk karakteri bir sesli olup olmadığını denetleyin. Bu durumda, "yay" sözcüğün sonuna ekleyin. Aksi takdirde, bu ilk karakteri sözcüğün sonuna taşıyın ve "ay" ekleyin.

Bu konuda fark için son bir şey yok: birçok diğer diller ölçeklendiriyor aksine işlevi döndürmek için açık bir yönerge yoktur. F # ifade tabanlı, ve bir işlev gövdesine son deyim dönüş değeri olduğundan budur. Çünkü `if..then..else` kendisi gövdesi bir ifade değildir `then` engelleme veya gövdesini `else` blok bağlı olarak giriş değeri döndürülecek.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Uygulama dosyasına betik kodunuzu taşıma

Bu makalede önceki bölümlerde gösterildiği F # kodu yazarken ortak bir ilk adım: bir başlangıç işlevi yazma ve etkileşimli olarak FSI ile çalıştırma. Bu REPL güdümlü geliştirme bilinir nerede [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) "Okuma değerlendirmek yazdırma döngü için" anlamına gelir. Bir çalışma elde edene kadar işlevsellikle denemek için harika bir yoludur.

REPL güdümlü geliştirme sonraki adımda, bir F # uygulama dosyasına çalışan kodu taşımaktır. Ardından yürütülebilir bir derlemeye F # derleyici tarafından olarak da derlenebilir.

Başlamak için açın `ClassLibraryDemo.fs`.  Bazı kodu zaten da olduğunu fark edeceksiniz. Devam edin ve sınıf tanımını silin, ancak bıraktığınızdan emin olun [ `namespace` ](../language-reference/namespaces.md) bildiriminin en üstünde.

Ardından, yeni bir oluşturun [ `module` ](../language-reference/modules.md) adlı `PigLatin` ve kopyalama `toPigLatin` şekilde işlevi içine:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Ardından, açık `Script.fsx` dosyasını yeniden ve tüm silme `toPigLatin` çalışır, ancak aşağıdaki iki satırı dosyasında sakladığınızdan emin olun:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

İlk satırı FSI yüklemek için komut dosyası için gereken `ClassLibraryDemo.fs`. İkinci satır bir kolaylık bağlı: Bu atlama isteğe bağlıdır ancak yazmanız gerekir `open ClassLibraryDemo` getirmek isterseniz, bir FSI penceresinde `ToPigLatin` kapsam modüle.

Ardından, FSI penceresinde işlev çağrısı `PigLatin` daha önce tanımlanan Modülü:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Başarılı! Önce aynı sonuçları alırsınız, ancak bir F # uygulaması dosyasından şimdi yüklendi. Burada en önemli fark, F # kaynak dosyaları yalnızca FSI içinde herhangi bir yere, yürütülebilir derlemeler içine derlenen ' dir.

## <a name="summary"></a>Özet

Bu makalede, öğrendiniz:

1. Visual Studio kodu Ionide ile kurulur.
2. Ionide ile ilk F # projenizi oluşturma
3. F # komut dosyası yazma, ilk F # için nasıl kullanılacağını Ionide içinde işlev ve FSI içinde yürütün.
4. Kodunuzu geçirmek nasıl F # kaynak kodu ve sonra bu kodu FSI çağırın.

Şimdi Visual Studio Code ile Ionide olan çok daha fazla F # kod yazmaya donatılmış.

## <a name="troubleshooting"></a>Sorun giderme

İçine çalışabilir belirli sorunları giderme birkaç şekilde şunlardır:

1. Ionide özelliklerini düzenleme kod almak için F # dosyalarınızı diske ve Visual Studio Code çalışma alanında açık olan bir klasör içinde kaydedilmesi gerekir.
2. Sisteminizde değişiklik yapılan veya Visual Studio Code ile açık Ionide Önkoşullar yüklendi, Visual Studio Code yeniden başlatın.
3. F # derleyici ve F # Etkileşimli bir tam yol olmadan komut satırından kullanıp kullanmadığını denetleyin. Yazarak yapabilirsiniz `fsc` F # derleyici, bir komut satırında ve `fsi` veya `fsharpi` Visual F # için Araçlar Windows ve Mac/Linux üzerinde Mono sırasıyla.
4. Proje dizinlerinizi geçersiz karakterler varsa, Ionide çalışmayabilir.  Bu durumda proje dizinlerinizi yeniden adlandırın.
5. Ionide komutları hiçbiri çalışıyorsanız, denetleyin, [Visual Studio Code taşıyan](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) , bunları yanlışlıkla geçersiz kılma olmadığını görmek için.
6. Ionide makinenizde bozuk ve Yukarıdakilerin hiçbiri sorununuzu düzeltti kaldırmayı deneyin `ionide-fsharp` makinenizde dizin ve eklenti paketi yeniden yükleyin.

Ionide yerleşik ve F # topluluk üyeleri tarafından korunan bir açık kaynak projesidir. Lütfen raporu sorunları ve adresindeki katkıda bulunmaktan çekinmeyin [Ionide VSCode: FSharp GitHub deposunu](https://github.com/ionide/ionide-vscode-fsharp).

Rapor için bir sorun varsa, lütfen izleyin [bir sorun raporlama yapılırken kullanılacak günlüklerini alma yönergeleri](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Daha fazla yardım için Ionide geliştiriciler ve F # topluluğuna sorabilirsiniz [Ionide Gitter kanal](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Sonraki adımlar

F # ve dil özellikleri hakkında daha fazla bilgi için kullanıma [Tur, F #](../tour.md).

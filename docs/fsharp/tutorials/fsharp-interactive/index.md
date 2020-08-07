---
title: F# Etkileşimli (fsi.exe) Başvurusu
description: 'F # kodunu konsolda etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için F# Etkileşimli (fsi.exe) nasıl kullanılacağını öğrenin.'
ms.date: 05/16/2016
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 8bb1563ad34e65101fb9f09d6e347278e4b0de78
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854951"
---
# <a name="interactive-programming-with-f"></a>F ile etkileşimli programlama\#

> [!NOTE]
> Bu makalede şu anda yalnızca Windows deneyimi açıklanmaktadır.

F# Etkileşimli (fsi.exe), konsolda F # kodu etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için kullanılır. Diğer bir deyişle, F # Interactive F # dili için bir REPL (okuma, değerlendirme, yazdırma döngüsü) yürütür.

Konsolundan F# Etkileşimli çalıştırmak için fsi.exe çalıştırın. fsi.exe şu şekilde bulacaksınız:

```console
C:\Program Files (x86)\Microsoft Visual Studio\2019\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

nerede `sku` `Community` , veya olur `Professional` `Enterprise` .

Kullanılabilen komut satırı seçenekleri hakkında daha fazla bilgi için bkz. [F# etkileşimli seçenekleri](../../language-reference/fsharp-interactive-options.md).

Visual Studio aracılığıyla F# Etkileşimli çalıştırmak için **F# Etkileşimli**etiketli uygun araç çubuğu düğmesine tıklayabilir veya **Ctrl + Alt + F**tuşlarına basın. Bunu yapmak, F# Etkileşimli oturum çalıştıran bir araç penceresi olan etkileşimli pencereyi açar. Ayrıca etkileşimli pencerede çalıştırmak istediğiniz kod ve **Alt + Enter**tuş birleşimine basabilirsiniz. F# Etkileşimli, **F# Etkileşimli**etiketli bir araç penceresinde başlatılır. Bu tuş birleşimini kullandığınızda, düzenleyici penceresinin odağa sahip olduğundan emin olun.

Konsolunu veya Visual Studio 'Yu kullanıp kullanmayacağınızı bir komut istemi belirir ve yorumlayıcı, girişinizi bekler. Kodu, kod dosyasında olduğu gibi girebilirsiniz. Kodu derlemek ve yürütmek için, bir satırı veya birkaç giriş satırını sonlandırmak üzere iki noktalı virgül (**;;**) girin.

F# Etkileşimli kodu derlemeye çalışır ve başarılı olursa, kodu yürütür ve derlenen türlerin ve değerlerin imzasını yazdırır. Hata oluşursa yorumlayıcı hata iletilerini yazdırır.

Aynı oturumda girilen kod, daha önce girilmiş olan her türlü yapıya erişebilir, böylece programları oluşturabilirsiniz. Araç penceresindeki kapsamlı bir arabellek, gerekirse kodu bir dosyaya kopyalamanızı sağlar.

Visual Studio 'da çalıştırıldığında F# Etkileşimli projenizden bağımsız olarak çalışır. bu nedenle, örneğin, işlev için kodu etkileşimli pencereye kopyalamadıkça, projenizde tanımlanan yapıları F# Etkileşimli kullanamazsınız.

Bazı kitaplıklara başvuruda bulunan bir proje açıksa, bu F# Etkileşimli **Çözüm Gezgini**aracılığıyla bunlara başvurabilirsiniz. F# Etkileşimli bir kitaplığa başvurmak için, **Başvurular** düğümünü genişletin, kitaplığın kısayol menüsünü açın ve **F# Etkileşimli gönder**' i seçin.

Ayarları ayarlayarak F# Etkileşimli komut satırı bağımsız değişkenlerini (Seçenekler) kontrol edebilirsiniz. **Araçlar** menüsünde **Seçenekler...**' i seçin ve ardından **F # araçları**' nı genişletin. Değiştirebileceğiniz iki ayar F# Etkileşimli seçenekleridir ve **64 bit F# Etkileşimli** ayarıdır ve bu, yalnızca 64 bit makinede F# Etkileşimli çalıştırıyorsanız geçerlidir. Bu ayar, 32 bit veya 64 bit işlem olarak çalıştırılıp çalıştırılmadığını belirleyen fsi.exe veya fsianycpu.exe adanmış 64 bitlik sürümünü çalıştırmak isteyip istemediğinizi belirler.

## <a name="scripting-with-f"></a>F ile betik oluşturma\#

Betikler **. FSX** veya **. fsscript**dosya uzantısını kullanır. Kaynak kodu derlemek ve daha sonra derlenen derlemeyi çalıştırmak yerine yalnızca **fsi.exe** çalıştırabilir ve f # Kaynak Kodu betiğinin dosya adını belirtebilir ve f # Interactive kodu okur ve gerçek zamanlı olarak yürütür.

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Etkileşimli, komut dosyası ve derlenmiş ortamlar arasındaki farklar

Etkileşimli olarak çalıştırdığınız veya bir betiği çalıştıran F# Etkileşimli kod derlerken **etkileşimli** sembol tanımlanmıştır. Derleyicide kod derlerken, **derlenen** sembol tanımlanmıştır. Bu nedenle, kodun derlenmiş ve etkileşimli modlarda farklı olması gerekiyorsa, hangisinin kullanılacağını belirleyebilmek için koşullu derleme için önişlemci yönergelerini kullanabilirsiniz.

Derleyici yürütürken kullanılamayan F# Etkileşimli betikler çalıştırırken bazı yönergeler kullanılabilir... Aşağıdaki tabloda F# Etkileşimli kullanırken kullanılabilir olan yönergeler özetlenmektedir.

|Deki|Açıklama|
|---------|-----------|
|**#help**|Kullanılabilir yönergeler hakkındaki bilgileri görüntüler.|
|**#I**|Bir derleme arama yolunu tırnak işaretleri halinde belirtir.|
|**#load**|Bir kaynak dosyayı okur, derler ve çalıştırır.|
|**#quit**|F# Etkileşimli oturumunu sonlandırır.|
|**#r**|Bir derlemeye başvurur.|
|**#time ["," &#124; "kapalı"]**|**#Time** , performans bilgilerinin görüntülenip görüntülenmeyeceğini gösterir. Etkinleştirildiğinde, F# Etkileşimli yorumlanan ve yürütülen kodun her bölümü için gerçek zamanlı, CPU süresini ve çöp toplama bilgilerini ölçer.|

F# Etkileşimli dosya veya yolları belirttiğinizde, bir dize sabit değeri beklenmektedir. Bu nedenle, dosyalar ve yollar tırnak işaretleri içinde olmalı ve normal kaçış karakterleri de geçerlidir. Ayrıca, bir yolu içeren dizeyi tam bir dize olarak yorumlamasını F# Etkileşimli neden olması için @ karakterini kullanabilirsiniz. Bu, F# Etkileşimli kaçış karakterlerini yoksaymasına neden olur.

Derlenmiş ve etkileşimli mod arasındaki farklardan biri, komut satırı bağımsız değişkenlerine erişme yöntemidir. Derlenmiş modda **System. Environment. Getcommandbir GS**kullanın. Betikler ' de, **fsi. Commandbir g**kullanın.

Aşağıdaki kod, bir betikteki komut satırı bağımsız değişkenlerini okuyan bir işlevin nasıl oluşturulduğunu ve ayrıca bir betikten başka bir derlemeye nasıl başvurulacağını gösterir. İlk kod dosyası **MyAssembly. FS**, başvurulmakta olan derlemenin kodudur. Bu dosyayı komut satırı ile derleyin: **FSC-a MyAssembly. FS** ve sonra ikinci dosyayı komut satırı ile komut dosyası olarak yürütün: **fsi--exec FILE1. FSX** test

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

Çıktı aşağıdaki şekilde olacaktır:

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="related-articles"></a>İlgili makaleler:

|Başlık|Açıklama|
|-----|-----------|
|[F# Etkileşimli Seçenekleri](../../language-reference/fsharp-interactive-options.md)|F# Etkileşimli fsi.exe için komut satırı sözdizimini ve seçeneklerini açıklar.|
|[F# Etkileşimli kitaplığı başvurusu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|F # Interactive 'de kod yürütürken kullanılabilen kitaplık işlevlerini açıklar.|

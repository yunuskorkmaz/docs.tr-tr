---
title: F# Etkileşimli (DotNet) başvurusu
description: 'F # kodunu konsolda etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için F# Etkileşimli (DotNet fsi) nasıl kullanılacağını öğrenin.'
ms.date: 08/20/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 760b096c8a3ee0d495b893ab66fa6f9007cdbbf9
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867626"
---
# <a name="interactive-programming-with-f"></a>F ile etkileşimli programlama\#

F# Etkileşimli (DotNet fsi), konsolda F # kodunu etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için kullanılır. Diğer bir deyişle, F # Interactive F # dili için bir REPL (okuma, değerlendirme, yazdırma döngüsü) yürütür.

Konsolundan F# Etkileşimli çalıştırmak için, öğesini çalıştırın `dotnet fsi` . `dotnet fsi`Herhangi bir .NET SDK 'sında bulabilirsiniz.

Kullanılabilen komut satırı seçenekleri hakkında daha fazla bilgi için bkz. [F# etkileşimli seçenekleri](../../language-reference/fsharp-interactive-options.md).

Visual Studio aracılığıyla F# Etkileşimli çalıştırmak için **F# Etkileşimli**etiketli uygun araç çubuğu düğmesine tıklayabilir veya **Ctrl + Alt + F**tuşlarına basın. Bunu yapmak, F# Etkileşimli oturum çalıştıran bir araç penceresi olan etkileşimli pencereyi açar. Ayrıca etkileşimli pencerede çalıştırmak istediğiniz kod ve **Alt + Enter**tuş birleşimine basabilirsiniz. F# Etkileşimli, **F# Etkileşimli**etiketli bir araç penceresinde başlatılır. Bu tuş birleşimini kullandığınızda, düzenleyici penceresinin odağa sahip olduğundan emin olun.

Konsolunu veya Visual Studio 'Yu kullanıp kullanmayacağınızı bir komut istemi belirir ve yorumlayıcı, girişinizi bekler. Kodu, kod dosyasında olduğu gibi girebilirsiniz. Kodu derlemek ve yürütmek için, bir satırı veya birkaç giriş satırını sonlandırmak üzere iki noktalı virgül (**;;**) girin.

F# Etkileşimli kodu derlemeye çalışır ve başarılı olursa, kodu yürütür ve derlenen türlerin ve değerlerin imzasını yazdırır. Hata oluşursa yorumlayıcı hata iletilerini yazdırır.

Aynı oturumda girilen kod, daha önce girilmiş olan her türlü yapıya erişebilir, böylece programları oluşturabilirsiniz. Araç penceresindeki kapsamlı bir arabellek, gerekirse kodu bir dosyaya kopyalamanızı sağlar.

Visual Studio 'da çalıştırıldığında F# Etkileşimli projenizden bağımsız olarak çalışır. bu nedenle, örneğin, işlev için kodu etkileşimli pencereye kopyalamadıkça, projenizde tanımlanan yapıları F# Etkileşimli kullanamazsınız.

Bazı kitaplıklara başvuruda bulunan bir proje açıksa, bu F# Etkileşimli **Çözüm Gezgini**aracılığıyla bunlara başvurabilirsiniz. F# Etkileşimli bir kitaplığa başvurmak için, **Başvurular** düğümünü genişletin, kitaplığın kısayol menüsünü açın ve **F# Etkileşimli gönder**' i seçin.

Ayarları ayarlayarak F# Etkileşimli komut satırı bağımsız değişkenlerini (Seçenekler) kontrol edebilirsiniz. **Araçlar** menüsünde **Seçenekler...**' i seçin ve ardından **F # araçları**' nı genişletin. Değiştirebileceğiniz iki ayar F# Etkileşimli seçenekleridir ve **64 bit F# Etkileşimli** ayarıdır ve bu, yalnızca 64 bit makinede F# Etkileşimli çalıştırıyorsanız geçerlidir. Bu ayar, 32 bit veya 64 bit işlem olarak çalıştırılıp çalıştırılmadığını belirleyen fsi.exe veya fsianycpu.exe adanmış 64 bitlik sürümünü çalıştırmak isteyip istemediğinizi belirler.

## <a name="scripting-with-f"></a>F ile betik oluşturma\#

Betikler **. FSX** veya **. fsscript**dosya uzantısını kullanır. Kaynak kodu derlemek ve daha sonra derlenen derlemeyi çalıştırmak yerine **DotNet fsi** 'yi çalıştırabilir ve f # Kaynak Kodu betiğinin dosya adını belirtebilir ve f # Interactive kodu okur ve gerçek zamanlı olarak yürütür.

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

## <a name="package-management-in-f-interactive"></a>F# Etkileşimli Paket Yönetimi

[!NOTE] Paket Yönetimi, .NET SDK 'nın `dotnet fsi` `3.1.300` ve sonraki sürümlerinde ve .NET SDK 'sının tüm sürümlerinde sevk edilen sürümlerinde bir önizleme özelliği olarak kullanılabilir `5.*` . Bu önizleme sürümünde etkinleştirmek için `dotnet fsi` `--langversion:preview` bağımsız değişkenle çalıştırın.

`#r`Aşağıdaki sözdizimi aracılığıyla bir NuGet paketine başvurmak için F# Etkileşimli içindeki BIR DLL 'ye başvurmak üzere sözdizimi de kullanılabilir:

```fsharp
#r "nuget: <package name>
```

Örneğin, pakete başvurmak için `FSharp.Data` aşağıdaki `#r` başvuruyu kullanın:

```fsharp
#r "nuget: FSharp.Data"
```

Bu satırı yürüttükten sonra, paketin en son sürümü `FSharp.Data` NuGet önbelleğinize indirilir ve geçerli F# Etkileşimli oturumunda başvurulacaktır.

Paket adına ek olarak, bir paketin belirli sürümlerine kısa bir sözdizimi aracılığıyla başvurulabilir:

```fsharp
#r "nuget: FSharp.Data, 3.3.2"
```

daha açık bir biçimde:

```fsharp
#r "nuget: FSharp.Data, Version=3.3.2"
```

## <a name="related-articles"></a>İlgili makaleler:

|Başlık|Açıklama|
|-----|-----------|
|[F# Etkileşimli Seçenekleri](../../language-reference/fsharp-interactive-options.md)|F# Etkileşimli fsi.exe için komut satırı sözdizimini ve seçeneklerini açıklar.|
|[F# Etkileşimli kitaplığı başvurusu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|F # Interactive 'de kod yürütürken kullanılabilen kitaplık işlevlerini açıklar.|

---
title: F# Etkileşimli (fsi.exe) Başvurusu
description: Etkileşimli ( F# fsi. exe) bir kodu konsolda etkileşimli olarak çalıştırmak F# veya betikleri yürütmek F# için nasıl kullanılacağını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 9f4b5c0e7527d29e375265bb31a5de2df098f8e1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419903"
---
# <a name="interactive-programming-with-f"></a>F\# ile etkileşimli programlama

> [!NOTE]
> Bu makalede şu anda yalnızca Windows deneyimi açıklanmaktadır.  Yeniden yazılır.

> [!NOTE]
> API başvuru bağlantısı sizi MSDN 'ye götürür.  Docs.microsoft.com API başvurusu tamamlanmadı.

F#Etkileşimli (fsi. exe) kodu konsolda etkileşimli olarak F# çalıştırmak veya betikleri yürütmek F# için kullanılır. Diğer bir deyişle etkileşimli F# , F# dil Için bir REPL (okuma, değerlendirme, yazdırma döngüsü) yürütür.

Konsolundan etkileşimli F# çalıştırmak için, fsi. exe ' yi çalıştırın.  Şu şekilde fsi. exe ' yi bulacaksınız:

```console
C:\Program Files (x86)\Microsoft Visual Studio\2019\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

`sku` `Community`, `Professional` ya da `Enterprise` ' dir.

Kullanılabilen komut satırı seçenekleri hakkında daha fazla bilgi için bkz [ F# . Interactive Options](../../language-reference/fsharp-interactive-options.md).

Etkileşimli olarak F# Visual Studio aracılığıyla çalıştırmak için,  **F# etkileşimli**etiketli uygun araç çubuğu düğmesine tıklayabilir veya **Ctrl + Alt + F**tuşlarını kullanabilirsiniz. Bunu yaptığınızda etkileşimli bir oturum çalıştıran bir araç penceresi olan F# etkileşimli pencere açılır. Ayrıca etkileşimli pencerede çalıştırmak istediğiniz kod ve **Alt + Enter**tuş birleşimine basabilirsiniz. F#Etkileşimli,  **F# etkileşimli**etiketli bir araç penceresinde başlar. Bu tuş birleşimini kullandığınızda, düzenleyici penceresinin odağa sahip olduğundan emin olun.

Konsolunu veya Visual Studio 'Yu kullanıp kullanmayacağınızı bir komut istemi belirir ve yorumlayıcı, girişinizi bekler. Kodu, kod dosyasında olduğu gibi girebilirsiniz. Kodu derlemek ve yürütmek için, bir satırı veya birkaç giriş satırını sonlandırmak üzere iki noktalı virgül ( **;;** ) girin.

F#Etkileşimli kodu derlemeye çalışır ve başarılı olursa, kodu yürütür ve derlenen türlerin ve değerlerin imzasını yazdırır. Hata oluşursa yorumlayıcı hata iletilerini yazdırır.

Aynı oturumda girilen kod, daha önce girilmiş olan her türlü yapıya erişebilir, böylece programları oluşturabilirsiniz. Araç penceresindeki kapsamlı bir arabellek, gerekirse kodu bir dosyaya kopyalamanızı sağlar.

Visual Studio 'da çalıştırdığınızda, F# etkileşimli olarak projenizden bağımsız olarak çalışır. bu nedenle, işlev için kodu etkileşimli pencereye kopyalamadıkça projenizde tanımlanan yapıları etkileşimli F# olarak kullanamazsınız.

Bazı kitaplıklara başvuruda bulunan bir proje açıksa, F# **Çözüm Gezgini**ile etkileşimli olarak bunlara başvurabilirsiniz. Etkileşimli olarak F# bir kitaplığa başvurmak için **Başvurular** düğümünü genişletin, kitaplığın kısayol menüsünü açın ve **etkileşimli 'a F# gönder**' i seçin.

Ayarları ayarlayarak F# etkileşimli komut satırı bağımsız değişkenlerini (Seçenekler) kontrol edebilirsiniz. **Araçlar** menüsünde **Seçenekler...** ' i seçin ve ardından  **F# araçlar**' ı genişletin. Değiştirebileceğiniz iki ayar F# etkileşimli seçenekler ve **64-bit F# etkileşimli** ayarıdır ve yalnızca, bir 64 bit makinede F# etkileşimli olarak çalışıyorsanız ilgilidir. Bu ayar, bir 32 bit veya 64 bit işlem olarak çalıştırılıp çalıştırılmayacağını anlamak için makine mimarisini kullanan fsi. exe veya fsıanycpu. exe ' nin adanmış 64 bit sürümünü çalıştırmak isteyip istemediğinizi belirler.

## <a name="scripting-with-f"></a>F\# betiği oluşturma

Betikler **. FSX** veya **. fsscript**dosya uzantısını kullanır. Kaynak kodu derlemek ve daha sonra derlenen derlemeyi çalıştırmak yerine, yalnızca **fsi. exe** ' yi çalıştırabilir ve F# Kaynak Kodu betiğinin dosya adını belirtebilir, kodu F# etkileşimli olarak okur ve gerçek zamanlı olarak yürütür.

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Etkileşimli, komut dosyası ve derlenmiş ortamlar arasındaki farklar

Etkileşimli olarak F# kod derlerken, ister etkileşimli çalışıyor ister bir betiği çalıştırdığınıza bakılmaksızın **etkileşimli** simgesi tanımlanmıştır. Derleyicide kod derlerken, **derlenen** sembol tanımlanmıştır. Bu nedenle, kodun derlenmiş ve etkileşimli modlarda farklı olması gerekiyorsa, hangisinin kullanılacağını belirleyebilmek için koşullu derleme için önişlemci yönergelerini kullanabilirsiniz.

Etkileşimli olarak F# , derleyicisini yürütürken kullanılamayan komut dosyalarını yürütürken bazı yönergeler kullanılabilir. Aşağıdaki tabloda, etkileşimli kullanırken F# kullanılabilen yönergeler özetlenmektedir.

|Deki|Açıklama|
|---------|-----------|
|**#help**|Kullanılabilir yönergeler hakkındaki bilgileri görüntüler.|
|**#I**|Bir derleme arama yolunu tırnak işaretleri halinde belirtir.|
|**#load**|Bir kaynak dosyayı okur, derler ve çalıştırır.|
|**#quit**|Etkileşimli bir F# oturumu sonlandırır.|
|**#r**|Bir derlemeye başvurur.|
|**#time ["on"&#124;"off"]**|**#Time** , performans bilgilerinin görüntülenip görüntülenmeyeceğini gösterir. Etkinleştirildiğinde, etkileşimli olarak, F# yorumlanan ve yürütülen kodun her bölümü için, Interactive gerçek ZAMANLı, CPU süresi ve çöp toplama bilgilerini ölçer.|

Etkileşimli olarak F# dosya veya yol belirttiğinizde, bir dize sabit değeri beklenmektedir. Bu nedenle, dosyalar ve yollar tırnak işaretleri içinde olmalı ve normal kaçış karakterleri de geçerlidir. Ayrıca, bir yol içeren dizeyi tam bir dize olarak F# yorumlamasını sağlamak için @ karakterini kullanabilirsiniz. Bu, F# etkileşimli herhangi bir kaçış karakterini yok saymasına neden olur.

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

Çıktı aşağıdaki gibidir:

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[F# Interactive Seçenekleri](../../language-reference/fsharp-interactive-options.md)|F# Etkileşimli, fsi. exe için komut satırı söz dizimini ve seçeneklerini açıklar.|
|[F#Etkileşimli kitaplık başvurusu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|Etkileşimli olarak F# kod yürütürken kullanılabilen kitaplık işlevlerini açıklar.|

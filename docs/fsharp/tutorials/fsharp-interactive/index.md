---
title: F# Etkileşimli (fsi.exe) Başvurusu
description: 'Nasıl F # Etkileşimli (fsi.exe) konsolda F # kodunu etkileşimli olarak çalıştırmak için veya F # betiklerini yürütmek için kullanılan öğrenin.'
keywords: 'Visual f #, f # işlevsel programlama'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 36af8d1b-dc08-4a37-9497-d23c0a0ac11c
ms.openlocfilehash: a18f339d898374a59858cd774154b3846594d183
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="interactive-programming-with-f"></a>İle F # Etkileşimli programlama #

> [!NOTE]
Bu makalede Windows deneyimi yalnızca şu anda açıklanmıştır.  Yazılacak.

> [!NOTE]
API başvuru bağlantısı sizi MSDN'ye götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

F # Etkileşimli (fsi.exe) konsolda F # kodunu etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için kullanılır. Diğer bir deyişle, F # Etkileşimli REPL (oku, değerlendir, yazdırma döngü) F # dili için yürütür.

F # Etkileşimli Konsolu'ndan çalıştırmak için fsi.exe çalıştırın.  İçinde fsi.exe bulacaksınız "c:\Program dosyaları (x86) \Microsoft SDKs\F#\<sürüm > \Framework\<sürüm >\". Kullanılabilen komut satırı seçenekleri hakkında daha fazla bilgi için bkz: [F # Etkileşimli Seçenekleri](../../language-reference/fsharp-interactive-options.md).

F # Etkileşimli aracılığıyla Visual Studio çalıştırmak için etiketli uygun araç çubuğu düğmesini tıklatabilirsiniz **F # Etkileşimli**, veya tuşlarını **Ctrl + Alt + F**. Bunun yapılması, etkileşimli bir pencere, F # Etkileşimli oturum çalıştıran bir araç penceresi açılır. Tuş bileşimine basın ve etkileşimli pencerede çalıştırmak istediğiniz bazı kodu da seçebilirsiniz **ALT + ENTER**. F # Etkileşimli başlar etiketli araç penceresinde **F # Etkileşimli**. Bu tuş bileşimini kullandığınızda Düzenleyicisi penceresini odağa sahip olduğundan emin olun.

Konsol veya Visual Studio kullanıp kullanmadığınızı bir komut istemi belirir ve yorumlayıcı girişinizi bekler. Bir kod dosyasında gibi kodu girebilirsiniz. Derleme ve kod yürütmek için iki noktalı girin (**;** ) bir veya birkaç satıra giriş sonlandırılacak.

Kodu derlemek F # etkileşimli çalışır ve başarılı olursa, kodu yürütür ve türleri ve derlenmiş değerleri imzasını yazdırır. Hatalar oluşursa, yorumlayıcı hata iletilerini yazdırır.

Programları oluşturabilmeniz aynı oturumda girilen kod daha önce girdiğiniz yapıları erişebilir. Araç penceresi kapsamlı bir arabellek kodu gerekirse bir dosyaya kopyalayın izin verir.

Visual Studio, projenizin bağımsız olarak F # etkileşimli çalışır çalıştırdığınızda, bu nedenle, örneğin, F # Etkileşimli'projenizdeki işlevi kodunu etkileşimli penceresine kopyalayın sürece tanımlanan yapıları kullanamazsınız.

Bazı kitaplıklarına başvuruda bulunan bir Proje Aç varsa, bunlar F # Etkileşimli ' başvurabilir **Çözüm Gezgini**. F # Etkileşimli kitaplığa başvurmak için genişletme **başvuruları** düğümü, kitaplık için kısayol menüsünü açın ve seçin **F # Etkileşimli için Gönder**.

F # etkileşimli komut satırı bağımsız değişkenleri (Seçenekler) ayarlarını denetleyebilirsiniz. Üzerinde **Araçları** menüsünde, select **seçenekleri...** , genişletin ve ardından **F # Araçları**. F # Etkileşimli Seçenekleri değiştirebileceğiniz iki ayar olan ve **64-bit F # Etkileşimli** yalnızca F # Etkileşimli bir 64-bit makine üzerinde çalıştırıyorsanız, ilgili ayarı. Bu ayar, fsi.exe veya 32 bit veya 64-bit işlem olarak çalıştırılıp çalıştırılmayacağını belirlemek için makine mimarisi kullanır fsianycpu.exe ayrılmış 64-bit sürümünü çalıştıran isteyip istemediğinizi belirler.


## <a name="scripting-with-f"></a>F # ile komut dosyası #
Komut dosyaları, dosya uzantısı kullanır **.fsx** veya **.fsscript**. Kaynak kodu derleme ve ardından daha sonra derlenmiş bütünleştirilmiş kodu çalıştırmak yerine, yalnızca çalıştırabilirsiniz **fsi.exe** ve F # kaynak kodu komut dosyasının dosya adını belirtin ve F # Etkileşimli kodu okur ve gerçek zamanlı olarak yürütür.


## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Etkileşimli, komut dosyası ve derlenmiş ortamlar arasındaki farklar
Ne zaman, etkileşimli olarak çalıştırıp çalıştırmadığınızı kodu F # Etkileşimli'derleme veya sembolün bir betik çalıştırarak **etkileşimli** tanımlanır. Ne zaman derlediğiniz simgenin derleyici kodda **COMPILED** tanımlanır. Bu nedenle, kod derlenmiş ve etkileşimli modda farklı olması gerekiyorsa, kullanılacak belirlemek için koşullu derleme için önişlemci yönergeleri kullanabilirsiniz.

F # derleyici yürütülürken bulunmayan etkileşimli komut yürütülürken bazı yönergeler kullanılabilir. Aşağıdaki tabloda, F # etkileşimli olarak kullanırken, kullanılabilir olan yönergeleri özetler.

|Yönergesi|Açıklama|
|---------|-----------|
|**#help**|Kullanılabilir yönergeleri hakkında bilgileri görüntüler.|
|**#I**|Bir derleme arama yolu tırnak işaretleri içine belirtir.|
|**#load**|Bir kaynak dosyasını okur, derlendiğinden ve çalıştırır.|
|**#quit**|F # Etkileşimli oturum sona erer.|
|**#r**|Bir derlemeye başvurur.|
|**#time ["on"&#124;"off"]**|Kendi kendine **#time** performans bilgileri görüntülenip görüntülenmeyeceğini değiştirir. Etkinleştirildiğinde, F # Etkileşimli gerçek zamanlı, CPU süresi ve atık toplama bilgi yorumlanır ve yürütülen kod her bölüm için ölçer.|

Dosyaları veya yolları F # Etkileşimli'de belirttiğiniz zaman, bir dize sabit değeri bekleniyordu. Bu nedenle, dosyaları ve yolları tırnak işaretleri içinde olmalıdır ve her zamanki kaçış karakterleri uygulayın. Ayrıca, kullanabileceğiniz @ karakteri F # yol verbatim bir dize olarak içeren bir dize yorumlamaya etkileşimli neden olacak. F # herhangi bir kaçış karakteri yoksaymak etkileşimli neden olur.

Derlenmiş ve etkileşimli mod arasındaki farklar birini komut satırı bağımsız değişkenlerine erişim yoludur. Derlenmiş modunda kullanmak **System.Environment.GetCommandLineArgs**. Komut dosyalarında **fsi.CommandLineArgs**.

Aşağıdaki kod bir betik içinde komut satırı bağımsız değişkenleri okuyan ve ayrıca bir komut dosyasından başka bir derleme başvurusu yapmayı gösteren bir işlevin nasıl oluşturulacağı gösterilmektedir. İlk kod dosyası **MyAssembly.fs**, başvurulan derleme kodudur. Bu dosya komut satırı ile derleyin: **fsc - a MyAssembly.fs** ve komut satırı komut dosyası olarak ikinci dosyayı yürütün: **fsi--exec file1.fsx** test

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

```
Command line arguments: 
file1.fsx
test
60
```

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[F# Interactive Seçenekleri](../../language-reference/fsharp-interactive-options.md)|Komut satırı sözdizimi ve F # Etkileşimli için seçenekleri açıklar fsi.exe.|
|[F # Etkileşimli Kitaplık Başvurusu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|Kullanılabilir kitaplık işlevlerini kod F # Etkileşimli yürütülürken açıklar.|

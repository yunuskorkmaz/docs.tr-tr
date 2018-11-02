---
title: F# Etkileşimli (fsi.exe) Başvurusu
description: Bilgi nasıl F# etkileşimli (fsi.exe) çalıştırmak için kullanılan F# etkileşimli olarak konsolda veya yürütülecek kodu F# betikler.
ms.date: 05/16/2016
ms.openlocfilehash: 459a2a4ba49ba0f55455797617781d010efecc0b
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50195261"
---
# <a name="interactive-programming-with-f"></a>Etkileşimli ile programlamaF# #

> [!NOTE]
Bu makalede, şu anda Windows deneyimi yalnızca açıklanmıştır.  Yazılacak.

> [!NOTE]
MSDN için API başvuru bağlantısı sizi yönlendirir.  Docs.microsoft.com API başvuru tamamlanmadı.

F#Etkileşimli (fsi.exe) çalıştırmak için kullanılan F# etkileşimli konsolu veya yürütülecek kodu F# betikler. Diğer bir deyişle, F# için etkileşimli REPL (okuma, Evaluate, yazdırma döngüsü) yürütür F# dili.

Çalıştırılacak F# etkileşimli konsolundan fsi.exe çalıştırın.  İçinde fsi.exe bulacaksınız:

```console
C:\Program Files (x86)\Microsoft Visual Studio\2017\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

Burada `sku` ya da `Community`, `Professional`, veya `Enterprise`.

Kullanılabilir komut satırı seçenekleri hakkında daha fazla bilgi için bkz: [ F# etkileşimli seçenekleri](../../language-reference/fsharp-interactive-options.md).

Çalıştırılacak F# etkileşimli Visual Studio aracılığıyla etiketli uygun bir araç çubuğu düğmesini tıklatabilirsiniz  **F# etkileşimli**, veya anahtarlarının **Ctrl + Alt + F**. Bunun yapılması etkileşimli pencere, çalışan bir araç penceresi açılır bir F# etkileşimli oturumu. Etkileşimli pencerede çalıştırın ve tuş bileşimine istediğiniz kod belirleyebilirsiniz **ALT + ENTER**. F#Etiketli bir araç penceresinde etkileşimli başlatır  **F# etkileşimli**. Bu tuş bileşimini kullanın, düzenleyici penceresinde odağı olduğundan emin olun.

Konsolu veya Visual Studio kullanarak, bir komut istemi görünür ve yorumlayıcı girişinizi bekler. Bir kod dosyasında yaptığınız gibi kod girebilirsiniz. Derlemek ve kodu yürütmek için iki noktalı virgül girin (**;** ) bir veya birkaç satıra giriş sonlandırmak için.

F#Kodu derlemek etkileşimli çalışır ve başarılı olursa, kodu yürütür türleri imzası yazdırır ve derlenmiş BT'nin değerleri. Hatalar oluşursa yorumlayıcı hata iletilerini yazdırır.

Programları oluşturmanıza yardımcı olacak aynı oturumda girilen kod daha önce girilen tüm yapıları erişimi vardır. Kapsamlı bir araç penceresi arabellekteki kod gerekirse bir dosyaya kopyalayın sağlar.

Visual Studio'da çalıştırdığınızda F# etkileşimli çalıştırılan bağımsız olarak, proje, bu nedenle, örneğin, kullanamazsınız projenizde tanımlanan yapıları F# etkileşimli sürece etkileşimli pencereye işlev kodunu kopyalayın.

Bazı kitaplıklar başvuran bir proje açıksa, bunları başvurabilirsiniz F# üzerinden etkileşimli **Çözüm Gezgini**. Bir kitaplıkta başvurmak için F# Interactive genişletin **başvuruları** düğümü, kitaplık için kısayol menüsünü açın ve seçin **göndermek F# etkileşimli**.

Denetleyebileceğiniz F# ayarları ayarlayarak etkileşimli komut satırı bağımsız değişkenleri (Seçenekler). Üzerinde **Araçları** menüsünde **seçenekleri...** ve ardından  **F# Araçları**. Değiştirebileceğiniz iki ayar F# etkileşimli seçenekleri ve **64-bit F# etkileşimli** yalnızca çalıştırıyorsanız, ilgili ayarı F# etkileşimli bir 64-bit makinedeki. Bu ayar, fsi.exe veya 32 bit veya 64-bit işlem olarak çalıştırılacak şekilde belirlemek için makine mimarisi kullanan fsianycpu.exe adanmış 64-bit sürümünü çalıştırmak istediğiniz olup olmadığını belirler.


## <a name="scripting-with-f"></a>İle betik oluşturmaF# #
Betiklerini kullanan dosya uzantısı **.fsx** veya **.fsscript**. Kaynak kodu derleme ve daha sonra derlemede çalıştıran yerine yalnızca çalıştırabilirsiniz **fsi.exe** ve komut dosyasının dosya adı belirtin F# kaynak kodu, ve F# etkileşimli kod okur ve gerçek yürütür saat.


## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Etkileşimli, komut dosyası ve derlenmiş ortamlar arasındaki farklar
Ne zaman derlediğiniz kod F# etkileşimli, etkileşimli olarak çalıştırılıyor veya sembolün bir betik çalıştırarak **etkileşimli** tanımlanır. Ne zaman derlediğiniz kod derleyici, sembol **COMPILED** tanımlanır. Bu nedenle, kod derlenmiş ve etkileşimli modda farklı olması gerekiyorsa, hangisini kullanacağınızı belirlemek için koşullu derleme için ön işlemci yönergeleri kullanabilirsiniz.

Komut yürütülürken bazı yönergeler kullanılabilir F# derleyici yürütülürken bulunmayan etkileşimli. Aşağıdaki tabloda özetlenmiştir kullanırken mevcut olan yönergeleri F# etkileşimli.

|Yönergesi|Açıklama|
|---------|-----------|
|**#help**|Kullanılabilir yönergeleri hakkında bilgileri görüntüler.|
|**#I**|Tırnak işaretleri içine bir bütünleştirilmiş kod arama yolunu belirtir.|
|**#load**|Bir kaynak dosyasını okur, derlendiğinden ve çalıştırır.|
|**#quit**|Sonlandıran bir F# etkileşimli oturumu.|
|**#r**|Bir derlemeye başvurur.|
|**#time ["on"&#124;"kapalı"]**|Kendi kendine **#time** performans bilgilerini görüntülenip görüntülenmeyeceğini değiştirir. Etkinleştirildiğinde, F# etkileşimli, gerçek zamanlı, CPU süresi ve çöp toplama bilgileri yorumlanan ve yürütülen kodun her bölüm için ölçer.|

Dosyaları veya yolları belirttiğinizde F# etkileşimli, bir dize sabit değeri bekleniyor. Bu nedenle, dosyaları ve yolları tırnak işaretleri içinde olmalıdır ve her zamanki kaçış karakterleri uygulayın. Ayrıca, kullanabileceğiniz @ karakteri neden F# etkileşimli bir yolu olarak verbatim dizesi içeren bir dize yorumlamak için. Bu neden F# etkileşimli herhangi bir kaçış karakteri yok sayılacak.

Derlenmiş ve etkileşimli mod arasındaki farklardan biri, komut satırı bağımsız değişkenlerine erişim yoludur. Derlenmiş modunda kullanmak **System.Environment.GetCommandLineArgs**. Komut dosyalarında **fsi.CommandLineArgs**.

Aşağıdaki kod, komut satırı bağımsız değişkenleri koddaki okur ve ayrıca bir komut dosyasından başka bir derlemeye başvuru yapmayı gösteren bir işlev oluşturma işlemini gösterir. İlk kod dosyasını **MyAssembly.fs**, başvurulan bütünleştirilmiş kodun kodudur. Bu dosya komut satırı ile Derle: **fsc - bir MyAssembly.fs** ve sonra komut satırı ile bir betik olarak ikinci dosyasını yürütün: **fsı--exec file1.fsx** test

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
90
```

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[F# Interactive Seçenekleri](../../language-reference/fsharp-interactive-options.md)|Komut satırı söz dizimini açıklar ve seçenekleri F# etkileşimli, fsi.exe.|
|[F#Etkileşimli Kitaplık Başvurusu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|Kitaplık işlevleri kullanılabilir kod yürütülürken açıklanmaktadır F# etkileşimli.|

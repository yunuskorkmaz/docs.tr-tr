---
description: csc.exe ile komut satırı oluşturma
title: csc.exe ile komut satırı oluşturma
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 3dafb35011a1d3c77ae05baa5d25c69f39681ab8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258448"
---
# <a name="command-line-build-with-cscexe"></a>csc.exe ile komut satırı oluşturma

Komut istemine yürütülebilir dosyasının adını (*csc.exe*) yazarak C# derleyicisini çağırabilirsiniz.

Visual Studio 'nun yüklediği komut satırı kabukların birini kullanırsanız, gerekli tüm ortam değişkenleri sizin için ayarlanır. Bu kabukların nasıl erişebileceği hakkında bilgi için bkz. [Geliştirici komut satırı kabukları](/visualstudio/ide/reference/command-prompt-powershell).

Normal bir komut istemi kullanıyorsanız, bilgisayarınızdaki herhangi bir alt dizinden *csc.exe* çağırabilmeniz için önce yolunu ayarlamanız gerekir. Ayrıca, komut satırı yapılarını desteklemek için uygun ortam değişkenlerini ayarlamak üzere *VsDevCmd.bat* çalıştırmanız gerekir. *VsDevCmd.bat* hakkında daha fazla bilgi edinmek için, bkz. [Visual Studio komut satırı için ortam değişkenlerini ayarlama](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Yalnızca Windows yazılım geliştirme seti (SDK) olan bir bilgisayarda çalışıyorsanız, C# derleyicisini **Microsoft .NET Framework SDK** menü seçeneğinden açtığınız **SDK komut istemi**' nde kullanabilirsiniz.

Ayrıca C# programlarını program aracılığıyla oluşturmak için MSBuild'i kullanabilirsiniz. Daha fazla bilgi için bkz. [MSBuild](/visualstudio/msbuild/msbuild).

*csc.exe* çalıştırılabilir dosya genellikle \\ *\<Version>* *Windows* dizini altındaki Microsoft. NET\Framework klasöründe bulunur. Bu dosyanın yeri, belirli bir bilgisayarın tam yapılandırmasına bağlı olarak değişebilir. Bilgisayarınızda .NET Framework'ün birden fazla sürümü yüklüyse, bu dosyanın birden fazla sürümünü bulacaksınız. Bu tür yüklemeler hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
> Visual Studio IDE kullanarak bir proje oluşturduğunuzda, **CSC** komutunu ve ilgili derleyici seçeneklerini **Çıkış** penceresinde görüntüleyebilirsiniz. Bu bilgileri görüntülemek için nasıl yapılır: günlük verilerinin ayrıntı düzeyini **normal** veya **ayrıntılı** olarak değiştirmek üzere [derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) konusundaki yönergeleri izleyin. Projenizi yeniden oluşturduktan sonra, C# derleyicisinin çağrılmasını bulmak için **CSC** **Çıkış** penceresinde arama yapın.

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>C# derleyicisi için komut satırı söz dizimi kuralları

C# derleyicisi, işletim sistemi komut satırında verilen bağımsız değişkenleri yorumladığı zaman aşağıdaki kuralları kullanır:

- Bağımsız değişkenler boşluk veya sekme olan boşluk ile sınırlandırılmıştır.

- Giriş işareti karakteri (^) bir kaçış karakteri veya sınırlayıcı olarak tanınmıyor. Karakter, programdaki diziye geçirilmeden önce işletim sistemindeki komut satırı ayrıştırıcısı tarafından işlenir `argv` .

- Çift tırnak işaretleri ("String") içine alınmış bir dize, içinde yer alan boşluklardan bağımsız olarak tek bir bağımsız değişken olarak yorumlanır. Tırnak içine alınmış bir dize bir bağımsız değişkene gömülebilir.

- Önünde ters eğik çizgi (") olan bir çift tırnak işareti \\ , sabit değer çift tırnak işareti karakteri (") olarak yorumlanır.

- Ters eğik çizgiler, bir çift tırnak işaretinden hemen önce gelmedikleri takdirde tam olarak yorumlanır.

- İki ters eğik çizgi daha sonra çift tırnak işareti kullanıyorsa, bir ters eğik çizgi `argv` her çift eğik çizgi için diziye konur ve çift tırnak işareti dize sınırlayıcısı olarak yorumlanır.

- Tek bir ters eğik çizgiden sonra çift tırnak işareti varsa, her ters eğik çizgi çifti için bir ters eğik çizgi konur `argv` ve çift tırnak işareti kalan ters eğik çizgi için "kaçışlı" olur. Bu, içinde bir sabit değer çift tırnak işareti (") eklenmesine neden olur `argv` .

## <a name="sample-command-lines-for-the-c-compiler"></a>C# derleyicisi için örnek komut satırları

- *File.cs* üreten *File.exe* derler:

  ```console
  csc File.cs
  ```

- *File.cs* üreten *File.dll* derler:

  ```console
  csc -target:library File.cs
  ```

- *File.cs* derler ve *My.exe* oluşturur:

  ```console
  csc -out:My.exe File.cs
  ```

- Geçerli dizindeki tüm C# dosyalarını iyileştirmeler etkin olacak şekilde derler ve hata ayıklama sembolünü tanımlar. Çıktı *File2.exe*:

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- Geçerli dizindeki tüm C# dosyalarını, *File2.dll* hata ayıklama sürümü üreten şekilde derler. Amblem yoktur ve hiçbir uyarı gösterilmez:

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- Geçerli dizindeki tüm C# dosyalarını bir *. xyz* (bir dll) olarak derler:

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>C# derleyicisi ve C++ derleyici çıkışı arasındaki farklılıklar

C# derleyicisini çağırma sonucu olarak oluşturulan herhangi bir nesne (*. obj*) dosyası yoktur; çıktı dosyaları doğrudan oluşturulur. Bunun sonucunda, C# derleyicisinin bir bağlayıcıya ihtiyacı yoktur.

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Alfabetik Listelenmiş C# Derleyici Seçenekleri](./listed-alphabetically.md)
- [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](./listed-by-category.md)
- [Main () ve Command-Line bağımsız değişkenleri](../../programming-guide/main-and-command-args/index.md)
- [Komut Satırı Bağımsız Değişkenleri](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [Komut satırı bağımsız değişkenlerini görüntüleme](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Ana() Dönüş Değerleri](../../programming-guide/main-and-command-args/main-return-values.md)

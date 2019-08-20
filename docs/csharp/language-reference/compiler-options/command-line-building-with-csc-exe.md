---
title: Csc. exe ile komut satırı oluşturma
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 54306c79bc2856996925756ee4261fbe67692aea
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606981"
---
# <a name="command-line-build-with-cscexe"></a>Csc. exe ile komut satırı oluşturma
Bir komut isteminde yürütülebilir C# dosyasının adını (*CSC. exe*) yazarak derleyiciyi çağırabilirsiniz.

**Visual Studio için geliştirici komut istemi** kullanıyorsanız, tüm gerekli ortam değişkenleri sizin için ayarlanır. Bu araca erişme hakkında daha fazla bilgi için bkz. [Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md) konusu. 

Standart bir komut Istemi penceresi kullanıyorsanız, bilgisayarınızdaki herhangi bir alt dizinden *CSC. exe* ' yi çağırabilmeniz için önce yolunu ayarlamanız gerekir. Ayrıca, komut satırı yapılarını desteklemek üzere uygun ortam değişkenlerini ayarlamak için *vsvars32. bat* dosyasını çalıştırmanız gerekir. *Vsvars32. bat*hakkında daha fazla bilgi için, bkz [. nasıl yapılır: Visual Studio komut satırı](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)için ortam değişkenlerini ayarlayın.

Yalnızca Windows yazılım geliştirme seti (SDK) olan bir bilgisayarda çalışıyorsanız, C# **Microsoft .NET Framework SDK** menü seçeneğinden açtığınız **SDK komut isteminde**derleyiciyi kullanabilirsiniz.

Ayrıca C# programlarını program aracılığıyla oluşturmak için MSBuild'i kullanabilirsiniz. Daha fazla bilgi için bkz. [MSBuild](/visualstudio/msbuild/msbuild).

*CSC. exe* yürütülebilir dosyası genellikle\\ *Windows* dizini altındaki Microsoft. NET\Framework *\<Version >* klasöründe bulunur. Bu dosyanın yeri, belirli bir bilgisayarın tam yapılandırmasına bağlı olarak değişebilir. Bilgisayarınızda .NET Framework'ün birden fazla sürümü yüklüyse, bu dosyanın birden fazla sürümünü bulacaksınız. Bu tür yüklemeler hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
>  Visual Studio IDE kullanarak bir proje oluşturduğunuzda, **CSC** komutunu ve ilgili derleyici seçeneklerini **Çıkış** penceresinde görüntüleyebilirsiniz. Bu bilgileri göstermek için aşağıdaki yönergeleri [izleyin: Günlük verilerinin ayrıntı düzeyini **normal** veya **ayrıntılı**olarak değiştirmek](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) için yapı günlüğü dosyalarını görüntüleyin, kaydedin ve yapılandırın. Projenizi yeniden oluşturduktan sonra, C# derleyicinin çağrılmasını bulmak Için **CSC** **Çıkış** penceresinde arama yapın.

 **Bu konudaki**

- [Komut satırı söz dizimi için kurallar](#rules-for-command-line-syntax-for-the-c-compiler)

- [Örnek komut satırları](#sample-command-lines-for-the-c-compiler)

- [Derleyici ve C# C++ derleyici çıkışı arasındaki farklılıklar](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>C# Derleyici komut satırı sözdizimi için kurallar

C# Derleyici, işletim sistemi komut satırında verilen bağımsız değişkenleri yorumladığı zaman aşağıdaki kuralları kullanır:

- Bağımsız değişkenler boşluk veya sekme olan boşluk ile sınırlandırılmıştır.

- Giriş işareti karakteri (^) bir kaçış karakteri veya sınırlayıcı olarak tanınmıyor. Karakter, programdaki `argv` diziye geçirilmeden önce işletim sistemindeki komut satırı ayrıştırıcısı tarafından işlenir.

- Çift tırnak işaretleri ("String") içine alınmış bir dize, içinde yer alan boşluklardan bağımsız olarak tek bir bağımsız değişken olarak yorumlanır. Tırnak içine alınmış bir dize bir bağımsız değişkene gömülebilir.

- Önünde ters eğik çizgi (\\") olan bir çift tırnak işareti, sabit değer çift tırnak işareti karakteri (") olarak yorumlanır.

- Ters eğik çizgiler, bir çift tırnak işaretinden hemen önce gelmedikleri takdirde tam olarak yorumlanır.

- İki ters eğik çizgi daha sonra çift tırnak işareti kullanıyorsa, bir ters eğik çizgi her çift eğik çizgi için `argv` diziye konur ve çift tırnak işareti dize sınırlayıcısı olarak yorumlanır.

- Tek bir ters eğik çizgiden sonra çift tırnak işareti varsa, her ters eğik çizgi çifti için bir ters eğik `argv` çizgi konur ve çift tırnak işareti kalan ters eğik çizgi için "kaçışlı" olur. Bu, içinde `argv`bir sabit değer çift tırnak işareti (") eklenmesine neden olur.

## <a name="sample-command-lines-for-the-c-compiler"></a>C# Derleyici için örnek komut satırları

- *File.cs* üreten *dosya. exe*' yi derler:

```console
csc File.cs 
```

- *File.cs* üreten *dosyayı derler. dll*:

```console
csc -target:library File.cs
```

- *File.cs* derler ve *My. exe dosyasını*oluşturur:

```console
csc -out:My.exe File.cs
```

- Geçerli dizindeki tüm C# dosyaları iyileştirmeler etkin olacak şekilde derler ve hata ayıklama sembolünü tanımlar. Çıktı, *dosya2. exe*' dir:

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- Geçerli dizindeki tüm C# dosyaları, *dosya2. dll*' nin hata ayıklama sürümünü üreten şekilde derler. Amblem yoktur ve hiçbir uyarı gösterilmez:

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- Geçerli dizindeki tüm C# dosyaları *bir. xyz* (bir dll) olarak derler:

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Derleyici ve C# C++ derleyici çıkışı arasındaki farklılıklar
Derleyiciyi çağırma sonucu olarak oluşturulan nesne ( *. obj*) dosyaları yoktur; C# çıktı dosyaları doğrudan oluşturulur. Bunun sonucunda, C# derleyicinin bir bağlayıcıya ihtiyacı yoktur.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Alfabetik Listelenmiş C# Derleyici Seçenekleri](./listed-alphabetically.md)
- [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](./listed-by-category.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../programming-guide/main-and-command-args/index.md)
- [Komut Satırı Bağımsız Değişkenleri](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüle](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Ana() Dönüş Değerleri](../../programming-guide/main-and-command-args/main-return-values.md)

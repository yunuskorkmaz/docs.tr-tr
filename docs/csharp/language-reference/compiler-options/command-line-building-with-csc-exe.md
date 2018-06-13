---
title: Csc.exe ile komut satırı derleme
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 3cd49a17991f3d7606b0364a83be2b2e30ba0cce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218065"
---
# <a name="command-line-build-with-cscexe"></a>Csc.exe ile komut satırı derleme
Yürütülebilir dosyanın adını yazarak C# Derleyici çağırabileceği (*csc.exe*) bir komut isteminde.

Kullanırsanız **Visual Studio için geliştirici komut istemi** penceresinde, tüm gerekli ortam değişkenlerini sizin için ayarlanır. Bu araç erişim hakkında daha fazla bilgi için bkz: [Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md) konu. 

Standart bir komut istemi penceresi kullanırsanız, çağırabilirsiniz önce yolunuzu değiştirmelisiniz *csc.exe* bilgisayarınızdaki herhangi bir alt dizinden. Ayrıca çalıştırmalısınız *vsvars32.bat* komut satırı derlemeleri desteklemek için uygun ortam değişkenlerini ayarlamak için. Hakkında daha fazla bilgi için *vsvars32.bat*, bulma ve görmek hakkında yönergeler de dahil olmak üzere [nasıl yapılır: ortam değişkenleri ayarlamak için Visual Studio komut satırı](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Yalnızca sahip bir bilgisayarda çalışırken [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], C# Derleyici adresindeki kullanabilirsiniz **SDK Komut İstemi**, uyguladığınız **Microsoft .NET Framework SDK** menü seçeneği.

Ayrıca C# programlarını program aracılığıyla oluşturmak için MSBuild'i kullanabilirsiniz. Daha fazla bilgi için bkz: [MSBuild](/visualstudio/msbuild/msbuild).

*Csc.exe* yürütülebilir dosya genellikle bulunan Microsoft.NET\Framework\\*\<sürüm >* klasörü altında *Windows* Dizin. Bu dosyanın yeri, belirli bir bilgisayarın tam yapılandırmasına bağlı olarak değişebilir. Bilgisayarınızda .NET Framework'ün birden fazla sürümü yüklüyse, bu dosyanın birden fazla sürümünü bulacaksınız. Yüklemeler hakkında daha fazla bilgi için bkz: [nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
>  Visual Studio IDE kullanarak bir projeyi derlerken görüntüleyebileceğiniz **csc** komut ve onun ilişkili derleyici seçenekleri **çıkış** penceresi. Bu bilgileri görüntülemek için'ndaki yönergeleri izleyin [nasıl yapılır: görünümü, kaydetme ve yapı günlük dosyalarını Yapılandır](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) günlük verilerini ayrıntı düzeyini değiştirmek için **Normal** veya **ayrıntılı**. Projenizi yeniden oluşturduktan sonra arama **çıkış** penceresi **csc** C# Derleyici çağırma bulunamıyor.

 **Bu konudaki**

- [Komut satırı sözdizimi için kurallar](#-rules-for-command-line-syntax-for-the-c-compiler)

- [Örnek komut satırları](#sample-command-lines-for-the-c-compiler)

- [C# Derleyici ve C++ Derleyici çıktısı arasındaki farklar](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>C# derleyici komut satırı sözdizimi için kurallar

C# Derleyici işletim sistemi komut satırında belirtilen bağımsız değişkenler yorumlar aşağıdaki kuralları kullanır:

- Bağımsız değişkenler, bir boşluk veya bir sekme olduğu boşluk tarafından sınırlandırılır.

- Şapka (^) karakteri kaçış karakteri veya sınırlayıcı tanınmıyor. İçin geçmeden önce karakter işletim sisteminde komut satırı ayrıştırıcı tarafından işlenir `argv` program dizisinde.

- Çift tırnak işaretleri ("dize") içine bir dize kapsamında yer alan boşluk bakılmaksızın tek bir bağımsız değişken olarak yorumlanır. Tırnak içine alınan bir dizeyi bir bağımsız değişken katıştırılabilir.

- Çift tırnak işareti eğik çizgi işaretinden (\\") değişmez değer çift tırnak işareti karakteri (") olarak yorumlanır.

- Bunlar hemen çift tırnak işareti koyun sürece ters eğik çizgi tam anlamıyla, yorumlanır.

- Ters eğik çizgi çift sayıda çift tırnak işareti izlediyseniz, bir ters eğik çizgi içine `argv` dizi her çift ters eğik çizgi ve çift tırnak işareti dize ayırıcı olarak yorumlanır.

- Ters eğik çizgi tek sayıda çift tırnak işareti izlediyseniz, bir ters eğik çizgi içine `argv` dizi her çift ters eğik çizgi ve çift tırnak işareti "önce" kalan ters eğik çizgi tarafından. Bu sabit çift tırnak içinde eklenecek işareti (") neden olan `argv`.

## <a name="sample-command-lines-for-the-c-compiler"></a>C# derleyici için örnek komut satırları

- Derlenen *File.cs* oluşturan *File.exe*:

```console
csc File.cs 
```

- Derlenen *File.cs* oluşturan *File.dll*:

```console
csc -target:library File.cs
```

- Derlenen *File.cs* ve oluşturur *My.exe*:

```console
csc -out:My.exe File.cs
```

- Tüm C# dosyalarını geçerli dizinde iyileştirmeler etkinleştirilerek derler ve hata ayıklama simgesi tanımlar. Çıktı *File2.exe*:

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- Tüm C# geçerli dizindeki dosyaları bir hata ayıklama sürümü üreten derleyen *File2.dll*. Logo ve uyarı görüntülenir:

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- Tüm C# dosyalarını geçerli dizine derler *Something.xyz* (DLL):

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>C# Derleyici ve C++ Derleyici çıktısı arasındaki farklar
Hiçbir nesne vardır (*.obj*) dosyaları oluşturan C# Derleyici çağrılması sonucunda; çıktı dosyaları doğrudan oluşturulur. Bunun sonucunda, C# Derleyici bir bağlayıcı gerektirmez.

## <a name="see-also"></a>Ayrıca bkz.
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Alfabetik Listelenmiş C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
 [Nasıl yapılır: komut satırı bağımsız değişkenlerini görüntüleme](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Ana() Dönüş Değerleri](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

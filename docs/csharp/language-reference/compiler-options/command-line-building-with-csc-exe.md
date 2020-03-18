---
title: komut satırı csc.exe ile inşa
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: f692e66672b1804a309c6ac04c158af948a1b1ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789866"
---
# <a name="command-line-build-with-cscexe"></a>komut satırı csc.exe ile inşa

C# derleyicisini komut istemine çalıştırılabilir dosyasının *(csc.exe)* adını yazarak çağırabilirsiniz.

Visual Studio **için Geliştirici Komut İstemi** penceresini kullanıyorsanız, gerekli tüm ortam değişkenleri sizin için ayarlanır. Bu araca nasıl erişiğihakkında bilgi için [Visual Studio için Geliştirici Komut Komut Istem konusuna](../../../framework/tools/developer-command-prompt-for-vs.md) bakın.

Standart bir Komut İstem penceresi kullanıyorsanız, bilgisayarınızdaki herhangi bir alt dizinden *csc.exe'yi* çağırmadan önce yolunuzu ayarlamanız gerekir. Ayrıca komut satırı yapılarını desteklemek için uygun ortam değişkenlerini ayarlamak için *vsvars32.bat* çalıştırmalısınız. *vsvars32.bat*hakkında daha fazla bilgi için , nasıl bulup çalıştırılacağı yla ilgili talimatlar da dahil olmak üzere, [Visual Studio Komut Satırı için ortam değişkenlerinin nasıl ayarlanmasına](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)bakın.

Yalnızca Windows Yazılım Geliştirme Kiti 'ne (SDK) sahip bir bilgisayarda çalışıyorsanız, **Microsoft .NET Framework SDK** menü seçeneğinden açtığınız **SDK Komut İstemi'nde**C# derleyicisini kullanabilirsiniz.

Ayrıca C# programlarını program aracılığıyla oluşturmak için MSBuild'i kullanabilirsiniz. Daha fazla bilgi için [MSBuild'e](/visualstudio/msbuild/msbuild)bakın.

*csc.exe* yürütülebilir dosya genellikle *Windows* dizininin altındaki\\Microsoft.NET\Framework*\<Version>* klasöründe bulunur. Bu dosyanın yeri, belirli bir bilgisayarın tam yapılandırmasına bağlı olarak değişebilir. Bilgisayarınızda .NET Framework'ün birden fazla sürümü yüklüyse, bu dosyanın birden fazla sürümünü bulacaksınız. Bu tür yüklemeler hakkında daha fazla bilgi için [bkz: .NET Framework'ün hangi sürümlerinin yüklü olduğunu belirleyin.](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)

> [!TIP]
> Visual Studio IDE'yi kullanarak bir proje oluşturduğunuzda, **CSC** komutunu ve ilişkili derleyici seçeneklerini **Çıkış** penceresinde görüntüleyebilirsiniz. Bu bilgileri görüntülemek için, günlük verilerinin ayrıntılılık düzeyini **Normal** veya **Ayrıntılı**olarak değiştirmek için [Yapı Günlüğü Dosyalarını Görüntüleme, Kaydet ve Yapılandırma](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) yönergelerini izleyin. Projenizi yeniden yaptıktan sonra C# derleyicisinin çağrısını bulmak için **CSC** için **Çıktı** penceresinde arama yapın.

 **Bu konuda**

- [Komut satırı sözdizimi için kurallar](#rules-for-command-line-syntax-for-the-c-compiler)

- [Örnek komut satırları](#sample-command-lines-for-the-c-compiler)

- [C# derleyicisi ile C++ derleyici çıkışı arasındaki farklar](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>C# derleyicisi için komut satırı sözdizimi kuralları

C# derleyicisi, işletim sistemi komut satırında verilen bağımsız değişkenleri yorumlarken aşağıdaki kuralları kullanır:

- Bağımsız değişkenler, bir boşluk veya sekme olan beyaz boşlukla sınırlandırılır.

- Caret karakteri (^) bir kaçış karakteri veya sınır layıcı olarak tanınmıyor. Karakter, programdaki `argv` diziye geçirilmeden önce işletim sistemindeki komut satırı parertarafından işlenir.

- Çift tırnak işaretleri ("string") içine bir dize, içinde bulunan beyaz boşluk ne olursa olsun, tek bir bağımsız değişken olarak yorumlanır. Alıntı yapılan bir dize bir bağımsız değişkene katıştı.

- Bir ters eğik çizgiden önce\\gelen çift tırnak işareti ( ") gerçek bir çift tırnak işareti karakteri (") olarak yorumlanır.

- Ters eğik çizgiler, hemen çift tırnak işaretinden önce olmadıkça, kelimenin tam anlamıyla yorumlanır.

- Çift etek li bir çift tırnak işareti takip edilirse, her çift `argv` eğik çizgi için diziye bir ters eğik çizgi konur ve çift tırnak işareti dize delimiter olarak yorumlanır.

- Tek sayıda ters eğik çizgi çift tırnak işareti takip edilirse, bir `argv` ters çizgi diziye her çift ters eğik çizgi için konur ve çift tırnak işareti kalan ters eğik çizgi tarafından "kaçtı". Bu, bir çift tırnak işaretinin (") `argv`eklenmesine neden olur.

## <a name="sample-command-lines-for-the-c-compiler"></a>C# derleyicisi için örnek komut satırları

- *File.exe* *üreten File.cs* derler:

  ```console
  csc File.cs
  ```

- *Dosya.dll* *File.cs* derler:

  ```console
  csc -target:library File.cs
  ```

- *derlemeler File.cs* ve *My.exe*oluşturur:

  ```console
  csc -out:My.exe File.cs
  ```

- Geçerli dizindeki tüm C# dosyalarını etkinleştirilmiş en iyi duruma sahip dosyaları derler ve HATA Ayıklama simgesini tanımlar. Çıktı *File2.exe:*

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- *File2.dll'nin*hata ayıklama sürümünü üreten geçerli dizindeki tüm C# dosyalarını derler. Logo ve uyarı görüntülenmez:

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- *Bir Şey.xyz* (bir DLL) için geçerli dizindeki tüm C# dosyalarını derler:

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>C# derleyicisi ile C++ derleyici çıkışı arasındaki farklar

C# derleyicisinin çağırılanması sonucu oluşturulan nesne (*.obj*) dosyaları yoktur; çıktı dosyaları doğrudan oluşturulur. Bunun bir sonucu olarak, C# derleyicisinin bir bağlayıcıya ihtiyacı yoktur.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Alfabetik Listelenmiş C# Derleyici Seçenekleri](./listed-alphabetically.md)
- [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](./listed-by-category.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../programming-guide/main-and-command-args/index.md)
- [Komut Satırı Bağımsız Değişkenleri](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [Komut satırı bağımsız değişkenlerini görüntüleme](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Ana() Dönüş Değerleri](../../programming-guide/main-and-command-args/main-return-values.md)

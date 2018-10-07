---
title: 'Nasıl yapılır: Tek Dosyalı Derleme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fff84266dd99b84cc99c1996a3063dc962fa2e94
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841144"
---
# <a name="how-to-build-a-single-file-assembly"></a>Nasıl yapılır: Tek Dosyalı Derleme Oluşturma

Tür bilgilerini ve uygulama, derlemenin basit türü olan bir tek dosyalı bütünleştirilmiş kod içeren yanı sıra [derleme bildirimi](../../../docs/framework/app-domains/assembly-manifest.md). Komut satırı derleyicilerini veya Visual Studio, tek dosyalı derleme oluşturmak için kullanabilirsiniz. Varsayılan olarak, derleyici bir .exe uzantılı bir derleme dosyası oluşturur.

> [!NOTE]
> Visual Studio C# ve Visual Basic için yalnızca tek dosya derlemeleri oluşturmak için kullanılabilir. Çok dosyalı derlemeler oluşturmak istiyorsanız, komut satırı derleyicilerini veya Visual C++ kullanmanız gerekir.

Aşağıdaki yordamlar, komut satırı derleyicilerini kullanarak tek dosya derlemeleri oluşturmak nasıl gösterir.

## <a name="to-create-an-assembly-with-an-exe-extension"></a>.Exe uzantısına bir derleme oluşturmak için

1.  Komut satırında, aşağıdaki komutu yazın:

     \<*derleyici komut*> \<*modül adı*>

     Bu komutta *derleyici komut* kod modülünde, kullanılan dil derleyici komut ve *modül adı* birleştirme dosyasına derlemek için kod modülünün adı.

 Aşağıdaki örnekte adlı bir derleme oluşturur `myCode.exe` adlı kod modülünde `myCode`.

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Bir .exe uzantılı bir derleme oluşturun ve çıktı dosyası adını belirtin

1.  Komut satırında, aşağıdaki komutu yazın:

     \<*derleyici komut*> **/out:**\<*dosya adı*> \<*modül adı*>

     Bu komutta *derleyici komut* kod modülünde, kullanılan dil derleyici komut *dosya adı* çıkış dosyası adı ve *modül adı* adıdır bir birleştirme dosyasına derlemek için kod modülü.

 Aşağıdaki örnekte adlı bir derleme oluşturur `myAssembly.exe` adlı kod modülünde `myCode`.

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a>Kitaplık derlemeleri oluşturma
 Kitaplık derlemesi, bir sınıf kitaplığı'na benzer. Diğer derlemeler tarafından başvurulan türleri içerir, ancak bu yürütme başlamak için hiç giriş noktası yok.

### <a name="to-create-a-library-assembly"></a>Bir kitaplığı derlemesi oluşturmak için

1.  Komut satırında, aşağıdaki komutu yazın:

     \<*derleyici komut*> **- t: Kitaplık** \< *modül adı*>

     Bu komutta *derleyici komut* kod modülünde, kullanılan dil derleyici komut ve *modül adı* birleştirme dosyasına derlemek için kod modülünün adı. Gibi diğer derleyici seçenekleri kullanabilirsiniz **-out:** seçeneği.

 Aşağıdaki örnekte adlı Kitaplık derlemesi oluşturur `myCodeAssembly.dll` adlı kod modülünde `myCode`.

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)
- [Çok Dosyalı Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/multifile-assemblies.md)
- [Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
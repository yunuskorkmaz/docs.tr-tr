---
title: 'Nasıl yapılır: tek dosya .NET Framework derleme oluşturma'
description: .NET ' te tek dosya derleme oluşturmayı öğrenin. Tek dosya derlemesi, .NET 'i hedefleyen bir kitaplık (. dll) olabilir veya bir yürütülebilir (. exe) dosya olabilir.
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: 482a973631e899b8d4bfc4640eef1ea26173605e
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104921"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>Nasıl yapılır: tek dosya .NET Framework derleme oluşturma

En basit derleme türü olan tek dosya derlemesi, tür bilgilerini ve uygulamayı, ayrıca [derleme bildirimini](../../standard/assembly/manifest.md)içerir. .NET Framework hedefleyen tek dosya derleme oluşturmak için komut satırı derleyicilerini veya Visual Studio 'Yu kullanabilirsiniz. Varsayılan olarak, derleyici *. exe* uzantılı bir derleme dosyası oluşturur.

> [!NOTE]
> C# ve Visual Basic için Visual Studio yalnızca tek dosya derlemeler oluşturmak için kullanılabilir. Çoklu dosya derlemeleri oluşturmak istiyorsanız, komut satırı derleyicilerini veya Visual C++ kullanmanız gerekir.

Aşağıdaki yordamlarda, komut satırı derleyicileri kullanılarak tek dosya derlemelerinin nasıl oluşturulacağı gösterilmektedir.

## <a name="create-an-assembly-with-an-exe-extension"></a>. Exe uzantısıyla derleme oluşturma

Komut isteminde aşağıdaki komutu yazın:

\<*compiler command*> \<*module name*>

Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır.

Aşağıdaki örnek, adlı bir kod modülünden *myCode.exe* adlı bir derleme oluşturur `myCode` .

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>. Exe uzantısıyla bir derleme oluşturun ve çıkış dosyası adını belirtin

Komut isteminde aşağıdaki komutu yazın:

\<*compiler command*>**/Out:** \<*file name*>\<*module name*>

Bu komutta *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu, *dosya adı* ise çıkış dosyası adı ve *Modül adı* , derlemeye derlenecek kod modülünün adıdır.

Aşağıdaki örnek, adlı bir kod modülünden *myAssembly.exe* adlı bir derleme oluşturur `myCode` .

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>Kitaplık derlemeleri oluşturma
 Kitaplık derlemesi, sınıf kitaplığına benzer. Diğer derlemeler tarafından başvurulacak türleri içerir, ancak yürütmeye başlamak için bir giriş noktası yoktur.

Bir kitaplık derlemesi oluşturmak için, komut isteminde aşağıdaki komutu yazın:

\<*compiler command*>**-t:Library**\<*module name*>

Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır. **-Out:** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.

Aşağıdaki örnek, adlı bir kod modülünden *myCodeAssembly.dll* adlı bir kitaplık derlemesi oluşturur `myCode` .

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme oluşturma](../../standard/assembly/create.md)
- [Birden çok dosyalı derlemeler](multifile-assemblies.md)
- [Nasıl yapılır: Birden çok dosyalı derleme oluşturma](build-multifile-assembly.md)
- [Derlemeler ile programlama](../../standard/assembly/index.md)

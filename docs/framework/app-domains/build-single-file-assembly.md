---
title: 'Nasıl yapılır: Tek dosya .NET Framework derleme oluşturma'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98f06e62e1070f78faa77ef7d83fd80a62984684
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991244"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>Nasıl yapılır: Tek dosya .NET Framework derleme oluşturma

En basit derleme türü olan tek dosya derlemesi, tür bilgilerini ve uygulamayı, ayrıca [derleme bildirimini](../../standard/assembly/manifest.md)içerir. .NET Framework hedefleyen tek dosya derleme oluşturmak için komut satırı derleyicilerini veya Visual Studio 'Yu kullanabilirsiniz. Varsayılan olarak, derleyici *. exe* uzantılı bir derleme dosyası oluşturur.

> [!NOTE]
> Ve Visual Basic için C# Visual Studio yalnızca tek dosya derlemeler oluşturmak için kullanılabilir. Çok dosyalı derlemeler oluşturmak istiyorsanız, komut satırı derleyicileri veya görsel C++kullanmanız gerekir.

Aşağıdaki yordamlarda, komut satırı derleyicileri kullanılarak tek dosya derlemelerinin nasıl oluşturulacağı gösterilmektedir.

## <a name="create-an-assembly-with-an-exe-extension"></a>. Exe uzantısıyla derleme oluşturma

Komut satırında, aşağıdaki komutu yazın:

\<*derleyici komut*> modül\<*adı*>

Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır.

Aşağıdaki örnek, adlı `myCode`bir kod modülünden *MyCode. exe* adlı bir derleme oluşturur.

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>. Exe uzantısıyla bir derleme oluşturun ve çıkış dosyası adını belirtin

Komut satırında, aşağıdaki komutu yazın:

\<*Derleyici komutu*>  **/Out:** \<*Dosya*adımodül> adı\<>

Bu komutta *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu, *dosya adı* ise çıkış dosyası adı ve *Modül adı* , derlemeye derlenecek kod modülünün adıdır.

Aşağıdaki örnek, adlı `myCode`bir kod modülünden *MyAssembly. exe* adlı bir derleme oluşturur.

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>Kitaplık derlemeleri oluşturma
 Kitaplık derlemesi, sınıf kitaplığına benzer. Diğer derlemeler tarafından başvurulacak türleri içerir, ancak yürütmeye başlamak için bir giriş noktası yoktur.

Bir kitaplık derlemesi oluşturmak için, komut isteminde aşağıdaki komutu yazın:

\<*Derleyici komutu*>  **-t:Library** \< *Modül adı*>

Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır. **-Out:** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.

Aşağıdaki örnek, adlı `myCode`bir kod modülünden *mycodeassembly. dll* adlı bir kitaplık derlemesi oluşturur.

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler oluştur](../../standard/assembly/create.md)
- [Çoklu dosya derlemeleri](multifile-assemblies.md)
- [Nasıl yapılır: Çoklu dosya derlemesi oluşturma](build-multifile-assembly.md)
- [Bütünleştirilmiş kod içeren program](../../standard/assembly/program.md)

---
title: '-target: library (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: e15210d189c4a553da72b418f583e44666bac2fc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130964"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target: library (C# Derleyici Seçenekleri)
**-Target: library** seçeneği bir yürütülebilir dosya (EXE) yerine bir dinamik bağlantı kitaplığı (DLL) oluşturmak derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Açıklamalar  
 DLL, .dll uzantısıyla oluşturulur.  
  
 İle aksi belirtilmediği sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıkış dosyası adı ilk giriş dosyasının adını alır.  
  
 Tüm komut satırında belirtildiğinde kadar sonraki dosyalar **-out** veya **-target: module** seçeneği .dll dosyası oluşturmak için kullanılır.  
  
 Bir .dll dosyası oluştururken bir [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfası.  
  
2.  Tıklayın **uygulama** özellik sayfası.  
  
3.  Değiştirme **çıkış türü** özelliği.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs`, oluşturma `in.dll`:  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [-target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

---
title: '-target: winexe (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: f77137e3cc2f734435d3b1d391a303fcd3e16332
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970181"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target: winexe (C# Derleyici Seçenekleri)
**-Target: winexe** seçeneği bir yürütülebilir (EXE), Windows programı oluşturmak derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yürütülebilir dosyanın .exe uzantısı ile oluşturulur. Bir Windows ya da .NET Framework Kitaplığı'ndan veya Win32 API'ları ile bir kullanıcı arabirimi sağlayan bir programdır.  
  
 Kullanım [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) bir konsol uygulaması oluşturmak için.  
  
 İle aksi belirtilmediği sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıkış dosyası adını içeren giriş dosyasının adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.  
  
 Tüm komut satırında belirtildiğinde kadar sonraki dosyalar **-out** veya [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) seçeneği, Windows programı oluşturmak için kullanılır.  
  
 Bir ve yalnızca bir **ana** yöntemi bir .exe dosyasına derlenir kaynak kodu dosyalarında gereklidir. [-Ana](../../../csharp/language-reference/compiler-options/main-compiler-option.md) seçeneği hangi sınıfı içeren belirtmenize olanak tanır **ana** yöntemi ile birden fazla sınıf kodunuzu sahip olduğu durumlarda bir **ana** yöntemi.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfası.  
  
2.  Tıklayın **uygulama** özellik sayfası.  
  
3.  Değiştirme **çıkış türü** özelliği.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` Windows programı:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [-target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

---
title: "-target: winexe (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e155c64689f34c89443c7ff0a3dee38d6c190fcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="targetwinexe-c-compiler-options"></a>/target:winexe (C# Derleyici Seçenekleri)
**/Target: winexe** seçeneği bir yürütülebilir dosya (EXE), Windows programı oluşturmak derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/target:winexe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yürütülebilir dosyanın .exe uzantısı ile oluşturulur. Bir .NET Framework kitaplığından veya Win32 API'ları ile bir kullanıcı arabirimi sağlayan bir programdır.  
  
 Kullanım [/target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) bir konsol uygulaması oluşturmak için.  
  
 İle aksi belirtilmediği sürece [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adını içeren giriş dosyası adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.  
  
 Tüm komut satırında belirtildiğinde kadar sonraki dosyaları **/out** veya [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) seçeneği, Windows programı oluşturmak için kullanılır.  
  
 Yalnızca tek **ana** yöntemi bir .exe dosyasına derlenmiş kaynak kodu dosyaları gereklidir. [/Ana](../../../csharp/language-reference/compiler-options/main-compiler-option.md) seçeneği hangi sınıfı içeren belirtmenize olanak sağlar **ana** yöntemi ile birden fazla sınıf kodunuzu sahip olduğu durumlarda bir **ana** yöntemi.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **uygulama** özellik sayfası.  
  
3.  Değiştirme **çıktı türü** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` bir Windows programı içine:  
  
```console  
csc /target:winexe in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

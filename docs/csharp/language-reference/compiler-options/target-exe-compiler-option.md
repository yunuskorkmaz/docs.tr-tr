---
title: "-target: exe (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b66ab51b30e17ab2f34f88158c3f6095e185468d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="targetexe-c-compiler-options"></a>/target:exe (C# Derleyici Seçenekleri)
**/Target: exe** seçeneği bir yürütülebilir dosya (EXE) oluşturmak için konsol uygulaması derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/target:exe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **/Target: exe** seçeneği varsayılan olarak etkin olan. Yürütülebilir dosyanın .exe uzantısı ile oluşturulur.  
  
 Kullanım [/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) yürütülebilir bir Windows programı oluşturmak için.  
  
 İle aksi belirtilmediği sürece [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adını içeren giriş dosyası adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.  
  
 Tüm komut satırında belirtildiğinde kadar sonraki dosyaları **/out** veya **/target: Module** seçeneği .exe dosyası oluşturmak için kullanılır  
  
 Yalnızca tek **ana** yöntemi bir .exe dosyasına derlenmiş kaynak kodu dosyaları gereklidir. [/Ana](../../../csharp/language-reference/compiler-options/main-compiler-option.md) derleyici seçeneği hangi sınıfı içeren belirtmenize olanak sağlar **ana** yöntemi ile birden fazla sınıf kodunuzu sahip olduğu durumlarda bir **ana** yöntemi.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **uygulama** özellik sayfası.  
  
3.  Değiştirme **çıktı türü** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut satırlarını her derlenir `in.cs`, oluşturma `in.exe`:  
  
```console  
csc /target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

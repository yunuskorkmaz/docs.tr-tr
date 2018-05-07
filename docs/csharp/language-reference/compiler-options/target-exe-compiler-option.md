---
title: '-target: exe (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 194e4f7efaebd9523791090bcab09c019f8554a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-targetexe-c-compiler-options"></a>-target: exe (C# Derleyici Seçenekleri)
**-Target: exe** seçeneği bir yürütülebilir dosya (EXE) oluşturmak için konsol uygulaması derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **-Target: exe** seçeneği varsayılan olarak etkin olan. Yürütülebilir dosyanın .exe uzantısı ile oluşturulur.  
  
 Kullanım [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) yürütülebilir bir Windows programı oluşturmak için.  
  
 İle aksi belirtilmediği sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adını içeren giriş dosyası adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.  
  
 Tüm komut satırında belirtildiğinde kadar sonraki dosyaları **-out** veya **-target: module** seçeneği .exe dosyası oluşturmak için kullanılır  
  
 Yalnızca tek **ana** yöntemi bir .exe dosyasına derlenmiş kaynak kodu dosyaları gereklidir. [-Ana](../../../csharp/language-reference/compiler-options/main-compiler-option.md) derleyici seçeneği hangi sınıfı içeren belirtmenize olanak sağlar **ana** yöntemi ile birden fazla sınıf kodunuzu sahip olduğu durumlarda bir **ana** yöntemi.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **uygulama** özellik sayfası.  
  
3.  Değiştirme **çıktı türü** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut satırlarını her derlenir `in.cs`, oluşturma `in.exe`:  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [-target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

---
title: "-target: library (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e66e2edd86dc4a1302b23dab07226a5d56cb79b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="targetlibrary-c-compiler-options"></a>/target:library (C# Derleyici Seçenekleri)
**/Target: library** seçeneği yürütülebilir bir dosyanın (EXE) yerine bir dinamik bağlantı kitaplığı (DLL) oluşturmak derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/target:library  
```  
  
## <a name="remarks"></a>Açıklamalar  
 DLL .dll uzantısı ile oluşturulur.  
  
 İle aksi belirtilmediği sürece [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adı ilk giriş dosyasının adını alır.  
  
 Tüm komut satırında belirtildiğinde kadar sonraki dosyaları **/out** veya **/target: Module** seçeneği .dll dosyasını oluşturmak için kullanılır.  
  
 Bir .dll dosyasını oluştururken bir [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **uygulama** özellik sayfası.  
  
3.  Değiştirme **çıktı türü** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs`, oluşturma `in.dll`:  
  
```console  
csc /target:library in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

---
description: '-target: Library (C# derleyici seçenekleri)'
title: '-target: Library (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 0f5b1e1bec8fd601bf111e1c2c64adf22d0a064e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193731"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target: Library (C# derleyici seçenekleri)

**-Target: Library** seçeneği derleyicinin yürütülebilir dosya (exe) yerine bir dinamik bağlantı KITAPLıĞı (dll) oluşturmasına neden olur.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Açıklamalar  

 DLL,. dll uzantısıyla oluşturulacaktır.  
  
 Aksi belirtilmediği [takdirde, çıkış](./out-compiler-option.md) dosyası adı ilk giriş dosyasının adını alır.  
  
 Komut satırında belirtildiğinde, bir sonraki **-Out** veya **-target: Module** seçeneğine kadar olan tüm dosyalar,. dll dosyasını oluşturmak için kullanılır.  
  
 Bir. dll dosyası oluştururken [Main](../../programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Uygulama** Özellik sayfasına tıklayın.  
  
3. **Çıktı türü** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..  
  
## <a name="example"></a>Örnek  

 Derle `in.cs` , oluşturma `in.dll` :  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# derleyici seçenekleri)](./target-compiler-option.md)
- [C# derleyici seçenekleri](./index.md)

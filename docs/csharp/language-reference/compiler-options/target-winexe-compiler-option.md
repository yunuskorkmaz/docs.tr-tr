---
description: '-target: winexe (C# derleyici seçenekleri)'
title: '-target: winexe (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 8a1be07455b54b375106fef1fb480d7abd2f1ca4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124727"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target: winexe (C# derleyici seçenekleri)
**-Target: winexe** seçeneği derleyicinin YÜRÜTÜLEBILIR (exe), Windows programı oluşturmasına neden olur.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yürütülebilir dosya,. exe uzantısıyla oluşturulacaktır. Windows programı, .NET Framework kitaplığından veya Windows API 'Leriyle bir kullanıcı arabirimi sağlayan bir programdır.  
  
 Bir konsol uygulaması oluşturmak için [-target: exe](./target-exe-compiler-option.md) ' yi kullanın.  
  
 Aksi belirtilmedikçe, çıkış dosyası [adı,](./out-compiler-option.md) [ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.  
  
 Komut satırında belirtildiğinde, Windows programını oluşturmak için sonraki **dışarı** veya [-hedef](./target-compiler-option.md) seçeneğine kadar tüm dosyalar kullanılır.  
  
 Bir. exe dosyasına derlenen kaynak kodu dosyalarında bir ve yalnızca bir **ana** Yöntem gereklidir. [-Main](./main-compiler-option.md) seçeneği, kodunuzun bir **Main** yöntemi olan birden fazla sınıfa sahip olduğu durumlarda, hangi sınıfın **ana** yöntemi içerdiğini belirtmenizi sağlar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Uygulama** Özellik sayfasına tıklayın.  
  
3. **Çıktı türü** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..  
  
## <a name="example"></a>Örnek  
 `in.cs`Bir Windows programında derle:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# derleyici seçenekleri)](./target-compiler-option.md)
- [C# derleyici seçenekleri](./index.md)

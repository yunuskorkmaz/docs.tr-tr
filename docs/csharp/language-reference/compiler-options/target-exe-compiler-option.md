---
title: '-target: exe (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 6087a64bea5a59bfcfc5372f6a9d6eb8b9c940cb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606459"
---
# <a name="-targetexe-c-compiler-options"></a>-target: exe (C# derleyici seçenekleri)
**-Target: exe** seçeneği derleyicinin YÜRÜTÜLEBILIR (exe), konsol uygulaması oluşturmasına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **-Target: exe** seçeneği varsayılan olarak etkindir. Yürütülebilir dosya,. exe uzantısıyla oluşturulacaktır.  
  
 Bir Windows program yürütülebilir dosyası oluşturmak için [-target: winexe](./target-winexe-compiler-option.md) kullanın.  
  
 Aksi belirtilmedikçe, çıkış dosyası [](./out-compiler-option.md) adı, [ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.  
  
 Komut satırında belirtildiğinde, bir sonraki **-Out** veya **-target: Module** seçeneğine kadar olan tüm dosyalar,. exe dosyasını oluşturmak için kullanılır  
  
 Bir. exe dosyasına derlenen kaynak kodu dosyalarında bir ve yalnızca bir **ana** Yöntem gereklidir. [-Main](./main-compiler-option.md) derleyici seçeneği, kodunuzun bir **Main** yöntemi olan birden fazla sınıfa sahip olduğu durumlarda **Main** yöntemini hangi sınıfın içerdiğini belirtmenizi sağlar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Uygulama** Özellik sayfasına tıklayın.  
  
3. **Çıktı türü** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut satırlarından her biri derler `in.cs`, şunu oluşturur: `in.exe`  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# derleyici seçenekleri)](./target-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)

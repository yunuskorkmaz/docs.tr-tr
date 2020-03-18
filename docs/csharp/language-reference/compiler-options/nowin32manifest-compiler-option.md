---
title: -nowin32manifest (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602720"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (C# Derleyici Seçenekleri)
Derleyiciye yürütülebilir dosyaya herhangi bir uygulama bildirimi yerleştirmemesi için talimat vermek için **-nowin32manifest** seçeneğini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek kullanıldığında, Win32 Kaynak dosyasında veya daha sonraki bir yapı adımında bir uygulama bildirimi sağlamadığınız sürece uygulama Windows Vista'da sanallaştırmaya tabi olacaktır.  
  
 Visual Studio'da, **Bildirim** açılır listesinde **Manifest olmayan Uygulama Oluştur** seçeneğini seçerek bu seçeneği Uygulama **Özelliği** sayfasında ayarlayın. Daha fazla bilgi için [Uygulama Sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)sayfasına bakın.  
  
 Bildirim oluşturma hakkında daha fazla bilgi için bkz: [-win32manifest (C# Derleyici Seçenekleri)](./win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

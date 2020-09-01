---
description: -nowin32manifest (C# derleyici seçenekleri)
title: -nowin32manifest (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8514ab5b118e320d456d1b7367fab3b463c3607a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125065"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (C# derleyici seçenekleri)
Derleyicinin herhangi bir uygulama bildirimini yürütülebilir dosyaya katıştırmamasını sağlamak için **-nowin32manifest** seçeneğini kullanın.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek kullanıldığında, bir Win32 kaynak dosyasında veya sonraki bir derleme adımı sırasında uygulama bildirimi belirtmediğiniz müddetçe uygulama Windows Vista 'da sanallaştırmaya tabi olacaktır.  
  
 Visual Studio 'da, **bildirim** açılan listesinde **bildirim olmadan uygulama oluştur** seçeneğini belirleyerek **uygulama özelliği** sayfasında bu seçeneği ayarlayın. Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Bildirim oluşturma hakkında daha fazla bilgi için bkz. [-win32manifest (C# derleyici seçenekleri)](./win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

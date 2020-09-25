---
description: '-target: Module (C# derleyici seçenekleri)'
title: '-target: Module (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: d8691e5e4477dbbe989344469b44382d5e0e7c8b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193614"
---
# <a name="-targetmodule-c-compiler-options"></a>-target: Module (C# derleyici seçenekleri)

Bu seçenek derleyicinin bir derleme bildirimi üretmesine neden olur.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Varsayılan olarak, bu seçenekle derleme tarafından oluşturulan çıkış dosyası. netmodule uzantısına sahip olacaktır.  
  
 Derleme bildirimine sahip olmayan bir dosya .NET çalışma zamanı tarafından yüklenemez. Ancak, bu tür bir dosya, [-addmodule](./addmodule-compiler-option.md)aracılığıyla bir derlemenin derleme bildirimine eklenebilir.  
  
 Tek bir derlemede birden fazla modül oluşturulduysa, bir modüldeki [iç](../keywords/internal.md) türler derlemedeki diğer modüller için kullanılabilir olacaktır. Bir modüldeki kod `internal` , başka bir modüldeki türlere başvurduğunda, her iki modülün da **-addmodule**aracılığıyla bir derleme bildirimine dahil olması gerekir.  
  
 Visual Studio geliştirme ortamında modül oluşturma desteklenmez.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..  
  
## <a name="example"></a>Örnek  

 Derle `in.cs` , oluşturma `in.netmodule` :  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# derleyici seçenekleri)](./target-compiler-option.md)
- [C# derleyici seçenekleri](./index.md)

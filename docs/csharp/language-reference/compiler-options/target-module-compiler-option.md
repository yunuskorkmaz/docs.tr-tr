---
title: '-target: Module (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602445"
---
# <a name="-targetmodule-c-compiler-options"></a>-target: Module (C# derleyici seçenekleri)
Bu seçenek derleyicinin bir derleme bildirimi üretmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, bu seçenekle derleme tarafından oluşturulan çıkış dosyası. netmodule uzantısına sahip olacaktır.  
  
 Derleme bildirimine sahip olmayan bir dosya, .NET Framework ortak dil çalışma zamanı tarafından yüklenemez. Ancak, bu tür bir dosya, [-addmodule](./addmodule-compiler-option.md)aracılığıyla bir derlemenin derleme bildirimine eklenebilir.  
  
 Tek bir derlemede birden fazla modül oluşturulduysa, bir modüldeki [iç](../keywords/internal.md) türler derlemedeki diğer modüller için kullanılabilir olacaktır. Bir modüldeki kod, başka bir `internal` modüldeki türlere başvurduğunda, her iki modülün da **-addmodule**aracılığıyla bir derleme bildirimine dahil olması gerekir.  
  
 Visual Studio geliştirme ortamında modül oluşturma desteklenmez.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Derle `in.cs`, oluşturma `in.netmodule`:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# derleyici seçenekleri)](./target-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)

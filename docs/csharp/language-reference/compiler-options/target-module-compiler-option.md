---
title: -hedef:modül (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602445"
---
# <a name="-targetmodule-c-compiler-options"></a>-hedef:modül (C# Derleyici Seçenekleri)
Bu seçenek derleyicinin derleme bildirimi oluşturmamasını sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, bu seçenekle derleyerek oluşturulan çıkış dosyası .netmodule uzantısına sahip olacaktır.  
  
 Derleme bildirimi olmayan bir dosya .NET Framework ortak dil çalışma süresi tarafından yüklenemez. Ancak, böyle bir dosya [-addmodule](./addmodule-compiler-option.md)yoluyla bir derleme derleme manifestosuna dahil edilebilir.  
  
 Tek bir derlemede birden fazla modül oluşturulursa, bir modüldeki [dahili](../keywords/internal.md) türler derlemedeki diğer modüller tarafından kullanılabilir. Bir modüldeki kod `internal` başka bir modüldeki türlere atıfta bulununca, her iki modül de **-addmodule**ile bir montaj manifestosuna dahil edilmelidir.  
  
 Visual Studio geliştirme ortamında modül oluşturma desteklenmez.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>  
  
## <a name="example"></a>Örnek  
 Derlemek `in.cs`, `in.netmodule`oluşturma :  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-hedef (C# Derleyici Seçenekleri)](./target-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)

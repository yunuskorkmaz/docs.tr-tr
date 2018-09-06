---
title: '-target: module (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 7cc0e48a7a4a3ec3f28c89e80fadf6aa7e1130f2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724584"
---
# <a name="-targetmodule-c-compiler-options"></a>-target: module (C# Derleyici Seçenekleri)
Bu seçenek, bir derleme bildirimi oluşturulmayacağını derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, bu seçenekle derlenerek oluşturulan çıktı dosyası, bir .netmodule uzantısına sahip olacaktır.  
  
 .NET Framework ortak dil çalışma zamanı tarafından bir derleme bildirimi içermeyen bir dosya yüklenemiyor. Ancak, böyle bir dosya derleme bildirimi aracılığıyla bir derlemenin içine dahil edilebilir [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Tek bir derlemede birden fazla modülü oluşturulursa [iç](../../../csharp/language-reference/keywords/internal.md) bir modüldeki türler derlemeye diğer modüller için kullanıma sunulacaktır. Bir modül başvurularında kod `internal` iki modülü yoluyla bir derleme bildirimine birleştirilmesi gerekir sonra başka bir modülde türleri **- addmodule**.  
  
 Visual Studio geliştirme ortamında, bir modül oluşturma desteklenmiyor.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs`, oluşturma `in.netmodule`:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [-target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

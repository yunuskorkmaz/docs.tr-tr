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
ms.openlocfilehash: 89139867cb0a207dbe82168015629fcb9e2fa6eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601902"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

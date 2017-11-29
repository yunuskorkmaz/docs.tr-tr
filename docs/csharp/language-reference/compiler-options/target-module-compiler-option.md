---
title: "-target: module (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2b54ea9085ecc23d4a535d440d0634c997f22615
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="targetmodule-c-compiler-options"></a>/target:module (C# Derleyici Seçenekleri)
Bu seçenek, bir derleme bildirimi Oluştur değil derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/target:module  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, bu seçenek ile derleme tarafından oluşturulan çıktı dosyası .netmodule bir uzantısına sahip olacaktır.  
  
 .NET Framework ortak dil çalışma zamanı tarafından bir derleme bildirimi sahip olmayan bir dosya yüklenemiyor. Ancak, böyle bir dosya yoluyla bir derlemenin derleme bildirimi içine birleştirilebilir [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Tek bir derleme birden fazla modülü oluşturduysanız [iç](../../../csharp/language-reference/keywords/internal.md) bir modüldeki türleri derlemedeki diğer modüllerle kullanılabilir olacak. Ne zaman bir modül başvurularında kod `internal` hem modülleri yoluyla bir derleme bildirimine birleştirilmesi gerekir sonra başka bir modülde türleri **/addmodule**.  
  
 Visual Studio geliştirme ortamında, bir modül oluşturma desteklenmiyor.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs`, oluşturma `in.netmodule`:  
  
```console  
csc /target:module in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

---
description: -noconfig (C# derleyici seçenekleri)
title: -noconfig (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: d62f16a3926aaa78e79c25b1c9b8d84e4401795a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194082"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (C# derleyici seçenekleri)

**-Noconfig** seçeneği, derleyicinin ' de bulunan ve csc.exe dosyasıyla aynı dizinden yüklenen csc. rsp dosyası ile derlenmeyeceğini söyler.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Csc. rsp dosyası .NET Framework ile gönderilen tüm derlemelere başvurur. Visual Studio .NET geliştirme ortamının içerdiği gerçek başvurular proje türüne bağlıdır.  
  
 Csc. rsp dosyasını değiştirebilir ve csc.exe ( **-noconfig** seçeneği dışında) komut satırından her derlemede yer alan ek derleyici seçeneklerini belirtebilirsiniz.  
  
 Derleyici, son olarak **CSC** komutuna geçirilen seçenekleri işler. Bu nedenle, komut satırındaki herhangi bir seçenek CSC. rsp dosyasında aynı seçeneğin ayarını geçersiz kılar.  
  
 Derleyicinin Csc. rsp dosyasındaki ayarları bulup kullanmasını istemiyorsanız **-noconfig**' i belirtin.  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

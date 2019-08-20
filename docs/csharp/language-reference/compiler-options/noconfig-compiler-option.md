---
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
ms.openlocfilehash: 2d6d0c52be2306292224d7831f8818c6f865f2f4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602745"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (C# derleyici seçenekleri)
**-Noconfig** seçeneği, derleyicinin ' de bulunan ve CSC. exe dosyası ile aynı dizinden yüklenen csc. rsp dosyası ile derlenmeyeceğini söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Csc. rsp dosyası .NET Framework ile gönderilen tüm derlemelere başvurur. Visual Studio .NET geliştirme ortamının içerdiği gerçek başvurular proje türüne bağlıdır.  
  
 Csc. rsp dosyasını değiştirebilir ve CSC. exe ile komut satırından her derlemeye dahil edilecek ek derleyici seçeneklerini belirtebilirsiniz ( **-noconfig** seçeneği hariç).  
  
 Derleyici, son olarak **CSC** komutuna geçirilen seçenekleri işler. Bu nedenle, komut satırındaki herhangi bir seçenek CSC. rsp dosyasında aynı seçeneğin ayarını geçersiz kılar.  
  
 Derleyicinin Csc. rsp dosyasındaki ayarları bulup kullanmasını istemiyorsanız **-noconfig**' i belirtin.  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

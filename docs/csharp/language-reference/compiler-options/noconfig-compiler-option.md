---
title: -noconfig (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: b689a4bf0d8a1e57bf36f8ded7f2c9308f241670
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402700"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (C# Derleyici Seçenekleri)
**- Noconfig** seçeneği bulunan ve aynı dizinden csc.exe dosyası olarak yüklenen csc.rsp dosyasını derlemek değil derleyicinin söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Csc.rsp dosyasını .NET Framework ile birlikte gelen tüm derlemelere başvurur. Visual Studio .NET geliştirme ortamını içeren gerçek başvuruları proje türüne bağlıdır.  
  
 Csc.rsp dosyasını değiştirebilir ve her derleme komut satırından csc.exe dahil edilmesi gereken ek derleyici seçeneklerini belirtin (dışında **- noconfig** seçeneği).  
  
 Derleyici geçirilecek seçeneklerini işler **csc** son komutu. Bu nedenle, komut satırında herhangi bir seçenek csc.rsp dosyasını aynı seçeneğinin ayarını geçersiz kılar.  
  
 Derleyicinin arayın ve csc.rsp dosyasındaki ayarları kullanın, belirtmek istemiyorsanız **- noconfig**.  
  
 Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

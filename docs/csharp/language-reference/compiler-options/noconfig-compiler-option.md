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
ms.openlocfilehash: 96321de5982a79cb073b658a84e0e580dd466539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (C# Derleyici Seçenekleri)
**- Noconfig** seçeneği bulunan ve csc.exe dosyasıyla aynı dizinden yüklenen csc.rsp dosyasıyla değil derlemeye derleyici söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Csc.rsp dosyasını .NET Framework ile gönderilen tüm derlemelere başvurur. Visual Studio .NET geliştirme ortamı içerir gerçek başvurular proje türüne bağlıdır.  
  
 Csc.rsp dosyasını değiştirebilir ve csc.exe ile komut satırından her derlemeyi dahil edilmesi gereken ek derleyici seçeneklerini belirtin (dışında **- noconfig** seçeneği).  
  
 Derleyici geçirilen seçenekleri işler **csc** son komutu. Bu nedenle, komut satırında herhangi bir seçenek csc.rsp dosyasındaki aynı seçeneği ayarını geçersiz kılar.  
  
 Derleyicinin arayın ve csc.rsp dosyasındaki ayarları kullanmak için belirtmek istemiyorsanız **- noconfig**.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

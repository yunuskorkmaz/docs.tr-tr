---
title: "-noconfig (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2b15853cdd6ee9fe12b8b3ba3388a74e49c9701
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig-c-compiler-options"></a>/noconfig (C# Derleyici Seçenekleri)
**/Noconfig** seçeneği bulunan ve csc.exe dosyasıyla aynı dizinden yüklenen csc.rsp dosyasıyla değil derlemeye derleyici söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Csc.rsp dosyasını .NET Framework ile gönderilen tüm derlemelere başvurur. Visual Studio .NET geliştirme ortamı içerir gerçek başvurular proje türüne bağlıdır.  
  
 Csc.rsp dosyasını değiştirebilir ve csc.exe ile komut satırından her derlemeyi dahil edilmesi gereken ek derleyici seçeneklerini belirtin (dışında **/noconfig** seçeneği).  
  
 Derleyici geçirilen seçenekleri işler **csc** son komutu. Bu nedenle, komut satırında herhangi bir seçenek csc.rsp dosyasındaki aynı seçeneği ayarını geçersiz kılar.  
  
 Derleyicinin arayın ve csc.rsp dosyasındaki ayarları kullanmak için belirtmek istemiyorsanız **/noconfig**.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)

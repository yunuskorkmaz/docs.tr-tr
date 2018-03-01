---
title: "-noconfig (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1004f70547ca3a841c59338a1344235132af3fa7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
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

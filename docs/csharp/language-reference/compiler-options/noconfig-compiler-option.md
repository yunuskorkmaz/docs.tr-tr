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
ms.openlocfilehash: 2d6d0c52be2306292224d7831f8818c6f865f2f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602745"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (C# Derleyici Seçenekleri)
**-noconfig** seçeneği derleyiciye csc.exe dosyasıyla aynı dizinde bulunan ve yüklenen csc.rsp dosyasıyla derlememelerini söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 csc.rsp dosyası ,NET Framework ile gönderilen tüm derlemelere başvurur. Visual Studio .NET geliştirme ortamının içerdiği gerçek başvurular proje türüne bağlıdır.  
  
 CSc.rsp dosyasını değiştirebilir ve komut satırından csc.exe ile **(-noconfig** seçeneği hariç) her derlemeye eklenmesi gereken ek derleyici seçenekleri belirtebilirsiniz.  
  
 Derleyici, **csc** komutuna geçen seçenekleri en son işler. Bu nedenle, komut satırındaki herhangi bir seçenek csc.rsp dosyasında aynı seçeneğin ayarını geçersiz kılar.  
  
 Derleyicinin csc.rsp dosyasındaki ayarları aramasını ve kullanmasını **istemiyorsanız, -noconfig'** i belirtin.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamaz ve programlı olarak değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

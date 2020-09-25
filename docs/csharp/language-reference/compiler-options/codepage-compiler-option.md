---
description: -CodePage (C# derleyici seçenekleri)
title: -CodePage (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: eda4ce5604beb25ae2d72ac94fbbe7dde9695820
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196812"
---
# <a name="-codepage-c-compiler-options"></a>-CodePage (C# derleyici seçenekleri)

Bu seçenek, gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse, derleme sırasında kullanılacak kod sayfasını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `id`  
 Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasının kimliği.  
  
## <a name="remarks"></a>Açıklamalar  

 Derleyici önce tüm kaynak dosyalarını UTF-8 olarak yorumlamaya çalışacaktır. Kaynak kodu dosyalarınız UTF-8 dışındaki bir kodlamadeyse ve 7 bit ASCII karakterlerden farklı karakterler kullanıyorsa, hangi kod sayfasının kullanılacağını belirtmek için **-CodePage** seçeneğini kullanın. **-CodePage** , derinizdeki tüm kaynak kodu dosyaları için geçerlidir.  

 Sisteminizde hangi kod sayfalarının desteklendiğini bulma hakkında bilgi için bkz. [Getcpınfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) .  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

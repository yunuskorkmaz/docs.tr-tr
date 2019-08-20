---
title: -CodePage (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: c85cd8935bcefd1353707624052b62ee982f7b07
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603057"
---
# <a name="-codepage-c-compiler-options"></a>-CodePage (C# derleyici seçenekleri)
Bu seçenek, gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse, derleme sırasında kullanılacak kod sayfasını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
 `id`  
 Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasının kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici önce tüm kaynak dosyalarını UTF-8 olarak yorumlamaya çalışacaktır. Kaynak kodu dosyalarınız UTF-8 dışındaki bir kodlamadeyse ve 7 bit ASCII karakterlerden farklı karakterler kullanıyorsa, hangi kod sayfasının kullanılacağını belirtmek için **-CodePage** seçeneğini kullanın. **-CodePage** , derinizdeki tüm kaynak kodu dosyaları için geçerlidir.  
    
 Sisteminizde hangi kod sayfalarının desteklendiğini bulma hakkında bilgi için bkz. [Getcpınfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) .  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

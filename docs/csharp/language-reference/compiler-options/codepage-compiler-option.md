---
title: -kod sayfası (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 3352e7fc446ace391540360a3b6b36d604ca5f13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173763"
---
# <a name="-codepage-c-compiler-options"></a>-kod sayfası (C# Derleyici Seçenekleri)
Bu seçenek, gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse, derleme sırasında hangi kod sayfasının kullanılacağını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `id`  
 Derlemedeki tüm kaynak kod dosyaları için kullanılacak kod sayfasının kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici ilk olarak tüm kaynak dosyaları UTF-8 olarak yorumlamaya çalışır. Kaynak kod dosyalarınız UTF-8 dışındaki bir kodlamadaysa ve 7 bit ASCII karakterleri dışındaki karakterleri kullanıyorsa, hangi kod sayfasının kullanılması gerektiğini belirtmek için **-codepage** seçeneğini kullanın. **-codepage** derlemenizdeki tüm kaynak kod dosyaları için geçerlidir.  

 Sisteminizde hangi kod sayfalarının desteklendiği hakkında bilgi için [GetCPInfo'ya](/windows/desktop/api/winnls/nf-winnls-getcpinfo) bakın.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamaz ve programlı olarak değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

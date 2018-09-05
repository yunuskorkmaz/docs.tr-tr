---
title: -codepage (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 66edb32d24dd1dc543097b98ff3744f0aa0a7145
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511878"
---
# <a name="-codepage-c-compiler-options"></a>-codepage (C# Derleyici Seçenekleri)
Bu seçenek, gerekli sayfa sistemi için geçerli varsayılan kod sayfası değilse derleme sırasında kullanılacak hangi kod sayfasını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
 `id`  
 Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Bilgisayarınızda varsayılan kod sayfası kullanılacak oluşturulmayan bir veya daha fazla kaynak kodu dosyaları derleme yaparsanız, kullanabileceğiniz **- kod sayfası** hangi kod sayfası kullanılması gerektiğini belirtmek için seçeneği. **-codepage** derlemenizdeki tüm kaynak kodu dosyaları için geçerlidir.  
  
 Kaynak kodu dosyaları bilgisayarınızda geçerli olan kod sayfası ile oluşturulan veya kaynak kodu dosyaları UNICODE veya UTF-8 ile oluşturulduysa, kullanılmıyor ihtiyacınız varsa **- kod sayfası**.  
  
 Bkz: [desteklendiğinin](/windows/desktop/api/winnls/nf-winnls-getcpinfo) nasıl hangi kodun bulunacağı hakkında bilgi için sisteminizde sayfaları desteklenir.  
  
 Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

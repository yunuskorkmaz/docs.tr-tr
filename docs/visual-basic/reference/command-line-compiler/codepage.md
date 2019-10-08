---
title: -CodePage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: e4cdc27ab021fe055f157b78946538f2b76870e1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002366"
---
# <a name="-codepage-visual-basic"></a>-CodePage (Visual Basic)
Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`id`|Gerekli. Derleyici, kaynak dosyaların kodlamasını yorumlamak için `id` tarafından belirtilen kod sayfasını kullanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Belirli bir kodlamayla kaydedilen kaynak kodu derlemek için, hangi kod sayfasının kullanılacağını belirtmek için `-codepage` kullanabilirsiniz. @No__t-0 seçeneği, derinizdeki tüm kaynak kodu dosyaları için geçerlidir. Daha fazla bilgi için [.NET Framework karakter kodlaması](../../../standard/base-types/character-encoding.md)bölümüne bakın.  
  
 Kaynak kodu dosyaları bir imzayla geçerli ANSI kod sayfası, Unicode veya UTF-8 kullanılarak kaydedilmişse `-codepage` seçeneği gerekli değildir. Kullanıcı **kodlama** iletişim kutusunda başka bir kodlama belirtmediği takdirde, Visual Studio tüm kaynak kodu dosyalarını varsayılan olarak geçerli ANSI kod sayfasıyla kaydeder. Visual Studio, farklı bir kod sayfasıyla kaydedilen kaynak kodu dosyalarını açmak için **kodlama** iletişim kutusunu kullanır.  
  
> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

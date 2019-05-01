---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: fda75383435fdff718d1d50bc8583afc9858e7e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944709"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`id`|Gerekli. Derleyici tarafından belirtilen kod sayfası kullanır `id` kaynak dosyalarını kodlama yorumlamak için.|  
  
## <a name="remarks"></a>Açıklamalar  
 Belirli bir kodlama ile kaydedilmiş kaynak kodu derlemek için kullanabileceğiniz `-codepage` hangi kod sayfası kullanılması gerektiğini belirtmek için. `-codepage` Derlemenizdeki tüm kaynak kodu dosyaları seçeneğini uygular. Daha fazla bilgi için [karakter kodlaması .NET Framework'teki](../../../standard/base-types/character-encoding.md).  
  
 `-codepage` Seçeneği kaynak kodu dosyaları bir imza ile geçerli ANSI kod sayfası, Unicode veya UTF-8 kullanarak kaydedildiyse gerekli değildir. Visual Studio kaydeder tüm kaynak kodu dosyaları geçerli ANSI kod sayfasıyla varsayılan olarak, kullanıcı, başka bir kodlama belirtmediği sürece **kodlama** iletişim kutusu. Visual Studio kullanan **kodlama** farklı bir kod sayfası ile kaydedilen kaynak kodu dosyaları açmak için iletişim kutusu.  
  
> [!NOTE]
>  `-codepage` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

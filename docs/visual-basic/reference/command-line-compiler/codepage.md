---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 8aee51df3ba9f92ca662fbbfbd73998e4a3b4538
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405702"
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
 Belirli bir kodlama ile kaydedilmiş kaynak kodu derlemek için kullanabileceğiniz `-codepage` hangi kod sayfası kullanılması gerektiğini belirtmek için. `-codepage` Derlemenizdeki tüm kaynak kodu dosyaları seçeneğini uygular. Daha fazla bilgi için [karakter kodlaması .NET Framework'teki](https://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 `-codepage` Seçeneği kaynak kodu dosyaları bir imza ile geçerli ANSI kod sayfası, Unicode veya UTF-8 kullanarak kaydedildiyse gerekli değildir. Visual Studio kaydeder tüm kaynak kodu dosyaları geçerli ANSI kod sayfasıyla varsayılan olarak, kullanıcı, başka bir kodlama belirtmediği sürece **kodlama** iletişim kutusu. Visual Studio kullanan **kodlama** farklı bir kod sayfası ile kaydedilen kaynak kodu dosyaları açmak için iletişim kutusu.  
  
> [!NOTE]
>  `-codepage` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

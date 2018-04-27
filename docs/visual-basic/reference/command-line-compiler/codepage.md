---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f098dd04b457b7db008788bcfb141af3f69843f8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
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
|`id`|Gerekli. Derleyici tarafından belirtilen kod sayfası kullanan `id` kaynak dosyalarını kodlama yorumlayamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Belirli bir kodlama ile kaydedilmiş kaynak kodu derlemek için kullanabileceğiniz `-codepage` hangi kod sayfası kullanılması gerektiğini belirtmek için. `-codepage` Seçenek derlemeniz tüm kaynak kodu dosyaları için geçerlidir. Daha fazla bilgi için bkz: [karakter kodlamasını .NET Framework'teki](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 `-codepage` Seçeneği kaynak kodu dosyaları geçerli ANSI kod sayfası, Unicode veya UTF-8 bir imza ile kullanılarak kaydedildiyse gerekli değildir. Visual Studio kaydeder tüm kaynak kodu dosyaları geçerli ANSI kod sayfası ile varsayılan olarak, kullanıcı, başka bir kodlama belirtmedikçe **kodlama** iletişim kutusu. Visual Studio kullanan **kodlama** farklı kod sayfası ile kaydedilen kaynak kodu dosyaları açmak için iletişim kutusu.  
  
> [!NOTE]
>  `-codepage` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

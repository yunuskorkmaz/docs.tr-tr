---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 769f3586ddef7f430fa96d6101b250a5bbc4e26c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065742"
---
# <a name="-codepage-visual-basic"></a>-CodePage (Visual Basic)

Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`id`|Gereklidir. Derleyici, `id` kaynak dosyaların kodlamasını yorumlamak için tarafından belirtilen kod sayfasını kullanır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Belirli bir kodlamayla kaydedilen kaynak kodu derlemek için, `-codepage` hangi kod sayfasının kullanılacağını belirtmek için kullanabilirsiniz. Bu `-codepage` seçenek, derinizdeki tüm kaynak kodu dosyaları için geçerlidir. Daha fazla bilgi için [.NET Framework karakter kodlaması](../../../standard/base-types/character-encoding.md)bölümüne bakın.  
  
 `-codepage`Kaynak kodu dosyaları bir imzayla GEÇERLI ANSI kod sayfası, Unicode veya UTF-8 kullanılarak kaydedilmişse seçenek gerekli değildir. Kullanıcı **kodlama** iletişim kutusunda başka bir kodlama belirtmediği takdirde, Visual Studio tüm kaynak kodu dosyalarını varsayılan olarak geçerli ANSI kod sayfasıyla kaydeder. Visual Studio, farklı bir kod sayfasıyla kaydedilen kaynak kodu dosyalarını açmak için **kodlama** iletişim kutusunu kullanır.  
  
> [!NOTE]
> `-codepage`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)

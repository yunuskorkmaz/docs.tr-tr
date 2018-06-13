---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9c854060e5254cedc6c1004ac3e4f25fbdbbd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650673"
---
# <a name="-filealign"></a>-filealign
Çıkış dosyasının bölümlerinin hizalamak konumu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Gerekli. Çıktı dosyasında bölüm hizalamasını belirten bir değer. Geçerli değerler 512, 1024, 2048, 4096 ve 8192 ' dir. Bu değerler bayt cinsinden.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `-filealign` seçeneği çıkış dosyanızın bölüm hizalamasını belirtin. Kod veya veri içeren bir taşınabilir yürütülebilir (PE) dosyasında bitişik bellek bloklarını bölümleridir. `-filealign` Seçeneği standart olmayan bir hizalama uygulamanızla derleme olanak tanır; bu seçeneği kullanmak çoğu Geliştirici gerekmez.  
  
 Her bölümü olan bir sınır ile hizalanır `-filealign` değeri. Sabit varsayılan yok. Varsa `-filealign` belirtilmezse, derleyici varsayılan derleme zamanında seçer.  
  
 Bölüm boyutunu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz. Bölüm boyutunu değiştirme küçük cihazlarda çalışan programlar için yararlı olabilir.  
  
> [!NOTE]
>  `-filealign` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

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
ms.openlocfilehash: db70749f28592ae6711b6d9544f8704af9416490
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128173"
---
# <a name="-filealign"></a>-filealign
Çıktı dosyasının bölümlerinin hizalanacağı yeri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Gerekli. Çıkış dosyasında bölüm hizalamasını belirten bir değeri. Geçerli değerler, 512, 1024, 2048, 4096 ve 8192:. Bu değerler bayt.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `-filealign` seçeneği, çıkış dosyasında bölüm hizalamasını belirtin. Kod veya veri içeren taşınabilir yürütülebilir (PE) dosyası bitişik bellek blokları bölümleridir. `-filealign` Seçeneği ile standart olmayan bir hizalama uygulamanızı derleyin olanak sağlar; geliştiricilerin çoğu, bu seçeneği kullanmak gerekmez.  
  
 Her bölümde katları olan bir sınır üzerinde hizalanır `-filealign` değeri. Sabit varsayılan yok. Varsa `-filealign` belirtilmezse, derleyici derleme zamanında bir varsayılan seçer.  
  
 Bölüm boyutu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz. Bölüm boyutu değiştirme daha küçük cihazlarda çalıştırılacak programları için yararlı olabilir.  
  
> [!NOTE]
>  `-filealign` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

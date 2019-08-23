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
ms.openlocfilehash: 2893c1760a856a7d736e9c03ba33d9771722b5b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929479"
---
# <a name="-filealign"></a>-filealign
Çıktı dosyasının bölümlerinin hangi noktada hizalanacağını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Gerekli. Çıkış dosyasındaki bölümlerin hizalamasını belirten bir değer. Geçerli değerler 512, 1024, 2048, 4096 ve 8192. Bu değerler baytlardır.  
  
## <a name="remarks"></a>Açıklamalar  
 Çıkış dosyanızdaki bölümlerin hizalamasını `-filealign` belirtmek için seçeneğini kullanabilirsiniz. Bölümler, bir Taşınabilir çalıştırılabilir (PE) dosyasında kod veya veri içeren bitişik bellek bloklarıdır. `-filealign` Seçeneği uygulamanızı standart olmayan hizalamayla derlemenize olanak tanır; çoğu geliştirici bu seçeneği kullanmak zorunda kalmaz.  
  
 Her bölüm, `-filealign` değerin katı olan bir sınır üzerine hizalanır. Sabit bir varsayılan yoktur. `-filealign` Belirtilmemişse, derleyici derleme zamanında bir varsayılan değer seçer.  
  
 Bölüm boyutunu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz. Bölüm boyutunu değiştirmek, daha küçük cihazlarda çalıştırılacak programlar için yararlı olabilir.  
  
> [!NOTE]
> Bu `-filealign` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

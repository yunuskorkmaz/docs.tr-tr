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
ms.openlocfilehash: 3877757185030b0dba914a79d8c760fb8033ae5f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408653"
---
# <a name="-filealign"></a>-filealign
Çıktı dosyasının bölümlerinin hangi noktada hizalanacağını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `number`  
 Gereklidir. Çıkış dosyasındaki bölümlerin hizalamasını belirten bir değer. Geçerli değerler 512, 1024, 2048, 4096 ve 8192. Bu değerler baytlardır.  
  
## <a name="remarks"></a>Açıklamalar  
 `-filealign`Çıkış dosyanızdaki bölümlerin hizalamasını belirtmek için seçeneğini kullanabilirsiniz. Bölümler, bir Taşınabilir çalıştırılabilir (PE) dosyasında kod veya veri içeren bitişik bellek bloklarıdır. `-filealign`Seçeneği uygulamanızı standart olmayan hizalamayla derlemenize olanak tanır; çoğu geliştirici bu seçeneği kullanmak zorunda kalmaz.  
  
 Her bölüm, değerin katı olan bir sınır üzerine hizalanır `-filealign` . Sabit bir varsayılan yoktur. `-filealign`Belirtilmemişse, derleyici derleme zamanında bir varsayılan değer seçer.  
  
 Bölüm boyutunu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz. Bölüm boyutunu değiştirmek, daha küçük cihazlarda çalıştırılacak programlar için yararlı olabilir.  
  
> [!NOTE]
> `-filealign`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)

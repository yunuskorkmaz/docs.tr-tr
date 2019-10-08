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
ms.openlocfilehash: fef2652f591e713140c651a9cb0df1ea9e6236c8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005590"
---
# <a name="-filealign"></a>-filealign
Çıktı dosyasının bölümlerinin hangi noktada hizalanacağını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Gerekli. Çıkış dosyasındaki bölümlerin hizalamasını belirten bir değer. Geçerli değerler 512, 1024, 2048, 4096 ve 8192. Bu değerler baytlardır.  
  
## <a name="remarks"></a>Açıklamalar  
 Çıkış dosyanızdaki bölümlerin hizalamasını belirtmek için `-filealign` seçeneğini kullanabilirsiniz. Bölümler, bir Taşınabilir çalıştırılabilir (PE) dosyasında kod veya veri içeren bitişik bellek bloklarıdır. @No__t-0 seçeneği, uygulamanızı standart olmayan hizalamayla derlemenize olanak sağlar; çoğu geliştiricilerin bu seçeneği kullanması gerekmez.  
  
 Her bölüm `-filealign` değerinin katı olan bir sınıra hizalanır. Sabit bir varsayılan yoktur. @No__t-0 belirtilmemişse, derleyici derleme zamanında bir varsayılan değer seçer.  
  
 Bölüm boyutunu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz. Bölüm boyutunu değiştirmek, daha küçük cihazlarda çalıştırılacak programlar için yararlı olabilir.  
  
> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

---
description: Daha fazla bilgi edinin:-filealign
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
ms.openlocfilehash: f32ae370c0ef832b501f085351eadb9b6156c730
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470297"
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

- [Visual Basic Command-Line derleyicisi](index.md)

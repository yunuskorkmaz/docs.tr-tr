---
title: /filealign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbabc19c85501b97ef5443a6f6e12524f8de7d91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="filealign"></a>/filealign
Çıkış dosyasının bölümlerinin hizalamak konumu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Gerekli. Çıktı dosyasında bölüm hizalamasını belirten bir değer. Geçerli değerler 512, 1024, 2048, 4096 ve 8192 ' dir. Bu değerler bayt cinsinden.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `/filealign` seçeneği çıkış dosyanızın bölüm hizalamasını belirtin. Kod veya veri içeren bir taşınabilir yürütülebilir (PE) dosyasında bitişik bellek bloklarını bölümleridir. `/filealign` Seçeneği standart olmayan bir hizalama uygulamanızla derleme olanak tanır; bu seçeneği kullanmak çoğu Geliştirici gerekmez.  
  
 Her bölümü olan bir sınır ile hizalanır `/filealign` değeri. Sabit varsayılan yok. Varsa `/filealign` belirtilmezse, derleyici varsayılan derleme zamanında seçer.  
  
 Bölüm boyutunu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz. Bölüm boyutunu değiştirme küçük cihazlarda çalışan programlar için yararlı olabilir.  
  
> [!NOTE]
>  `/filealign` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

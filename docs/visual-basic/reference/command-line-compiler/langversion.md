---
title: /langversion (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cfe91588471cc8410b25addea8d66a0388c9c5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-visual-basic"></a>/langversion (Visual Basic)
Derleyicinin yalnızca belirtilen Visual Basic dil sürümü dahil sözdizimini kabul etmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a>Arguments  
 `version`  
 Gerekli. Derleme sırasında kullanılacak dil sürümü. Değerler kabul `9`, `9.0`, `10`, ve `10.0`.  
  
## <a name="remarks"></a>Açıklamalar  
 `/langversion` Seçeneği derleyici kabul hangi sözdizimini belirtir. Örneğin, dil sürümü 9.0 olduğunu belirtirseniz, derleyici geçerli yalnızca sürümünde 10.0 ve sonraki sözdizimi hataları oluşturur.  
  
 Bu hedef farklı sürümlerini .NET Framework uygulamaları geliştirirken, bu seçeneği kullanabilirsiniz. Örneğin, .NET Framework 3.5 hedefliyorsanız, 10.0 dil sürümünden sözdizimi kullanmayın emin olmak için bu seçeneği kullanabilirsiniz.  
  
 Ayarlayabileceğiniz `/langversion` doğrudan komut satırını kullanarak yalnızca. Daha fazla bilgi için bkz: [belirli bir .NET Framework sürümü hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `sample.vb` Visual Basic 9.0.  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Belirli bir .NET Framework sürümünü hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)

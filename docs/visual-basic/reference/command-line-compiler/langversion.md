---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9b91bf8efa6fabd21d257e51062dc881ab288f5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Derleyicinin yalnızca belirtilen Visual Basic dil sürümü dahil sözdizimini kabul etmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a>Arguments  
 `version`  
 Gerekli. Derleme sırasında kullanılacak dil sürümü. Değerler kabul `9`, `9.0`, `10`, ve `10.0`.  
  
## <a name="remarks"></a>Açıklamalar  
 `-langversion` Seçeneği derleyici kabul hangi sözdizimini belirtir. Örneğin, dil sürümü 9.0 olduğunu belirtirseniz, derleyici geçerli yalnızca sürümünde 10.0 ve sonraki sözdizimi hataları oluşturur.  
  
 Bu hedef farklı sürümlerini .NET Framework uygulamaları geliştirirken, bu seçeneği kullanabilirsiniz. Örneğin, .NET Framework 3.5 hedefliyorsanız, 10.0 dil sürümünden sözdizimi kullanmayın emin olmak için bu seçeneği kullanabilirsiniz.  
  
 Ayarlayabileceğiniz `-langversion` doğrudan komut satırını kullanarak yalnızca. Daha fazla bilgi için bkz: [belirli bir .NET Framework sürümü hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `sample.vb` Visual Basic 9.0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Belirli Bir .NET Framework Sürümünü Hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)

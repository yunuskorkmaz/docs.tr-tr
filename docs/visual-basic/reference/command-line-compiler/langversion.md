---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 82a7114027451d1342e6dc0846799933ce44d968
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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

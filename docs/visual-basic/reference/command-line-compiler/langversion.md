---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 15f334f280c2aca83ba5b628a1137464c31c6282
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005559"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Derleyicinin yalnızca belirtilen Visual Basic dil sürümünde bulunan sözdizimini kabul etmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>Arguments  
 `version`  
 Gerekli. Derleme sırasında kullanılacak dil sürümü. Kabul edilen değerler `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` ve `latest` ' dur.

 Tüm sayıların tamamı, ikincil sürüm olarak `.0` kullanılarak da belirtilebilir. Örneğin, `11.0`.

 Komut satırında `-langversion:?` belirterek, olası tüm değerlerin listesini görebilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 seçeneği derleyicinin kabul ettiği sözdizimini belirtir. Örneğin, dil sürümünün 9,0 olduğunu belirtirseniz, derleyici yalnızca 10,0 ve sonraki sürümlerde geçerli olan sözdizimi için hatalar oluşturur.  
  
 .NET Framework farklı sürümlerini hedefleyen uygulamalar geliştirirken, bu seçeneği kullanabilirsiniz. Örneğin, .NET Framework 3,5 ' i hedefliyorsanız, dil sürümü 10,0 ' den sözdizimini kullanmamanız için bu seçeneği kullanabilirsiniz.  
  
 Yalnızca komut satırını kullanarak doğrudan `-langversion` ayarlayabilirsiniz. Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, Visual Basic 9,0 için `sample.vb` derler.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Belirli Bir .NET Framework Sürümünü Hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)

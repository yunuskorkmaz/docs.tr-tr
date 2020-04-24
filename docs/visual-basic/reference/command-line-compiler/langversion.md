---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 72a5638a5c5364381ffd68604b0d44830d53f365
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344207"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Derleyicinin yalnızca belirtilen Visual Basic dil sürümünde bulunan sözdizimini kabul etmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `version`  
 Gereklidir. Derleme sırasında kullanılacak dil sürümü. Kabul edilen değerler `9`, `10` `11` `12` `14`,,,, `15`, `15.3`, `15.5` `default` ve `latest`.

 Tüm sayıların tümü, alt sürüm olarak (örneğin, `.0` `11.0`) kullanılarak da belirtilebilir.

 Komut satırında belirterek `-langversion:?` , olası tüm değerlerin listesini görebilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 `-langversion` Seçeneği derleyicinin kabul ettiği sözdizimini belirtir. Örneğin, dil sürümünün 9,0 olduğunu belirtirseniz, derleyici yalnızca 10,0 ve sonraki sürümlerde geçerli olan sözdizimi için hatalar oluşturur.  
  
 .NET Framework farklı sürümlerini hedefleyen uygulamalar geliştirirken, bu seçeneği kullanabilirsiniz. Örneğin, .NET Framework 3,5 ' i hedefliyorsanız, dil sürümü 10,0 ' den sözdizimini kullanmamanız için bu seçeneği kullanabilirsiniz.  
  
 Doğrudan yalnızca komut `-langversion` satırını kullanarak ayarlayabilirsiniz. Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](/visualstudio/ide/visual-studio-multi-targeting-overview).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod Visual Basic 9,0 `sample.vb` için derlenir.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Belirli Bir .NET Framework Sürümünü Hedefleme](/visualstudio/ide/visual-studio-multi-targeting-overview)

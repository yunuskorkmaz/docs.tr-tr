---
description: :-Langversion (Visual Basic) hakkında daha fazla bilgi edinin
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.custom: updateeachrelease
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 52bf910e5d6f579ec535d9de5698a8921f058002
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466867"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)

Derleyicinin yalnızca belirtilen Visual Basic dil sürümünde bulunan sözdizimini kabul etmesine neden olur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler

 `version`\
 Gereklidir. Derleme sırasında kullanılacak dil sürümü. Kabul edilen değerler şunlardır,,,,,, `9` `10` `11` `12` `14` `15` `15.3` , `15.5` , `16` `default` ve `latest` .

 Tüm sayıların tümü, alt sürüm olarak (örneğin,) kullanılarak da belirtilebilir `.0` `11.0` .

 Komut satırında belirterek, olası tüm değerlerin listesini görebilirsiniz `-langversion:?` .

## <a name="remarks"></a>Açıklamalar

`-langversion`Seçeneği derleyicinin kabul ettiği sözdizimini belirtir. Örneğin, dil sürümünün 9,0 olduğunu belirtirseniz, derleyici yalnızca 10,0 ve sonraki sürümlerde geçerli olan sözdizimi için hatalar oluşturur.

.NET Framework farklı sürümlerini hedefleyen uygulamalar geliştirirken, bu seçeneği kullanabilirsiniz. Örneğin, .NET Framework 3,5 ' i hedefliyorsanız, dil sürümü 10,0 ' den sözdizimini kullanmamanız için bu seçeneği kullanabilirsiniz.

`-langversion`Doğrudan yalnızca komut satırını kullanarak ayarlayabilirsiniz. Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="example"></a>Örnek

Aşağıdaki kod `sample.vb` Visual Basic 9,0 için derlenir.

```console
vbc -langversion:9.0 sample.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: db2cb1eb107973e9ce60ecb0d669c677d4fa2c51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793968"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Derleyicinin, belirtilen Visual Basic dil sürümü dahil edilen sözdizimini kabul etmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a>Arguments  
 `version`  
 Gerekli. Derleme sırasında kullanılacak dil sürümü. Kabul edilen değerler `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` ve `latest`.

 Tam sayılar da kullanırken belirtilebilir `.0` alt sürümü için olarak `11.0`.

 Tüm olası değerlerin listesi belirterek gördüğünüz `-langversion:?` komut satırında.  
  
## <a name="remarks"></a>Açıklamalar  
 `-langversion` Seçeneği derleyici kabul hangi sözdizimini belirtir. Örneğin, dil sürüm 9.0 olduğunu belirtirseniz, derleyici geçerli yalnızca sürüm 10.0 ve üstü söz dizimi hataları oluşturur.  
  
 Farklı sürümlerini hedefleyen .NET Framework'ün Uygulama geliştirirken, bu seçeneği kullanabilirsiniz. Örneğin, .NET Framework 3.5 hedefliyorsanız, dil sürüm 10.0 sözdizimini kullanmayın emin olmak için bu seçeneği kullanabilirsiniz.  
  
 Ayarlayabileceğiniz `-langversion` doğrudan komut satırını kullanarak yalnızca. Daha fazla bilgi için [belirli bir .NET Framework sürümünü hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `sample.vb` Visual Basic 9.0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Belirli Bir .NET Framework Sürümünü Hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)

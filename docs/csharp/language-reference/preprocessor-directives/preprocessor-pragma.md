---
title: '#pragma - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712461"
---
# <a name="pragma-c-reference"></a>#pragma (C# Başvurusu)
`#pragma`göründüğü dosyanın derleyicisi için özel talimatlar verir. Yönergeler derleyici tarafından desteklenmelidir. Başka bir deyişle, `#pragma` özel ön işleme yönergeleri oluşturmak için kullanamazsınız. Microsoft C# derleyicisi `#pragma` aşağıdaki iki yönergeyi destekler:  
  
 [#pragma uyarısı](./preprocessor-pragma-warning.md)  
  
 [#pragma checksum](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>Parametreler  
 `pragma-name`  
 Tanınan bir pragmanın adı.  
  
 `pragma-arguments`  
 Pragma'ya özgü argümanlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](./index.md)
- [#pragma uyarısı](./preprocessor-pragma-warning.md)
- [#pragma checksum](./preprocessor-pragma-checksum.md)

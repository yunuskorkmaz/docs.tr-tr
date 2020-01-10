---
title: '#pragma- C# Reference'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712461"
---
# <a name="pragma-c-reference"></a>#pragma (C# Başvurusu)
`#pragma`, derleyicinin göründüğü dosyanın derlenmesi için özel yönergeler sağlar. Yönergeler derleyici tarafından desteklenmelidir. Diğer bir deyişle, özel ön işleme yönergeleri oluşturmak için `#pragma` kullanamazsınız. Microsoft C# derleyicisi aşağıdaki iki `#pragma` yönergeleri destekler:  
  
 [#pragma uyarısı](./preprocessor-pragma-warning.md)  
  
 [#pragma sağlama toplamı](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>Parametreler  
 `pragma-name`  
 Tanınan bir pragma adı.  
  
 `pragma-arguments`  
 Pragma 'a özgü bağımsız değişkenler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
- [#pragma uyarısı](./preprocessor-pragma-warning.md)
- [#pragma sağlama toplamı](./preprocessor-pragma-checksum.md)

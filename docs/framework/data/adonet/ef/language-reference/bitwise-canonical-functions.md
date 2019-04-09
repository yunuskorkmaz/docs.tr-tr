---
title: Bit Düzeyinde Kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: 67d78e8d31f0bc3564a0a111b9bc71cbd0e14f5c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127809"
---
# <a name="bitwise-canonical-functions"></a>Bit Düzeyinde Kurallı İşlevler
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] bit düzeyinde kurallı işlevler içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda, bit düzeyinde gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler. Bu işlevler döndüreceği `Null` varsa `Null` giriş sağlanır. İşlevlerin dönüş türü bağımsız değişken türleri ile aynıdır. İşlevi, birden fazla bağımsız değişken alır, bağımsız değişkenler aynı türde olmalıdır. Farklı türleri üzerinde bit düzeyinde işlemler gerçekleştirmek için aynı türe açıkça cast gerekir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|Bit tabanlı ve işlecini birini döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.<br /><br /> **Arguments**<br /><br /> A `Byte`, `Int16`, `Int32`, ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Bitwise olumsuzlama, döndürür `value`.<br /><br /> **Arguments**<br /><br /> A `Byte`, `Int16`, `Int32`, ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|' In bit tabanlı veya işlecini verir `value1` ve `value2` türü olarak `value1` ve `value2`.<br /><br /> **Arguments**<br /><br /> A `Byte`, `Int16`, `Int32` ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|Bit tabanlı Dışlayıcı veya işlecini verir `value1` ve `value2` türü olarak `value1` ve `value2`.<br /><br /> **Arguments**<br /><br /> A `Byte`, `Int16`, `Int32` ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)

---
title: Bit düzeyinde kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: 882ecd2e82c64981dd76b3c860711433293145b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742279"
---
# <a name="bitwise-canonical-functions"></a>Bit düzeyinde kurallı İşlevler
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] bit düzeyinde kurallı işlevler içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda, bit düzeyinde gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler. Bu işlevler döndüreceği `Null` varsa `Null` giriş sağlanır. İşlevlerin dönüş türü bağımsız değişken türleri ile aynıdır. İşlevi, birden fazla bağımsız değişken alır, bağımsız değişkenler aynı türde olmalıdır. Farklı türleri üzerinde bit düzeyinde işlemler gerçekleştirmek için aynı türe açıkça cast gerekir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|Bit tabanlı ve işlecini birini döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Byte`, `Int16`, `Int32`, ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Bitwise olumsuzlama, döndürür `value`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Byte`, `Int16`, `Int32`, ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|' In bit tabanlı veya işlecini verir `value1` ve `value2` türü olarak `value1` ve `value2`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Byte`, `Int16`, `Int32` ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|Bit tabanlı Dışlayıcı veya işlecini verir `value1` ve `value2` türü olarak `value1` ve `value2`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Byte`, `Int16`, `Int32` ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)

---
title: Bit Düzeyinde Kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: 3c1f32acc7a035658198b807646c1ceb95dfed0b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251305"
---
# <a name="bitwise-canonical-functions"></a>Bit Düzeyinde Kurallı İşlevler
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]bit düzeyinde kurallı işlevler içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda bit düzeyinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler gösterilmektedir. Bu işlevler, `Null` giriş `Null` sağlanırsa döndürülür. İşlevlerin dönüş türü, bağımsız değişken türleri ile aynıdır. İşlevin birden fazla bağımsız değişken alırsa bağımsız değişkenlerin aynı türde olması gerekir. Farklı türlerde bit düzeyinde işlemler gerçekleştirmek için, aynı türe açıkça atamalısınız.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|`value2` `value1` Ve`value2`türüolarak ve için bit düzeyinde birlikte döndürür. `value1`<br /><br /> **Bağımsız Değişkenler**<br /><br /> ,,, Ve`Int64`. `Byte` `Int16` `Int32`<br /><br /> **Örnek**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Bit düzeyinde olumsuzunu `value`döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> ,,, Ve`Int64`. `Byte` `Int16` `Int32`<br /><br /> **Örnek**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|`value1` `value2` , Ve türü`value2`olarak bit düzeyinde bir debirleşimin döndürür. `value1`<br /><br /> **Bağımsız Değişkenler**<br /><br /> `Byte`, ,`Int16` Ve`Int64`. `Int32`<br /><br /> **Örnek**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|Ve`value1` `value1` türüolarakbit`value2` düzeyinde dışlamalı dışlamalı ve ' i döndürür. `value2`<br /><br /> **Bağımsız Değişkenler**<br /><br /> `Byte`, ,`Int16` Ve`Int64`. `Int32`<br /><br /> **Örnek**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](canonical-functions.md)

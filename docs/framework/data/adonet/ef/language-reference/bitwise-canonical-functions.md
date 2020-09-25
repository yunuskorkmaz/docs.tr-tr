---
title: Bit Düzeyinde Kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: 67ae0302f6faf0fb7284bc0c4a53a90ba6d55e08
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185268"
---
# <a name="bitwise-canonical-functions"></a>Bit Düzeyinde Kurallı İşlevler

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] bit düzeyinde kurallı işlevler içerir.  
  
## <a name="remarks"></a>Açıklamalar  

 Aşağıdaki tabloda bit düzeyinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler gösterilmektedir. Bu işlevler, `Null` `Null` giriş sağlanırsa döndürülür. İşlevlerin dönüş türü, bağımsız değişken türleri ile aynıdır. İşlevin birden fazla bağımsız değişken alırsa bağımsız değişkenlerin aynı türde olması gerekir. Farklı türlerde bit düzeyinde işlemler gerçekleştirmek için, aynı türe açıkça atamalısınız.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|`value1`Ve türü olarak ve için bit düzeyinde birlikte döndürür `value2` `value1` `value2` .<br /><br /> **Arguments**<br /><br /> `Byte`,, `Int16` , `Int32` Ve `Int64` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Bit düzeyinde olumsuzunu döndürür `value` .<br /><br /> **Arguments**<br /><br /> `Byte`,, `Int16` , `Int32` Ve `Int64` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|, `value1` `value2` Ve türü olarak bit düzeyinde bir debirleşimin döndürür `value1` `value2` .<br /><br /> **Arguments**<br /><br /> `Byte`, `Int16` , `Int32` Ve `Int64` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|`value1` `value2` Ve türü olarak bit düzeyinde dışlamalı dışlamalı ve ' i `value1` döndürür `value2` .<br /><br /> **Arguments**<br /><br /> `Byte`, `Int16` , `Int32` Ve `Int64` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](canonical-functions.md)

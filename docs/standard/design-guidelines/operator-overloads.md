---
title: İşleç aşırı yüklemeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ca42d25a5f3456c6a10eff76d7015656322abae
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874062"
---
# <a name="operator-overloads"></a>İşleç aşırı yüklemeleri
İşleç aşırı yüklemeleri framework türleri yerleşik dil temelleri oldukları gibi görünmesine izin verin.  
  
 İzin verilen ve bazı durumlarda yararlı olsa da, İşleç aşırı yüklemeleri dikkatli kullanılmalıdır. Hangi işlecinde aşırı yükleme, framework tasarımcıları işleçleri basit yöntemleri olmalıdır işlemlerinde kullanılacak başlatıldığında gibi kötüye birçok durumlar vardır. Aşağıdaki yönergeleri İşleç aşırı yüklemesi kullanma nasıl ve ne zaman karar vermenize yardımcı olmalıdır.  
  
 **X AVOID** gibi (yerleşik) ilkel türlerinde geliyor olmalıdır türlerinde dışında işleci aşırı tanımlama.  
  
 **✓ CONSIDER** gibi basit tür geliyor olmalıdır bir türdeki işlecin tanımlama.  
  
 Örneğin, <xref:System.String?displayProperty=nameWithType> sahip `operator==` ve `operator!=` tanımlı.  
  
 **✓ DO** numaralarını temsil eden yapılar için işleç aşırı yüklemeleri tanımlayın (gibi <xref:System.Decimal?displayProperty=nameWithType>).  
  
 **X DO NOT** işlecin tanımlarken şirin olabilir.  
  
 İşleç aşırı yüklemesi, işlemin sonucunu ne olacağını hemen açık olduğu durumlarda kullanışlıdır. Örneğin, bir çıkarma için mantıklıdır <xref:System.DateTime> başka bir `DateTime` ve bir <xref:System.TimeSpan>. Ancak, UNION iki veritabanı sorguları için mantıksal birleşim işleci kullanmayı veya bir akışa yazmak için kaydırma işleci kullanmak için uygun değildir.  
  
 **X DO NOT** işleci aşırı yüklemeler işlenen en az biri aşırı tanımlama türü olmadıkça sağlayın.  
  
 **✓ DO** bir simetrik şekilde işleçleri aşırı yükleme.  
  
 Örneğin, aşırı yükleme `operator==`, siz de aşırı `operator!=`. Benzer şekilde, işlecini aşırı yüklediyseniz `operator<`, siz de aşırı `operator>`ve benzeri.  
  
 **✓ CONSIDER** yöntemleri karşılık gelen kolay adlarla her aşırı yüklenmiş işleç sağlama.  
  
 Birçok diller, İşleç aşırı yüklemesi desteklemez. Bu nedenle, aşırı yükleme işleçleri türleri eşdeğer bir işlevselliği sağlayan uygun bir etki alanına özgü ad ile ikincil bir yöntem içerdiğini önerilir.  
  
 Aşağıdaki tabloda, işleçler ve karşılık gelen kolay bir yöntem adları listesini içerir.  
  
|C# işleç simgesi|Meta veri adı|Kolay ad|  
|-------------------------|-------------------|-------------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|  
|`=`|`op_Assign`|`Assign`|  
|`<<`|`op_LeftShift`|`LeftShift`|  
|`>>`|`op_RightShift`|`RightShift`|  
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|  
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|  
|`==`|`op_Equality`|`Equals`|  
|`!=`|`op_Inequality`|`Equals`|  
|`>`|`op_GreaterThan`|`CompareTo`|  
|`<`|`op_LessThan`|`CompareTo`|  
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|  
|`<=`|`op_LessThanOrEqual`|`CompareTo`|  
|`*=`|`op_MultiplicationAssignment`|`Multiply`|  
|`-=`|`op_SubtractionAssignment`|`Subtract`|  
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|  
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|  
|`%=`|`op_ModulusAssignment`|`Mod`|  
|`+=`|`op_AdditionAssignment`|`Add`|  
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|  
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### <a name="overloading-operator-"></a>İşleç aşırı yüklemesi ==  
 Aşırı yükleme `operator ==` oldukça karmaşıktır. İşleci semantiği gibi çeşitli diğer üyeleriyle uyumlu olmasına gerek <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
### <a name="conversion-operators"></a>Dönüşüm İşleçleri  
 Dönüştürme işleçleri, bir türden diğerine dönüştürme izin birli işleçler şunlardır. İşleçler, statik üye işlenen ya da dönüş türü olarak tanımlanmalıdır. Dönüştürme işleçleri iki tür vardır: örtük ve açık.  
  
 **X DO NOT** tür dönüştürme son kullanıcılar tarafından açıkça görülmüyorsa bir dönüşüm işleci sağlayın.  
  
 **X DO NOT** dönüşüm işleçleri dışında bir tür etki alanını tanımlayın.  
  
 Örneğin, <xref:System.Int32>, <xref:System.Double>, ve <xref:System.Decimal> ise tüm sayısal türlerin olan <xref:System.DateTime> değil. Bu nedenle, bulunmamalıdır dönüştürmek için hiçbir dönüştürme işleci bir `Double(long)` için bir `DateTime`. Böyle bir durumda bir oluşturucu tercih edilir.  
  
 **X DO NOT** dönüştürme olası kayıplı ise bir örtük dönüşüm işleci sağlayın.  
  
 Örneğin, olmamalıdır örtük bir dönüştürme `Double` için `Int32` çünkü `Double` daha geniş bir sahip `Int32`. Dönüştürme, olası kayıplı olsa bile, açık bir dönüştürme operatörü sağlanabilir.  
  
 **X DO NOT** örtük atamaları özel durumlar atar.  
  
 Son kullanıcılar için neler olduğunu, bunlar bir dönüştürme yer aldığını haberdar olmayabilir çünkü anlamak çok zordur.  
  
 **✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> atama işleci için bir çağrı sonuçları kayıplı dönüştürmede ve sözleşmenin işlecinin kayıplı dönüşümleri izin vermez.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)

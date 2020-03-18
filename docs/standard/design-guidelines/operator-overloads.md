---
title: İşleç Aşırı Yüklemeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400570"
---
# <a name="operator-overloads"></a>İşleç Aşırı Yüklemeleri
İşleç aşırı yükleri, çerçeve türlerinin yerleşik dil ilkelleri gibi görünmesine izin verir.

 İzin verilen ve bazı durumlarda yararlı olsa da, operatör aşırı yükleri dikkatli kullanılmalıdır. Framework tasarımcılarının basit yöntemler olması gereken işlemler için işleçler kullanmaya başlaması gibi, operatör aşırı yüklemenin kötüye kullanıldığı birçok durum vardır. Aşağıdaki yönergeler, operatör aşırı yüklemesinin ne zaman ve nasıl kullanılacağına karar vermenize yardımcı olur.

 ❌İlkel (yerleşik) türler gibi hissetmesi gereken türler dışında, işleciaşırı tanımlamaktan kaçının.

 ✔️, operatör aşırı yüklerini ilkel bir tür gibi hissetmesi gereken bir türde tanımlamayı göz önünde bulundurun.

 Örneğin, <xref:System.String?displayProperty=nameWithType> var `operator==` `operator!=` ve tanımlanır.

 ✔️ DO işleci nin sayıları temsil eden (örneğin) <xref:System.Decimal?displayProperty=nameWithType>yapıtlarında aşırı yüklerini tanımlar.

 ❌Operatör aşırı yükleri tanımlarken SEVIMLI OLMAYIN.

 Operatör aşırı yüklemesi, işlemin sonucunun ne olacağı hemen belli olduğu durumlarda yararlıdır. Örneğin, birini <xref:System.DateTime> diğerinden `DateTime` çıkarabilmek ve bir <xref:System.TimeSpan>. Ancak, mantıksal birleşim işlecinin iki veritabanı sorgusunu birleşim için kullanması veya akışa yazmak için kaydırma işlecinin kullanılması uygun değildir.

 ❌Operandlardan en az biri aşırı yükü tanımlayan türden olmadıkça operatöre aşırı yükleme YAPMAYIN.

 ✔️ do operatörleri simetrik bir şekilde aşırı yükleyin.

 Örneğin, aşırı `operator==`yüklerseniz, `operator!=`'yi de aşırı yüklemeniz gerekir. Benzer şekilde, aşırı `operator<`yüklerseniz, ayrıca aşırı `operator>`yüklemeniz gerekir, ve benzeri.

 ✔️ Her aşırı yüklenilebilen operatöre karşılık gelen dost adlarla yöntemler sağlamayı düşünün.

 Birçok dil operatör aşırı yükleme desteklemez. Bu nedenle, aşırı yükleme işleçleri türleri eşdeğer işlevsellik sağlayan uygun bir etki alanına özgü ada sahip ikincil bir yöntem içermelidir önerilir.

 Aşağıdaki tablo, işleçlerin ve karşılık gelen dostu yöntem adlarının bir listesini içerir.

|C# Operatör Sembolü|Meta veri adı|Dost Adı|
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

### <a name="overloading-operator-"></a>Aşırı Yükleme Operatörü ==
 Aşırı `operator ==` yükleme oldukça karmaşıktır. İşleticinin anlamtisi gibi <xref:System.Object.Equals%2A?displayProperty=nameWithType>diğer birkaç üye ile uyumlu olması gerekir.

### <a name="conversion-operators"></a>Dönüşüm İşleçleri
 Dönüşüm işleçleri, bir türden diğerine dönüştürmeye izin veren unary işleçlerdir. İşleçler, operand veya dönüş türünde statik üyeler olarak tanımlanmalıdır. İki tür dönüştürme işleci vardır: örtük ve açık.

 ❌Son kullanıcılar tarafından bu tür bir dönüşüm açıkça beklenmiyorsa, bir dönüşüm işleci sağlamayın.

 ❌Dönüşüm işleçlerini bir türün etki alanı nın dışında tanımlamaYIN.

 Örneğin, <xref:System.Int32>, <xref:System.Double>, <xref:System.Decimal> ve tüm sayısal türleri, <xref:System.DateTime> oysa değildir. Bu nedenle, a'yı `Double(long)` bir `DateTime`.'e dönüştürmek için dönüştürme işleci olmamalıdır. Böyle bir durumda bir yapıcı tercih edilir.

 ❌Dönüştürme potansiyel olarak kayıpsa örtülü bir dönüştürme işleci sağlamaYIN.

 Örneğin, `Double` 'den daha geniş bir `Int32` aralığı `Double` var çünkü `Int32`örtülü bir dönüştürme olmamalıdır. Dönüştürme potansiyel olarak kayıp olsa bile açık bir dönüştürme işleci sağlanabilir.

 ❌Örtük dökümlerden istisnalar ATMAYIN.

 Bir dönüştürmenin gerçekleştiğinin farkında olmadıklarından, son kullanıcıların neler olduğunu anlamaları çok zordur.

 ✔️ bir <xref:System.InvalidCastException?displayProperty=nameWithType> döküm operatörüne yapılan bir çağrı kayıplı dönüşümle sonuçlanırsa ve işleç sözleşmesi kayıplı dönüşümlere izin vermiyorsa ATAMAYIN.

 *2005, 2009 Microsoft Corporation © bölümleri. Tüm hakları saklıdır.*

 *Pearson Education, Inc.'in izniyle [Framework Design Guidelines: Conventions, Idioms and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina ve Brad Abrams tarafından 22 Ekim 2008'de Addison-Wesley Professional tarafından Microsoft Windows Geliştirme Serisi'nin bir parçası olarak yayımlandı.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)

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
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743692"
---
# <a name="operator-overloads"></a>İşleç Aşırı Yüklemeleri
İşleç aşırı yüklemeleri, çerçeve türlerinin yerleşik dil temelleri gibi görünmesine izin verir.

 Bazı durumlarda izin verilen ve yararlı olsa da, işleç aşırı yüklemeleri dikkatle kullanılmalıdır. Çerçeve tasarımcılarının basit yöntemler olması gereken işlemler için İşleçleri kullanmaya başladığı durumlar gibi, operatör aşırı yüklemesinde çok sayıda durum vardır. Aşağıdaki kılavuzlar, işleç aşırı yüklemesini ne zaman ve nasıl kullanacağınızı belirlemenize yardımcı olmalıdır.

 ❌, ilkel (yerleşik) türler gibi olması gereken türler dışında işleç aşırı yüklemeleri tanımlamaktan KAÇıNıN.

 ✔️, bir temel tür gibi olması gereken bir türde operatör aşırı yüklerini tanımlamayı düşünün.

 Örneğin, <xref:System.String?displayProperty=nameWithType> `operator==` ve `operator!=` tanımlı.

 ✔️, sayıları temsil eden yapılarda işleç aşırı yüklerini tanımlama (<xref:System.Decimal?displayProperty=nameWithType>gibi).

 operatör aşırı yüklerini tanımlarken ❌ şirin yok.

 İşleç aşırı yüklemesi, işlemin sonucunun anında daha açık olduğu durumlarda faydalıdır. Örneğin, bir <xref:System.DateTime> başka bir `DateTime` çıkarmak ve bir <xref:System.TimeSpan>alabilmesi mantıklı olur. Ancak, iki veritabanı sorgusu UNION veya bir akışa yazmak için SHIFT işlecini kullanmak üzere mantıksal UNION işlecini kullanmak uygun değildir.

 ❌ işleçlerden en az biri aşırı yüklemeyi tanımlayan türde olmadığı için işleç aşırı yüklemeleri sağlamaz.

 aşırı yükleme işleçlerini bir simetrik biçimde ✔️.

 Örneğin, `operator==`aşırı yüklüyorsanız `operator!=`da aşırı yükleme yapmalısınız. Benzer şekilde, `operator<`aşırı yüklüyorsanız `operator>`da aşırı yüklemesi yapmanız gerekir.

 ✔️, her bir aşırı yüklenmiş işlece karşılık gelen kolay adlara sahip Yöntemler sağlamayı düşünün.

 Birçok dil, işleç aşırı yüklemesini desteklemez. Bu nedenle, aşırı yükleme işleçleri 'nin eşdeğer işlevselliği sağlayan uygun bir etki alanına özgü ada sahip ikincil bir yöntem içermesi önerilir.

 Aşağıdaki tabloda, işleçler ve ilgili kolay yöntem adları listelenmiştir.

|C#İşleç simgesi|Meta veri adı|Kolay Ad|
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

### <a name="overloading-operator-"></a>Aşırı yükleme Işleci = =
 Aşırı yükleme `operator ==` oldukça karmaşıktır. İşlecinin semantiğinin <xref:System.Object.Equals%2A?displayProperty=nameWithType>gibi çeşitli diğer üyelerle uyumlu olması gerekir.

### <a name="conversion-operators"></a>Dönüşüm İşleçleri
 Dönüştürme işleçleri, bir türden diğerine dönüştürmeye izin veren birli işleçlerdir. İşleçler, işlenen ya da dönüş türü üzerinde statik üye olarak tanımlanmalıdır. İki tür dönüştürme işleci vardır: örtük ve açık.

 Bu dönüştürme son kullanıcılar tarafından açıkça beklenmiyorsa, ❌ dönüştürme işleci sağlamaz.

 ❌ bir türün etki alanı dışında dönüştürme işleçleri tanımlamaz.

 Örneğin, <xref:System.Int32>, <xref:System.Double>ve <xref:System.Decimal> tüm sayısal türlerdir, ancak <xref:System.DateTime> değildir. Bu nedenle, bir `Double(long)` `DateTime`dönüştürmek için bir dönüştürme işleci olmaması gerekir. Böyle bir durumda bir Oluşturucu tercih edilir.

 dönüştürme potansiyel olarak kayıplı ise, ❌ örtük bir dönüştürme işleci sağlamaz.

 Örneğin, `Double` `Int32`daha geniş bir aralığa sahip olduğundan, `Double` `Int32` ' dan örtük bir dönüşüm olmaması gerekir. Dönüştürme potansiyel olarak kayıplı olsa bile açık bir dönüştürme işleci sağlayabilirsiniz.

 ❌ örtük olarak özel durumlar oluşturmaz.

 Son kullanıcıların ne olduğunu anlaması çok zordur, çünkü bir dönüştürmenin gerçekleştiğinden haberdar olmayabilir.

 bir cast işlecine yapılan çağrı kayıplı dönüştürmeye neden olursa ve işlecin sözleşmesi kayıplı Dönüştürmelere izin vermediğinden ✔️ <xref:System.InvalidCastException?displayProperty=nameWithType> throw.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)

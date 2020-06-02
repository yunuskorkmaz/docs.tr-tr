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
ms.openlocfilehash: 893b7d1f76dfb059a0ddca77dfd8654812e9ae12
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289739"
---
# <a name="operator-overloads"></a>İşleç Aşırı Yüklemeleri
İşleç aşırı yüklemeleri, çerçeve türlerinin yerleşik dil temelleri gibi görünmesine izin verir.

 Bazı durumlarda izin verilen ve yararlı olsa da, işleç aşırı yüklemeleri dikkatle kullanılmalıdır. Çerçeve tasarımcılarının basit yöntemler olması gereken işlemler için İşleçleri kullanmaya başladığı durumlar gibi, operatör aşırı yüklemesinde çok sayıda durum vardır. Aşağıdaki kılavuzlar, işleç aşırı yüklemesini ne zaman ve nasıl kullanacağınızı belirlemenize yardımcı olmalıdır.

 ❌İlkel (yerleşik) türler gibi olması gereken türler dışında işleç aşırı yüklemeleri tanımlamaktan KAÇıNıN.

 ✔️, bir temel tür gibi olması gereken bir türde operatör aşırı yüklerini tanımlamayı düşünün.

 Örneğin, <xref:System.String?displayProperty=nameWithType> `operator==` ve `operator!=` tanımlı.

 ✔️, sayıları temsil eden yapılarda işleç aşırı yüklerini tanımlama (örneğin <xref:System.Decimal?displayProperty=nameWithType> ).

 ❌Operatör aşırı yüklerini tanımlarken şirin olun.

 İşleç aşırı yüklemesi, işlemin sonucunun anında daha açık olduğu durumlarda faydalıdır. Örneğin, bir diğerinden çıkartabilir <xref:System.DateTime> `DateTime` ve bir alabilir <xref:System.TimeSpan> . Ancak, iki veritabanı sorgusu UNION veya bir akışa yazmak için SHIFT işlecini kullanmak üzere mantıksal UNION işlecini kullanmak uygun değildir.

 ❌İşlenenlerin en az biri aşırı yüklemeyi tanımlayan türde değilse, işleç aşırı yüklemeleri sağlamadığınız.

 aşırı yükleme işleçlerini bir simetrik biçimde ✔️.

 Örneğin, öğesini tekrar yüklüyorsanız, `operator==` öğesini de aşırı yükleyebilirsiniz `operator!=` . Benzer şekilde, öğesini aşırı yüklüyorsanız, `operator<` ve de ' i de aşırı yükleyebilirsiniz `operator>` .

 ✔️, her bir aşırı yüklenmiş işlece karşılık gelen kolay adlara sahip Yöntemler sağlamayı düşünün.

 Birçok dil, işleç aşırı yüklemesini desteklemez. Bu nedenle, aşırı yükleme işleçleri 'nin eşdeğer işlevselliği sağlayan uygun bir etki alanına özgü ada sahip ikincil bir yöntem içermesi önerilir.

 Aşağıdaki tabloda, işleçler ve ilgili kolay yöntem adları listelenmiştir.

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

### <a name="overloading-operator-"></a>Aşırı yükleme Işleci = =
 Aşırı yükleme `operator ==` oldukça karmaşıktır. İşlecinin semantiğinin, gibi diğer birçok üye ile uyumlu olması gerekir <xref:System.Object.Equals%2A?displayProperty=nameWithType> .

### <a name="conversion-operators"></a>Dönüşüm İşleçleri
 Dönüştürme işleçleri, bir türden diğerine dönüştürmeye izin veren birli işleçlerdir. İşleçler, işlenen ya da dönüş türü üzerinde statik üye olarak tanımlanmalıdır. İki tür dönüştürme işleci vardır: örtük ve açık.

 ❌Bu dönüştürme, son kullanıcılar tarafından açıkça beklenmiyorsa, bir dönüştürme işleci sağlamayan.

 ❌Dönüştürme işleçlerini bir türün etki alanı dışında tanımlamayın.

 Örneğin,, <xref:System.Int32> <xref:System.Double> ve <xref:System.Decimal> tüm sayısal türlerdir, ancak bu <xref:System.DateTime> değildir. Bu nedenle, bir öğesine dönüştürmek için bir dönüştürme işleci olmamalıdır `Double(long)` `DateTime` . Böyle bir durumda bir Oluşturucu tercih edilir.

 ❌Dönüştürme potansiyel olarak kayıplı ise örtük bir dönüştürme işleci sağlamaın.

 Örneğin, öğesinden öğesine örtük bir dönüşüm olmaması gerekir, `Double` çünkü öğesinden `Int32` `Double` daha geniş bir Aralık vardır `Int32` . Dönüştürme potansiyel olarak kayıplı olsa bile açık bir dönüştürme işleci sağlayabilirsiniz.

 ❌Örtülü kaynaklardan özel durumlar atamayın.

 Son kullanıcıların ne olduğunu anlaması çok zordur, çünkü bir dönüştürmenin gerçekleştiğinden haberdar olmayabilir.

 <xref:System.InvalidCastException?displayProperty=nameWithType>bir cast işlecine yapılan bir çağrı kayıplı dönüştürmeye neden olursa ve işlecin sözleşmesi kayıplı Dönüştürmelere izin vermezse throw ✔️.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye tasarımı yönergeleri](member.md)
- [Çerçeve tasarım yönergeleri](index.md)

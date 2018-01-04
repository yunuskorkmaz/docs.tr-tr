---
title: "İşleç aşırı yüklemeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1d17aa00ce551d951b0e178304632572abf592b6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="operator-overloads"></a>İşleç aşırı yüklemeleri
İşleç aşırı yüklemeleri yerleşik dil temelleri oldukları gibi görünmesi framework türü izin verir.  
  
 İzin verilen ve bazı durumlarda yararlı olsa da, işlecin dikkatli kullanılmalıdır. Hangi İşleç aşırı yüklemesi, framework tasarımcıları işleçleri basit yöntemleri olmalıdır işlemleri için kullanılacak başladığında gibi kötüye birçok durumlar vardır. Aşağıdaki yönergeler ne zaman ve nasıl İşleç aşırı yüklemesi kullanma karar vermenize yardımcı olmalıdır.  
  
 **KAÇININ x** gibi (yerleşik) ilkel türlerinde geliyor olmalıdır türlerinde dışında işleci aşırı tanımlama.  
  
 **✓ DÜŞÜNÜN** gibi basit tür geliyor olmalıdır bir türdeki işlecin tanımlama.  
  
 Örneğin, <xref:System.String?displayProperty=nameWithType> sahip `operator==` ve `operator!=` tanımlanmış.  
  
 **✓ YAPMAK** numaralarını temsil eden yapılar için işleç aşırı yüklemeleri tanımlayın (gibi <xref:System.Decimal?displayProperty=nameWithType>).  
  
 **X yok** işlecin tanımlarken şirin olabilir.  
  
 İşleç aşırı yüklemesi işlemin sonucunu ne olacağını hemen göze olduğu durumlarda faydalıdır. Örneğin, bir çıkarma yapabilmek için mantıklıdır <xref:System.DateTime> başka bir `DateTime` ve bir <xref:System.TimeSpan>. Ancak, mantıksal birleşim işlecini bileşim iki veritabanı sorgularını kullanın ya da bir akışa yazmak üzere kaydırma işleci kullanmak için uygun değil.  
  
 **X yok** işleci aşırı yüklemeler işlenen en az biri aşırı tanımlama türü olmadıkça sağlayın.  
  
 **✓ YAPMAK** bir simetrik şekilde işleçleri aşırı yükleme.  
  
 Örneğin, aşırı yükleme `operator==`, ayrıca aşırı `operator!=`. Benzer şekilde, aşırı yükleme varsa `operator<`, ayrıca aşırı `operator>`ve benzeri.  
  
 **✓ DÜŞÜNÜN** yöntemleri karşılık gelen kolay adlarla her aşırı yüklenmiş işleç sağlama.  
  
 İşleç aşırı yüklemesi birçok dil desteklemez. Bu nedenle, işleçleri aşırı yükleme türleri ikincil bir yöntem uygun bir etki alanına özgü adıyla eşdeğer işlevsellik sağlayan olmaması önerilir.  
  
 Aşağıdaki tabloda işleçler ve karşılık gelen kolay yöntem adlarının bir listesini içerir.  
  
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
 Aşırı yükleme `operator ==` oldukça karmaşıktır. İşleci semantiği gibi birkaç diğer üyeleriyle uyumlu olması gereken <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
### <a name="conversion-operators"></a>Dönüşüm İşleçleri  
 Dönüştürme işleçleri bir türden diğerine dönüştürme izin birli işleçler şunlardır. İşleçler statik üyeler işlenen ya da dönüş türü olarak tanımlanmış olması gerekir. Dönüştürme işleçleri iki tür vardır: örtük ve açık.  
  
 **X yok** tür dönüştürme son kullanıcılar tarafından açıkça görülmüyorsa bir dönüşüm işleci sağlayın.  
  
 **X yok** dönüşüm işleçleri dışında bir tür etki alanını tanımlayın.  
  
 Örneğin, <xref:System.Int32>, <xref:System.Double>, ve <xref:System.Decimal> tüm sayısal ancak türleridir <xref:System.DateTime> değil. Bu nedenle, olmamalıdır dönüştürmek için hiçbir dönüştürme işleci bir `Double(long)` için bir `DateTime`. Bir oluşturucu, böyle bir durumda tercih edilir.  
  
 **X yok** dönüştürme olası kayıplı ise bir örtük dönüşüm işleci sağlayın.  
  
 Örneğin, olmamalıdır örtük bir dönüştürme `Double` için `Int32` çünkü `Double` daha geniş bir sahip `Int32`. Dönüştürme olası kayıplı olsa bile bir açık dönüşüm işleci sağlanabilir.  
  
 **X yok** örtük atamaları özel durumlar atar.  
  
 Neler olduğunu, bunların dönüştürme yer aldığı kullanan olmayabileceğinden anlamak son kullanıcılar için çok zor olabilir.  
  
 **✓ YAPMAK** throw <xref:System.InvalidCastException?displayProperty=nameWithType> atama işleci için bir çağrı sonuçları kayıplı dönüştürmede ve sözleşmenin işlecinin kayıplı dönüşümleri izin vermez.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)

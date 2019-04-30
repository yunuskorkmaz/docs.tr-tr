---
title: Temel türler - C# Kılavuzu
description: Tüm C# programlarında temel türleri (sayısal türler, dizeler ve nesne) hakkında bilgi edinin
ms.date: 10/10/2016
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: dc91452bb261b7c799cf3b69cab5b33175148b8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646754"
---
# <a name="types-variables-and-values"></a>Türler, değişkenler ve değerleri

C# bir türü kesin belirlenmiş dildir. Bir değere Değerlenen her ifadenin gibi her değişken ve sabit bir türü vardır. Her yöntem imzası bir tür için her giriş parametresi ve dönüş değeri belirtir. .NET Framework sınıf kitaplığı bir yerleşik sayısal türler ve bunun yanı sıra çok çeşitli dosya sistemi, ağ bağlantıları, koleksiyonlar ve diziler nesneleri ve tarihler gibi mantıksal yapıları temsil eden daha karmaşık türleri kümesi tanımlar. Tipik bir C# programı sınıf kitaplığından alınan türleri aynı zamanda programın sorun etki alanına özgü kavramları modelleyen kullanıcı tanımlı türler kullanır.  
  
Bir tür içinde depolanan bilgiler aşağıdakileri içerebilir:  
  
- Bir tür değişkeninin gerektirdiği depolama alanı.  
  
- Temsil edebileceği maksimum ve minimum değerler.  
  
- İçerdiği üyeler (yöntemler, alanlar, olaylar vb.).  
  
- Devraldığı taban türü.  
  
- Değişkenler için belleğin çalışma zamanında burada ayrılacak konumu.  
  
- İzin verilen işlem türleri.  
  
Derleyici, kodunuzda gerçekleştirilen tüm işlemler olduğundan emin olmak için tür bilgilerini kullanır. *denkliği*. Örneğin, türünde bir değişken bildirirseniz [int](language-reference/keywords/int.md), derleyici değişkeni buna ek olarak kullanmanızı ve çıkarma işlemleri sağlar. Türünde bir değişkende aynı işlemleri gerçekleştirmeyi denerseniz [bool](language-reference/keywords/bool.md), aşağıdaki örnekte gösterildiği gibi derleyici bir hata oluşturur:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> C ve C++ geliştiricileri seçeneğinde bu C# ' ta [bool](language-reference/keywords/bool.md) öğesine dönüştürülebilir değildir [int](language-reference/keywords/int.md).  
  
Derleyicinin tür bilgisini yürütülebilir dosya meta veri olarak gömer. Ortak dil çalışma zamanı (CLR) ayırır ve belleği geri kazanır, daha fazla tür güvenliği sağlamak için çalışma zamanında bu meta verileri kullanır.  

## <a name="specifying-types-in-variable-declarations"></a>Değişken bildirimlerinde türleri belirtme

Ne zaman bir değişken bildirdiğinizde veya sabit bir program, türünü belirtmeniz veya kullanın [var](language-reference/keywords/var.md) anahtar sözcüğünü kullanarak derleyicinin türü sağlar. Aşağıdaki örnek, hem yerleşik sayısal türler hem de kullanıcı tanımlı karmaşık türler kullanan bazı değişken bildirimlerini gösterir:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Yöntem parametreleri ve dönüş değerlerinin türleri Yöntem imzasında belirtilir. Aşağıdaki imza gerektiren bir yöntemi gösterir bir [int](language-reference/keywords/int.md) giriş bağımsız değişkeni olarak bir dize döndürür:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Bir değişken bildirildikten sonra yeni bir türle yeniden bildirilemez ve bildirilen türle uyumlu olmayan bir değer atanamaz. Örneğin, bildiremezsiniz bir [int](language-reference/keywords/int.md) Boolean değerini atayın [true](language-reference/keywords/true.md). Ancak, değerler örneğin yeni değişkenlere eklendiklerinde veya yöntem bağımsız değişkenleri olarak geçtiklerinde diğer türlere dönüştürülebilir. A *tür dönüştürme* , yoksa veri kaybına neden olmayan derleyici tarafından otomatik olarak gerçekleştirilir. Veri kaybına neden olabilecek bir dönüştürme gerektiren bir *atama* kaynak kodunda.

Daha fazla bilgi için [atama ve tür dönüştürmeleri](programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Yerleşik türler

C# Standart tamsayılar, kayan nokta değerleri, Boolean ifadeler, metin karakterleri, ondalık değerleri temsil etmek için yerleşik sayısal türler ve diğer veri türleri kümesi sağlar. Ayrıca vardır yerleşik **dize** ve **nesne** türleri. Bunlar, bir C# programında kullanabilmeniz için kullanılabilir. Yerleşik türler hakkında daha fazla bilgi için bkz. [türler için başvuru tablosu](language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Özel türler

Kullandığınız [yapı](language-reference/keywords/class.md), [sınıfı](language-reference/keywords/class.md), [arabirimi](language-reference/keywords/interface.md), ve [enum](language-reference/keywords/enum.md) yapılar, kendi özel türlerinizi oluşturmak için. .NET Framework sınıf kitaplığının kendisi, uygulamalarınızda kullanabileceğiniz Microsoft tarafından sağlanan özel türler koleksiyonudur. Varsayılan olarak, Sınıf Kitaplığı'nda en sık kullanılan türleri bir C# programı içinde kullanılabilir. Diğerleri yalnızca açıkça tanımlanmış derlemenin bir proje başvurusu eklediğinizde kullanılabilir. Derleyici derlemesine bir başvuru olduğunda, değişkenler (ve sabitler) türlerinin derlemeye kaynak kodunda bildirilen bildirebilir.
  
## <a name="generic-types"></a>Genel türler

Bir türü bir veya daha fazla bildirilmiş *tür parametrelerindeki* gerçek tür için bir yer tutucu olarak hizmet veren ( *somut tür*) türün bir örneğini oluşturduğunda, istemci kodunun sağlayacağı. Bu türler olarak adlandırılır *genel türler*. Örneğin, .NET Framework türü <xref:System.Collections.Generic.List%601> gereği adı verilen bir tür parametresine sahip *T*. Bir türün örneğini oluşturduğunuzda dize listesi yer alacak nesnelerin türünü belirtin:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
Tür parametresinin kullanımı, her öğesine dönüştürmek zorunda kalmadan herhangi bir türde öğe için aynı sınıf yeniden mümkün kılar [nesne](language-reference/keywords/object.md). Genel koleksiyon sınıflarına çağrılır *kesin olarak belirtilmiş koleksiyonlar* derleyici koleksiyonun öğelerinin belirli tür bilir ve derleme sırasında bir hata gönderebilirsiniz olduğundan, örneğin, bir tamsayı içineklemeyideneyin`strings` önceki örnekte nesne. Daha fazla bilgi için [genel türler](programming-guide/generics/index.md).

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Örtülü türler, anonim türler ve tanımlama grubu türleri

Daha önce belirtildiği gibi örtük olarak yerel bir değişken (ancak sınıf üyeleri olmamak) kullanarak yazabilirsiniz [var](language-reference/keywords/var.md) anahtar sözcüğü. Değişken derleme zamanında hala bir türü alır, ancak türü derleyici tarafından sağlanır. Daha fazla bilgi için [örtülü olarak yazılan yerel değişkenler](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
Bazı durumlarda, bu depolamak veya yöntemi sınırları dışında geçirmek istemediğiniz ilgili değer kümeleri için adlandırılmış bir tür oluşturmak çok kullanışsız olur. Oluşturabileceğiniz *anonim türler* bu amaç için. Daha fazla bilgi için [anonim türler](programming-guide/classes-and-structs/anonymous-types.md).

Bir yöntemin birden fazla değer döndürmek için yaygın bir uygulamadır. Oluşturabileceğiniz *tanımlama grubu türleri* tek yöntem çağrısında birden çok değer döndürür. Daha fazla bilgi için [diziler](tuples.md)

## <a name="the-common-type-system"></a>Ortak tür sistemi

.NET Framework içindeki tür sisteminde iki temel noktanın anlaşılması önemlidir:  
  
- Bu devralma ilkesini destekler. Türleri olarak adlandırılan diğer türlerden türetilebilir *taban türler*. Türetilmiş bir tür, yöntemleri, özellikleri ve diğer temel türün üyelerini (bazı sınırlamalarla birlikte) devralır. Temel tür sırayla durumda türetilmiş tür devralma hiyerarşisinde her iki taban türün üyelerini devralan başka bir türden türeyebilir. Gibi yerleşik sayısal türler dahil olmak üzere tüm türleri <xref:System.Int32> (C# anahtar sözcüğünü: `int`), türetilen sonuçta tek temel türünden olduğu <xref:System.Object> (C# anahtar sözcüğünü: `object`). Bu birleşik tür hiyerarşisine adlı [ortak tür sistemi](../standard/common-type-system.md) (CTS). C# içinde devralma hakkında daha fazla bilgi için bkz: [devralma](programming-guide/classes-and-structs/inheritance.md).  
  
- Cts'deki her tür olarak tanımlanan bir *değer türü* veya *başvuru türüne*. Bu, .NET Framework sınıf kitaplığı ve ayrıca kendi kullanıcı tanımlı türler tüm özel türleri içerir. Kullanarak tanımladığınız türler [yapı](language-reference/keywords/struct.md) anahtar değer türleri; tüm yerleşik sayısal türler **yapılar**. Değer türleri hakkında daha fazla bilgi için bkz: [yapılar](structs.md). Kullanarak tanımladığınız türler [sınıfı](language-reference/keywords/class.md) anahtar sözcüğü olan başvuru türleri. Başvuru türleri hakkında daha fazla bilgi için bkz: [sınıfları](classes.md). Başvuru türleri ve değer türleri farklı derleme zamanı kuralları ve farklı çalışma zamanı davranışı sahiptir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar](structs.md)
- [Sınıflar](classes.md)

---
title: Temel türler-C# Kılavuzu
description: Tüm C# programlarında çekirdek türleri (Numerics, dizeler ve nesne) hakkında bilgi edinin
ms.date: 10/10/2016
ms.technology: csharp-fundamentals
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 18a73e62bf45cdc4a4eaa0985c3fe036ac3b55a8
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465266"
---
# <a name="types-variables-and-values"></a>Türler, değişkenler ve değerler

C# türü kesin belirlenmiş bir dildir. Her değişken ve sabitin, bir değeri değerlendiren her ifadeyi olduğu gibi bir türü vardır. Her yöntem imzası her giriş parametresi ve dönüş değeri için bir tür belirtir. .NET sınıf kitaplığı, dosya sistemi, ağ bağlantıları, koleksiyon ve nesne dizileri ve tarihler gibi çok çeşitli mantıksal yapıları temsil eden daha karmaşık türler ve yerleşik sayısal türlerin bir kümesini tanımlar. Tipik bir C# programı, sınıf kitaplığından türleri ve programın sorunlu etki alanına özgü kavramları modeleden Kullanıcı tanımlı türleri kullanır.  
  
Bir tür içinde depolanan bilgiler şunları içerebilir:  
  
- Türün bir değişkeninin gerektirdiği depolama alanı.  
  
- Temsil ettiği maksimum ve en düşük değerler.  
  
- İçerdiği Üyeler (Yöntemler, alanlar, olaylar vb.).  
  
- Devraldığı temel tür.  
  
- Değişkenlere yönelik belleğin çalışma zamanında ayrılabileceği konum.  
  
- İzin verilen işlem türleri.  
  
Derleyici, kodunuzda gerçekleştirilen tüm işlemlerin *tür açısından güvenli*olduğundan emin olmak için tür bilgilerini kullanır. Örneğin, [int](language-reference/builtin-types/integral-numeric-types.md)türünde bir değişken bildirirseniz, derleyici değişkeni toplama ve çıkarma işlemlerinde kullanmanıza izin verir. [Bool](language-reference/builtin-types/bool.md)türünde bir değişkende aynı işlemleri gerçekleştirmeye çalışırsanız, derleyici aşağıdaki örnekte gösterildiği gibi bir hata oluşturur:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> C ve C++ geliştiricileri, C# ' ta [bool](language-reference/builtin-types/bool.md) ' ın [int](language-reference/builtin-types/integral-numeric-types.md)'e dönüştürülebilir olmadığına dikkat edin.  
  
Derleyici, tür bilgilerini yürütülebilir dosyaya meta veriler olarak katıştırır. Ortak dil çalışma zamanı (CLR), bellek ayırdığı ve geri kazanır daha fazla güvence altına almak için çalışma zamanında bu meta verileri kullanır.  

## <a name="specifying-types-in-variable-declarations"></a>Değişken bildirimlerinde türleri belirtme

Bir programda bir değişken veya sabit belirttiğinizde, onun türünü belirtmeniz veya [var](language-reference/keywords/var.md) anahtar sözcüğünü kullanarak derleyicinin türü saymasına izin vermelisiniz. Aşağıdaki örnek, hem yerleşik sayısal türler hem de Kullanıcı tanımlı karmaşık türler kullanan bazı değişken bildirimlerini gösterir:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Yöntem parametrelerinin türleri ve dönüş değerleri Yöntem imzasında belirtilmiştir. Aşağıdaki imza, giriş bağımsız değişkeni olarak bir [int](language-reference/builtin-types/integral-numeric-types.md) gerektiren ve bir dize döndüren bir yöntemi gösterir:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Bir değişken oluşturulduktan sonra, yeni bir türle yeniden bildirilemez ve belirtilen türle uyumlu olmayan bir değer atanamaz. Örneğin, bir [int](language-reference/builtin-types/integral-numeric-types.md) bildiremez ve bunu Boolean değeri atayabilirsiniz `true` . Ancak, değerler başka türlere dönüştürülebilir (örneğin, yeni değişkenlere atandığında veya yöntem bağımsız değişkenleri olarak geçirildiğinde). Veri kaybına neden olmayan bir *tür dönüştürmesi* , derleyici tarafından otomatik olarak gerçekleştirilir. Veri kaybına neden olabilecek bir dönüştürme, kaynak kodda bir *tür dönüştürme* gerektirir.

Daha fazla bilgi için bkz. [atama ve tür dönüştürmeleri](programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Yerleşik türler

C#, tamsayıları, kayan nokta değerlerini, Boole ifadelerini, metin karakterlerini, ondalık değerleri ve diğer veri türlerini temsil etmek için standart bir yerleşik sayısal türler kümesi sağlar. Ayrıca yerleşik **dize** ve **nesne** türleri de vardır. Bunlar, herhangi bir C# programında kullanabileceğiniz şekilde kullanılabilir. Yerleşik türlerin tam listesi için bkz. [Yerleşik türler](language-reference/builtin-types/built-in-types.md).
  
## <a name="custom-types"></a>Özel türler

Kendi özel türlerinizi oluşturmak için [struct](language-reference/builtin-types/struct.md), [Class](language-reference/keywords/class.md), [Interface](language-reference/keywords/interface.md)ve [enum](language-reference/builtin-types/enum.md) yapılarını kullanırsınız. .NET sınıf kitaplığı, Microsoft tarafından kendi uygulamalarınızda kullanabileceğiniz özel türlerin bir koleksiyonudur. Varsayılan olarak, sınıf kitaplığındaki en sık kullanılan türler, herhangi bir C# programında kullanılabilir. Diğerleri yalnızca tanımlandıkları derlemeye açıkça bir proje başvurusu eklediğinizde kullanılabilir hale gelir. Derleyicinin derlemeye bir başvurusu olduktan sonra, kaynak kodda o derlemede belirtilen türlerin değişkenlerini (ve sabitleri) bildirebilirsiniz.
  
## <a name="generic-types"></a>Genel türler

Bir tür, istemci kodunun türün bir örneğini oluşturduğunda sağladığı gerçek tür ( *somut tür*) için yer tutucu olarak görev yapan bir veya daha fazla *tür parametresiyle* bildirilemez. Bu tür türler *Genel türler*olarak adlandırılır. Örneğin, <xref:System.Collections.Generic.List%601> kuralına göre bir tür parametresine sahip *T*adı verilir. Türün bir örneğini oluşturduğunuzda, listenin içereceği nesnelerin türünü (örneğin, dize) belirtirsiniz:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
Tür parametresinin kullanımı, her öğeyi [nesneye](language-reference/builtin-types/reference-types.md#the-object-type)dönüştürmek zorunda kalmadan her türlü öğe türünü tutmak için aynı sınıfı yeniden kullanmayı mümkün kılar. Derleyici, koleksiyon öğelerinin belirli türünü bildiğinden ve derleme zamanında bir hata, örneğin, önceki örnekteki nesnesine bir tamsayı eklemeye çalışırsanız, genel koleksiyon sınıfları *kesin türü belirtilmiş koleksiyonlar* olarak adlandırılır `strings` . Daha fazla bilgi için bkz. [Genel türler](programming-guide/generics/index.md).

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Örtülü türler, anonim türler ve demet türleri

Daha önce belirtildiği gibi, [var](language-reference/keywords/var.md) anahtar sözcüğünü kullanarak yerel bir değişkeni (sınıf üyelerini değil) örtük olarak yazabilirsiniz. Değişken hala derleme zamanında bir tür alır, ancak tür derleyici tarafından sağlanır. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
Bazı durumlarda, yöntem sınırlarını depolamayı veya geçişi istemediğiniz ilgili değerlerin basit kümeleri için adlandırılmış bir tür oluşturmak uygun değildir. Bu amaçla *anonim türler* oluşturabilirsiniz. Daha fazla bilgi için bkz. [anonim türler](programming-guide/classes-and-structs/anonymous-types.md).

Bir yöntemden birden fazla değer döndürmek, yaygın bir yöntemdir. Tek bir yöntem çağrısında birden çok değer döndüren *demet türleri* oluşturabilirsiniz. Daha fazla bilgi için bkz. [demet türleri](language-reference/builtin-types/value-tuples.md).

## <a name="the-common-type-system"></a>Ortak tür sistemi

.NET 'teki tür sistemi hakkında iki temel noktayı anlamak önemlidir:  
  
- Devralma ilkesini destekler. Türler, *temel türler*olarak adlandırılan diğer türlerden türetilebilir. Türetilmiş tür, yöntemleri, özellikleri ve temel türün diğer üyelerini devralır (bazı kısıtlamalarla). Temel tür başka bir türden türetebilir, bu durumda türetilmiş tür, devralma hiyerarşisindeki her iki temel türün üyelerini devralır. (C# anahtar sözcüğü:) gibi yerleşik sayısal türler de dahil olmak üzere tüm türler, <xref:System.Int32> `int` sonunda <xref:System.Object> (c# anahtar sözcüğü:) tek bir temel türden türetilir `object` . Bu Birleşik tür hiyerarşisine [ortak tür sistemi](../standard/common-type-system.md) (Cts) denir. C# ' de devralma hakkında daha fazla bilgi için bkz. [Devralma](programming-guide/classes-and-structs/inheritance.md).  
  
- CTS içindeki her tür, bir *değer türü* veya bir *başvuru türü*olarak tanımlanır. Bu, .NET sınıf kitaplığı 'ndaki tüm özel türleri ve ayrıca kendi Kullanıcı tanımlı türlerinizi içerir. `struct`Veya anahtar sözcüğünü kullanarak tanımladığınız türler `enum` değer türlerdir. Değer türleri hakkında daha fazla bilgi için bkz. [değer türleri](language-reference/builtin-types/value-types.md). [Sınıf](language-reference/keywords/class.md) anahtar sözcüğünü kullanarak tanımladığınız türler başvuru türleridir. Başvuru türleri hakkında daha fazla bilgi için bkz. [sınıflar](programming-guide/classes-and-structs/classes.md). Başvuru türleri ve değer türlerinde farklı derleme zamanı kuralları ve farklı çalışma zamanı davranışları vardır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yapı türleri](language-reference/builtin-types/struct.md)
- [Numaralandırma türleri](language-reference/builtin-types/enum.md)
- [Sınıftır](programming-guide/classes-and-structs/classes.md)

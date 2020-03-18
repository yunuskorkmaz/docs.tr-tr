---
title: Temel Türler - C# Rehberi
description: Tüm C# programlarındaki çekirdek türleri (sayısallar, dizeleri ve nesne) hakkında bilgi edinin
ms.date: 10/10/2016
ms.technology: csharp-fundamentals
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: bb2177026afb2eef2e14ece0c306bfd3ffe7af39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673270"
---
# <a name="types-variables-and-values"></a>Türleri, değişkenleri ve değerleri

C# güçlü bir şekilde yazılan bir dildir. Her değişken ve sabit, bir değere değer biçen her ifade gibi bir türü vardır. Her yöntem imzası, her giriş parametresi ve iade değeri için bir tür belirtir. .NET Framework sınıf kitaplığı, dosya sistemi, ağ bağlantıları, koleksiyonlar ve nesne dizileri ve tarihler gibi çok çeşitli mantıksal yapıları temsil eden yerleşik sayısal türlerin yanı sıra daha karmaşık türleri tanımlar. Tipik bir C# programı, sınıf kitaplığından gelen türlerin yanı sıra programın sorunlu etki alanına özgü kavramları modelleyen kullanıcı tanımlı türleri kullanır.  
  
Bir türde depolanan bilgiler aşağıdakileri içerebilir:  
  
- Türünün bir değişkeninin gerektirdiği depolama alanı.  
  
- Temsil edebileceği maksimum ve minimum değerler.  
  
- İçerdiği üyeler (yöntemler, alanlar, olaylar vb.)  
  
- Devraldığı temel türü.  
  
- Değişkenler için belleğin çalışma zamanında ayrılacağı konum.  
  
- İzin verilen işlem türleri.  
  
Derleyici, kodunuzda gerçekleştirilen tüm işlemlerin *tür güvenli*olduğundan emin olmak için tür bilgilerini kullanır. Örneğin, tür [int](language-reference/builtin-types/integral-numeric-types.md)bir değişken bildirirseniz, derleyici ek ve çıkarma işlemlerinde değişken kullanmanıza olanak sağlar. Aynı işlemleri tür [bool](language-reference/builtin-types/bool.md)değişkeninde gerçekleştirmeye çalışırsanız, derleyici aşağıdaki örnekte gösterildiği gibi bir hata oluşturur:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> C ve C++ geliştiricileri, C#'da [bool'un](language-reference/builtin-types/bool.md) [int'e](language-reference/builtin-types/integral-numeric-types.md)dönüştürülemez olduğuna dikkat edin.  
  
Derleyici, tür bilgilerini yürütülebilir dosyaya meta veri olarak yerzetir. Ortak dil çalışma süresi (CLR), bellek tahsis ettiğinde ve geri aldığında tür güvenliğini daha da garanti etmek için bu meta verileri çalışma zamanında kullanır.  

## <a name="specifying-types-in-variable-declarations"></a>Değişken bildirimlerde türleri belirtme

Bir programda bir değişken veya sabit beyan ettiğinizde, derleyicinin türü çıkarmasına izin vermek için türünü belirtmeniz veya [var](language-reference/keywords/var.md) anahtar sözcükünü kullanmanız gerekir. Aşağıdaki örnek, hem yerleşik sayısal türleri hem de karmaşık kullanıcı tanımlı türleri kullanan bazı değişken bildirimleri gösterir:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Yöntem imzasında yöntem parametreleri ve iade değerleri belirtilir. Aşağıdaki imza, giriş bağımsız değişkeni olarak bir [int](language-reference/builtin-types/integral-numeric-types.md) gerektiren bir yöntemi gösterir ve bir dize döndürür:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Bir değişken beyan edildikten sonra, yeni bir türle yeniden bildirilemez ve beyan edilen türüyle uyumlu olmayan bir değer atanamaz. Örneğin, bir [int](language-reference/builtin-types/integral-numeric-types.md) bildiremez ve sonra bir Boolean `true`değeri atayabilirsiniz. Ancak, değerler, örneğin yeni değişkenlere atandığında veya yöntem bağımsız değişkenleri olarak geçirildiğinde diğer türlere dönüştürülebilir. Veri kaybına neden olmayan bir *tür dönüştürme* derleyici tarafından otomatik olarak gerçekleştirilir. Veri kaybına neden olabilecek bir dönüştürme, kaynak kodunda bir *döküm* gerektirir.

Daha fazla bilgi için [Bkz. Döküm ve tür dönüşümleri.](programming-guide/types/casting-and-type-conversions.md)

## <a name="built-in-types"></a>Yerleşik türler

C#, tamsayılar, kayan nokta değerleri, Boolean ifadeleri, metin karakterleri, ondalık değerler ve diğer veri türlerini temsil edecek standart bir yerleşik sayısal türleri kümesi sağlar. Yerleşik **dize** ve **nesne** türleri de vardır. Bunlar herhangi bir C# programında kullanabileceğiniz bir programdır. Yerleşik türlerin tam listesi için Yerleşik [türleri'ne](language-reference/builtin-types/built-in-types.md)bakın.
  
## <a name="custom-types"></a>Özel türleri

Kendi özel türleri oluşturmak için [yapı,](language-reference/keywords/class.md) [sınıf,](language-reference/keywords/class.md) [arayüz](language-reference/keywords/interface.md)ve [enum](language-reference/builtin-types/enum.md) yapıları kullanın. .NET Framework sınıf kitaplığı, Microsoft tarafından sağlanan ve kendi uygulamalarınızda kullanabileceğiniz özel türler topluluğudur. Varsayılan olarak, sınıf kitaplığında en sık kullanılan türler herhangi bir C# programında kullanılabilir. Diğerleri yalnızca tanımlandıkları derlemeye açıkça bir proje başvurusu eklediğinizde kullanılabilir hale gelir. Derleyici derlemeye bir başvuru yaptıktan sonra, bu derlemede bildirilen türlerin değişkenlerini (ve sabitlerini) kaynak kodunda bildirebilirsiniz.
  
## <a name="generic-types"></a>Genel türler

Bir tür, istemci kodunun türün bir örneğini oluşturduğunda sağlayacağı gerçek tür *(somut tür)* için yer tutucu olarak hizmet veren bir veya daha fazla *tür parametresiyle* bildirilebilir. Bu tür *türler genel türleri*denir. Örneğin, .NET Framework <xref:System.Collections.Generic.List%601> türünde, kuralla *T*adı verilen bir tür parametresi vardır. Türbir örneğini oluşturduğunuzda, listenin içereceği nesnelerin türünü( örneğin, dizeyi) belirtirsiniz:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
Tür parametresinin kullanılması, her öğeyi [nesneye](language-reference/builtin-types/reference-types.md#the-object-type)dönüştürmek zorunda kalmadan, her tür öğeyi tutmak için aynı sınıfı yeniden kullanmayı mümkün kılar. Derleyici koleksiyonun öğelerinin belirli türünü bildiğinden ve örneğin önceki örnekteki `strings` nesneye bir arastım eklemeye çalışırsanız derleme zamanında hata kaldırabileceğinden, genel koleksiyon sınıfları güçlü şekilde yazılan *koleksiyonlar* olarak adlandırılır. Daha fazla bilgi için [Genel Bilgiler'e](programming-guide/generics/index.md)bakın.

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Örtük türler, anonim türleri ve tuple türleri

Daha önce belirtildiği gibi, [var](language-reference/keywords/var.md) anahtar sözcük kullanarak örtülü olarak yerel bir değişken (ancak sınıf üyeleri değil) yazabilirsiniz. Değişken hala derleme zamanında bir tür alır, ancak tür derleyici tarafından sağlanır. Daha fazla bilgi için [bkz.](programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
  
Bazı durumlarda, depolamak veya yöntem sınırları dışında geçmek niyetinde olmadığınız ilgili değerlerin basit kümeleri için adlandırılmış bir tür oluşturmak sakıncalıdır. Bu amaçla *anonim türleri* oluşturabilirsiniz. Daha fazla bilgi için [Bkz. Anonim türleri.](programming-guide/classes-and-structs/anonymous-types.md)

Bir yöntemden birden fazla değer döndürmek istemek yaygındır. Tek bir yöntem çağrısında birden çok değer döndüren *tuple türleri* oluşturabilirsiniz. Daha fazla bilgi için Bkz. [Tuples.](tuples.md)

## <a name="the-common-type-system"></a>Ortak tür sistemi

.NET Çerçevesi'nde tür sistemi ile ilgili iki temel noktayı anlamak önemlidir:  
  
- Miras ilkesini destekler. Türleri, *temel türleri*olarak adlandırılan diğer türlerden türetilebilir. Türetilen tür , yöntemleri, özellikleri ve temel türün diğer üyelerini (bazı kısıtlamalarla) devralır. Taban türü sırayla başka bir türden türetilebilir ve bu durumda türemiş tür, devralma hiyerarşisinde her iki temel türün üyelerini devralır. <xref:System.Int32> (C# anahtar kelimesi: `int`), sonuçta tek bir temel türden türetilmiş <xref:System.Object> (C# anahtar kelimesi: ). `object` Bu birleşik tür hiyerarşisi [Ortak tür sistemi](../standard/common-type-system.md) (CTS) olarak adlandırılır. C#'daki kalıtım hakkında daha fazla bilgi için [bkz.](programming-guide/classes-and-structs/inheritance.md)  
  
- CTS'deki her tür bir *değer türü* veya *başvuru türü*olarak tanımlanır. Bu, .NET sınıf kitaplığındaki tüm özel türleri ve aynı zamanda kendi kullanıcı tanımlı türlerinizi içerir. Veya `enum` anahtar sözcüğü `struct` kullanarak tanımladığınız türler değer türleridir. Değer türleri hakkında daha fazla bilgi için [Bkz. Değer türleri.](language-reference/builtin-types/value-types.md) [Sınıf](language-reference/keywords/class.md) anahtar sözcük kullanarak tanımladığınız türler başvuru türleridir. Başvuru türleri hakkında daha fazla bilgi için [Sınıflar'a](programming-guide/classes-and-structs/classes.md)bakın. Başvuru türleri ve değer türleri farklı derleme zamanı kuralları ve farklı çalışma zamanı davranışı vardır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yapı türleri](language-reference/builtin-types/struct.md)
- [Numaralandırma türleri](language-reference/builtin-types/enum.md)
- [Sınıflar](programming-guide/classes-and-structs/classes.md)

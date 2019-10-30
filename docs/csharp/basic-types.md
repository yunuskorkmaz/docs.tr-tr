---
title: Temel türler- C# kılavuz
description: Tüm C# programlarda çekirdek türleri (Numerics, dizeler ve nesne) hakkında bilgi edinin
ms.date: 10/10/2016
ms.technology: csharp-fundamentals
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: f984321ab01fc4b5ddd92a20b178748de50246da
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037663"
---
# <a name="types-variables-and-values"></a>Türler, değişkenler ve değerler

C#türü kesin belirlenmiş bir dildir. Her değişken ve sabitin, bir değeri değerlendiren her ifadeyi olduğu gibi bir türü vardır. Her yöntem imzası her giriş parametresi ve dönüş değeri için bir tür belirtir. .NET Framework sınıf kitaplığı, dosya sistemi, ağ bağlantıları, koleksiyon ve nesne dizileri ve tarihler gibi çok çeşitli mantıksal yapıları temsil eden daha karmaşık türler ve yerleşik sayısal türlerin bir kümesini tanımlar. Tipik C# bir program, sınıf kitaplığından türleri ve programın sorunlu etki alanına özgü kavramları modelleyebilir Kullanıcı tanımlı türleri kullanır.  
  
Bir tür içinde depolanan bilgiler şunları içerebilir:  
  
- Türün bir değişkeninin gerektirdiği depolama alanı.  
  
- Temsil ettiği maksimum ve en düşük değerler.  
  
- İçerdiği Üyeler (Yöntemler, alanlar, olaylar vb.).  
  
- Devraldığı temel tür.  
  
- Değişkenlere yönelik belleğin çalışma zamanında ayrılabileceği konum.  
  
- İzin verilen işlem türleri.  
  
Derleyici, kodunuzda gerçekleştirilen tüm işlemlerin *tür açısından güvenli*olduğundan emin olmak için tür bilgilerini kullanır. Örneğin, [int](language-reference/builtin-types/integral-numeric-types.md)türünde bir değişken bildirirseniz, derleyici değişkeni toplama ve çıkarma işlemlerinde kullanmanıza izin verir. [Bool](language-reference/keywords/bool.md)türünde bir değişkende aynı işlemleri gerçekleştirmeye çalışırsanız, derleyici aşağıdaki örnekte gösterildiği gibi bir hata oluşturur:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> C ve C++ geliştiricilerle, [bool](language-reference/keywords/bool.md) 'un C# [int](language-reference/builtin-types/integral-numeric-types.md)'e dönüştürülebilir olmadığına dikkat edin.  
  
Derleyici, tür bilgilerini yürütülebilir dosyaya meta veriler olarak katıştırır. Ortak dil çalışma zamanı (CLR), bellek ayırdığı ve geri kazanır daha fazla güvence altına almak için çalışma zamanında bu meta verileri kullanır.  

## <a name="specifying-types-in-variable-declarations"></a>Değişken bildirimlerinde türleri belirtme

Bir programda bir değişken veya sabit belirttiğinizde, onun türünü belirtmeniz veya [var](language-reference/keywords/var.md) anahtar sözcüğünü kullanarak derleyicinin türü saymasına izin vermelisiniz. Aşağıdaki örnek, hem yerleşik sayısal türler hem de Kullanıcı tanımlı karmaşık türler kullanan bazı değişken bildirimlerini gösterir:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Yöntem parametrelerinin türleri ve dönüş değerleri Yöntem imzasında belirtilmiştir. Aşağıdaki imza, giriş bağımsız değişkeni olarak bir [int](language-reference/builtin-types/integral-numeric-types.md) gerektiren ve bir dize döndüren bir yöntemi gösterir:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Bir değişken oluşturulduktan sonra, yeni bir türle yeniden bildirilemez ve belirtilen türle uyumlu olmayan bir değer atanamaz. Örneğin, bir [int](language-reference/builtin-types/integral-numeric-types.md) bildiremez ve bunu [true](language-reference/keywords/true-literal.md)Boolean değeri atayabilirsiniz. Ancak, değerler başka türlere dönüştürülebilir (örneğin, yeni değişkenlere atandığında veya yöntem bağımsız değişkenleri olarak geçirildiğinde). Veri kaybına neden olmayan bir *tür dönüştürmesi* , derleyici tarafından otomatik olarak gerçekleştirilir. Veri kaybına neden olabilecek bir dönüştürme, kaynak kodda bir *tür dönüştürme* gerektirir.

Daha fazla bilgi için bkz. [atama ve tür dönüştürmeleri](programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Yerleşik türler

C#tamsayılar, kayan nokta değerleri, Boole ifadeleri, metin karakterleri, ondalık değerler ve diğer veri türlerini temsil etmek için standart bir yerleşik sayısal türler kümesi sağlar. Ayrıca yerleşik **dize** ve **nesne** türleri de vardır. Bunlar, herhangi bir C# programda kullanabilmeniz için kullanılabilir. Yerleşik türler hakkında daha fazla bilgi için bkz. [Yerleşik türler Için başvuru tablosu](language-reference/keywords/built-in-types-table.md).  
  
## <a name="custom-types"></a>Özel türler

Kendi özel türlerinizi oluşturmak için [struct](language-reference/keywords/class.md), [Class](language-reference/keywords/class.md), [Interface](language-reference/keywords/interface.md)ve [enum](language-reference/keywords/enum.md) yapılarını kullanırsınız. .NET Framework sınıf kitaplığı, Microsoft tarafından kendi uygulamalarınızda kullanabileceğiniz özel türlerin bir koleksiyonudur. Varsayılan olarak, sınıf kitaplığındaki en sık kullanılan türler her C# programda kullanılabilir. Diğerleri yalnızca tanımlandıkları derlemeye açıkça bir proje başvurusu eklediğinizde kullanılabilir hale gelir. Derleyicinin derlemeye bir başvurusu olduktan sonra, kaynak kodda o derlemede belirtilen türlerin değişkenlerini (ve sabitleri) bildirebilirsiniz.
  
## <a name="generic-types"></a>Genel türler

Bir tür, istemci kodunun türün bir örneğini oluşturduğunda sağladığı gerçek tür ( *somut tür*) için yer tutucu olarak görev yapan bir veya daha fazla *tür parametresiyle* bildirilemez. Bu tür türler *Genel türler*olarak adlandırılır. Örneğin .NET Framework tür <xref:System.Collections.Generic.List%601>, kuralına göre bir tür parametresine sahiptir ve *t*adı verilir. Türün bir örneğini oluşturduğunuzda, listenin içereceği nesnelerin türünü (örneğin, dize) belirtirsiniz:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
Tür parametresinin kullanımı, her öğeyi [nesneye](language-reference/keywords/object.md)dönüştürmek zorunda kalmadan her türlü öğe türünü tutmak için aynı sınıfı yeniden kullanmayı mümkün kılar. Derleyici, koleksiyon öğelerinin belirli türünü bildiğinden ve derleme zamanında bir hata tetikleyebildiğinden, genel koleksiyon sınıfları *kesin türü belirtilmiş koleksiyonlar* olarak adlandırılır. `strings` Örneğin, önceki örnek. Daha fazla bilgi için bkz. [Genel türler](programming-guide/generics/index.md).

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Örtülü türler, anonim türler ve demet türleri

Daha önce belirtildiği gibi, [var](language-reference/keywords/var.md) anahtar sözcüğünü kullanarak yerel bir değişkeni (sınıf üyelerini değil) örtük olarak yazabilirsiniz. Değişken hala derleme zamanında bir tür alır, ancak tür derleyici tarafından sağlanır. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
Bazı durumlarda, yöntem sınırlarını depolamayı veya geçişi istemediğiniz ilgili değerlerin basit kümeleri için adlandırılmış bir tür oluşturmak uygun değildir. Bu amaçla *anonim türler* oluşturabilirsiniz. Daha fazla bilgi için bkz. [anonim türler](programming-guide/classes-and-structs/anonymous-types.md).

Bir yöntemden birden fazla değer döndürmek, yaygın bir yöntemdir. Tek bir yöntem çağrısında birden çok değer döndüren *demet türleri* oluşturabilirsiniz. Daha fazla bilgi için bkz. [tanımlama](tuples.md)bilgileri.

## <a name="the-common-type-system"></a>Ortak tür sistemi

.NET Framework sistem hakkında iki temel noktayı anlamak önemlidir:  
  
- Devralma ilkesini destekler. Türler, *temel türler*olarak adlandırılan diğer türlerden türetilebilir. Türetilmiş tür, yöntemleri, özellikleri ve temel türün diğer üyelerini devralır (bazı kısıtlamalarla). Temel tür başka bir türden türetebilir, bu durumda türetilmiş tür, devralma hiyerarşisindeki her iki temel türün üyelerini devralır. <xref:System.Int32> (C# anahtar sözcük:`int`) gibi yerleşik sayısal türler dahil olmak üzere tüm türler, sonunda<xref:System.Object>(C# anahtar sözcük:`object`) olan tek bir temel türden türetilir. Bu Birleşik tür hiyerarşisine [ortak tür sistemi](../standard/common-type-system.md) (Cts) denir. ' De C#devralma hakkında daha fazla bilgi için bkz. [Devralma](programming-guide/classes-and-structs/inheritance.md).  
  
- CTS içindeki her tür, bir *değer türü* veya bir *başvuru türü*olarak tanımlanır. Bu, .NET Framework sınıf kitaplığındaki tüm özel türleri ve ayrıca kendi Kullanıcı tanımlı türlerinizi içerir. [Struct](language-reference/keywords/struct.md) anahtar sözcüğünü kullanarak tanımladığınız türler değer türleridir; Tüm yerleşik sayısal türler **yapılar**' dur. Değer türleri hakkında daha fazla bilgi için bkz. [yapılar](structs.md). [Sınıf](language-reference/keywords/class.md) anahtar sözcüğünü kullanarak tanımladığınız türler başvuru türleridir. Başvuru türleri hakkında daha fazla bilgi için bkz. [sınıflar](classes.md). Başvuru türleri ve değer türlerinde farklı derleme zamanı kuralları ve farklı çalışma zamanı davranışları vardır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar](structs.md)
- [Sınıflar](classes.md)

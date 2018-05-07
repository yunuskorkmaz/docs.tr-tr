---
title: Temel türler - C# Kılavuzu
description: Tüm C# programları çekirdek türler (sayısal türler, dizeler ve nesne) hakkında bilgi edinin
ms.date: 10/10/2016
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 2e62a461e41f4172bd6dd512a71babb998924978
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="types-variables-and-values"></a>Türleri, değişkenler ve değerleri  
C# bir kesin türü belirtilmiş bir dildir. Bir değer veren her ifade yaptığı gibi her değişken ve sabit bir türe sahip. Her yöntem imzası her giriş parametre ve dönüş değeri için bir türünü belirtir. .NET Framework sınıf kitaplığı çok çeşitli dosya sistemi, ağ bağlantıları, koleksiyonları ve nesneleri ve tarihleri dizileri gibi mantıksal yapıları temsil eden daha karmaşık türlerin yanı sıra yerleşik sayısal türler kümesini tanımlar. Tipik bir C# programı sınıf kitaplığı türlerinden yanı sıra kullanıcı tanımlı türler, programın sorunu etki alanına özgü kavramları modeli kullanır.  
  
Bir tür depolanan bilgileri aşağıdakileri içerebilir:  
  
-   Türünde bir değişken gerektirir depolama alanı.  
  
-   Temsil edebilir maksimum ve minimum değerler.  
  
-   İçerdiği üyeler (yöntemler, alanları, olayları ve benzeri).  
  
-   Öğesinden devralınan temel türü.  
  
-   Çalışma zamanında değişkenleri için bellek burada ayrılır konumu.  
  
-   İzin verilen işlem türleri.  
  
Derleyici türü bilgileri kodunuzdaki tüm işlemler olduğundan emin olmak için kullanır. *denkliği*. Örneğin, türünde bir değişken bildirirseniz [int](language-reference/keywords/int.md), değişkeni ayrıca kullanmanızı ve çıkarma işlemleri derleyici sağlar. Bir değişken türü bu aynı işlemleri gerçekleştirmek deneyin [bool](language-reference/keywords/bool.md), derleyici aşağıdaki örnekte gösterildiği gibi bir hata oluşturur:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
>  C ve C++ geliştiriciler, fark, C# ' ta [bool](language-reference/keywords/bool.md) parametresinin [int](language-reference/keywords/int.md).  
  
Derleyici yürütülebilir dosyasına türü bilgisini meta veri olarak katıştırır. Ortak dil çalışma zamanı (CLR) ayırır ve bellek kaldırsa daha fazla tür güvenliği güvence altına almak için çalışma zamanında meta verilerin kullanır.  

## <a name="specifying-types-in-variable-declarations"></a>Değişken bildirimlerinde türlerini belirtme  
Ne zaman bir değişken bildirme veya sabit bir programda türünü belirtin veya kullanmak [var](language-reference/keywords/var.md) türü Infer derleyici izin vermek için anahtar sözcüğü. Aşağıdaki örnek, yerleşik sayısal türler ve kullanıcı tanımlı karmaşık türler kullanan bazı değişken bildirimleri gösterir:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Yöntem parametreleri ve dönüş değerleri türlerini yöntemi imzada belirtilir. Aşağıdaki imzası gerektiren bir yöntemi gösterir bir [int](language-reference/keywords/int.md) giriş bağımsız değişken olarak ve bir dize döndürür:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Bir değişken bildirildikten sonra yeni bir türüyle yeniden bildirilen olamaz ve onun bildirilen türü ile uyumlu olmayan bir değer atanamaz. Örneğin, bildiremezsiniz bir [int](language-reference/keywords/int.md) ve bir Boolean değeri atamak [doğru](language-reference/keywords/true.md). Ancak, örneğin yeni değişkenlere atanan veya yöntem bağımsız değişken olarak geçirilen diğer türleri için değerleri dönüştürülebilir. A *yazın dönüştürme* o mu neden veri kaybı derleyici tarafından otomatik olarak gerçekleştirilir. Veri kaybına neden bir dönüştürme gerektiren bir *cast* kaynak kodundaki. 

Daha fazla bilgi için bkz: [atama ve tür dönüştürmeleri](programming-guide/types/casting-and-type-conversions.md).
 
## <a name="built-in-types"></a>Yerleşik türler
C# tamsayı, kayan nokta değerleri, Boole ifadeleri, metin karakterler, ondalık değerleri temsil etmek için yerleşik sayısal türler ve diğer veri türleri standart kümesi sağlar. Ayrıca vardır yerleşik **dize** ve **nesne** türleri. Bu, tüm C# programında kullanmanız için kullanılabilir. Yerleşik türleri hakkında daha fazla bilgi için bkz: [türler için başvuru tablosu](language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Özel türler  
Kullandığınız [yapısı](language-reference/keywords/class.md), [sınıfı](language-reference/keywords/class.md), [arabirimi](language-reference/keywords/interface.md), ve [enum](language-reference/keywords/enum.md) yapıları kendi özel türleri oluşturmak için. .NET Framework sınıf kitaplığı kendisi, kendi uygulamalarında kullanabileceğiniz Microsoft tarafından sağlanan özel türler koleksiyonudur. Varsayılan olarak, en sık kullanılan türleri sınıf kitaplığı'nda tüm C# programı içinde kullanılabilir. Yalnızca açıkça tanımlanmış derleme proje başvurusu eklediğinizde diğerleri kullanılabilir hale gelir. Derleyici derlemesine başvuru sahip olduktan sonra değişkenlerin (ve sabitleri) türleri bu derleme kaynak kodunda bildirilen bildirebilirsiniz. 
  
## <a name="generic-types"></a>Genel türler  
Bir veya daha fazla ile bir türü bildirilebilir *tür parametrelerindeki* , gerçek tür için bir yer tutucu olarak hizmet verir ( *somut türü*) türünün bir örneğini oluşturduğunda, istemci kodu sağlayacaktır. Bu tür türleri olarak adlandırılır *genel türler*. Örneğin, .NET Framework türü <xref:System.Collections.Generic.List%601> , kural tarafından adı verilen bir tür parametresi sahip *T*. Türünün bir örneği oluşturduğunuzda, bu liste, örneğin, dize içerir nesnelerin türünü belirtin:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)] 
  
Tür parametresi kullanımını her öğeye Dönüştür gerek kalmadan herhangi bir türde öğe tutmak için aynı sınıfı yeniden mümkün kılar [nesne](language-reference/keywords/object.md). Genel koleksiyon sınıfları çağrılır *kesin türü belirtilmiş koleksiyonları* derleyici koleksiyonun öğelerini belirli türünü bilir ve neden olabilir, derleme zamanı IF sırasında bir hata olduğundan, örneğin, bir tamsayı eklemeyideneyin`strings` önceki örnekte nesnesi. Daha fazla bilgi için bkz: [genel türler](programming-guide/generics/index.md). 

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Örtük türleri, anonim türler ve dizi türleri  
Daha önce belirtildiği gibi örtük olarak yerel bir değişken (ancak sınıf üyeleri) kullanarak yazabilirsiniz [var](language-reference/keywords/var.md) anahtar sözcüğü. Değişkeni derleme zamanında hala bir türü alır, ancak türü derleyici tarafından sağlanır. Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
Bazı durumlarda depolamak veya yöntemi sınırları dışında geçirmek istemediğiniz ilgili değerleri basit kümeleri için adlandırılmış bir türü oluşturmak uygun değildir. Oluşturabileceğiniz *anonim türler* bu amaç için. Daha fazla bilgi için bkz: [anonim türler](programming-guide/classes-and-structs/anonymous-types.md).

Bir yöntemin birden fazla değer döndürmek için yaygın bir durumdur. Oluşturabileceğiniz *kayıt türlerinin* tek yöntem çağrısında birden çok değeri döndürür. Daha fazla bilgi için bkz: [diziler](tuples.md)

## <a name="the-common-type-system"></a>Ortak tür sistemi  
.NET Framework'te tür sistemi hakkında iki temel noktaları anlamak önemlidir:  
  
-   Devralma ilkesini destekler. Türler adlı diğer türlerinden türetmek *temel türleri*. Türetilmiş bir tür (bazı sınırlamalarla birlikte) yöntemler, özellikler ve diğer temel türün üyeleri devralır. Temel türü sırayla çalışması türetilmiş bir tür devralma hiyerarşisi içinde her iki temel tür üyeleri devralır başka türü, türetilen. Yerleşik sayısal türler gibi dahil tüm türleri <xref:System.Int32> (C# anahtar sözcüğü: `int`), türetilen sonuçta tek taban türünden olduğu <xref:System.Object> (C# anahtar sözcüğü: `object`). Bu birleşik türü hiyerarşi adı verilen [ortak tür sistemi](../standard/common-type-system.md) (CTS). C# devralma hakkında daha fazla bilgi için bkz: [devralma](programming-guide/classes-and-structs/inheritance.md).  
  
-   Her türde CTS olarak tanımlanan bir *değer türü* veya *başvuru türüne*. Bu, .NET Framework sınıf kitaplığı yanı sıra kendi kullanıcı tanımlı türler tüm özel türler içerir. Kullanarak tanımladığınız türleri [yapısı](language-reference/keywords/struct.md) anahtar değer türleri; tüm yerleşik sayısal türler **yapılar**. Değer türleri hakkında daha fazla bilgi için bkz: [yapılar](structs.md). Kullanarak tanımladığınız türleri [sınıfı](language-reference/keywords/class.md) bir anahtar sözcüktür başvuru türleri. Başvuru türleri hakkında daha fazla bilgi için bkz: [sınıfları](classes.md). Başvuru türleri ve değer türleri farklı derleme zamanı kurallar ve farklı bir çalışma zamanı davranışı sahiptir.
 
  
## <a name="see-also"></a>Ayrıca bkz.
[Yapılar](structs.md)
[sınıfları](classes.md)

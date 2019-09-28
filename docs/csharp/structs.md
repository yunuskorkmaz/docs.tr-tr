---
title: Yapılar- C# kılavuz
description: Yapı türü ve bunları nasıl oluşturacağınız hakkında bilgi edinin
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: e0974b7dcf3c0888cb52bea81b07a58e3a98640b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396130"
---
# <a name="structs"></a>Yapılar

*Struct* bir değer türüdür. Bir struct oluşturulduğunda, yapının atandığı değişken yapının gerçek verilerini barındırır. Yapı yeni bir değişkene atandığında, kopyalanır. Bu nedenle, yeni değişken ve özgün değişken aynı verilerin iki ayrı kopyasını içerir. Bir kopyada yapılan değişiklikler diğer kopyayı etkilemez.

Değer türü değişkenleri doğrudan değerlerini içerir, bu da belleğin, değişkenin bildirildiği bağlamda satır içi olarak ayrıldığı anlamına gelir. Değer türü değişkenler için ayrı bir yığın ayırma veya çöp toplama ek yükü yoktur.  
  
Değer türlerinin iki kategorisi vardır: [struct](./language-reference/keywords/struct.md) ve [enum](./language-reference/keywords/enum.md).  
  
Yerleşik sayısal türler yapı birimleridir ve erişebileceğiniz özelliklere ve yöntemlere sahiptirler:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ancak bunları, basit olmayan türler gibi bu değerlere bildirir ve bunlara atanır:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Değer türleri *Sealed*olur, yani örneğin, <xref:System.Int32> ' den bir tür türetilemez ve bir yapı yalnızca <xref:System.ValueType> ' den devralabileceği için Kullanıcı tanımlı herhangi bir sınıftan veya yapıdan devralacak bir yapı tanımlayamazsınız. Ancak, bir struct bir veya daha fazla arabirim uygulayabilir. Bir yapı türünü arabirim türüne çevirebilirsiniz; Bu, bir *kutulama* işleminin yapıyı yönetilen yığında bir başvuru türü nesnesinin içine sarmasına neden olur. Kutulama işlemleri bir değer türünü, giriş parametresi olarak <xref:System.Object> alan bir yönteme geçirdiğinizde oluşur. Daha fazla bilgi için bkz. [kutulama ve kutudan](./programming-guide/types/boxing-and-unboxing.md )çıkarma.  
  
Kendi özel değer türlerinizi oluşturmak için [struct](./language-reference/keywords/struct.md) anahtar sözcüğünü kullanırsınız. Genellikle, bir yapı aşağıdaki örnekte gösterildiği gibi küçük bir ilgili değişkenler kümesi için kapsayıcı olarak kullanılır:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
.NET Framework değer türleri hakkında daha fazla bilgi için bkz. [ortak tür sistemi](../standard/common-type-system.md).  
    
Yapılar sınıflarla aynı sözdiziminin çoğunu paylaşır, ancak yapılar sınıflardan daha sınırlıdır:  
  
- Bir struct bildiriminde, `const` veya `static` olarak belirtilmedikçe alanlar başlatılamaz.  
  
- Struct parametresiz bir Oluşturucu (parametresiz bir Oluşturucu) veya sonlandırıcısı bildiremez.  
  
- Yapılar atamaya kopyalanır. Bir yapı yeni bir değişkene atandığında, tüm veriler kopyalanır ve yeni kopyada yapılan değişiklikler özgün kopyanın verilerini değiştirmez. Bu, sözlük < dize, myStruct > gibi değer türlerinin koleksiyonlarıyla çalışırken unutmamak önemlidir.  
  
- Yapılar, değer türlerdir ve sınıflardır başvuru türleridir.  
  
- Sınıfların aksine, yapılar `new` işleci kullanılmadan örneklenebilir.  
  
- Yapılar, parametreleri olan oluşturucular bildirebilir.  
  
- Yapı, başka bir struct veya sınıftan devralınabilir ve bir sınıfın temeli olamaz. Tüm yapılar, <xref:System.Object> ' den devralan <xref:System.ValueType> ' dan devralır.  
  
- Bir struct, arabirimler uygulayabilir.

## <a name="literal-values"></a>Değişmez değerler

' C#De, değişmez değerler derleyicisinden bir tür alır. Sayının sonuna bir harf ekleyerek sayısal bir sabit değerin nasıl yazılması gerektiğini belirtebilirsiniz. Örneğin, 4,56 değerinin bir float olarak değerlendirilip değerlendirilmeyeceğini belirtmek için, sayının sonuna bir "f" veya "F" ekleyin: `4.56f`. Hiçbir harf eklenyoksa, derleyici değişmez değer için `double` türünü çıkaracaktır. Hangi türlerin harf sonekleriyle belirtibileceği hakkında daha fazla bilgi için bkz. [değer türlerinde](./language-reference/keywords/value-types.md)bağımsız türler için başvuru sayfaları.  
  
Değişmez değerler yazıldığı ve tüm türlerin sonunda <xref:System.Object> ' dan türetiğinden, aşağıdaki gibi bir kod yazabilir ve derleyebilirsiniz:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Son iki örnekte 7,0 ' de C# tanıtılan dil özellikleri gösterilmektedir. İlki, sayısal değişmez değerler içinde *rakam ayırıcısı* olarak bir alt çizgi karakterini kullanmanıza olanak sağlar. Okunabilirliği artırmak için bunları basamaklar arasında istediğiniz yere yerleştirebilirsiniz. Değer üzerinde hiçbir etkisi yoktur.

İkincisi, onaltılık Gösterim kullanmak yerine doğrudan bit desenleri belirtmenize imkan tanıyan *ikili sabit değerleri*gösterir.

## <a name="nullable-value-types"></a>Null yapılabilir değer türleri

Sıradan değer türlerinin değeri [null](language-reference/keywords/null.md)olamaz. Ancak, türden sonra `?` ' ı birleştirerek null yapılabilir değer türleri oluşturabilirsiniz. Örneğin, `int?`, [null](./language-reference/keywords/null.md)değeri de olan bir `int` türüdür. Null yapılabilir değer türleri, <xref:System.Nullable%601> genel yapı türünün örnekleridir. Null olabilen değer türleri, genellikle sayısal değerlerin null veya tanımsız olabileceği veritabanlarına veri geçirirken faydalıdır. Daha fazla bilgi için bkz. [Nullable değer türleri](programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar](classes.md)
- [Temel Türler](basic-types.md)

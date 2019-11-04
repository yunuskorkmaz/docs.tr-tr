---
title: Yapılar- C# kılavuz
description: Yapı türü ve bunları nasıl oluşturacağınız hakkında bilgi edinin
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 10971dc1a0b2c9d64ac8766734b3f6f630aa3ccf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423113"
---
# <a name="structs"></a>Yapılar

*Struct* bir değer türüdür. Bir struct oluşturulduğunda, yapının atandığı değişken yapının gerçek verilerini barındırır. Yapı yeni bir değişkene atandığında, kopyalanır. Bu nedenle, yeni değişken ve özgün değişken aynı verilerin iki ayrı kopyasını içerir. Bir kopyada yapılan değişiklikler diğer kopyayı etkilemez.

Değer türü değişkenleri doğrudan değerlerini içerir, bu da belleğin, değişkenin bildirildiği bağlamda satır içi olarak ayrıldığı anlamına gelir. Değer türü değişkenler için ayrı bir yığın ayırma veya çöp toplama ek yükü yoktur.  
  
Değer türlerinin iki kategorisi vardır: [struct](./language-reference/keywords/struct.md) ve [enum](./language-reference/keywords/enum.md).  
  
Yerleşik sayısal türler yapı birimleridir ve erişebileceğiniz özelliklere ve yöntemlere sahiptirler:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ancak bunları, basit olmayan türler gibi bu değerlere bildirir ve bunlara atanır:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Değer türleri *korumalıdır*, yani örneğin, bir türü <xref:System.Int32>türetemezsiniz ve Kullanıcı tanımlı herhangi bir sınıftan veya yapıdan devralacak bir struct tanımlayamazsınız, çünkü bir struct yalnızca <xref:System.ValueType>devralabilir. Ancak, bir struct bir veya daha fazla arabirim uygulayabilir. Bir yapı türünü arabirim türüne çevirebilirsiniz; Bu, bir *kutulama* işleminin yapıyı yönetilen yığında bir başvuru türü nesnesinin içine sarmasına neden olur. Paketleme işlemleri, bir <xref:System.Object> giriş parametresi olarak alan bir yönteme bir değer türü geçirdiğinizde oluşur. Daha fazla bilgi için bkz. [kutulama ve kutudan](./programming-guide/types/boxing-and-unboxing.md )çıkarma.  
  
Kendi özel değer türlerinizi oluşturmak için [struct](./language-reference/keywords/struct.md) anahtar sözcüğünü kullanırsınız. Genellikle, bir yapı aşağıdaki örnekte gösterildiği gibi küçük bir ilgili değişkenler kümesi için kapsayıcı olarak kullanılır:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
.NET Framework değer türleri hakkında daha fazla bilgi için bkz. [ortak tür sistemi](../standard/common-type-system.md).  
    
Yapılar sınıflarla aynı sözdiziminin çoğunu paylaşır, ancak yapılar sınıflardan daha sınırlıdır:  
  
- Bir struct bildiriminde, `const` veya `static`olarak belirtilemediği sürece alanlar başlatılamaz.  
  
- Struct parametresiz bir Oluşturucu (parametresiz bir Oluşturucu) veya sonlandırıcısı bildiremez.  
  
- Yapılar atamaya kopyalanır. Bir yapı yeni bir değişkene atandığında, tüm veriler kopyalanır ve yeni kopyada yapılan değişiklikler özgün kopyanın verilerini değiştirmez. Bu, sözlük < dize, myStruct > gibi değer türlerinin koleksiyonlarıyla çalışırken unutmamak önemlidir.  
  
- Yapılar, değer türlerdir ve sınıflardır başvuru türleridir.  
  
- Sınıfların aksine, yapılar `new` işleci kullanılmadan oluşturulabilir.  
  
- Yapılar, parametreleri olan oluşturucular bildirebilir.  
  
- Yapı, başka bir struct veya sınıftan devralınabilir ve bir sınıfın temeli olamaz. Tüm yapılar, <xref:System.Object>devralan <xref:System.ValueType>doğrudan devralır.  
  
- Bir struct, arabirimler uygulayabilir.

## <a name="literal-values"></a>Değişmez değerler

' C#De, değişmez değerler derleyicisinden bir tür alır. Sayının sonuna bir harf ekleyerek sayısal bir sabit değerin nasıl yazılması gerektiğini belirtebilirsiniz. Örneğin, 4,56 değerinin bir float olarak değerlendirilip değerlendirilmeyeceğini belirtmek için, sayının sonuna bir "f" veya "F" ekleyin: `4.56f`. Hiçbir harf eklenyoksa, derleyici değişmez değer için `double` türünü çıkaracaktır. Hangi türlerin harf sonekleriyle belirtibileceği hakkında daha fazla bilgi için bkz. [değer türlerinde](./language-reference/keywords/value-types.md)bağımsız türler için başvuru sayfaları.  
  
Değişmez değerler yazıldığı ve tüm türler <xref:System.Object>sonunda sonuç olarak türettiğinden, aşağıdaki gibi bir kod yazabilir ve derleyebilirsiniz:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Son iki örnekte 7,0 ' de C# tanıtılan dil özellikleri gösterilmektedir. İlki, sayısal değişmez değerler içinde *rakam ayırıcısı* olarak bir alt çizgi karakterini kullanmanıza olanak sağlar. Okunabilirliği artırmak için bunları basamaklar arasında istediğiniz yere yerleştirebilirsiniz. Değer üzerinde hiçbir etkisi yoktur.

İkincisi, onaltılık Gösterim kullanmak yerine doğrudan bit desenleri belirtmenize imkan tanıyan *ikili sabit değerleri*gösterir.

## <a name="nullable-value-types"></a>Boş değer atanabilen değer türleri

Sıradan değer türlerinin değeri [null](language-reference/keywords/null.md)olamaz. Ancak, türden sonra bir `?` ekleyerek null yapılabilir değer türleri oluşturabilirsiniz. Örneğin `int?`, [null](./language-reference/keywords/null.md)değeri de olan bir `int` türüdür. Null yapılabilir değer türleri <xref:System.Nullable%601>genel yapı türü örnekleridir. Null olabilen değer türleri, genellikle sayısal değerlerin null veya tanımsız olabileceği veritabanlarına veri geçirirken faydalıdır. Daha fazla bilgi için bkz. [Nullable değer türleri](programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar](programming-guide/classes-and-structs/classes.md)
- [Temel Türler](basic-types.md)

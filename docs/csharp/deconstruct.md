---
title: Tanımlama grupları ve diğer türleri deconstructing
description: Tanımlama grupları ve diğer türleri deconstruct öğrenin.
author: rpetrusha
ms.author: ronpet
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 726a391a4a747e5446e252e669c5b16248a5e0ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217751"
---
# <a name="deconstructing-tuples-and-other-types"></a>Tanımlama grupları ve diğer türleri deconstructing #

Bir tanımlama grubu hafif bir yöntem çağrısının birden çok değer almanıza olanak sağlar. Ancak tanımlama grubu almak sonra bireysel öğeleri işlemek vardır. Bir öğe öğeli temelinde bunu aşağıdaki örnekte gösterildiği gibi uğraş. `QueryCityData` Yöntemi 3-tanımlama grubu döndürür ve alt öğelerin her biri ayrı bir işlemde bir değişkene atanır.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Bir nesneden birden çok alan ve özellik değerlerini alma eşit sıkıcı olabilir: bir alan veya özellik değeri bir üyesi tarafından üye temelinde bir değişkene atamış olmanız gerekir. 

C# 7. 0'dan başlayarak, birden çok öğe tanımlama grubundan almak veya birden çok alan, özellik ve hesaplanan değerler tek bir nesneden almak *deconstruct* işlemi. Bir tanımlama grubu deconstruct bağımsız değişkenlere öğeleri atayın. Bir nesne deconstruct bağımsız değişkenleri için seçilen değerler atayın. 

## <a name="deconstructing-a-tuple"></a>Bir tanımlama grubu deconstructing

C# özellikleri yerleşik bir tanımlama grubu tek bir işlemde tüm öğelerde gitmeniz imkan tanıyan bir tanımlama grubu deconstructing için destek. Bir tanımlama grubu deconstructing genel söz dizimi bir tanımlama söz dizimi benzerdir: her öğeye sahip olduğu parantez içinde Atama ifadesinin sol tarafındaki atanacak değişkenleri alın. Örneğin, aşağıdaki deyim, dört ayrı değişkenlere 4 bölütlü öğelerini atar:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Bir tanımlama grubu deconstruct üç yolu vardır:

- Parantez içindeki her bir alan türü açıkça bildirebilir. Aşağıdaki örnek, tarafından döndürülen 3-tanımlama grubu deconstruct için bu yaklaşımı kullanır `QueryCityData` yöntemi.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Kullanabileceğiniz `var` C# her bir değişken türü algılar anahtar sözcüğü. Yerleştirdiğiniz `var` anahtar sözcüğü parantez dışında. Aşağıdaki örnek tür çıkarımı tarafından döndürülen 3-tanımlama grubu deconstructing kullanır `QueryCityData` yöntemi.
 
    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Aynı zamanda `var` ayrı ayrı veya tamamını parantez içinde değişken bildirimleri olan anahtar sözcük. 

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    Bu sıkıcı ve önerilmez.

- Son olarak, tanımlama grubu zaten tanımlanmış değişkenleri deconstruct.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Dizideki her alan aynı türde olsa bile belirli bir tür parantez dışında belirtemezsiniz. Derleyici Hatası "Deconstruction 'var (...)' form 'var' için belirli bir tür izin vermez." CS8136 oluşturur.

Not, ayrıca her bir tanımlama grubu öğesi bir değişkene atamanız gerekir. Herhangi bir öğe atlarsanız, derleyici hatası "'x' öğelerini tanımlama grubu 'y' değişkenleri deconstruct yapılamıyor." CS8132 oluşturur.

Bildirimler ve bir deconstruction sol taraftaki mevcut değişkenler için atamaları karıştıramazsınız unutmayın. Derleyici Hatası "bir deconstruction bildirimler ve sol-hand tarafı ifadeleri karıştıramazsınız." CS8184 oluşturur ne zaman üyeleri yeni bildirilen ve varolan değişkenleri içerir.

## <a name="deconstructing-tuple-elements-with-discards"></a>Tuple öğeleriyle deconstructing atar

Genellikle bir tanımlama grubu deconstructing, yalnızca bazı öğeler değerlerde ilgilendiğiniz. C# 7. 0'dan başlayarak, C# ' nin desteğini yararlanabilirsiniz *atar*, değerleri yoksaymak için seçtiğiniz salt yazılır değişkenleri olduğu. Bir atma bir alt çizgi karakteriyle belirlenmiş ("\_") bir atamayı. İstediğiniz kadar çok değerle atabilirsiniz; tüm tek atma tarafından temsil edilen `_`.

Aşağıdaki örnek iptali içeren başlık kullanımını göstermektedir. `QueryCityDataForYears` Yöntemi bir şehir, kendi alanı, bir yılın, o yıl, ikinci bir yıl ve bu ikinci yıl Şehir 's popülasyon Şehir 's popülasyon adıyla 6-tanımlama grubu döndürür. Örnek popülasyondaki bu iki yıl arasında değişiklik gösterir. Verileri tanımlama grubu bulunan, biz Şehir alanıyla unconcerned ve şehir adı ve tasarım zamanında iki tarih biliyoruz. Sonuç olarak, biz yalnızca düzeninde depolanan iki popülasyon değerleri ilgileniyor ve onun kalan değerler iptali olarak işleyebilir.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

### <a name="deconstructing-user-defined-types"></a>Deconstructing kullanıcı tanımlı türler

Olmayan tanımlama grubu türleri için yerleşik destek atar sağlamaz. Ancak, bir sınıf, yapı veya arabirim yazarı, bir veya daha fazla uygulayarak deconstructed için türün örneklerinin izin verebilirsiniz `Deconstruct` yöntemleri. Yöntem void döndürür ve deconstructed için her bir değeri tarafından belirtilen bir [çıkışı](language-reference/keywords/out-parameter-modifier.md) yöntem imzası parametresi. Örneğin, aşağıdaki `Deconstruct` yöntemi bir `Person` sınıfı, Orta, adı ve Soyadı döndürür:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Ardından örneği deconstruct `Person` adlı sınıf `p` aşağıdaki gibi bir atama:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Aşağıdaki örnek aşırı `Deconstruct` özelliklerini çeşitli döndürülecek yöntemi bir `Person` nesnesi. Tek tek aşırı döndürün:

- İlk ve son adı.
- İlk, son olarak ve ikinci adı.
- Ad, Soyadı, bir şehrin adı ve durum adı.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Aşırı yüklenebilir olduğundan `Deconstruct` genellikle bir nesneden ayıklanır veri grupları yansıtacak şekilde yöntemi tanımlamak dikkatli olmalıdır `Deconstruct` ayırt edici ve anlaşılır imzaları yöntemleriyle. Birden çok `Deconstruct` aynı sayıda yöntemleri `out` parametreleri veya aynı sayı ve tür `out` farklı bir düzende parametreleri karışıklığa neden olabilir. 

Aşırı yüklenmiş `Deconstruct` yöntemi aşağıdaki örnekte bir olası kaynak karışıklık göstermektedir. Ad, ikinci adı, Soyadı ve yaş ilk aşırı döndürür bir `Person` bu sırayla nesnesi. İkinci aşırı yalnızca yıllık geliri yanı sıra adı bilgi verir, ancak, Orta, adı ve Soyadı farklı bir sırada olur. Bu bağımsız değişkenler sırasını deconstructing zaman karıştırır kolaylaştırır bir `Person` örneği.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Kullanıcı tanımlı bir tür ile deconstructing atar

İle yapmak gibi [diziler](#deconstructing-tuple-elements-with-discards), iptali tarafından döndürülen seçilen öğeleri yoksaymak için kullanabileceğiniz bir `Deconstruct` yöntemi. Her atma adlı bir değişkeni tarafından tanımlanan "\_", bir tek deconstruction işlemi birden çok iptali içerebilir.

Aşağıdaki örnek deconstructs bir `Person` dört dizeleri (ilk ve son adları, şehir ve durumu) nesnesine ancak son adı ve durum atar.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Kullanıcı tanımlı bir tür bir genişletme yöntemi ile deconstructing

Bir sınıf, yapı veya arabirim kaydetmedi yazarsanız, hala bu tür nesneleri bir veya daha fazla uygulayarak deconstruct `Deconstruct` [genişletme yöntemleri](programming-guide/classes-and-structs/extension-methods.md) içinde ilgi değer döndürmek için. 

Aşağıdaki örnekte iki tanımlar `Deconstruct` için genişletme yöntemleri <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> sınıfı. İlk statik olup, türü de dahil olmak üzere bu özelliği özelliklerini göstermek veya örnek değerleri, salt okunur olup ve olup dizine kümesini döndürür. İkinci özelliğin erişilebilirlik gösterir. Çünkü get erişilebilirliğini ve set erişimcileri farklı, Boole değerleri gösteren özelliği ayrı olup alma ve ayarlama erişimcisi ve aynı erişilebilirlik olup, varsa. Yalnızca bir erişimci veya aynı erişilebilirlik, hem get hem de set erişimcisine sahip `access` değişkeni özelliği erişilebilirlik bir bütün olarak gösterir. Aksi halde, get erişilebilirliğini ve erişimciler accessaccessibility tarafından belirtilen kümesi tarafından belirtilir `getAccess` ve `setAccess` değişkenleri.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]
 
## <a name="see-also"></a>Ayrıca bkz.
[Atar](discards.md)   
[Demetler](tuples.md)  

---
title: Listeler (F#)
description: 'F # listeleri, aynı türdeki öğeleri sıralı, sabit bir dizi hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e29dbdac5e920c009bf7758fd2cc1ad486041cad
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="lists"></a>Listeler

> [!NOTE]
Bu makalede API başvuru bağlantılar için MSDN götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

F # listedeki öğeleri aynı türde sıralı, değişmez dizisidir. Listeler temel işlemleri gerçekleştirmek için işlevlerde kullanmak [List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).


## <a name="creating-and-initializing-lists"></a>Oluşturma ve başlatma listeler
Noktalı virgülle ayırarak ve aşağıdaki kod satırını gösterildiği gibi köşeli parantez içine alınmış öğeleri çıkışı açıkça listeleyerek listesini tanımlayabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Satır sonları öğeler arasında de koyabilirsiniz, bu durumda noktalı isteğe bağlıdır. İkinci sözdizimi daha okunabilir kodda öğe başlatma ifadeleri uzun olduğunda ya da her öğe için bir açıklama eklemek istediğinizde neden olabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

Normalde, tüm liste öğeleri aynı türde olmalıdır. Öğeleri bir taban türü olan öğeler bulunabilir belirtilir listesini türetilmiş tür istisnadır. Böylece aşağıdaki kabul edilebilir, çünkü her ikisi de `Button` ve `CheckBox` öğesinden türetilen `Control`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Aralık işleci tarafından ayrılmış tamsayılar tarafından gösterilen bir aralık kullanarak liste öğeleri tanımlayabilirsiniz (`..`), aşağıdaki kodda gösterildiği gibi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Boş bir liste bir çift köşeli ayraç bunları Between hiçbir şey ile belirtilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Bir sıra ifadesi, bir liste oluşturmak için de kullanabilirsiniz. Bkz: [Sequence ifadeleri](sequences.md#sequence-expressions) daha fazla bilgi için. Örneğin, aşağıdaki kod, tamsayılar kareleri listesini 1'den 10'a oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Listeleri ile çalışmak için işleçleri
Kullanarak bir liste öğelerini ekleyebilirsiniz `::` (olumsuz) işleci. Varsa `list1` olan `[2; 3; 4]`, aşağıdaki kod oluşturur `list2` olarak `[100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Kullanarak uyumlu türleri olan listeleri birleştirme `@` aşağıdaki kodu olduğu gibi işleci. Varsa `list1` olan `[2; 3; 4]` ve `list2` olan `[100; 2; 3; 4 ]`, bu kod oluşturur `list3` olarak `[2; 3; 4; 100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

İşlevler listeleri üzerinde işlem gerçekleştirmek için kullanılabilir [List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

F # listeleri değişmez olduğundan değiştirme işlemleri varolan listeleri değiştirme yerine yeni liste oluşturur.

F # listeleri yalnızca listenin başında erişim işlemleri O(1) anlamına gelir, ayrı olarak bağlantılı liste olarak uygulanır ve öğesi erişimi O (*n*).


## <a name="properties"></a>Özellikler
Liste türü aşağıdaki özellikleri destekler:

|Özellik|Tür|Açıklama|
|--------|----|-----------|
|[HEAD](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|İlk öğe.|
|[boş](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|Uygun bir tür boş bir liste döndürür bir statik özellik.|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true` Listenin öğe varsa.|
|[Öğesi](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|(Sıfır tabanlı) belirtilen dizininde bulunan öğe.|
|[uzunluğu](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|Öğe sayısı.|
|[Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|Listenin ilk öğe olmadan.|
Bu özellikleri kullanarak bazı örnekler verilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]
    
## <a name="using-lists"></a>Listeleri kullanma
Listeleri ile programlama kodu küçük miktarda karmaşık işlemler gerçekleştirmenizi sağlar. Bu bölümde işlevsel programlama için önemli olan listelerde ortak işlemleri açıklanmaktadır.


### <a name="recursion-with-lists"></a>Özyineleme listeleriyle
Listeleri için yinelemeli teknikler programlama benzersiz olarak uygundur. Her bir liste öğesi üzerinde gerçekleştirilen bir işlem göz önünde bulundurun. Listenin başında işletim ve özgün listenin ilk öğe olmadan oluşan küçük bir listedir listesi kuyruğu geçirme tarafından bu yinelemeli olarak yapın, özyineleme sonraki seviyeye yeniden.

Bu tür bir özyinelemeli işlevi yazmak için olumsuz işlecini kullanın (`::`) desen eşleştirme içinde sağlayan listesini head tail ayırmak.

Aşağıdaki kod örneğinde desen eşleştirme listesini işlemleri gerçekleştiren bir özyinelemeli işlevi uygulamak için nasıl kullanılacağını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Önceki kod küçük listeler için iyi çalışır, ancak büyük listeler için yığın taşması. Aşağıdaki kod, accumulator bağımsız değişken, özyinelemeli işlevler ile çalışmak için standart bir yöntem kullanarak bu kodu artırır. Accumulator bağımsız değişken kullanımını yığın alanından tasarruf işlevi tail özyinelemeli sağlar.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

İşlev `RemoveAllMultiples` listelerini götüren bir özyinelemeli işlevdir. İlk liste, katları kaldırılacak sayıları içeren ve ikinci listesi sayıları kaldırılacağı listesidir. Aşağıdaki örnek kodda, tüm olmayan-asal sayılar asal sayılar listesini sonucu olarak bırakarak bir listeden ortadan kaldırmak için bu özyinelemeli işlev kullanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

Çıktı aşağıdaki gibidir:

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Modül işlevleri
[List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) bir liste öğelerini erişim işlevleri sağlar. Head öğesi, hızlı ve kolay erişim ' dir. Özelliğini kullanın [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) veya modül işlevi [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2). Tail listesini kullanarak erişebilirsiniz [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) özelliği veya [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) işlevi. Dizine göre bir öğeyi bulmak için [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) işlevi. `List.nth` Listenin erişir. Bu nedenle, O olur (*n*). Kodunuzu kullanıyorsa `List.nth` genellikle, bir dizi yerine bir listesini kullanarak düşünmek isteyebilirsiniz. Dizilerde öğesi erişim O(1) ' dir.


### <a name="boolean-operations-on-lists"></a>Boole işleçleri listeleri hakkında
[List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) işlevi listesini herhangi bir öğe sahip olup olmadığını belirler.

[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) işlevi geçerli bir Boole değeri öğeleri listesini döndürür ve test `true` herhangi bir öğe test uymazsa. [List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) benzer, ancak iki liste öğeleri art arda gelen çiftlerini çalıştırır.

Aşağıdaki kod kullanımını gösteren `List.exists`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

Çıktı aşağıdaki gibidir:

```
For list [0; 1; 2; 3], contains zero is true
```

Aşağıdaki örnek kullanımını gösteren `List.exists2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

Çıktı aşağıdaki gibidir:

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

Kullanabileceğiniz [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) listesini tüm öğeleri bir koşulu karşılayıp karşılamadığını sınamak istiyorsanız.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

Çıktı aşağıdaki gibidir:

```
true
false
```

Benzer şekilde, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) karşılık gelen konumlarda iki listelerindeki tüm öğeleri öğelerinin her çifti içerir Boolean bir ifadeye uygun olup olmadığını belirler.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

Çıktı aşağıdaki gibidir:

```
true
false
```

### <a name="sort-operations-on-lists"></a>Sıralama işlemi listeleri hakkında
[List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), ve [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) işlevleri sıralama listeler. Sıralama işlevini kullanmak için bu üç işlevlerin belirler. `List.sort` Varsayılan genel karşılaştırma kullanır. Genel karşılaştırma genel karşılaştırma işlevine dayalı genel işleçlerini değerleri karşılaştırmak için kullanır. Çok çeşitli basit sayısal türler, tanımlama grupları, kayıtları, ayrılmış birleşimler, listeler, dizileri ve uygulayan herhangi bir türü gibi öğe türleri ile verimli bir şekilde çalıştığını `System.IComparable`. Bu uygulama türleri için `System.IComparable`, genel karşılaştırma kullanır `System.IComparable.CompareTo()` işlevi. Genel karşılaştırma ayrıca dizelerle çalışır, ancak bir kültür bağımsız sıralama düzenini kullanır. İşlev türleri gibi desteklenmeyen türleri hakkında genel karşılaştırma kullanılmamalıdır. Ayrıca, varsayılan genel karşılaştırma performansını küçük yapılandırılmış türleri için en iyisidir; Karşılaştırılan ve sık sıralanmış gereken büyük yapılandırılmış türleri için uygulayın `System.IComparable` ve verimli uygulaması sağlama `System.IComparable.CompareTo()` yöntemi.

`List.sortBy` Sıralama ölçütü kullanılan bir değer döndüren bir işlev alır ve `List.sortWith` bir karşılaştırma işlevi bağımsız değişken olarak alır. Bu ikinci iki işlevleri karşılaştırma desteklemez veya ne zaman karşılaştırma kültür duyarlı dize durumunda olduğu gibi daha karmaşık karşılaştırma semantiği gerektiren türleriyle çalışırken faydalıdır.

Aşağıdaki örnek kullanımını gösteren `List.sort`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

Çıktı aşağıdaki gibidir:

```
[-2; 1; 4; 5; 8]
```

Aşağıdaki örnek kullanımını gösteren `List.sortBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

Çıktı aşağıdaki gibidir:

```
[1; -2; 4; 5; 8]
```

Sonraki örnek kullanımını gösteren `List.sortWith`. Bu örnekte, özel karşılaştırma işlevi `compareWidgets` önce bir alan karşılaştırmak için kullanılan bir özel tür ve ardından başka bir zaman ilk alan değerlerini eşit.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

Çıktı aşağıdaki gibidir:

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>Arama işlemleri listeleri hakkında
Çok sayıda arama işlemleri listeler için desteklenir. Basit, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), verilen bir koşul ile eşleşen ilk öğe bulmanızı sağlar.

Aşağıdaki kod örneğinde kullanımını gösteren `List.find` listesindeki 5 bölünebilir ilk numarasını bulmak için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

Sonuç 5'tir.

Öğeleri ilk dönüştürülmesi çağırır [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), bir işlev, aldığı bir seçenek döndürür ve ilk seçeneği arar değer olan `Some(x)`. Öğesini döndüren yerine `List.pick` sonucunu döndürür `x`. Eşleşen bir öğe bulunursa, `List.pick` oluşturur `System.Collections.Generic.KeyNotFoundException`. Aşağıdaki kod kullanımı gösterilmiştir `List.pick`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

Çıktı aşağıdaki gibidir:

```
"b"
```

Başka bir grup arama işlemlerinin [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) ve ilgili işlevler, bir seçenek değeri döndürür. `List.tryFind` İşlevi döndürür bu tür bir öğe varsa, bir koşulu karşılayan bir listesi, ancak seçenek değeri ilk öğesi `None` değilse. Değişim [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) , öğenin yerine bulunması durumunda öğenin dizinini döndürür. Bu işlevler aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

Çıktı aşağıdaki gibidir:

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Aritmetik işlemler listeleri hakkında
Toplam ve ortalama gibi ortak aritmetik işlemler yerleşik olarak bulunur [List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Çalışmak için [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), liste öğesi türü desteklemelidir `+` işleci ve sıfır değerine sahip. Tüm yerleşik aritmetik türleri bu koşullarını. Çalışmak için [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), öğe türü olan tam sayı türleri dışlar ancak kayan nokta türleri için verir kalan, olmadan bölme desteklemesi gerekir. [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) ve [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) işlevleri işlevi parametre olarak alın ve bu işlevin sonuçları sum veya ortalama için değerleri hesaplamak için kullanılır.

Aşağıdaki kod kullanımını gösteren `List.sum`, `List.sumBy`, ve `List.average`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

Çıktı `1.000000`.

Aşağıdaki kod kullanımı gösterilmiştir `List.averageBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

Çıktı `5.5`.


### <a name="lists-and-tuples"></a>Listeler ve diziler
Tanımlama grupları içeren listeleri zip tarafından yönetilebilir ve işlevleri sıkıştırmasını açın. Bu işlevler listelerini tek değerlerin bir tanımlama grubu listesi birleştirebilir veya bir tanımlama grubu listesi tek değerlerin iki listeye ayırın. En basit [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) işlev iki tek öğelerin listesi alır ve tek bir tanımlama grubu çiftlerinin listesini oluşturur. Başka bir sürümü [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), üç tek öğeleri listesini alır ve tek üç öğeye sahip bir tanımlama grubu listesi oluşturur. Aşağıdaki kod örneğinde kullanımını gösteren `List.zip`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

Çıktı aşağıdaki gibidir:

```
[(1, -1); (2, -2); (3; -3)]
```

Aşağıdaki kod örneğinde kullanımını gösteren `List.zip3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

Çıktı aşağıdaki gibidir:

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

Unzip sürümleri, karşılık gelen [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) ve [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), başlıkların listesini alın ve dönüş listeleri bir tanımlama grubu burada ilk listenin her tanımlama grubu içinde ilk tüm öğeleri içerir ve ikinci liste her tanımlama grubu ve benzeri ikinci öğesini içerir.

Aşağıdaki kod örneğinde kullanımını gösteren [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

Çıktı aşağıdaki gibidir:

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

Aşağıdaki kod örneğinde kullanımını gösteren [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

Çıktı aşağıdaki gibidir:

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Liste öğeleri işletim
F # liste öğeleri üzerinde işlemler, çeşitli destekler. En kolayıdır [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), her bir liste öğesi üzerinde bir işlevi çağırmak sağlar. Çeşitlemeler içerir [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), iki liste öğeleri üzerinde bir işlemi gerçekleştirmenize olanak sağlayan [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), olduğu gibi `List.iter` her öğenin dizini olarak geçirilen dışında bir her öğe için adlı işlevin bağımsız değişkeni ve [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), işlevselliğini bileşimini olduğu `List.iter2` ve `List.iteri`. Aşağıdaki kod örneği, bu işlevler gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

Çıktı aşağıdaki gibidir:

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

Liste öğeleri dönüştüren başka bir sık kullanılan işlev [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), her bir liste öğesi için bir işlev uygulamak ve yeni bir liste olarak tüm sonuçları put sağlar. [List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) ve [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) birden çok listeyi ele Çeşitlemeler şunlardır. Aynı zamanda [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) ve [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), öğenin yanı sıra, işlevi her öğenin dizini geçirilmesi gerekiyorsa. Arasındaki tek fark `List.mapi2` ve `List.mapi` olan `List.mapi2` listelerini ile çalışır. Aşağıdaki örnek gösterilmektedir [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

Çıktı aşağıdaki gibidir:

```
[2; 3; 4]
```

Aşağıdaki örnek kullanımı gösterilmiştir `List.map2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

Çıktı aşağıdaki gibidir:

```
[5; 7; 9]
```

Aşağıdaki örnek kullanımı gösterilmiştir `List.map3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

Çıktı aşağıdaki gibidir:

```
[7; 10; 13]
```

Aşağıdaki örnek kullanımı gösterilmiştir `List.mapi`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

Çıktı aşağıdaki gibidir:

```
[1; 3; 5]
```

Aşağıdaki örnek kullanımı gösterilmiştir `List.mapi2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

Çıktı aşağıdaki gibidir:

```
[0; 7; 18]
```

[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) benzer `List.map`, her öğe bir liste oluşturur ve bu listeleri son listesine birleşir. Aşağıdaki kodda, listedeki her öğeye üç sayı oluşturur. Bunların tümünü tek listede toplanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

Çıktı aşağıdaki gibidir:

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Aynı zamanda [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), bir Boolean koşul alır ve belirtilen koşulu karşılıyor öğeleri içeren yeni bir liste oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

Sonuç listesi `[2; 4; 6]`.

Bir harita ve filtre birleşimi [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) dönüştürme ve öğeleri aynı anda seçmenize olanak sağlar. `List.choose` Her bir liste öğesi için bir seçenek döndürür ve işlev seçenek değeri döndürdüğünde sonuçlar öğeleri için yeni bir listesi döndüren bir işlev uygular `Some`.

Aşağıdaki kod kullanımını gösteren `List.choose` sözcüklerin listesini dışında büyük harfli sözcükleri seçin.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

Çıktı aşağıdaki gibidir:

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Birden çok listelerde işletim
Listeleri birlikte katılabilir. İki liste birine katılmak için kullanmak [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426). İkiden fazla listeleri katılmak için kullanmak [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]
    
### <a name="fold-and-scan-operations"></a>Katlama ve tarama işlemlerini
Bazı listesi işlemleri tüm liste öğelerinin arasındaki bağımlılıkları içerir. Katlama ve tarama işlemlerini gibidir `List.iter` ve `List.map` her öğe üzerinde bir işlevi çağırmak, ancak bu işlemleri adlı ek bir parametre sağlayın, *accumulator* , izleme bilgileri hesaplama.

Kullanım `List.fold` bir listede bir hesaplama gerçekleştirme.

Aşağıdaki kod örneğinde kullanımını gösteren [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) çeşitli işlemleri gerçekleştirmek için.

Listenin geçirildiği; accumulator `acc` hesaplama devam ettikçe boyunca geçirilen bir değerdir. İlk bağımsız değişken accumulator ve liste öğesi alır ve bu liste öğesi için hesaplama geçici sonucunu döndürür. İkinci bağımsız değişkeni accumulator başlangıç değeri.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

İşlev adı bir rakam olması bu işlevlerin sürümleri birden fazla listede çalışır. Örneğin, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) iki listelerde hesaplamalar gerçekleştirir.

Aşağıdaki örnek kullanımını gösteren `List.fold2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold` ve [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) içinde farklı `List.fold` fazladan parametresinin son değeri döndürür ancak `List.scan` fazladan parametresinin (birlikte son değer) Ara değer listesi döndürür.

Örneğin, bu işlevlerin her biri ters değişim içerir [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), farklı sırayla, listenin sonuna ve bağımsız değişkenlerin sırası. Ayrıca, `List.fold` ve `List.foldBack` çeşitlemeleri sahip [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) ve [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), iki liste eşit uzunlukta alın. Her öğe üzerinde yürüten işlev hem listelerinin karşılık gelen öğeleri bazı eylemleri gerçekleştirmek için kullanabilirsiniz. İki liste öğesi türlerini bir liste işlem tutarlarının bir banka hesabı içeren aşağıdaki örnekteki gibi farklı olabilir ve diğer listenin işlem türünü içerir: banka veya mevzuatı.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

Toplama gibi bir hesaplama için `List.fold` ve `List.foldBack` sonucu terabayt geçişi bağlı değildir çünkü aynı etkiye sahiptir. Aşağıdaki örnekte, `List.foldBack` listedeki öğeleri eklemek için kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

Aşağıdaki örnek, banka hesabı örneği döndürür. Bu zaman yeni bir işlem türü eklenir: faiz hesaplama. Bitiş bakiye şimdi terabayt işlemleri bağlıdır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

İşlev [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) bakıma olan `List.fold` ve `List.scan`dışında ayrı accumulator geçici geçirme yerine `List.reduce` yerine öğe türünün iki bağımsız değişken almayan bir işlev alır tek ve bu bağımsız değişkenlerden biri hesaplamanın Ara sonucu depolar anlamı accumulator davranır. `List.reduce` ilk iki liste öğeleri çalıştırılarak başlar ve ardından sonraki öğeye birlikte işleminin sonucu kullanır. Kendi türüne sahip ayrı bir accumulator olmadığından `List.reduce` yerine kullanılabilir `List.fold` yalnızca zaman accumulator ve öğe türü aynı türe sahip. Aşağıdaki kod kullanımını gösteren `List.reduce`. `List.reduce` sağlanan listesini öğe varsa, bir özel durum oluşturur.

Aşağıdaki kodda ilk çağrıda lambda ifadesi bağımsız değişkeni 2 ve 4 verilir ve 6 döndürür ve sonucu 16 nedenle sonraki çağrı bağımsız değişkenleri 6 ve 10 verilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]
    
### <a name="converting-between-lists-and-other-collection-types"></a>Listeler ve diğer koleksiyon türleri arasında dönüştürme
`List` Modülü sıraları ve diziler gelen ve giden dönüştürmek için işlevleri sağlar. İçin veya bir sırasından dönüştürmek için [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) veya [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0). İçin veya bir dizi dönüştürmek için [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) veya [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).


### <a name="additional-operations"></a>Ek işlemleri
Listelerde ek işlemleri hakkında daha fazla bilgi için Kitaplık Başvurusu konusuna [Collections.List Modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).


## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[F# Türleri](fsharp-types.md)

[Diziler](sequences.md)

[Diziler](arrays.md)

[Seçenekler](options.md)

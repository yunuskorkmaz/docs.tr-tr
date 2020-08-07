---
title: Listeler
description: 'Aynı türdeki sıralı, sabit bir öğe serisi olan F # listeleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 236ae77813a3448f159228c5c58d9fe3d024fbd8
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854977"
---
# <a name="lists"></a>Listeler

F # ' daki bir liste, aynı türde olan sıralı, sabit bir öğe serisidir. Listelerde temel işlemleri gerçekleştirmek için, [liste modülündeki](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)işlevleri kullanın.

> [!NOTE]
> F # için docs.microsoft.com API başvurusu tamamlanmadı. Bozuk bağlantılarla karşılaşırsanız, bunun yerine [F # Çekirdek Kitaplığı belgelerine](https://fsharp.github.io/fsharp-core-docs/) başvurun.

## <a name="creating-and-initializing-lists"></a>Liste oluşturma ve başlatma

Aşağıdaki kod satırında gösterildiği gibi, noktalı virgülle ayırarak ve köşeli parantez içine alınmış öğeleri açıkça listeleyerek bir liste tanımlayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Ayrıca, öğelerin arasına satır sonları koyabilirsiniz, bu durumda noktalı virgül isteğe bağlıdır. İkinci sözdizimi, öğe başlatma ifadeleri daha uzun olduğunda veya her öğe için bir açıklama eklemek istediğinizde daha okunabilir kod oluşmasına neden olabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

Normalde, tüm liste öğeleri aynı türde olmalıdır. Bir özel durum, öğelerin temel tür olarak belirtildiği bir listenin türetilmiş tür öğelerine sahip olması olabilir. Bu nedenle, her ikisi `Button` ve `CheckBox` öğesinden türetiğinden aşağıdakiler kabul edilebilir `Control` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Ayrıca `..` , aşağıdaki kodda gösterildiği gibi, Aralık işleci () ile ayrılmış tamsayılar tarafından belirtilen bir aralığı kullanarak liste öğelerini tanımlayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Boş bir liste, aralarında hiçbir şey olmadan köşeli ayraç çifti ile belirtilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Bir liste oluşturmak için bir dizi ifadesi de kullanabilirsiniz. Daha fazla bilgi için bkz. [dizi ifadeleri](sequences.md#sequence-expressions) . Örneğin, aşağıdaki kod, 1 ile 10 arasındaki sayıların karelerinin bir listesini oluşturur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Listelerle çalışma için işleçler

(Cons) işlecini kullanarak bir listeye öğe ekleyebilirsiniz `::` . `list1`İse `[2; 3; 4]` , aşağıdaki kod `list2` olarak oluşturulur `[100; 2; 3; 4]` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Aşağıdaki kodda olduğu gibi işlecini kullanarak uyumlu türleri olan listeleri birleştirebilirsiniz `@` . , `list1` Ve ise, `[2; 3; 4]` `list2` `[100; 2; 3; 4]` Bu kod olarak oluşturulur `list3` `[2; 3; 4; 100; 2; 3; 4]` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

Listelerde işlem gerçekleştirmeye yönelik işlevler, [liste modülünde](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)mevcuttur.

F # içindeki listeler sabit olduğundan, tüm değiştirme işlemleri var olan listeleri değiştirmek yerine yeni listeler oluşturur.

F # içindeki listeler, listedir bağlantılı listeler olarak uygulanır. Bu, yalnızca listenin baş başlarına erişen işlemlerin O (1) ve öğe erişiminin ise O (*n*) olduğu anlamına gelir.

## <a name="properties"></a>Özellikler

Liste türü aşağıdaki özellikleri destekler:

|Özellik|Tür|Açıklama|
|--------|----|-----------|
|[Başlı](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|İlk öğesi.|
|[Olmamalıdır](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|Uygun türdeki boş bir liste döndüren statik özellik.|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true`listede öğe yoksa.|
|[Öğe](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|Belirtilen dizindeki öğe (sıfır tabanlı).|
|[Uzunluk](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|Öğe sayısı.|
|[Kuyruk](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|İlk öğesi olmayan liste.|

Aşağıda bu özellikleri kullanmaya ilişkin bazı örnekler verilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>Listeleri kullanma

Listelerle programlama, az miktarda kodla karmaşık işlemler gerçekleştirmenize olanak sağlar. Bu bölümde, işlevsel programlama için önemli olan listelerle ilgili genel işlemler açıklanmaktadır.

### <a name="recursion-with-lists"></a>Listelerle özyineleme

Listeler özyinelemeli programlama tekniklerine benzersiz bir şekilde uygundur. Listenin her öğesinde gerçekleştirilmesi gereken bir işlem düşünün. Bu işlemi, listenin başından yararlanarak ve sonra listenin kuyruğunu geçirerek, ilk öğe olmayan orijinal listeden oluşan daha küçük bir liste olan bir sonraki özyineleme düzeyine geri dönerek yapabilirsiniz.

Bu tür bir özyinelemeli işlevi yazmak için, `::` bir listenin başını bir kuyruklu ayırmanızı sağlayan, model eşleme içinde Cons işlecini () kullanın.

Aşağıdaki kod örneği, bir liste üzerinde işlemler gerçekleştiren özyinelemeli bir işlevi uygulamak için nasıl model eşleştirmesinin kullanılacağını göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Önceki kod küçük listeler için iyi sonuç verir, ancak daha büyük listeler için yığın taşar. Aşağıdaki kod, özyinelemeli işlevlerle çalışmaya yönelik standart bir yöntem olan bir biriktirici bağımsız değişkeni kullanarak bu kodda gelişir. Biriktiricidir bağımsız değişkeninin kullanılması, yığın alanı kaydeden işlev kuyruklu özyinelemeli olur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

İşlevi, `RemoveAllMultiples` iki liste alan özyinelemeli bir işlevdir. İlk liste, katları kaldırılacak olan sayıları ve ikinci liste ise sayıların kaldırılacağı liste olduğunu içerir. Aşağıdaki örnekteki kod, bu özyinelemeli işlevi bir listeden tüm asal olmayan sayıları ortadan kaldırmak için kullanır ve sonuç olarak asal sayıların bir listesini bırakır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Modül Işlevleri

[Liste modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) , bir listenin öğelerine erişen işlevler sağlar. Baş öğe, erişimin en hızlı ve en kolay yoludur. Özellik [kafasını](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) veya [List. Head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2)modül işlevini kullanın. [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) özelliğini veya [List. tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) işlevini kullanarak bir listenin kuyruğunu erişebilirsiniz. Dizine göre bir öğe bulmak için [List. nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) işlevini kullanın. `List.nth`listede yer geçer. Bu nedenle, O (*n*). Kodunuz `List.nth` sıklıkla kullanılıyorsa, bir liste yerine bir dizi kullanmayı düşünmek isteyebilirsiniz. Dizilerde öğe erişimi O (1).

### <a name="boolean-operations-on-lists"></a>Listelerde Boole Işlemleri

[List. IsEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) işlevi bir listenin herhangi bir öğeye sahip olup olmadığını belirler.

[List. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) işlevi bir listenin öğelerine Boole testi uygular ve `true` herhangi bir öğe, testi karşılıyorsa döndürür. [List. exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) benzerdir ancak iki listede ardışık öğe çiftlerinde çalışır.

Aşağıdaki kod öğesinin kullanımını gösterir `List.exists` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
For list [0; 1; 2; 3], contains zero is true
```

Aşağıdaki örnek öğesinin kullanımını gösterir `List.exists2` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

List [. forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) ' i kullanarak bir listedeki tüm öğelerin bir koşula uyup uymadığını test etmek istiyorsanız.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
true
false
```

Benzer şekilde, [List. forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) , iki liste içindeki karşılık gelen konumlarda bulunan tüm öğelerin her bir öğe çiftini Içeren bir Boolean ifade karşılayıp karşılamadığını belirler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
true
false
```

### <a name="sort-operations-on-lists"></a>Listelerde sıralama Işlemleri

[List. Sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List. sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)ve [List. sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) işlevleri sıralama listeleri. Sıralama işlevi, bu üç işlevden hangisini kullanacağınızı belirler. `List.sort`Varsayılan genel karşılaştırmayı kullanır. Genel karşılaştırma, değerleri karşılaştırmak için genel karşılaştırma işlevini temel alan genel işleçleri kullanır. Basit sayısal türler, tanımlama grupları, kayıtlar, ayırt edici birleşimler, listeler, diziler ve uygulayan herhangi bir tür gibi çok sayıda öğe türü ile verimli bir şekilde çalışmaktadır `System.IComparable` . Uygulayan türler için `System.IComparable` , genel karşılaştırma `System.IComparable.CompareTo()` işlevini kullanır. Genel karşılaştırma dizelerle de birlikte çalışarak, ancak kültüre bağımsız bir sıralama düzeni kullanır. Genel karşılaştırma, işlev türleri gibi desteklenmeyen türlerde kullanılmamalıdır. Ayrıca, varsayılan genel karşılaştırmanın performansı, küçük yapılandırılmış türler için en iyisidir; sıklıkla karşılaştırılması ve sıralanması gereken daha büyük yapılandırılmış türler için, `System.IComparable` yöntemini uygulamayı ve verimli bir uygulama sağlamayı düşünün `System.IComparable.CompareTo()` .

`List.sortBy`sıralama ölçütü olarak kullanılan bir değer döndüren bir işlev alır ve bir `List.sortWith` karşılaştırma işlevini bağımsız değişken olarak alır. Bu ikinci iki işlev, karşılaştırmayı desteklemeyen türlerle çalışırken ya da karşılaştırma, kültüre duyarlı dizeler söz konusu olduğunda olduğu gibi daha karmaşık karşılaştırma semantiği gerektirdiğinde yararlıdır.

Aşağıdaki örnek öğesinin kullanımını gösterir `List.sort` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[-2; 1; 4; 5; 8]
```

Aşağıdaki örnek öğesinin kullanımını gösterir `List.sortBy` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[1; -2; 4; 5; 8]
```

Sonraki örnek öğesinin kullanımını gösterir `List.sortWith` . Bu örnekte, özel karşılaştırma işlevi öncelikle bir `compareWidgets` özel türün bir alanını ve ardından ilk alanın değerleri eşitse başka bir değeri karşılaştırmak için kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>Listelerde arama Işlemleri

Listeler için çok sayıda arama işlemi desteklenir. En basit, [List. Find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), belirli bir koşulla eşleşen ilk öğeyi bulmanızı sağlar.

Aşağıdaki kod örneği, `List.find` bir listede 5 ' e bölünebilen ilk sayıyı bulmak için kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

Sonuç 5 ' tir.

Öğelerin önce dönüştürülmesi gerekiyorsa, bir seçenek döndüren bir işlevi alan [List. Pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2)çağırın ve olan ilk seçenek değerini arar `Some(x)` . Öğesini döndürmek yerine `List.pick` sonucunu döndürür `x` . Eşleşen bir öğe bulunamazsa, `List.pick` oluşturur `System.Collections.Generic.KeyNotFoundException` . Aşağıdaki kod öğesinin kullanımını gösterir `List.pick` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
"b"
```

Başka bir arama işlemleri grubu olan [List. tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) ve related işlevleri, bir seçenek değeri döndürür. İşlevi, böyle bir öğe varsa bir `List.tryFind` koşulu karşılayan bir listenin ilk öğesini döndürür, ancak değilse seçenek değeri `None` . Çeşitleme [listesi. tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) , öğenin kendisi yerine, varsa, öğesinin dizinini döndürür. Bu işlevler aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Listelerde aritmetik Işlemler

Toplam ve ortalama gibi yaygın aritmetik işlemler [liste modülüne](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)yerleştirilmiştir. [List. Sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9)ile çalışmak için liste öğesi türü `+` işleci desteklemelidir ve sıfır değerine sahip olmalıdır. Tüm yerleşik aritmetik türler bu koşulları karşılar. [List. Average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1)ile çalışmak için, öğe türü, bir geri kalanı olmadan bir bölüm desteklemelidir, bu da integral türlerini dışlar, ancak kayan nokta türlerine izin verir. [List. sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) ve [List. averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) işlevleri bir işlevi parametre olarak alır ve bu işlevin sonuçları Sum veya Average değerlerini hesaplamak için kullanılır.

Aşağıdaki kod,, ve kullanımını gösterir `List.sum` `List.sumBy` `List.average` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

Çıktı `1.000000` .

Aşağıdaki kod öğesinin kullanımını gösterir `List.averageBy` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

Çıktı `5.5` .

### <a name="lists-and-tuples"></a>Listeler ve tanımlama grupları

Tanımlama gruplarını içeren listeler, zip ve unzip işlevleri tarafından değiştirilebilir. Bu işlevler, tek değerlerden oluşan iki listeyi tek bir tanımlama grubu içinde birleştirir veya bir tanımlama grubu listesini tek değerlerden oluşan iki listeye ayırır. En basit [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) işlevi, tek öğelerin iki listesini alır ve dizi kümesi çiftlerinin tek bir listesini oluşturur. Farklı bir sürüm olan [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), tek öğelerin üç listesini alır ve üç öğesi olan bir tanımlama grubu listesi oluşturur. Aşağıdaki kod örneği öğesinin kullanımını gösterir `List.zip` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[(1, -1); (2, -2); (3; -3)]
```

Aşağıdaki kod örneği öğesinin kullanımını gösterir `List.zip3` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

Karşılık gelen unzip sürümleri, [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) ve [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), tanımlama grubu ve dönüş listelerinin listesini alır, burada ilk liste her bir tanımlama grubunda ilk olan tüm öğeleri içerir ve ikinci liste her bir tanımlama grubunun ikinci öğesini içerir ve bu şekilde devam eder.

Aşağıdaki kod örneği [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)öğesinin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

Aşağıdaki kod örneği [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Liste öğelerinde çalışma

F #, liste öğelerinde çeşitli işlemleri destekler. Listenin her öğesinde bir işlevi çağırmanızı sağlayan en basit [List. iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f). Her bir öğenin dizininin her öğe için çağrılan işleve bir bağımsız değişken olarak geçirilmesi ve ve işlevlerinin bir birleşimi [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60)olan List. iteri2 ' yi, bu iki listenin öğelerinde bir işlem gerçekleştirmenize olanak sağlayan varyasyonlar Include [List. iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40) `List.iter` [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c) `List.iter2` `List.iteri` . Aşağıdaki kod örneği bu işlevleri gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
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

Liste öğelerini dönüştüren başka bir sık kullanılan işlev List [. Map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)olur ve bu, bir listedeki her öğeye bir işlev uygulamanıza ve tüm sonuçların yeni bir listeye yerleştirmenize olanak sağlar. [List. map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) ve [List. map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) birden çok liste alan değişimlerdir. [List. mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) ve [List. mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49)öğesini de kullanabilirsiniz. Buna ek olarak, işlevine her öğenin dizinini geçirilmesi gerekir. Ve arasındaki tek fark `List.mapi2` , `List.mapi` `List.mapi2` iki liste ile birlikte çalışmadır. Aşağıdaki örnekte [List. Map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[2; 3; 4]
```

Aşağıdaki örnek öğesinin kullanımını gösterir `List.map2` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[5; 7; 9]
```

Aşağıdaki örnek öğesinin kullanımını gösterir `List.map3` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[7; 10; 13]
```

Aşağıdaki örnek öğesinin kullanımını gösterir `List.mapi` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[1; 3; 5]
```

Aşağıdaki örnek öğesinin kullanımını gösterir `List.mapi2` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[0; 7; 18]
```

[List. Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) , `List.map` her öğe bir liste ürettiğinden ve tüm bu listelerin son bir liste ile bitiştirildiği durumlar haricinde gibidir. Aşağıdaki kodda, listenin her bir öğesi üç sayı üretir. Bunların hepsi tek bir listede toplanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Ayrıca, Boolean koşulunu alan ve yalnızca verilen koşulu karşılayan öğelerden oluşan yeni bir liste üreten [List. Filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248)öğesini de kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

Elde edilen liste `[2; 4; 6]` .

Map ve Filter, [List.](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) Select birleşimi, öğeleri aynı anda dönüştürmenizi ve seçmenizi sağlar. `List.choose`bir listedeki her öğeye bir seçenek döndüren bir işlev uygular ve işlev seçenek değerini döndürdüğünde öğelerin sonuçlarının yeni bir listesini döndürür `Some` .

Aşağıdaki kod, `List.choose` bir sözcük listesinden büyük harfli sözcükler seçmek için kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Birden çok liste üzerinde çalışma

Listeler birlikte birleştirilebilir. İki listeyi tek tek birleştirmek için [List. Append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426)kullanın. İkiden fazla listeyi birleştirmek için [List. Concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c)kullanın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Katlama ve tarama Işlemleri

Bazı liste işlemleri liste öğeleri arasında bağımlılıkları kapsar. Katlama ve tarama işlemleri, `List.iter` `List.map` her öğe üzerinde bir işlevi çağırmanıza benzer ancak bu işlemler, hesaplama aracılığıyla bilgi taşıyan bir ek parametre sağlar. *accumulator*

`List.fold`Bir liste üzerinde hesaplama gerçekleştirmek için kullanın.

Aşağıdaki kod örneği, çeşitli işlemleri gerçekleştirmek için [List. Fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) öğesinin kullanımını gösterir.

Listeye çapraz ve Biriktirici, `acc` Hesaplama ilerledikçe geçen bir değerdir. İlk bağımsız değişken, biriktiriciden ve List öğesini alır ve bu liste öğesi için hesaplamanın ara sonucunu döndürür. İkinci bağımsız değişken, biriktiricinin ilk değeridir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

İşlev adında basamak olan bu işlevlerin sürümleri birden fazla listede çalışır. Örneğin, [List. fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) iki listede hesaplamalar gerçekleştirir.

Aşağıdaki örnek öğesinin kullanımını gösterir `List.fold2` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold`ve [List. Scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) , `List.fold` ek parametrenin son değerini döndüren ' de farklılık gösterir, ancak `List.scan` ek parametrenin ara değerlerinin (son değeri ile birlikte) listesini döndürür.

Bu işlevlerin her biri, listenin geri alındığı sırada ve bağımsız değişkenlerin sırası farklı olan [List. foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7)gibi bir ters çeşitleme içerir. Ayrıca, `List.fold` ve aynı `List.foldBack` uzunlukta iki liste alan Çeşitlemeler, [List. fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) ve [List. foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2)' i de vardır. Her öğe üzerinde yürütülen işlev, bazı eylemler gerçekleştirmek için her iki listedeki ilgili öğeleri kullanabilir. Aşağıdaki örnekte olduğu gibi, iki listenin öğe türleri farklı olabilir. Bu, bir liste bir banka hesabı için işlem tutarlarını içerir ve diğer liste işlemin türünü içerir: depozito veya çekme al.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

Toplama gibi bir hesaplama için, `List.fold` `List.foldBack` sonuç çapraz geçiş sırasına bağlı olmadığından aynı etkiye sahiptir. Aşağıdaki örnekte, `List.foldBack` bir listedeki öğeleri eklemek için kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

Aşağıdaki örnek, banka hesabı örneğine geri döner. Yeni bir işlem türü eklendiğinde bu kez bir vade farkının hesaplanması. Bitiş bakiyesi artık işlem sırasına bağlıdır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

İşlev [listesi. küçültme](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) biraz benzer ve aynı şekilde, `List.fold` `List.scan` ayrı bir Biriktiricinin etrafında geçiş yerine `List.reduce` iki bağımsız değişken alan bir işlev alır, ancak bu bağımsız değişkenlerden biri yalnızca bir değil, bu bağımsız değişkenlerden biri de, hesaplamanın ara sonucunu depoladığı anlamına gelir. `List.reduce`ilk iki liste öğesinde çalışmaya başlar ve sonra işlemin sonucunu Next öğesiyle birlikte kullanır. Kendi türüne sahip ayrı bir biriktiricidir çünkü, `List.reduce` `List.fold` yalnızca biriktiricidir ve öğe türü aynı türde olduğunda ' nin yerine kullanılabilir. Aşağıdaki kod öğesinin kullanımını gösterir `List.reduce` . `List.reduce`Belirtilen listede öğe yoksa bir özel durum oluşturur.

Aşağıdaki kodda, lambda ifadesine yapılan ilk çağrıya 2 ve 4 bağımsız değişkenleri verilir ve 6, sonraki çağrıya ise 6 ve 10 bağımsız değişkenleri verilir, dolayısıyla sonuç 16 ' dır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>Listeler ve diğer koleksiyon türleri arasında dönüştürme

`List`Modülü, hem sıralara hem de dizilere dönüştürme için işlevler sağlar. Bir diziye veya bir diziye dönüştürmek için [List. toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) veya [List. ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0)kullanın. Bir diziye veya bir diziyi dönüştürmek için [List. ToArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) veya [List. ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032)kullanın.

### <a name="additional-operations"></a>Ek Işlemler

Listelerle ilgili ek işlemler hakkında daha fazla bilgi için bkz. kitaplık başvurusu konu [koleksiyonları. List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [F# Türleri](fsharp-types.md)
- [Diziler](sequences.md)
- [Diziler](arrays.md)
- [Seçenekler](options.md)

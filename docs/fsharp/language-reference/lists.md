---
title: Listeler
description: Hakkında bilgi edinin F# listeler, öğeleri aynı türde sıralı, sabit bir dizi.
ms.date: 05/16/2016
ms.openlocfilehash: cc4e292280cca0dca37f69cf5a46ec2822d08d5c
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656342"
---
# <a name="lists"></a>Listeler

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları için MSDN sürer.  Docs.microsoft.com API başvuru tamamlanmadı.

Bir listede F# öğeleri aynı türde sıralı, sabit bir dizi. Listeler temel işlemleri gerçekleştirmek için işlevleri kullanmak [List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

## <a name="creating-and-initializing-lists"></a>Oluşturma ve başlatma listeler

Bir liste öğeleri noktalı virgülle ayrılmış ve kod aşağıdaki satırda gösterildiği gibi köşeli parantezler içinde out açıkça listeleyerek tanımlayabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Satır sonları öğeler arasındaki de koyabilirsiniz, bu durumda noktalı virgül isteğe bağlıdır. İkinci sözdizimi daha okunabilir bir kod öğesi başlatma ifadeleri uzun olduğunda ya da her öğe için bir açıklama eklemek istediğiniz neden olabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

Normalde, tüm liste öğeleri aynı türde olmalıdır. Öğeleri olan öğeler bir taban türü olmasını sağlayabilirsiniz belirtilir listesini türetilmiş bir özel durumdur. Aşağıdaki kabul edilebilir, bu nedenle çünkü her ikisi de `Button` ve `CheckBox` öğesinden türetilen `Control`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Aralık işleci tarafından ayrılmış tamsayı tarafından gösterilen bir aralık kullanarak liste öğelerini de tanımlayabilirsiniz (`..`), aşağıdaki kodda gösterildiği gibi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Boş bir liste, bir çift köşeli ayraç ile bunların arasında bir şey tarafından belirtilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Bir sıralama ifadesi, bir liste oluşturmak için de kullanabilirsiniz. Bkz: [Sequence ifadeleri](sequences.md#sequence-expressions) daha fazla bilgi için. Örneğin, aşağıdaki kod, tamsayılar kareler listesini 1'den 10'a oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Listelerle çalışmak için işleçleri

Kullanarak liste öğelerini ekleyebilirsiniz `::` (olumsuz) işleci. Varsa `list1` olduğu `[2; 3; 4]`, aşağıdaki kod oluşturur `list2` olarak `[100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Kullanarak uyumlu türleri olan listeleri bitiştirebilirsiniz `@` işleci, aşağıdaki kodda gösterildiği gibi. Varsa `list1` olduğu `[2; 3; 4]` ve `list2` olduğu `[100; 2; 3; 4]`, bu kod oluşturur `list3` olarak `[2; 3; 4; 100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

Liste işlemleri gerçekleştirmek için işlevleri kullanılabilir [List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

Çünkü listeler F# olan herhangi bir değiştirme işlemi varolan listelerini değiştirmek yerine yeni listeleri oluşturmak, değişmez.

Listeler F# yalnızca listenin başındaki erişen işlemler: O(1) ve O öğe erişimi olan tek bağlantılı liste olarak uygulanır (*n*).

## <a name="properties"></a>Özellikler

Liste türü, aşağıdaki özellikleri destekler:

|Özellik|Tür|Açıklama|
|--------|----|-----------|
|[HEAD](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|İlk öğe.|
|[boş](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|Bir statik özellik uygun türde boş bir liste döndürür.|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true` listeye öğe varsa.|
|[Öğesi](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|(Sıfır tabanlı) belirtilen dizindeki öğe.|
|[Uzunluğu](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|Öğe sayısı.|
|[Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|İlk öğe olmadan listesi.|

Bu özellikler kullanmanın bazı örnekler aşağıda verilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>Listeleri kullanma

Programlama listeleriyle karmaşık işlemleri az miktarda kod ile sağlar. Bu bölümde, işlevsel programlama için önemli olan listelerde yaygın işlemleri açıklanmaktadır.

### <a name="recursion-with-lists"></a>Özyineleme listeleri

Listeleri için yinelemeli teknikler programlama benzersiz olarak uygundur. Her bir liste öğesi üzerinde gerçekleştirilen bir işlem göz önünde bulundurun. Listenin başındaki üzerinde çalışan ve ardından özgün listedeki ilk öğe olmadan oluşan küçük bir listedir listenin sonu geçirerek bu yinelemeli olarak yapın, özyineleme sonraki düzeye yeniden.

Böyle bir özyinelemeli işlevi yazmak için simgeler işlecini kullanın (`::`) desen eşleştirme içinde sağlayan tail listesini baş ayırmak.

Aşağıdaki kod örneği, bir liste işlemleri gerçekleştiren bir özyinelemeli işlev uygulamak için desen eşleştirme kullan gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Önceki kodun küçük listeler için iyi çalışır, ancak daha büyük listeler için yığın taşması. Aşağıdaki kod, accumulator bağımsız değişken, özyinelemeli işlevler ile çalışmak için standart bir yöntemi kullanarak bu kodu geliştirir. Yığın alanı kaydeder işlevi tail özyinelemeli accumulator bağımsız değişken kullanımı sağlar.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

İşlev `RemoveAllMultiples` iki liste götüren bir özyinelemeli işlevdir. İlk liste, katları kaldırılacak sayıları içeren ve ikinci listesi sayıları kaldırılacağı listesidir. Aşağıdaki örnek kodda, tüm olmayan-asal sayıları asal sayıları listesini sonucu olarak bırakarak listeden ortadan kaldırmak için bu özyinelemeli işlev kullanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Modül işlevleri

[List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) liste öğelerini erişim işlevleri sunar. Head öğesi, en hızlı ve kolay erişim ' dir. Özelliğini kullanın [baş](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) veya modül işlevi [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2). Kuyruk listesini kullanarak erişebileceğiniz [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) özelliği veya [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) işlevi. Dizine göre bir öğeyi bulmak için kullanın [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) işlevi. `List.nth` Listeyi dikkatle inceler. Bu nedenle, O olduğu (*n*). Kodunuzu kullanıyorsa `List.nth` sıklıkla bir dizi yerine bir liste kullanarak düşünmek isteyebilirsiniz. Öğe erişimi, diziler O(1) ' dir.

### <a name="boolean-operations-on-lists"></a>Boole işlemlerini listeler

[List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) işlevi, bir liste herhangi bir öğe olup olmadığını belirler.

[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) işlevi geçerli bir Boolean test listesini döndürür ve öğelerine `true` herhangi bir öğeyi test karşılıyorsa. [List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) benzer, ancak iki listelerindeki öğelerin art arda gelen çiftlerini çalışır.

Aşağıdaki kod kullanımını gösterir `List.exists`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
For list [0; 1; 2; 3], contains zero is true
```

Aşağıdaki örnek, kullanımını gösterir `List.exists2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

Kullanabileceğiniz [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) tüm liste öğelerinin bir koşulu karşılayıp karşılamadığını sınamak istiyorsanız.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
true
false
```

Benzer şekilde, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) karşılık gelen konumlarda iki listelerindeki tüm öğeleri içeren her bir öğe çiftinin bir Boole ifadesi uygun olup olmadığını belirler.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
true
false
```

### <a name="sort-operations-on-lists"></a>Sıralama işlemleri listeler

[List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), ve [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) işlevleri sıralama listeler. Sıralama işlevini kullanmak için bu üç işlevlerin belirler. `List.sort` Varsayılan genel karşılaştırma kullanır. Genel karşılaştırma genel karşılaştırma işleve göre genel işleçleri, değerleri karşılaştırmak için kullanır. Çok çeşitli gibi basit sayısal türler, diziler, kayıtları, ayrılmış birleşimler, listeler, diziler ve uygulayan herhangi bir tür öğe türleri ile verimli bir şekilde çalışır `System.IComparable`. Türleri uygulayan `System.IComparable`, genel karşılaştırma kullanır `System.IComparable.CompareTo()` işlevi. Genel karşılaştırma ayrıca dizeleri ile çalışır, ancak kültüre bağlı bir sıralama düzeni kullanır. Genel karşılaştırma işlevini türleri gibi desteklenmeyen türler üzerinde kullanılmamalıdır. Ayrıca, varsayılan genel karşılaştırma performansını küçük yapılandırılmış türleri için en iyi seçenektir; Karşılaştırma ve sık sıralanmış gereken büyük yapılandırılmış türleri için uygulamayı düşünün `System.IComparable` verimli uygulaması sağlayarak `System.IComparable.CompareTo()` yöntemi.

`List.sortBy` Sıralama ölçütü kullanılan bir değer döndüren bir işlev alır ve `List.sortWith` bir karşılaştırma işlevi bağımsız değişken olarak alır. Bu ikinci iki İşlevler, karşılaştırma desteklemez veya karşılaştırma kültüre duyarlı dize olduğu gibi daha karmaşık karşılaştırma semantiği gerektirdiğinde türleriyle çalışırken yararlıdır.

Aşağıdaki örnek, kullanımını gösterir `List.sort`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[-2; 1; 4; 5; 8]
```

Aşağıdaki örnek, kullanımını gösterir `List.sortBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[1; -2; 4; 5; 8]
```

Sonraki örnek, kullanımını gösterir `List.sortWith`. Bu örnekte, özel bir karşılaştırma işlevi `compareWidgets` önce bir alan karşılaştırmak için kullanılan özel bir tür ve başka bir zaman ilk alan değerlerini eşit.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>Listelerde arama işlemleri

Çok sayıda arama işlemleri listeler için desteklenir. Basit, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), belirli bir koşul ile eşleşen ilk öğe bulmanızı sağlar.

Aşağıdaki kod örneği, kullanımını gösterir `List.find` bölünebilir 5 listedeki ilk numarası bulunamadı.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

Sonuç 5'tir.

İlk öğeleri dönüştürülür, çağrı [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), bir işlev, alan bir seçenek verir ve ilk seçenek arar değeri olan `Some(x)`. Öğe döndürmek yerine `List.pick` sonucunu döndürür `x`. Eşleşen hiçbir öğe bulunamazsa `List.pick` oluşturur `System.Collections.Generic.KeyNotFoundException`. Aşağıdaki kod kullanımını gösterir `List.pick`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
"b"
```

Arama işlemleri, başka bir grup [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) ve ilgili işlevleri, bir seçenek değerini döndürür. `List.tryFind` İşlevi bu tür bir öğe varsa bir koşulu karşılayan bir liste, ancak seçenek değeri ilk öğeyi döndürür `None` Aksi takdirde. Değişim [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) , öğenin yerine bulunması durumunda, öğenin dizinini döndürür. Bu işlevler, aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Aritmetik işlemler listesi

Toplam ve ortalama gibi yaygın aritmetik işlemleri yerleşik olarak [List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Çalışmak için [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), liste öğesi türünü desteklemelidir `+` işleci ve sıfır değerine sahip. Tüm yerleşik aritmetik türler bu koşulları karşılayan. Çalışmak için [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), öğe türü olmadan tam sayı türleri dışlar ancak kayan nokta türleri için sağlayan bir geri kalan bölümü desteklemesi gerekir. [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) ve [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) işlevler bir işlev bir parametre olarak alır ve bu işlevin sonuçlarını Topla veya ortalama değerleri hesaplamak için kullanılır.

Aşağıdaki kod kullanımını gösterir `List.sum`, `List.sumBy`, ve `List.average`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

Çıktı `1.000000`.

Aşağıdaki kod kullanımını gösterir `List.averageBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

Çıktı `5.5`.

### <a name="lists-and-tuples"></a>Listeler ve diziler

Diziler içeren listeleri zip tarafından yönetilebilir ve işlevleri sıkıştırmasını açın. Bu işlevler, iki tek değerler listesi bir tanımlama grubu listesine birleştirebilir veya listelerini tek değerler bir diziler listesi ayırın. En basit [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) işlevi iki tek öğeleri listesini alır ve tek bir kayıt düzeni çiftlerinin listesini oluşturur. Başka bir sürümü [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), üç tek öğeleri listesini alır ve üç öğe içeren demetler tek bir listesini oluşturur. Aşağıdaki kod örneği, kullanımını gösterir `List.zip`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[(1, -1); (2, -2); (3; -3)]
```

Aşağıdaki kod örneği, kullanımını gösterir `List.zip3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

Unzip sürümleri, buna karşılık gelen [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) ve [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), tanımlama gruplarının listesini alan ve getiren listeleri bir tanımlama grubu burada ilk liste her bir tanımlama grubunu ilk tüm öğeleri içeren ve ikinci liste, her tanımlama grubu ve benzeri ikinci öğe içerir.

Aşağıdaki kod örneği, kullanımını gösterir [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

Aşağıdaki kod örneği, kullanımını gösterir [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Liste öğeleri üzerinde çalıştırma

F#liste öğeleri üzerinde işlemler çeşitli destekler. En basit olan [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), listesini her bir öğede bir işlev çağrısı sağlar. Çeşitlemeler içerir [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), iki listenin öğelerini bir işlem yapmanıza olanak sağlayan [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), olduğu gibi `List.iter` dışında her öğenin dizini olarak geçirilen bir her öğe için çağrılan işlev için bağımsız değişken ve [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), işlevselliğinin bir birleşimi olan `List.iter2` ve `List.iteri`. Aşağıdaki kod örneği, bu işlevler gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

Çıktı aşağıdaki şekilde olacaktır:

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

Liste öğeleri dönüştüren başka bir sık kullanılan işlev [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), her bir liste öğesine bir işlev uygulamak ve tüm sonuçları yeni bir liste olarak yerleştirmek sağlar. [List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) ve [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) birden çok listelerini Al farklılıklar şunlardır. Ayrıca [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) ve [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), öğe ek olarak, her öğenin dizinini geçirilecek işlevi gerekiyorsa. Arasındaki tek fark `List.mapi2` ve `List.mapi` olan `List.mapi2` iki liste ile çalışır. Aşağıdaki örnekte gösterilmiştir [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[2; 3; 4]
```

Aşağıdaki örnek kullanımını gösterir `List.map2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[5; 7; 9]
```

Aşağıdaki örnek kullanımını gösterir `List.map3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[7; 10; 13]
```

Aşağıdaki örnek kullanımını gösterir `List.mapi`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[1; 3; 5]
```

Aşağıdaki örnek kullanımını gösterir `List.mapi2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[0; 7; 18]
```

[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) benzer `List.map`, her öğe bir liste oluşturur ve bu listeler, son bir liste olarak bitiştirilir. Aşağıdaki kodda, listenin her öğesinin üç sayı oluşturur. Bunların tümünü tek listede toplanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Ayrıca [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), bir Boolean koşulu alır ve belirtilen koşulu karşılayan öğeleri içeren yeni bir liste oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

Sonuç listesi `[2; 4; 6]`.

Bir harita ve filtresi bileşimi [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) , dönüştürme ve aynı anda öğeleri seçmek sağlar. `List.choose` bir seçenek listesini her öğeye döndürür ve işlevin seçenek değeri döndürüldüğünde yeni bir öğe için sonuçları listesi döndüren bir işlev uygular `Some`.

Aşağıdaki kod kullanımını gösterir `List.choose` büyük harfli bir sözcük dışında bir kelimelerin listesini seçin.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Birden çok listelerde çalışma

Listeleri birlikte katılabilir. İki liste birine katılmak için kullanın [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426). İkiden fazla listeleri katılmak için kullanın [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Katlama ve tarama işlemleri

Tüm liste öğelerinin birbirine bazı listeleme işlemleri içerir. Katlama ve tarama işlemlerini gibidir `List.iter` ve `List.map` her öğe üzerinde bir işlevi çağırır, ancak bu işlemler adlı ek bir parametre sağlayın, *accumulator* , izleme bilgileri hesaplama.

Kullanım `List.fold` bir listede bir hesaplama gerçekleştirmek için.

Aşağıdaki kod örneği, kullanımını gösterir [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) çeşitli işlemler gerçekleştirmek için.

Listenin sonuna; accumulator `acc` hesaplama devam ettikçe boyunca geçirilen bir değerdir. İlk bağımsız değişken accumulator ve liste öğesi alır ve bu liste öğesi için hesaplama geçiş sonucunu döndürür. İkinci bağımsız değişkeni accumulator ilk değeridir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

İşlev adı bir basamak sahip bu işlevlerin sürümleri, birden fazla listede çalışır. Örneğin, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) iki liste üzerinde hesaplamalar gerçekleştirir.

Aşağıdaki örnek, kullanımını gösterir `List.fold2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold` ve [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) içinde farklı `List.fold` ek parametresinin son değeri döndürür, ancak `List.scan` ekstra parametresiyle Ara değerlerini (birlikte, son değer) listesini döndürür.

Örneğin, bu işlevlerin her biri bir ters değişim içerir [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), sırayla farklıdır, listenin sonuna ve bağımsız değişkenlerin sırası. Ayrıca, `List.fold` ve `List.foldBack` farklılıkları, sahip [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) ve [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), eşit uzunluktaki iki liste alır. Her bir öğede yürüten işlev karşılık gelen öğelerle iki listelerin bazı eylemleri gerçekleştirmek için kullanabilirsiniz. İki liste öğesi türlerinin bir listesi bir banka hesabı işlem tutarlarını içerir aşağıdaki örnekte olduğu gibi farklı olabilir ve diğer liste işlem türü bulunur: havale veya mevzuatı.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

Toplama gibi bir hesaplama `List.fold` ve `List.foldBack` sonucu bazında geçişi bağımlı değildir çünkü aynı etkiye sahiptir. Aşağıdaki örnekte, `List.foldBack` bir listedeki öğeleri eklemek için kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

Aşağıdaki örnek, banka hesabı örneği döndürür. Yeni bir işlem türü eklendiğinde bu süre: bir ilgi hesaplaması. Bitiş bakiyesi bazında işlemleri artık bağlıdır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

İşlev [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) bakıma olan `List.fold` ve `List.scan`dışında ayrı bir accumulator etrafında geçirmek yerine `List.reduce` yerine öğe türünün iki bağımsız değişken alan bir işlev alır Bu bağımsız değişkenlerden biri yanı sıra tek bir hesaplama Ara sonuçlarını saklar anlamı accumulator görev yapar. `List.reduce` ilk iki liste öğeleri üzerinde çalıştırılarak başlatılır ve ardından sonraki öğeye yanı sıra işleminin sonucu kullanır. Kendi türüne sahip ayrı bir accumulator olmadığından `List.reduce` yerine kullanılan `List.fold` yalnızca accumulator ve dizinin öğe türü aynı türe sahip olduğunda. Aşağıdaki kod kullanımını gösterir `List.reduce`. `List.reduce` sağlanan listesini hiçbir öğe içermeyen bir özel durum oluşturur.

Aşağıdaki kodda, ilk çağrı lambda ifadesine bağımsız değişkenleri 2 ve 4 verilir ve 6 döndürür ve 16 sonucu, bu nedenle sonraki çağrı bağımsız değişkenleri 6 ve 10 verilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>Listeler ve diğer toplama türleri arasında dönüştürme

`List` Modülü ve dizileri hem dizileri Bu nesnelerden dönüştürme için işlevler sağlar. İçin veya bir dizi dönüştürmek için [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) veya [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0). İçin veya bir diziden dönüştürmek için [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) veya [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).

### <a name="additional-operations"></a>Ek işlemler

Listeleri üzerinde ek işlemler hakkında daha fazla bilgi için Kitaplık Başvurusu konusuna [Collections.List Modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [F# Türleri](fsharp-types.md)
- [Diziler](sequences.md)
- [Diziler](arrays.md)
- [Seçenekler](options.md)

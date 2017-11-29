---
title: Diziler (F#)
description: "Oluşturma ve diziler F # programlama dilini kullanma hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 61fa9084-abdc-4cf5-8213-91ec1211866b
ms.openlocfilehash: 7c9d8405230f4d765d3afdeaa154ddc598d0d1ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="arrays"></a>Diziler

> [!NOTE]
API başvuru bağlantısı sizi MSDN'ye götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

Diziler, ardışık veri öğelerinin tümü aynı türde sabit boyutlu, sıfır tabanlı, değişebilir koleksiyonlarıdır.

## <a name="creating-arrays"></a>Diziler oluşturma
Diziler çeşitli yollarla oluşturabilirsiniz. Küçük bir dizi ardışık değerler arasında listeleyerek oluşturabileceğiniz `[|` ve `|]` ve aşağıdaki örneklerde gösterildiği gibi noktalı virgülle ayırarak.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

Bu gibi durumlarda, her öğe Ayrıca isteğe bağlı durumda noktalı virgül ayırıcısını ayrı bir satırda koyabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

Dizi öğelerin türü kullanılan değişmez değerleri algılanır ve tutarlı olması gerekir. Aşağıdaki kod, 2 ve 3 float 1.0 olan ve tamsayılar olduğundan hataya neden olur.

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

Sequence ifadeleri, dizi oluşturmak için de kullanabilirsiniz. Aşağıda 1'den 10'a bir dizi kare tamsayıların oluşturan bir örnek verilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

Hangi tüm öğeleri sıfır kullanılacağı başlatılır bir dizi oluşturmak için `Array.zeroCreate`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]
    
## <a name="accessing-elements"></a>Öğelere erişme

Nokta işleci kullanarak dizi öğeleri erişebilirsiniz (`.`) ve parantezler (`[` ve `]`).

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

Dizi dizini 0'da başlatın.

Dizi öğeleri dizinin alt aralığı belirtmenize olanak tanıyan dilim gösterimini kullanarak da erişebilirsiniz. Dilim gösterimi örnekleri izleyin.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

Dilim gösterimi kullanıldığında, dizi yeni bir kopyası oluşturulur.


## <a name="array-types-and-modules"></a>Dizi türleri ve modülleri
Tüm F # dizi türü .NET Framework türüdür <xref:System.Array?displayProperty=nameWithType>. Bu nedenle, F # dizileri bulunan tüm işlevselliği desteklemek <xref:System.Array?displayProperty=nameWithType>.

Kitaplık Modülü [ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) tek boyutlu diziler işlemlerini destekler. Modülleri `Array2D`, `Array3D`, ve `Array4D` dizileri üzerinde işlemler iki, üç ve dört boyut sırasıyla destek işlevler içerir. Rank dizileri dört kullanarak sıfırdan oluşturabilir <xref:System.Array?displayProperty=nameWithType>.

### <a name="simple-functions"></a>Basit işlevleri
[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)bir öğeyi alır. [`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)bir dizi uzunluğu, sağlar. [`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)bir öğe için belirtilen değere ayarlar. Aşağıdaki kod örneği, bu işlevler kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

Çıktı aşağıdaki gibidir:

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>Diziler oluşturma işlevleri

Çeşitli işlevler, var olan bir dizi gerek kalmadan diziler oluşturun. [`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)herhangi bir öğe içermiyor yeni bir dizi oluşturur. [`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)Belirtilen boyutta bir dizi oluşturur ve sağlanan değerlere tüm öğelerini ayarlar. [`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)bir dizi verilen boyut ve öğeleri oluşturmak için bir işlev oluşturur. [`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)içinde tüm öğeleri sıfır değeri dizinin türü için başlatılan bir dizi oluşturur. Aşağıdaki kod, bu işlevler gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

Çıktı aşağıdaki gibidir:

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)Varolan dizisinden kopyalanır öğeleri içeren yeni bir dizi oluşturur. Kopya öğe türüne bir başvuru türü ise yalnızca başvuru kopyalanır anlamına gelir basit bir kopyası olduğunu unutmayın, temel alınan nesnesi değil. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

Önceki kod çıkışı aşağıdaki gibidir:

```
[|Test1; Test2; |]
[|; Test2; |]
```

Dize `Test1` yeni bir öğe oluşturma işlemi başvurusunda yazdığından yalnızca ilk dizisinde görünür `firstArray` içinde hala mevcut olduğu boş bir dize özgün referansı etkilemez ancak `secondArray`. Dize `Test2` çünkü her iki dizilerde görünür `Insert` işlemi <xref:System.Text.StringBuilder?displayProperty=nameWithType> türü etkiler arka plandaki <xref:System.Text.StringBuilder?displayProperty=nameWithType> hem dizilerde başvurulan nesne.

[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)Yeni bir dizi bir dizi alt aralığı oluşturur. Başlangıç dizini ve uzunluk sağlayarak alt aralığı belirtin. Aşağıdaki kod kullanımını gösteren `Array.sub`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

Çıkış subarray 5 öğede başlar ve 10 öğeleri içeren gösterir.

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)Yeni bir dizi varolan dizilerinin birleştirerek oluşturur.

Aşağıdaki kodda **Array.append**.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

Önceki kod çıkışı aşağıdaki gibidir.

```
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)Yeni bir dizi dahil etmek için bir dizi öğeleri seçer. Aşağıdaki kodda `Array.choose`. Dizi öğesi türü seçenek türü döndürülen değer türüyle eşleşecek şekilde yok unutmayın. Bu örnekte, öğe türü olan `int` ve seçeneği polinom işlevin sonucu `elem*elem - 1`, olarak bir kayan nokta sayısı.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

Önceki kod çıkışı aşağıdaki gibidir.

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)Belirtilen işlev var olan bir dizi her dizi öğesi üzerinde çalışır ve işlev tarafından oluşturulan öğelerin toplar ve bunları yeni bir dizi birleştirir. Aşağıdaki kodda `Array.collect`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

Önceki kod çıkışı aşağıdaki gibidir.

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)diziler dizisi alır ve bunları tek bir dizi birleştirir. Aşağıdaki kodda `Array.concat`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

Önceki kod çıkışı aşağıdaki gibidir.

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)Boole koşul işlevi alır ve yalnızca koşulun doğru olması Giriş dizisinden öğeleri içeren yeni bir dizi oluşturur. Aşağıdaki kodda `Array.filter`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

Önceki kod çıkışı aşağıdaki gibidir.

```
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)Yeni bir dizi var olan bir dizi sırasını döndürerek oluşturur. Aşağıdaki kodda `Array.rev`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

Önceki kod çıkışı aşağıdaki gibidir.

```
"Hello world!"
```

Ardışık Düzen işleci kullanılarak dizilerin dönüştürme işlevleri dizi modülünde kolayca birleştirebilirsiniz (`|>`), aşağıdaki örnekte gösterildiği gibi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

Çıktı

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>Çok Boyutlu Diziler

Çok boyutlu bir diziye oluşturulabilir ancak sabit boyutlu bir diziye yazmak için hiçbir sözdizimi vardır. İşleç kullanma [ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) bir dizi bir dizi öğelerin sıralarının serisinden oluşturmak için. Dizileri dizi ya da liste değişmez değerleri olabilir. Örneğin, aşağıdaki kod iki boyutlu bir dizi oluşturur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

İşlevi de kullanabilirsiniz [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) dizi iki boyutlarının ve benzer başlatmak için işlevleri üç ve dört boyutları diziler için kullanılabilir. Bu işlevler öğeleri oluşturmak için kullanılan bir işlev alın. Bir işlev belirtme yerine ilk bir değere ayarlayın öğeleri içeren iki boyutlu bir dizi oluşturmak için kullanın [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) için de kullanılabilir işlevi diziler en fazla dört boyut. Aşağıdaki kod örneğinde ilk oluşan istediğiniz öğeleri içeren bir dizi oluşturulacağını gösterir ve ardından kullanır `Array2D.init` istenen iki boyutlu dizi oluşturmak için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

Dizin oluşturma ve sözdizimi dilimleme dizi derece 4 kadar diziler için desteklenir. Birden çok boyutlarında dizin belirttiğinizde, virgül dizinler, aşağıdaki kod örneğinde gösterildiği gibi kullanın.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]
    
İki boyutlu bir dizi türü olarak yazılır `<type>[,]` (örneğin, `int[,]`, `double[,]`), ve üç boyutlu bir dizi türü olarak yazılır `<type>[,,]`, daha yüksek boyutlarının dizileri ve benzeri için.

Tek boyutlu diziler için kullanılabilen işlevleri yalnızca bir kısmı ayrıca çok boyutlu diziler için kullanılabilir. Daha fazla bilgi için bkz: [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), ve [ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).

### <a name="array-slicing-and-multidimensional-arrays"></a>Dizi dilimleme ve çok boyutlu diziler

İki boyutlu bir dizi içinde (matrisi), bir alt matris aralıkları belirtme ve bir joker karakter kullanılması ayıklayabilirsiniz (`*`) karakter tüm satırları veya sütunları belirtin.

```fsharp
/ Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

F # 3.1 sürümünden itibaren aynı veya daha düşük boyut subarrays boyutlu bir diziye bozabilir. Örneğin, tek bir satır veya sütun belirterek bir matristen vektör edinebilirsiniz.

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

Bu öğe erişim işleçler ve aşırı türleri için sözdizimi dilimleme kullanmak `GetSlice` yöntemleri. Örneğin, F # 2B dizi sarmalar, dizi dizin oluşturma işlemi için destek sağlamak için bir öğe özelliği uygulayan ve üç sürümü uygulayan bir matris türü aşağıdaki kodu oluşturur `GetSlice`. Bu kod, matris türleri için bir şablon olarak kullanabilirsiniz, bu bölümde açıklanmıştır dilimleme işlemlerini kullanabilirsiniz.

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish = 
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a>Diziler Boolean işlevleri

İşlevler [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) ve [ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) öğelerini sırasıyla bir veya iki dizilerde test. Bu işlevlerin bir sınama işlevini alın ve dönüş `true` bir öğe yoksa (veya öğesi çifti için `Array.exists2`) koşulu karşılayan.

Aşağıdaki kod kullanımını gösteren `Array.exists` ve `Array.exists2`. Bu örneklerde, bu durumda, işlevi bağımsız değişken bağımsız değişken yalnızca birini uygulayarak yeni işlevler oluşturulur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

Önceki kod çıkışı aşağıdaki gibidir.

```
true
false
false
true
```

Benzer şekilde, işlevi [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) her öğe bir Boolean koşulu karşılayıp karşılamadığını belirlemek için bir dizi sınar. Değişim [ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) eşit uzunlukta iki dizi öğeleri içeren bir Boolean işlevini kullanarak aynı şeyi yapar. Aşağıdaki kod Bu işlevlerden birinin kullanımını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

Bu örnekler için çıktı aşağıdaki gibidir.

```
false
true
true
false
```

### <a name="searching-arrays"></a>Arama diziler

[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)Boolean işlevi alır ve işlevin döndüğü ilk öğeyi döndürür `true`, veya başlatır bir <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> koşulu karşılayan herhangi bir öğe bulunursa. [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)benzer `Array.find`, ancak bu öğenin kendisi yerine öğenin dizinini döndürür.

Aşağıdaki kod `Array.find` ve `Array.findIndex` bir mükemmel kare ve mükemmel küpe numarasını bulmak için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

Çıktı aşağıdaki gibidir:

```
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9)benzer `Array.find`sonucunu bir seçenek türü ve onu döndürür dışında `None` hiçbir öğe bulunursa. `Array.tryFind`yerine kullanılmalıdır `Array.find` değil bildiğinizde eşleşen bir öğe dizide olup olmadığını. Benzer şekilde, [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) benzer [ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) dışında bu seçenek türü dönüş değeri değil. Hiçbir öğe bulunursa, seçenektir `None`.

Aşağıdaki kod kullanımını gösteren `Array.tryFind`. Bu kod, önceki koduna bağlıdır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

Çıktı aşağıdaki gibidir:

```
Found an element: 1
Found an element: 729
```

Kullanım [ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) bulmakta ek olarak bir öğe dönüştürmek gerektiğinde. Sonuç, işlevi döndürür bir seçenek değeri olarak dönüştürülmüş öğenin ilk öğedir veya `None` böyle bir öğe bulunursa.

Aşağıdaki kod kullanımı gösterilmiştir `Array.tryPick`. Bu durumda, bir lambda ifadesi yerine birkaç yerel yardımcı işlevleri kodu basitleştirmek için tanımlanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

Çıktı aşağıdaki gibidir:

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a>Dizileri hesaplamalar gerçekleştirme

[ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) İşlevi bir dizi her öğe ortalamasını döndürür. Kayan nokta türleri ancak olmayan tam sayı türleri içeren bir tamsayı tam bölme destekleyen öğe türleri için sınırlıdır. [ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) İşlevi her öğe üzerinde bir işlev çağırma sonuçları ortalamasını döndürür. Tamsayı türünde bir dizi için kullandığınız `Array.averageBy` ve kayan her öğeye Dönüştür işlevi noktası hesaplama türü.

Kullanım [ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) veya [ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) öğe türü destekliyorsa, en düşük veya en fazla öğe alınamıyor. Benzer şekilde, [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) ve [ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) önce yürütülecek, belki de karşılaştırma destekleyen türüne dönüştürmek için bir işlev izin.

[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)bir dizinin öğeleri ekler ve [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) her öğe üzerinde bir işlevini çağırır ve sonuçları bir araya getirir.

Dönüş değerleri depolamadan dizideki her öğe üzerinde bir işlev yürütmek için kullanın [ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516). İki dizi eşit uzunlukta içeren bir işlevi için [ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc). Bir dizi işlevinin sonuçlarını tutmak ihtiyacınız varsa, kullanmak [ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) veya [ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), aynı anda iki diziler üzerinde çalışır.

Çeşitlemeleri [ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) ve [ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) hesaplama yer alması için öğenin dizini izin ver; aynı için doğrudur [ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) ve [ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).

İşlevler [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [ `Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), ve [ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) bir dizinin tüm öğeleri içeren algoritmaları yürütün. Benzer şekilde, Çeşitlemeler [ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) ve [ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) iki dizilerinde hesaplamalar gerçekleştirin.

Aynı adlı işlevleri hesaplamalar gerçekleştirmek için bu işlevler karşılık [List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Kullanım örnekleri için bkz: [listeler](lists.md).

### <a name="modifying-arrays"></a>Diziler değiştirme

[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)bir öğe için belirtilen değere ayarlar. [`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)belirli bir değere bir dizide öğe aralığını ayarlar. Aşağıdaki kod örneği sağlar `Array.fill`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

Çıktı aşağıdaki gibidir:

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

Kullanabileceğiniz [ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) başka diziye bir dizi alt kopyalanacak.

### <a name="converting-to-and-from-other-types"></a>İçin ve diğer türleri dönüştürme

[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)bir dizi listesinden bir liste oluşturur. [`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)bir dizi bir dizisini oluşturur. [`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)ve [ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) dizi türünden diğer bu koleksiyon türleri dönüştürmek.

### <a name="sorting-arrays"></a>Sıralama dizileri

Kullanım [ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) genel karşılaştırma işlevini kullanarak bir dizi sıralamak için. Kullanım [ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) bir değer oluşturan bir işlev belirtmek için olarak bilinir bir *anahtar*anahtarı genel karşılaştırma işlevini kullanarak sıralama için. Kullanım [ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) özel karşılaştırma işlevi sağlamak istiyorsanız. `Array.sort`, `Array.sortBy`, ve `Array.sortWith` tüm yeni bir dizi olarak sıralanmış dizisi döndürür. Çeşitlemeleri [ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), ve [ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) yeni bir döndürme yerine mevcut dizisini değiştirin.

### <a name="arrays-and-tuples"></a>Diziler ve diziler

İşlevler [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) ve [ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) dizi ve diziler tanımlama grubu çiftleri dizileri Dönüştür. [`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)ve [ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) üç öğelerinin diziler veya üç dizi diziler çalışmak benzer.

## <a name="parallel-computations-on-arrays"></a>Diziler üzerinde paralel hesaplamalar

Modül [ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) diziler üzerinde paralel hesaplamalar gerçekleştirmek için işlevler içerir. Bu modül, .NET Framework 4. sürümden önceki sürümlerini hedefleyen uygulamalar de kullanılamaz.

## <a name="see-also"></a>Ayrıca Bkz.
[F # dili başvurusu](index.md)

[F #'TA; Türler](fsharp-types.md)

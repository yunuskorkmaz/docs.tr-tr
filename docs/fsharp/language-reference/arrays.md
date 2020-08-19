---
title: Diziler
description: 'F # programlama dilinde dizileri oluşturmayı ve kullanmayı öğrenin.'
ms.date: 08/13/2020
ms.openlocfilehash: 93d524046ff93a7f1b04e72d580d9d0e1360ba0b
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558887"
---
# <a name="arrays"></a>Diziler

Diziler, aynı türde olan ardışık veri öğelerinin sabit boyutlu, sıfır tabanlı ve değişebilir koleksiyonlarıdır.

## <a name="create-arrays"></a>Dizi oluştur

Çeşitli yollarla diziler oluşturabilirsiniz. `[|` `|]` Aşağıdaki örneklerde gösterildiği gibi, ve arasında ardışık değerleri noktalı virgülle ayırarak küçük bir dizi oluşturabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

Ayrıca her öğeyi ayrı bir satıra koyabilirsiniz, bu durumda noktalı virgül ayırıcı isteğe bağlıdır.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

Dizi öğelerinin türü, kullanılan değişmez değerlerden çıkarılan ve tutarlı olmalıdır. Aşağıdaki kod bir hataya neden olur, çünkü 1,0 bir float ve 2 ve 3 tamsayılardır.

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

Diziler oluşturmak için dizi ifadelerini de kullanabilirsiniz. Aşağıda, 1 ile 10 arasında bir tamsayı kare dizisi oluşturan bir örnek verilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

Tüm öğelerin sıfıra başlatıldığı bir dizi oluşturmak için kullanın `Array.zeroCreate` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a>Erişim öğeleri

Dizi öğelerine bir nokta işleci ( `.` ) ve köşeli ayraçlar (ve) kullanarak erişebilirsiniz `[` `]` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

Dizi dizinleri 0 ' dan başlar.

Ayrıca, dizi öğelerine, dizinin bir alt aralığını belirtmenizi sağlayan dilim gösterimini kullanarak erişebilirsiniz. Dilim gösterimi örnekleri aşağıda verilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

Dilim gösterimi kullanıldığında, dizinin yeni bir kopyası oluşturulur.

## <a name="array-types-and-modules"></a>Dizi türleri ve modülleri

Tüm F # dizilerinin türü .NET Framework türüdür <xref:System.Array?displayProperty=nameWithType> . Bu nedenle, F # dizileri ' de bulunan tüm işlevleri destekler <xref:System.Array?displayProperty=nameWithType> .

[ `Array` Modül](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) , tek boyutlu dizilerde işlemleri destekler. Modüller, `Array2D` `Array3D` ve `Array4D` sırasıyla iki, üç ve dört boyutun dizilerindeki işlemleri destekleyen işlevler içerir. Kullanarak dörtten büyük dizi dizileri oluşturabilirsiniz <xref:System.Array?displayProperty=nameWithType> .

### <a name="simple-functions"></a>Basit işlevler

[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) bir öğeyi alır. [`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) bir dizinin uzunluğuna izin verir. [`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) bir öğeyi belirtilen değere ayarlar. Aşağıdaki kod örneği, bu işlevlerin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

Çıktı aşağıdaki gibidir:

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>Dizi oluşturan işlevler

Çeşitli işlevler, var olan bir dizi gerekmeden diziler oluşturur. [`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) herhangi bir öğe içermeyen yeni bir dizi oluşturur. [`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) belirtilen boyuttaki bir dizi oluşturur ve tüm öğeleri sağlanmış değerlere ayarlar. [`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) öğeleri oluşturmak için bir boyut ve bir işlev verildiğinde bir dizi oluşturur. [`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) tüm öğelerin, dizinin türü için sıfır değere başlatıldığı bir dizi oluşturur. Aşağıdaki kod bu işlevleri gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

Çıktı aşağıdaki gibidir:

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) Varolan bir diziden kopyalanmış öğeleri içeren yeni bir dizi oluşturur. Kopyanın basit bir kopya olduğunu, yani öğe türü bir başvuru türü ise, temeldeki nesne değil yalnızca başvurunun kopyalanacağını unutmayın. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

Önceki kodun çıktısı aşağıdaki gibidir:

```console
[|Test1; Test2; |]
[|; Test2; |]
```

Dize `Test1` yalnızca ilk dizide görünür çünkü yeni bir öğe oluşturma işlemi içindeki başvurunun üzerine yazar, `firstArray` ancak hala içinde mevcut olan boş bir dizeye özgün başvuruyu etkilemez `secondArray` . Dize `Test2` her iki dizide de görünür çünkü `Insert` türdeki işlem, <xref:System.Text.StringBuilder?displayProperty=nameWithType> <xref:System.Text.StringBuilder?displayProperty=nameWithType> her iki dizide de başvurulan temel nesneyi etkiler.

[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) bir dizinin alt aralığından yeni bir dizi oluşturur. Başlangıç dizinini ve uzunluğunu belirterek alt aralığı belirtirsiniz. Aşağıdaki kod öğesinin kullanımını gösterir `Array.sub` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

Çıktı, alt dizinin 5. öğede başlayacağını ve 10 öğe içerdiğini gösterir.

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) Varolan iki diziyi birleştirerek yeni bir dizi oluşturur.

Aşağıdaki kodda **Array. Append**gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) Yeni bir diziye dahil etmek için bir dizinin öğelerini seçer. Aşağıdaki kod gösterilmektedir `Array.choose` . Dizinin öğe türünün, seçenek türünde döndürülen değer türüyle eşleşmesi gerekmediğini unutmayın. Bu örnekte, öğe türü ' dir `int` ve seçenek, `elem*elem - 1` kayan noktalı sayı olarak bir polinom işlevinin sonucudur.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) Varolan bir dizinin her bir dizi öğesinde belirtilen bir işlevi çalıştırır ve ardından işlev tarafından oluşturulan öğeleri toplar ve bunları yeni bir dizide birleştirir. Aşağıdaki kod gösterilmektedir `Array.collect` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) dizi dizisini alır ve bunları tek bir dizi halinde birleştirir. Aşağıdaki kod gösterilmektedir `Array.concat` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) bir Boolean koşul işlevi alır ve yalnızca koşulun doğru olduğu Giriş dizisindeki öğeleri içeren yeni bir dizi oluşturur. Aşağıdaki kod gösterilmektedir `Array.filter` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) Varolan bir dizinin sırasını tersine çevirerek yeni bir dizi oluşturur. Aşağıdaki kod gösterilmektedir `Array.rev` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
"Hello world!"
```

Aşağıdaki örnekte gösterildiği gibi, ardışık düzen işlecini () kullanarak dizileri dönüştüren dizi modülündeki işlevleri kolayca birleştirebilirsiniz `|>` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

Çıktı

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>Çok boyutlu diziler

Çok boyutlu bir dizi oluşturulabilir, ancak çok boyutlu bir dizi değişmez değeri yazmak için sözdizimi yoktur. [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html)Dizi öğelerinden oluşan dizilerden bir dizi oluşturmak için işlecini kullanın. Diziler dizi veya liste sabit değerleri olabilir. Örneğin, aşağıdaki kod iki boyutlu bir dizi oluşturur.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

Ayrıca, işlevini [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) iki boyutun dizilerini başlatmak için de kullanabilirsiniz ve benzer işlevler üç ve dört boyutlu diziler için kullanılabilir. Bu işlevler, öğeleri oluşturmak için kullanılan bir işlevi alır. Bir işlev belirtmek yerine bir başlangıç değeri olarak ayarlanan öğeleri içeren iki boyutlu bir dizi oluşturmak için, [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) en fazla dört boyuta kadar diziler için de kullanılabilir olan işlevini kullanın. Aşağıdaki kod örneği, önce istenen öğeleri içeren bir dizi dizinin nasıl oluşturulacağını gösterir ve ardından `Array2D.init` istenen iki boyutlu diziyi oluşturmak için kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

Dizi dizin oluşturma ve dilimleme sözdizimi, sıralama 4 ' e kadar olan diziler için desteklenir. Birden çok boyutta bir dizin belirttiğinizde, aşağıdaki kod örneğinde gösterildiği gibi, dizinleri ayırmak için virgül kullanırsınız.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

İki boyutlu bir dizinin türü olarak yazılır `<type>[,]` (örneğin,, `int[,]` `double[,]` ) ve üç boyutlu bir dizinin türü `<type>[,,]` , daha yüksek boyutlarda diziler için olarak yazılır.

Tek boyutlu diziler için kullanılabilen işlevlerin yalnızca bir alt kümesi, çok boyutlu diziler için de kullanılabilir.

### <a name="array-slicing-and-multidimensional-arrays"></a>Dizi Dilimleme ve çok boyutlu diziler

İki boyutlu bir dizide (bir matris), aralıkları belirterek ve `*` tüm satırları veya sütunları belirtmek için bir joker karakter () karakterini kullanarak bir alt matrisi ayıklayabilirsiniz.

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

Çok boyutlu bir diziyi, aynı veya alt boyutun alt dizileri halinde parçalara ayırmayı sağlayabilirsiniz. Örneğin, tek bir satır veya sütun belirterek bir matreden bir vektör elde edebilirsiniz.

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

Bu dilimleme sözdizimini, öğe erişim işleçleri ve aşırı yüklenmiş yöntemler uygulayan türler için kullanabilirsiniz `GetSlice` . Örneğin, aşağıdaki kod F # 2D dizisini sarmalayan bir matris türü oluşturur, dizi dizini oluşturma desteği sağlamak için bir öğe özelliği uygular ve üç sürümünü uygular `GetSlice` . Bu kodu matris türleriniz için bir şablon olarak kullanacaksanız, bu bölümde açıklanan tüm Dilimleme işlemlerini kullanabilirsiniz.

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

### <a name="boolean-functions-on-arrays"></a>Diziler üzerinde Boole işlevleri

[`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) Sırasıyla bir veya iki dizide bulunan işlevler ve test öğeleri. Bu işlevler bir test işlevi alır ve `true` koşulu karşılayan bir öğe (veya öğe çifti) varsa döndürülür `Array.exists2` .

Aşağıdaki kod, ve kullanımını göstermektedir `Array.exists` `Array.exists2` . Bu örneklerde, bağımsız değişkenlerden yalnızca biri uygulanarak, bu durumlarda işlev bağımsız değişkeni olarak yeni işlevler oluşturulur.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
true
false
false
true
```

Benzer şekilde, işlevi [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) her öğenin bir Boole koşulunu karşılayıp karşılamadığını tespit etmek için bir diziyi sınar. Çeşitleme, [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) aynı şeyi eşit uzunlukta iki dizinin öğelerini içeren bir Boolean işlevi kullanarak yapar. Aşağıdaki kod, bu işlevlerin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

Bu örneklerin çıktısı aşağıdaki gibidir.

```console
false
true
true
false
```

### <a name="search-arrays"></a>Dizileri ara

[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) bir Boole işlevi alır ve işlevin döndürdüğü ilk öğeyi döndürür `true` ya da <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> koşulu karşılayan bir öğe bulunursa, öğesini başlatır. [`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex)`Array.find`,, öğesinin kendisi yerine öğesinin dizinini döndürmesi dışında, gibidir.

Aşağıdaki kod, `Array.find` `Array.findIndex` hem mükemmel bir kare hem de kusursuz küp olan bir sayıyı bulmak için ve kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

Çıktı aşağıdaki gibidir:

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) , `Array.find` , sonucu bir seçenek türü olması dışında, bir öğe bulunmazsa, öğesini döndürür `None` . `Array.tryFind``Array.find`bir eşleşen öğenin dizide olup olmadığını bilinmediğinizde yerine kullanılmalıdır. Benzer şekilde, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) `Array.findIndex` seçenek türünün dönüş değeri olması dışında, benzer. Hiçbir öğe bulunmazsa, seçeneği olur `None` .

Aşağıdaki kod öğesinin kullanımını gösterir `Array.tryFind` . Bu kod, önceki koda bağlıdır.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

Çıktı aşağıdaki gibidir:

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

[`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick)Öğesini bulmaya ek olarak bir öğesi dönüştürmeniz gerektiğinde kullanın. Sonuç, işlevin dönüştürülmüş öğeyi bir seçenek değeri olarak döndürdüğü ilk öğedir, ya da `None` böyle bir öğe bulunmazsa.

Aşağıdaki kod öğesinin kullanımını gösterir `Array.tryPick` . Bu durumda, bir lambda ifadesi yerine, kodu basitleştirmek için birkaç yerel yardımcı işlev tanımlanmıştır.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

Çıktı aşağıdaki gibidir:

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a>Diziler üzerinde hesaplamalar gerçekleştirme

[`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average)İşlevi dizideki her öğenin ortalamasını döndürür. Bu, kayan nokta türleri de dahil olmak üzere, bir tamsayı ile tam bölme desteği olan öğe türleriyle sınırlıdır. [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy)İşlevi her öğe üzerinde bir işlev çağırma sonuçlarının ortalamasını döndürür. Bir integral türü dizisi için öğesini kullanabilir `Array.averageBy` ve işlevin her öğeyi hesaplama için bir kayan nokta türüne dönüştürmesini sağlayabilirsiniz.

[`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) Öğe türü destekliyorsa, en büyük veya en küçük öğeyi almak için veya kullanın. Benzer şekilde, ancak [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) önce bir işlevin yürütülmesini, belki de karşılaştırmayı destekleyen bir türe dönüştürülmeye izin verir.

[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) bir dizinin öğelerini ekler ve [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) her bir öğeye bir işlev çağırır ve sonuçları birlikte ekler.

Dönüş değerlerini depolamadan bir dizideki her öğe üzerinde bir işlevi yürütmek için kullanın [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) . Eşit uzunlukta iki dizi içeren bir işlev için kullanın [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) . Ayrıca, işlevin sonuçlarının bir dizisini tutmanız gerekiyorsa, [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) veya kullanın [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) , tek seferde iki dizi üzerinde çalışır.

Çeşitlemeler [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) ve [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) öğenin dizine eklenmesine izin verir; aynı değer ve için de geçerlidir [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) .

,,,, [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) Ve işlevleri, [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) bir dizinin tüm öğelerini içeren algoritmaları içerir. Benzer şekilde, Çeşitlemeler [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) ve [`Array.foldBack2`](foldBack2) iki dizi üzerinde hesaplamalar gerçekleştirir.

Hesaplamalar gerçekleştirmeye yönelik bu işlevler, [liste modülündeki](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)aynı adlı işlevlere karşılık gelir. Kullanım örnekleri için bkz. [listeler](lists.md).

### <a name="modify-arrays"></a>Dizileri değiştirme

[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) bir öğeyi belirtilen değere ayarlar. [`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) bir dizideki öğe aralığını belirtilen değere ayarlar. Aşağıdaki kod bir örneği sağlar `Array.fill` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

Çıktı aşağıdaki gibidir:

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

Bir [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) dizinin alt bölümünü başka bir diziye kopyalamak için ' i kullanabilirsiniz.

### <a name="convert-to-and-from-other-types"></a>Diğer türlere ve diğer türlerden Dönüştür

[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) bir listeden bir dizi oluşturur. [`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) diziden bir dizi oluşturur. [`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) ve [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) dizi türünden bu diğer koleksiyon türlerine Dönüştür.

### <a name="sort-arrays"></a>Dizileri Sırala

[`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort)Genel karşılaştırma işlevini kullanarak bir diziyi sıralamak için kullanın. Anahtar [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) olarak adlandırılan ve anahtardaki genel karşılaştırma işlevini kullanarak sıralamak için bir değer oluşturan *key*bir işlev belirtmek için kullanın. [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith)Özel bir karşılaştırma işlevi sağlamak istiyorsanız kullanın. `Array.sort`, `Array.sortBy` ve `Array.sortWith` All sıralanmış diziyi yeni bir dizi olarak döndürür. Çeşitlemeler, [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) ve yeni bir [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) tane döndürmek yerine mevcut diziyi değiştirir.

### <a name="arrays-and-tuples"></a>Diziler ve tanımlama grupları

İşlevler ve dizi kümesi [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) çiftlerinin dizilerini dizi dizilerine ve tersine dönüştürür. [`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) ve, [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) üç öğe tanımlama grubuyla veya üç dizi tanımlama grubu ile çalıştıkları sürece benzerdir.

## <a name="parallel-computations-on-arrays"></a>Diziler üzerinde paralel hesaplamalar

Modülü [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) diziler üzerinde paralel hesaplamalar gerçekleştirmeye yönelik işlevler içerir. Bu modül, sürüm 4 ' ten önceki .NET Framework sürümlerini hedefleyen uygulamalarda kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [F# Türleri](fsharp-types.md)

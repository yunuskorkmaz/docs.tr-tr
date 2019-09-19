---
title: Diziler
description: F# Programlama dilinde diziler oluşturmayı ve kullanmayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: ae8f3cfc84fbba4cac496d4221d140dadec25e10
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082960"
---
# <a name="arrays"></a>Diziler

> [!NOTE]
> API başvuru bağlantısı sizi MSDN 'ye götürür.  Docs.microsoft.com API başvurusu tamamlanmadı.

Diziler, aynı türde olan ardışık veri öğelerinin sabit boyutlu, sıfır tabanlı ve değişebilir koleksiyonlarıdır.

## <a name="creating-arrays"></a>Diziler oluşturma

Çeşitli yollarla diziler oluşturabilirsiniz. Aşağıdaki örneklerde gösterildiği gibi, ve `[|` `|]` arasında ardışık değerleri noktalı virgülle ayırarak küçük bir dizi oluşturabilirsiniz.

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

Tüm öğelerin sıfıra başlatıldığı bir dizi oluşturmak için kullanın `Array.zeroCreate`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a>Öğelere erişme

Dizi öğelerine bir nokta işleci (`.`) ve köşeli ayraçlar (`[` ve `]`) kullanarak erişebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

Dizi dizinleri 0 ' dan başlar.

Ayrıca, dizi öğelerine, dizinin bir alt aralığını belirtmenizi sağlayan dilim gösterimini kullanarak erişebilirsiniz. Dilim gösterimi örnekleri aşağıda verilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

Dilim gösterimi kullanıldığında, dizinin yeni bir kopyası oluşturulur.

## <a name="array-types-and-modules"></a>Dizi türleri ve modülleri

Tüm F# dizilerin türü .NET Framework türüdür <xref:System.Array?displayProperty=nameWithType>. Bu nedenle F# , diziler ' de <xref:System.Array?displayProperty=nameWithType>bulunan tüm işlevleri destekler.

Kitaplık modülü [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) , tek boyutlu dizilerde işlemleri destekler. Modüller `Array2D` ,`Array3D`ve sırasıylaiki,üçvedörtboyutundizilerindekiişlemleri`Array4D` destekleyen işlevler içerir. Kullanarak <xref:System.Array?displayProperty=nameWithType>dörtten büyük dizi dizileri oluşturabilirsiniz.

### <a name="simple-functions"></a>Basit Işlevler

[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)bir öğeyi alır. [`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)bir dizinin uzunluğuna izin verir. [`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)bir öğeyi belirtilen değere ayarlar. Aşağıdaki kod örneği, bu işlevlerin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

Çıktı aşağıdaki gibidir:

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>Dizi oluşturan işlevler

Çeşitli işlevler, var olan bir dizi gerekmeden diziler oluşturur. [`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)herhangi bir öğe içermeyen yeni bir dizi oluşturur. [`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)belirtilen boyuttaki bir dizi oluşturur ve tüm öğeleri sağlanmış değerlere ayarlar. [`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)öğeleri oluşturmak için bir boyut ve bir işlev verildiğinde bir dizi oluşturur. [`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)tüm öğelerin, dizinin türü için sıfır değere başlatıldığı bir dizi oluşturur. Aşağıdaki kod bu işlevleri gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

Çıktı aşağıdaki gibidir:

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)Varolan bir diziden kopyalanmış öğeleri içeren yeni bir dizi oluşturur. Kopyanın basit bir kopya olduğunu, yani öğe türü bir başvuru türü ise, temeldeki nesne değil yalnızca başvurunun kopyalanacağını unutmayın. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

Önceki kodun çıktısı aşağıdaki gibidir:

```console
[|Test1; Test2; |]
[|; Test2; |]
```

Dize `Test1` yalnızca ilk dizide görünür çünkü yeni bir öğe oluşturma işlemi içindeki `firstArray` başvurunun üzerine yazar, ancak hala içinde `secondArray`mevcut olan boş bir dizeye özgün başvuruyu etkilemez. Dize `Test2` her iki dizide de görünür `Insert` çünkü <xref:System.Text.StringBuilder?displayProperty=nameWithType> türdeki işlem, her iki dizide de başvurulan <xref:System.Text.StringBuilder?displayProperty=nameWithType> temel nesneyi etkiler.

[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)bir dizinin alt aralığından yeni bir dizi oluşturur. Başlangıç dizinini ve uzunluğunu belirterek alt aralığı belirtirsiniz. Aşağıdaki kod öğesinin `Array.sub`kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

Çıktı, alt dizinin 5. öğede başlayacağını ve 10 öğe içerdiğini gösterir.

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)Varolan iki diziyi birleştirerek yeni bir dizi oluşturur.

Aşağıdaki kodda **Array. Append**gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)Yeni bir diziye dahil etmek için bir dizinin öğelerini seçer. Aşağıdaki kod gösterilmektedir `Array.choose`. Dizinin öğe türünün, seçenek türünde döndürülen değer türüyle eşleşmesi gerekmediğini unutmayın. Bu örnekte, öğe türü ' dir `int` ve seçenek, kayan noktalı sayı olarak bir polinom `elem*elem - 1`işlevinin sonucudur.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)Varolan bir dizinin her bir dizi öğesinde belirtilen bir işlevi çalıştırır ve ardından işlev tarafından oluşturulan öğeleri toplar ve bunları yeni bir dizide birleştirir. Aşağıdaki kod gösterilmektedir `Array.collect`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)dizi dizisini alır ve bunları tek bir dizi halinde birleştirir. Aşağıdaki kod gösterilmektedir `Array.concat`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)bir Boolean koşul işlevi alır ve yalnızca koşulun doğru olduğu Giriş dizisindeki öğeleri içeren yeni bir dizi oluşturur. Aşağıdaki kod gösterilmektedir `Array.filter`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)Varolan bir dizinin sırasını tersine çevirerek yeni bir dizi oluşturur. Aşağıdaki kod gösterilmektedir `Array.rev`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
"Hello world!"
```

Aşağıdaki örnekte gösterildiği gibi, ardışık düzen işlecini (`|>`) kullanarak dizileri dönüştüren dizi modülündeki işlevleri kolayca birleştirebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

Çıktı

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>Çok Boyutlu Diziler

Çok boyutlu bir dizi oluşturulabilir, ancak çok boyutlu bir dizi değişmez değeri yazmak için sözdizimi yoktur. Dizi öğelerinden oluşan [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) dizilerden bir dizi oluşturmak için işlecini kullanın. Diziler dizi veya liste sabit değerleri olabilir. Örneğin, aşağıdaki kod iki boyutlu bir dizi oluşturur.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

Ayrıca, işlevini [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) iki boyutun dizilerini başlatmak için de kullanabilirsiniz ve benzer işlevler üç ve dört boyutlu diziler için kullanılabilir. Bu işlevler, öğeleri oluşturmak için kullanılan bir işlevi alır. Bir işlev belirtmek yerine bir başlangıç değeri olarak ayarlanan öğeleri içeren iki boyutlu bir dizi oluşturmak için, en fazla dört boyuta kadar [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) diziler için de kullanılabilir olan işlevini kullanın. Aşağıdaki kod örneği, önce istenen öğeleri içeren bir dizi dizinin nasıl oluşturulacağını gösterir ve ardından istenen iki boyutlu diziyi oluşturmak için `Array2D.init` kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

Dizi dizin oluşturma ve dilimleme sözdizimi, sıralama 4 ' e kadar olan diziler için desteklenir. Birden çok boyutta bir dizin belirttiğinizde, aşağıdaki kod örneğinde gösterildiği gibi, dizinleri ayırmak için virgül kullanırsınız.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

İki boyutlu bir `<type>[,]` dizinin türü olarak yazılır ( `int[,]`örneğin `double[,]`,,) ve üç boyutlu bir dizinin türü, daha yüksek boyutlarda diziler için olarak `<type>[,,]`yazılır.

Tek boyutlu diziler için kullanılabilen işlevlerin yalnızca bir alt kümesi, çok boyutlu diziler için de kullanılabilir. Daha fazla bilgi için bkz [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d) [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d) [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d).,, ve [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).

### <a name="array-slicing-and-multidimensional-arrays"></a>Dizi Dilimleme ve çok boyutlu diziler

İki boyutlu bir dizide (bir matris), aralıkları belirterek ve tüm satırları veya sütunları belirtmek için bir joker karakter (`*`) karakterini kullanarak bir alt matrisi ayıklayabilirsiniz.

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

F# 3,1 itibariyle, çok boyutlu bir diziyi aynı veya daha düşük boyutun alt dizileri halinde parçalara ayırmayı sağlayabilirsiniz. Örneğin, tek bir satır veya sütun belirterek bir matreden bir vektör elde edebilirsiniz.

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

Bu dilimleme sözdizimini, öğe erişim işleçleri ve aşırı yüklenmiş `GetSlice` Yöntemler uygulayan türler için kullanabilirsiniz. Örneğin, aşağıdaki kod, F# 2B diziyi sarmalayan bir matris türü oluşturur, dizi dizini oluşturma desteği sağlamak Için bir öğe özelliği uygular ve üç `GetSlice`sürümünü uygular. Bu kodu matris türleriniz için bir şablon olarak kullanacaksanız, bu bölümde açıklanan tüm Dilimleme işlemlerini kullanabilirsiniz.

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

### <a name="boolean-functions-on-arrays"></a>Diziler üzerinde Boole Işlevleri

Sırasıyla bir [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) veya [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) iki dizide bulunan işlevler ve test öğeleri. Bu işlevler bir test işlevi alır ve koşulu `true` karşılayan bir öğe (veya öğe `Array.exists2`çifti) varsa döndürülür.

Aşağıdaki kod, `Array.exists` ve `Array.exists2`kullanımını göstermektedir. Bu örneklerde, bağımsız değişkenlerden yalnızca biri uygulanarak, bu durumlarda işlev bağımsız değişkeni olarak yeni işlevler oluşturulur.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
true
false
false
true
```

Benzer şekilde, işlevi [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) her öğenin bir Boole koşulunu karşılayıp karşılamadığını tespit etmek için bir diziyi sınar. Çeşitleme [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) , aynı şeyi eşit uzunlukta iki dizinin öğelerini içeren bir Boolean işlevi kullanarak yapar. Aşağıdaki kod, bu işlevlerin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

Bu örneklerin çıktısı aşağıdaki gibidir.

```console
false
true
true
false
```

### <a name="searching-arrays"></a>Dizileri arama

[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)bir Boole işlevi alır ve işlevin döndürdüğü `true`ilk öğeyi döndürür ya da koşulu karşılayan bir <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> öğe bulunursa, öğesini başlatır. [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f),, `Array.find`öğesinin kendisi yerine öğesinin dizinini döndürmesi dışında, gibidir.

Aşağıdaki kod, hem `Array.find` mükemmel `Array.findIndex` bir kare hem de kusursuz küp olan bir sayıyı bulmak için ve kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

Çıktı aşağıdaki gibidir:

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9),, sonucu bir seçenek türü olması dışında, bir öğe bulunmazsa, öğesini döndürür `None`. `Array.find` `Array.tryFind`bir eşleşen öğenin dizide olup `Array.find` olmadığını bilinmediğinizde yerine kullanılmalıdır. Benzer şekilde [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) , seçenek [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) türünün dönüş değeri olması dışında, benzer. Hiçbir öğe bulunmazsa, seçeneği olur `None`.

Aşağıdaki kod öğesinin `Array.tryFind`kullanımını gösterir. Bu kod, önceki koda bağlıdır.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

Çıktı aşağıdaki gibidir:

```console
Found an element: 1
Found an element: 729
```

Öğesini [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) bulmaya ek olarak bir öğesi dönüştürmeniz gerektiğinde kullanın. Sonuç, işlevin dönüştürülmüş öğeyi bir seçenek değeri olarak döndürdüğü ilk öğedir, ya `None` da böyle bir öğe bulunmazsa.

Aşağıdaki kod öğesinin `Array.tryPick`kullanımını gösterir. Bu durumda, bir lambda ifadesi yerine, kodu basitleştirmek için birkaç yerel yardımcı işlev tanımlanmıştır.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

Çıktı aşağıdaki gibidir:

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a>Diziler üzerinde hesaplamalar gerçekleştirme

[`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) İşlevi dizideki her öğenin ortalamasını döndürür. Bu, kayan nokta türleri de dahil olmak üzere, bir tamsayı ile tam bölme desteği olan öğe türleriyle sınırlıdır. [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) İşlevi her öğe üzerinde bir işlev çağırma sonuçlarının ortalamasını döndürür. Bir integral türü dizisi için öğesini kullanabilir `Array.averageBy` ve işlevin her öğeyi hesaplama için bir kayan nokta türüne dönüştürmesini sağlayabilirsiniz.

Öğe [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) türü [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) destekliyorsa, en büyük veya en küçük öğeyi almak için veya kullanın. Benzer şekilde [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) , [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) ancak önce bir işlevin yürütülmesini, belki de karşılaştırmayı destekleyen bir türe dönüştürülmeye izin verir.

[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)bir dizinin öğelerini ekler ve [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) her bir öğeye bir işlev çağırır ve sonuçları birlikte ekler.

Dönüş değerlerini depolamadan bir dizideki her öğe üzerinde bir işlevi yürütmek için kullanın [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516). Eşit uzunlukta iki dizi içeren bir işlev için kullanın [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc). Ayrıca, işlevin sonuçlarının bir dizisini tutmanız gerekiyorsa, veya [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c)kullanın, tek seferde iki dizi üzerinde çalışır.

Çeşitlemeler [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) ve [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) öğenin dizine eklenmesine izin verir; aynı değer ve [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0)için [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) de geçerlidir.

,, [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d)Ve [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9) [işlevleri,`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0)bir dizinin tüm öğelerini içeren algoritmaları içerir. [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) Benzer şekilde, Çeşitlemeler [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) ve [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) iki dizi üzerinde hesaplamalar gerçekleştirir.

Hesaplamalar gerçekleştirmeye yönelik bu işlevler, [liste modülündeki](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)aynı adlı işlevlere karşılık gelir. Kullanım örnekleri için bkz. [listeler](lists.md).

### <a name="modifying-arrays"></a>Dizileri değiştirme

[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)bir öğeyi belirtilen değere ayarlar. [`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)bir dizideki öğe aralığını belirtilen değere ayarlar. Aşağıdaki kod bir örneği `Array.fill`sağlar.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

Çıktı aşağıdaki gibidir:

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

Bir dizinin alt [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) bölümünü başka bir diziye kopyalamak için ' i kullanabilirsiniz.

### <a name="converting-to-and-from-other-types"></a>Diğer türlere ve diğer türlerden dönüştürme

[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)bir listeden bir dizi oluşturur. [`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)diziden bir dizi oluşturur. [`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)ve [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) dizi türünden bu diğer koleksiyon türlerine Dönüştür.

### <a name="sorting-arrays"></a>Dizileri sıralama

Genel [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) karşılaştırma işlevini kullanarak bir diziyi sıralamak için kullanın. Anahtar [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) olarak adlandırılan ve anahtardaki genel karşılaştırma işlevini kullanarak sıralamak için bir değer oluşturanbir işlev belirtmek için kullanın. Özel [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) bir karşılaştırma işlevi sağlamak istiyorsanız kullanın. `Array.sort`, `Array.sortBy` ve`Array.sortWith` All sıralanmış diziyi yeni bir dizi olarak döndürür. Çeşitlemeler [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0) [,`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f)ve [Yenibirtanedöndürmekyerine`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) mevcut diziyi değiştirir.

### <a name="arrays-and-tuples"></a>Diziler ve tanımlama grupları

İşlevler [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) [ve`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) dizi kümesi çiftlerinin dizilerini dizi dizilerine ve tersine dönüştürür. [`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)ve [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) , üç öğe tanımlama grubuyla veya üç dizi tanımlama grubu ile çalıştıkları sürece benzerdir.

## <a name="parallel-computations-on-arrays"></a>Diziler üzerinde paralel hesaplamalar

Modülü [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) diziler üzerinde paralel hesaplamalar gerçekleştirmeye yönelik işlevler içerir. Bu modül, sürüm 4 ' ten önceki .NET Framework sürümlerini hedefleyen uygulamalarda kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [F# Türleri](fsharp-types.md)

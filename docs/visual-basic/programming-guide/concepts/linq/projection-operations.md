---
description: 'Daha fazla bilgi edinin: projeksiyon Işlemleri (Visual Basic)'
title: Projeksiyon İşlemleri
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: 5531bec915f3a9ee521e0d67941b8f1d49e90524
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466464"
---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="dacf3-103">Projeksiyon Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dacf3-103">Projection Operations (Visual Basic)</span></span>

<span data-ttu-id="dacf3-104">Projeksiyon, bir nesneyi genellikle daha sonra kullanılacak olan özelliklerden oluşan yeni bir forma dönüştürme işlemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="dacf3-104">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="dacf3-105">Projeksiyonu kullanarak her nesneden oluşturulan yeni bir tür oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dacf3-105">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="dacf3-106">Bir özelliği proje üzerinde bir matematik işlevi de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dacf3-106">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="dacf3-107">Özgün nesneyi değiştirmeden de proje oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dacf3-107">You can also project the original object without changing it.</span></span>

<span data-ttu-id="dacf3-108">Yansıtmayı gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="dacf3-108">The standard query operator methods that perform projection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="dacf3-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dacf3-109">Methods</span></span>

|<span data-ttu-id="dacf3-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="dacf3-110">Method Name</span></span>|<span data-ttu-id="dacf3-111">Description</span><span class="sxs-lookup"><span data-stu-id="dacf3-111">Description</span></span>|<span data-ttu-id="dacf3-112">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dacf3-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="dacf3-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="dacf3-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="dacf3-114">Şunu seçin:</span><span class="sxs-lookup"><span data-stu-id="dacf3-114">Select</span></span>|<span data-ttu-id="dacf3-115">Bir dönüşüm işlevine dayalı projeler değerleri.</span><span class="sxs-lookup"><span data-stu-id="dacf3-115">Projects values that are based on a transform function.</span></span>|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|
|<span data-ttu-id="dacf3-116">SelectMany</span><span class="sxs-lookup"><span data-stu-id="dacf3-116">SelectMany</span></span>|<span data-ttu-id="dacf3-117">Bir dönüşüm işlevine dayalı ve sonra bunları tek bir sırayla düzleştirir.</span><span class="sxs-lookup"><span data-stu-id="dacf3-117">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="dacf3-118">Birden çok `From` yan tümce kullanma</span><span class="sxs-lookup"><span data-stu-id="dacf3-118">Use multiple `From` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="dacf3-119">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="dacf3-119">Query Expression Syntax Examples</span></span>

### <a name="select"></a><span data-ttu-id="dacf3-120">Şunu seçin:</span><span class="sxs-lookup"><span data-stu-id="dacf3-120">Select</span></span>

<span data-ttu-id="dacf3-121">Aşağıdaki örnek, `Select` bir dize listesindeki her bir dizeden ilk harfi proje için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dacf3-121">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>

```vb
Dim words = New List(Of String) From {"an", "apple", "a", "day"}

Dim query = From word In words
            Select word.Substring(0, 1)

Dim sb As New System.Text.StringBuilder()
For Each letter As String In query
    sb.AppendLine(letter)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' a
' a
' a
' d
```

### <a name="selectmany"></a><span data-ttu-id="dacf3-122">SelectMany</span><span class="sxs-lookup"><span data-stu-id="dacf3-122">SelectMany</span></span>

<span data-ttu-id="dacf3-123">Aşağıdaki örnek, `From` her bir sözcüğü bir dize listesindeki her bir dizeden proje için birden çok yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="dacf3-123">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>

```vb
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}

Dim query = From phrase In phrases
            From word In phrase.Split(" "c)
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' an
' apple
' a
' day
' the
' quick
' brown
' fox
```

## <a name="select-versus-selectmany"></a><span data-ttu-id="dacf3-124">Select SelectMany</span><span class="sxs-lookup"><span data-stu-id="dacf3-124">Select versus SelectMany</span></span>

<span data-ttu-id="dacf3-125">Her ikisinin de işi `Select()` , `SelectMany()` kaynak değerlerinden bir sonuç değeri (veya değerler) üretmeniz.</span><span class="sxs-lookup"><span data-stu-id="dacf3-125">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="dacf3-126">`Select()` Her kaynak değer için bir sonuç değeri üretir.</span><span class="sxs-lookup"><span data-stu-id="dacf3-126">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="dacf3-127">Bu nedenle, genel sonuç, kaynak koleksiyonuyla aynı sayıda öğeye sahip olan bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="dacf3-127">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="dacf3-128">Buna karşılık, `SelectMany()` her kaynak değerden birleştirilmiş alt koleksiyonlar içeren tek bir genel sonuç üretir.</span><span class="sxs-lookup"><span data-stu-id="dacf3-128">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="dacf3-129">Bağımsız değişken olarak geçirilen dönüştürme işlevinin `SelectMany()` her kaynak değer için sıralanabilir bir değer dizisi döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dacf3-129">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="dacf3-130">Bu sıralanabilir sıralar daha sonra `SelectMany()` bir büyük sıra oluşturmak için ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="dacf3-130">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>

<span data-ttu-id="dacf3-131">Aşağıdaki iki çizimde, bu iki yöntemin eylemleri arasındaki kavramsal fark gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dacf3-131">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="dacf3-132">Her durumda, seçici (dönüşüm) işlevinin her kaynak değerden çiçekler dizisini seçtiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="dacf3-132">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>

<span data-ttu-id="dacf3-133">Bu çizimde, `Select()` kaynak koleksiyonuyla aynı sayıda öğeye sahip bir koleksiyonun nasıl döndürdüğü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dacf3-133">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>

![Select&#40;&#41; eylemini gösteren grafik](./media/projection-operations/select-action-graphic.png)

<span data-ttu-id="dacf3-135">Bu çizimde `SelectMany()` , dizi dizilerinin her bir ara dizideki her bir değeri içeren bir son sonuç değerine nasıl sıralanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dacf3-135">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>

![SelectMany&#40;&#41; eylemini gösteren grafik.](./media/projection-operations/select-many-action-graphic.png )

### <a name="code-example"></a><span data-ttu-id="dacf3-137">Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="dacf3-137">Code Example</span></span>

<span data-ttu-id="dacf3-138">Aşağıdaki örnek, ve davranışlarını karşılaştırır `Select()` `SelectMany()` .</span><span class="sxs-lookup"><span data-stu-id="dacf3-138">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="dacf3-139">Kod, kaynak koleksiyondaki her bir çiçek adı listesinden ilk iki öğeyi alarak çiçekler ' ın bir "Buquet" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dacf3-139">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="dacf3-140">Bu örnekte, Transform işlevinin kullandığı "tek değer" değeri <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> bir değer koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="dacf3-140">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="dacf3-141">Bu, her bir `For Each` alt dizideki her bir dizeyi numaralandırmak için ek döngü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dacf3-141">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>

```vb
Class Bouquet
    Public Flowers As List(Of String)
End Class

Sub SelectVsSelectMany()
    Dim bouquets = New List(Of Bouquet) From {
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}

    Dim output As New System.Text.StringBuilder

    ' Select()
    Dim query1 = bouquets.Select(Function(b) b.Flowers)

    output.AppendLine("Using Select():")
    For Each flowerList In query1
        For Each str As String In flowerList
            output.AppendLine(str)
        Next
    Next

    ' SelectMany()
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)

    output.AppendLine(vbCrLf & "Using SelectMany():")
    For Each str As String In query2
        output.AppendLine(str)
    Next

    ' Display the output
    MsgBox(output.ToString())

    ' This code produces the following output:
    '
    ' Using Select():
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

    ' Using SelectMany()
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

End Sub
```

## <a name="see-also"></a><span data-ttu-id="dacf3-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dacf3-142">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="dacf3-143">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dacf3-143">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="dacf3-144">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="dacf3-144">Select Clause</span></span>](../../../language-reference/queries/select-clause.md)
- [<span data-ttu-id="dacf3-145">Nasıl yapılır: birleşimlerle verileri birleştirme</span><span class="sxs-lookup"><span data-stu-id="dacf3-145">How to: Combine Data with Joins</span></span>](../../language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [<span data-ttu-id="dacf3-146">Nasıl yapılır: birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dacf3-146">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="dacf3-147">Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme</span><span class="sxs-lookup"><span data-stu-id="dacf3-147">How to: Return a LINQ Query Result as a Specific Type</span></span>](../../language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [<span data-ttu-id="dacf3-148">Nasıl yapılır: grupları (LINQ) kullanarak bir dosyayı birçok dosyaya bölme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dacf3-148">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)

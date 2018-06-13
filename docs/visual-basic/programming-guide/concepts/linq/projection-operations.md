---
title: Projeksiyon işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: f4d1f7531ee69ebdbfb4ccd283f9f5dcb2f000af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647650"
---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="bf0d1-102">Projeksiyon işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf0d1-102">Projection Operations (Visual Basic)</span></span>
<span data-ttu-id="bf0d1-103">Projeksiyon genellikle daha sonra kullanılacak bu özelliklerini içeren yeni bir forma bir nesne dönüştürme işlemi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="bf0d1-104">Projeksiyon kullanarak her nesneden oluşturulmuş yeni bir türü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="bf0d1-105">Bir özellik proje ve matematiksel işlevi gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="bf0d1-106">Özgün nesne değiştirmeden da yansıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="bf0d1-107">Projeksiyon gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf0d1-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bf0d1-108">Methods</span></span>  
  
|<span data-ttu-id="bf0d1-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="bf0d1-109">Method Name</span></span>|<span data-ttu-id="bf0d1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf0d1-110">Description</span></span>|<span data-ttu-id="bf0d1-111">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf0d1-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="bf0d1-112">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="bf0d1-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="bf0d1-113">Seçim</span><span class="sxs-lookup"><span data-stu-id="bf0d1-113">Select</span></span>|<span data-ttu-id="bf0d1-114">Bir dönüştürme işlevine dayalı projeleri değerleri.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-114">Projects values that are based on a transform function.</span></span>|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bf0d1-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="bf0d1-115">SelectMany</span></span>|<span data-ttu-id="bf0d1-116">Dönüşüm işlevi üzerinde temel alır ve bunları bir sıralı düzleştirir değerler projeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="bf0d1-117">Birden çok kullanmak `From` yan tümceleri</span><span class="sxs-lookup"><span data-stu-id="bf0d1-117">Use multiple `From` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="bf0d1-118">Sorgu ifade sözdizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="bf0d1-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="bf0d1-119">Seçim</span><span class="sxs-lookup"><span data-stu-id="bf0d1-119">Select</span></span>  
 <span data-ttu-id="bf0d1-120">Aşağıdaki örnek kullanır `Select` dizelerinin listesini her dizesinde ilk harfinden projeye yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-120">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="bf0d1-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="bf0d1-121">SelectMany</span></span>  
 <span data-ttu-id="bf0d1-122">Aşağıdaki örnek, birden çok kullanır `From` dizelerinin listesini her bir dizeden her sözcüğün projeye yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-122">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="bf0d1-123">SelectMany karşı seçin</span><span class="sxs-lookup"><span data-stu-id="bf0d1-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="bf0d1-124">Hem iş `Select()` ve `SelectMany()` sonuç değeri (veya değerler) oluşturmak için kaynak değerlerinden olduğu.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="bf0d1-125">`Select()` Her kaynak değeri için bir sonuç değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="bf0d1-126">Genel sonuç bu nedenle kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="bf0d1-127">Buna karşılık, `SelectMany()` her kaynak değerinden birleştirilmiş alt koleksiyonları içeren tek bir genel sonuç üretir.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="bf0d1-128">Bağımsız değişken olarak geçirilen dönüştürme işlevi `SelectMany()` değerleri her bir kaynak değer için numaralandırılabilir bir dizi döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="bf0d1-129">Bu numaralandırılabilir sıralarının tarafından birleşir `SelectMany()` bir büyük sıralı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="bf0d1-130">Aşağıdaki iki çizimler bu iki yöntem Eylemler kavramsal birbirinden göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="bf0d1-131">Her durumda, seçici (dönüştürme) işlevinin her kaynak değerinden çiçekler dizisi seçer varsayalım.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="bf0d1-132">Bu çizimde gösterilmektedir nasıl `Select()` kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="bf0d1-133">![Select eylem kavramsal çizimi&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="bf0d1-133">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="bf0d1-134">Bu çizimde gösterilmektedir nasıl `SelectMany()` diziler ara sıra her ara dizisinden her değeri içeren bir sonuç değeri içine art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="bf0d1-135">![SelectMany eylemini gösteren grafik&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span><span class="sxs-lookup"><span data-stu-id="bf0d1-135">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="bf0d1-136">Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="bf0d1-136">Code Example</span></span>  
 <span data-ttu-id="bf0d1-137">Aşağıdaki örnek davranışını karşılaştırır `Select()` ve `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="bf0d1-138">Kaynak koleksiyondaki her çiçek adları listesinden ilk iki öğenin gerçekleştirerek çiçek "demeti" kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="bf0d1-139">Bu örnekte, "tek değer", dönüştürme işlevi <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> kullanımdır kendisini değerler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="bf0d1-140">Bu ek gerektirir `For Each` her alt dizisindeki her dize numaralandırmak için döngü.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-140">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf0d1-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-141">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="bf0d1-142">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf0d1-142">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="bf0d1-143">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="bf0d1-143">Select Clause</span></span>](../../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="bf0d1-144">Nasıl yapılır: birleştirmeleri kullanarak veri birleştirme</span><span class="sxs-lookup"><span data-stu-id="bf0d1-144">How to: Combine Data with Joins</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)  
 [<span data-ttu-id="bf0d1-145">Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma</span><span class="sxs-lookup"><span data-stu-id="bf0d1-145">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [<span data-ttu-id="bf0d1-146">Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme</span><span class="sxs-lookup"><span data-stu-id="bf0d1-146">How to: Return a LINQ Query Result as a Specific Type</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)  
 [<span data-ttu-id="bf0d1-147">Nasıl yapılır: bir dosya grupları (LINQ) (Visual Basic) kullanarak birden çok dosyaya bölme</span><span class="sxs-lookup"><span data-stu-id="bf0d1-147">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)

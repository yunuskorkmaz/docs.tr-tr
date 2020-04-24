---
title: Kullanıcı tanımlı işlevler
ms.date: 12/13/2019
description: Kullanıcı tanımlı skaler ve toplama işlevleri oluşturmayı öğrenin.
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447176"
---
# <a name="user-defined-functions"></a><span data-ttu-id="64337-103">Kullanıcı tanımlı işlevler</span><span class="sxs-lookup"><span data-stu-id="64337-103">User-defined functions</span></span>

<span data-ttu-id="64337-104">Çoğu veritabanında kendi işlevlerinizi tanımlamak için kullanabileceğiniz işlemsel bir SQL diyalekti vardır.</span><span class="sxs-lookup"><span data-stu-id="64337-104">Most databases have a procedural dialect of SQL that you can use to define your own functions.</span></span> <span data-ttu-id="64337-105">SQLite ancak, uygulamanızla birlikte işlem içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="64337-105">SQLite however, runs in-process with your app.</span></span> <span data-ttu-id="64337-106">Yeni bir SQL diyalekti öğrenmeniz yerine uygulamanızın programlama dilini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64337-106">Instead of having to learn a new dialect of SQL, you can just use the programming language of your app.</span></span>

## <a name="scalar-functions"></a><span data-ttu-id="64337-107">Skaler işlevler</span><span class="sxs-lookup"><span data-stu-id="64337-107">Scalar functions</span></span>

<span data-ttu-id="64337-108">Skaler işlevler, sorgudaki her satır için tek ve skaler bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="64337-108">Scalar functions return a single, scalar value for each row in a query.</span></span> <span data-ttu-id="64337-109">Kullanarak <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>yeni skalar işlevleri tanımlayın ve yerleşik olanları geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="64337-109">Define new scalar functions and override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.</span></span>

<span data-ttu-id="64337-110">Bağımsız değişken için desteklenen bir parametre ve dönüş türleri listesi için bkz. [veri türleri.](types.md) `func`</span><span class="sxs-lookup"><span data-stu-id="64337-110">See [Data types](types.md) for a list of supported parameter and return types for the `func` argument.</span></span>

<span data-ttu-id="64337-111">`state` Bağımsız değişkeninin belirtilmesi, bu değeri işlevinin her çağrısına geçilecektir.</span><span class="sxs-lookup"><span data-stu-id="64337-111">Specifying the `state` argument will pass that value into every invocation of the function.</span></span> <span data-ttu-id="64337-112">Kapanışlar önlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="64337-112">Use this to avoid closures.</span></span>

<span data-ttu-id="64337-113">Bir `isDeterministic` SQLite 'un sorguları derlerken ek iyileştirmeler kullanmasına izin vermek için işlevinizin belirleyici olup olmadığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="64337-113">Specify `isDeterministic` if your function is deterministic to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="64337-114">Aşağıdaki örnek, bir silindirin yarıçapını hesaplamak için bir skalar işlevin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="64337-114">The following example shows how to add a scalar function to calculate the radius of a cylinder.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a><span data-ttu-id="64337-115">İşleçler</span><span class="sxs-lookup"><span data-stu-id="64337-115">Operators</span></span>

<span data-ttu-id="64337-116">Aşağıdaki SQLite işleçleri, karşılık gelen skaler işlevler tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="64337-116">The following SQLite operators are implemented by corresponding scalar functions.</span></span> <span data-ttu-id="64337-117">Bu skaler işlevlerin uygulamanızda tanımlanması, bu işleçlerin davranışını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="64337-117">Defining these scalar functions in your app will override the behavior of these operators.</span></span>

| <span data-ttu-id="64337-118">İşleç</span><span class="sxs-lookup"><span data-stu-id="64337-118">Operator</span></span>          | <span data-ttu-id="64337-119">İşlev</span><span class="sxs-lookup"><span data-stu-id="64337-119">Function</span></span>      |
| ----------------- | ------------- |
| <span data-ttu-id="64337-120">X GLOB Y</span><span class="sxs-lookup"><span data-stu-id="64337-120">X GLOB Y</span></span>          | <span data-ttu-id="64337-121">glob (Y, X)</span><span class="sxs-lookup"><span data-stu-id="64337-121">glob(Y, X)</span></span>    |
| <span data-ttu-id="64337-122">Y BENZERI X</span><span class="sxs-lookup"><span data-stu-id="64337-122">X LIKE Y</span></span>          | <span data-ttu-id="64337-123">benzer (Y, X)</span><span class="sxs-lookup"><span data-stu-id="64337-123">like(Y, X)</span></span>    |
| <span data-ttu-id="64337-124">X GIBI Y KAÇıŞ Z</span><span class="sxs-lookup"><span data-stu-id="64337-124">X LIKE Y ESCAPE Z</span></span> | <span data-ttu-id="64337-125">benzer (Y, X, Z)</span><span class="sxs-lookup"><span data-stu-id="64337-125">like(Y, X, Z)</span></span> |
| <span data-ttu-id="64337-126">X MATCH Y</span><span class="sxs-lookup"><span data-stu-id="64337-126">X MATCH Y</span></span>         | <span data-ttu-id="64337-127">Eşleştir (Y, X)</span><span class="sxs-lookup"><span data-stu-id="64337-127">match(Y, X)</span></span>   |
| <span data-ttu-id="64337-128">X REGEXP Y</span><span class="sxs-lookup"><span data-stu-id="64337-128">X REGEXP Y</span></span>        | <span data-ttu-id="64337-129">RegExp (Y, X)</span><span class="sxs-lookup"><span data-stu-id="64337-129">regexp(Y, X)</span></span>  |

<span data-ttu-id="64337-130">Aşağıdaki örnek, karşılık gelen işlecini etkinleştirmek için RegExp işlevinin nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="64337-130">The following example shows how to define the regexp function to enable its corresponding operator.</span></span> <span data-ttu-id="64337-131">SQLite, RegExp işlevinin varsayılan bir uygulamasını içermez.</span><span class="sxs-lookup"><span data-stu-id="64337-131">SQLite doesn't include a default implementation of the regexp function.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a><span data-ttu-id="64337-132">Toplama işlevleri</span><span class="sxs-lookup"><span data-stu-id="64337-132">Aggregate functions</span></span>

<span data-ttu-id="64337-133">Toplama işlevleri bir sorgudaki tüm satırlar için tek ve toplanmış bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="64337-133">Aggregate functions return a single, aggregated value for all the rows in a query.</span></span> <span data-ttu-id="64337-134">Kullanarak <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>toplama işlevlerini tanımlayın ve geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="64337-134">Define and override aggregate functions using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.</span></span>

<span data-ttu-id="64337-135">`seed` Bağımsız değişkeni, bağlamın ilk durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="64337-135">The `seed` argument specifies the initial state of the context.</span></span> <span data-ttu-id="64337-136">Kapanışlar da önlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="64337-136">Use this to avoid closures also.</span></span>

<span data-ttu-id="64337-137">Bağımsız `func` değişken, satır başına bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="64337-137">The `func` argument is invoked once per row.</span></span> <span data-ttu-id="64337-138">Son sonucu biriktirmek için bağlamını kullanın.</span><span class="sxs-lookup"><span data-stu-id="64337-138">Use the context to accumulate a final result.</span></span> <span data-ttu-id="64337-139">Bağlamı döndürün.</span><span class="sxs-lookup"><span data-stu-id="64337-139">Return the context.</span></span> <span data-ttu-id="64337-140">Bu model, bağlamın bir değer türü veya sabit olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="64337-140">This pattern allows the context to be a value type or immutable.</span></span>

<span data-ttu-id="64337-141">Hayır `resultSelector` belirtilirse, sonuç olarak bağlamın son durumu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="64337-141">If no `resultSelector` is specified, the final state of the context is used as the result.</span></span> <span data-ttu-id="64337-142">Bu, Sum ve Count gibi işlevlerin tanımını, yalnızca her bir satırı sayının artmasını ve döndürmesini sağlamak için basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="64337-142">This can simplify the definition of functions like sum and count that only need to increment a number each row and return it.</span></span>

<span data-ttu-id="64337-143">Tüm `resultSelector` satırlarda yineleme yaptıktan sonra, son sonucun bağlamını hesaplamak için belirtin.</span><span class="sxs-lookup"><span data-stu-id="64337-143">Specify `resultSelector` to calculate the final result from the context after iterating through all the rows.</span></span>

<span data-ttu-id="64337-144">Bağımsız değişkeni ve dönüş türleri için desteklenen parametre türlerinin bir listesi için bkz `resultSelector`. [veri türleri](types.md) . `func`</span><span class="sxs-lookup"><span data-stu-id="64337-144">See [Data types](types.md) for a list of supported parameter types for the `func` argument and return types for `resultSelector`.</span></span>

<span data-ttu-id="64337-145">İşleviniz belirleyici ise, SQLite 'un `isDeterministic` sorguları derlerken ek iyileştirmeler kullanmasına izin vermek için belirtin.</span><span class="sxs-lookup"><span data-stu-id="64337-145">If your function is deterministic, specify `isDeterministic` to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="64337-146">Aşağıdaki örnek bir sütunun standart sapmasını hesaplamak için bir toplama işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64337-146">The following example defines an aggregate function to calculate the standard deviation of a column.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a><span data-ttu-id="64337-147">Hatalar</span><span class="sxs-lookup"><span data-stu-id="64337-147">Errors</span></span>

<span data-ttu-id="64337-148">Kullanıcı tanımlı bir işlev bir özel durum oluşturursa, ileti SQLite 'a döndürülür.</span><span class="sxs-lookup"><span data-stu-id="64337-148">If a user-defined function throws an exception, the message is returned to SQLite.</span></span> <span data-ttu-id="64337-149">SQLite daha sonra bir hata ve Microsoft. Data. SQLite, bir SqliteException oluşturur.</span><span class="sxs-lookup"><span data-stu-id="64337-149">SQLite will then raise an error and Microsoft.Data.Sqlite will throw a SqliteException.</span></span> <span data-ttu-id="64337-150">Daha fazla bilgi için bkz. [veritabanı hataları](database-errors.md).</span><span class="sxs-lookup"><span data-stu-id="64337-150">For more information, see [Database errors](database-errors.md).</span></span>

<span data-ttu-id="64337-151">Varsayılan olarak, hata SQLite hata kodu SQLITE_ERROR (veya 1) olacaktır.</span><span class="sxs-lookup"><span data-stu-id="64337-151">By default, the error SQLite error code will be SQLITE_ERROR (or 1).</span></span> <span data-ttu-id="64337-152">Ancak, istediğiniz <xref:Microsoft.Data.Sqlite.SqliteException> <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> gibi, işlevinizde bir oluşturarak bunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64337-152">You can, however, change it by throwing a <xref:Microsoft.Data.Sqlite.SqliteException> in your function with the desired <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> specified.</span></span>

## <a name="debugging"></a><span data-ttu-id="64337-153">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="64337-153">Debugging</span></span>

<span data-ttu-id="64337-154">SQLite uygulamanızı doğrudan çağırır.</span><span class="sxs-lookup"><span data-stu-id="64337-154">SQLite calls your implementation directly.</span></span> <span data-ttu-id="64337-155">Bu, SQLite sorguları değerlendirirken tetiklenecek kesme noktaları eklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="64337-155">This lets you add breakpoints that trigger while SQLite is evaluating queries.</span></span> <span data-ttu-id="64337-156">Tam .NET hata ayıklama deneyimi, Kullanıcı tanımlı işlevlerinizi oluşturmanıza yardımcı olmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64337-156">The full .NET debugging experience is available to help you create your user-defined functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="64337-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64337-157">See also</span></span>

* [<span data-ttu-id="64337-158">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="64337-158">Data types</span></span>](types.md)
* [<span data-ttu-id="64337-159">SQLite çekirdek işlevleri</span><span class="sxs-lookup"><span data-stu-id="64337-159">SQLite Core functions</span></span>](https://www.sqlite.org/lang_corefunc.html)
* [<span data-ttu-id="64337-160">SQLite toplama Işlevleri</span><span class="sxs-lookup"><span data-stu-id="64337-160">SQLite Aggregate Functions</span></span>](https://www.sqlite.org/lang_aggfunc.html)

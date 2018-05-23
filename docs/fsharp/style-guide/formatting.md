---
title: 'F # kod biçimlendirme yönergeleri'
description: 'F # kod biçimlendirme yönergeleri hakkında bilgi edinin.'
ms.date: 05/14/2018
ms.openlocfilehash: 1433b6891a6a0ddcdc082c141365ae54fa40c27b
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="308a8-103">F # kod biçimlendirme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="308a8-103">F# code formatting guidelines</span></span>

<span data-ttu-id="308a8-104">Bu makalede, F # kodunuzun böylece kodunuzu biçimlendirme için yönergeler sunar:</span><span class="sxs-lookup"><span data-stu-id="308a8-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="308a8-105">Genel olarak daha okunabilir görüntülenebilir</span><span class="sxs-lookup"><span data-stu-id="308a8-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="308a8-106">Visual Studio Araçları ve diğer düzenleyicileri biçimlendirme tarafından uygulanan kurallarına uygun değil</span><span class="sxs-lookup"><span data-stu-id="308a8-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="308a8-107">Başka bir kod çevrimiçi benzer</span><span class="sxs-lookup"><span data-stu-id="308a8-107">Similar to other code online</span></span>

<span data-ttu-id="308a8-108">Bu yönergelere dayalı [F # biçimlendirme kuralları kapsamlı bir kılavuz](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) tarafından [Anh Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="308a8-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="308a8-109">Girinti için genel kurallar</span><span class="sxs-lookup"><span data-stu-id="308a8-109">General rules for indentation</span></span>

<span data-ttu-id="308a8-110">F # önemli boşluk varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="308a8-110">F# uses significant whitespace by default.</span></span> <span data-ttu-id="308a8-111">Aşağıdaki yönergeler bu uygulayabilir bazı zorluklar juggle nasıl konusunda yönergeler sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="308a8-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="308a8-112">Alanları kullanma</span><span class="sxs-lookup"><span data-stu-id="308a8-112">Using spaces</span></span>

<span data-ttu-id="308a8-113">Girinti gerekli olduğunda, boşluk, sekme değil kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="308a8-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="308a8-114">En az bir alan gereklidir.</span><span class="sxs-lookup"><span data-stu-id="308a8-114">At least one space is required.</span></span> <span data-ttu-id="308a8-115">Kuruluşunuz için girinti kullanmak için alanları sayısını belirtmek için kodlama standartları oluşturabilir; girinti girinti oluştuğu her düzeyde iki, üç veya dört boşluklardan tipiktir.</span><span class="sxs-lookup"><span data-stu-id="308a8-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="308a8-116">**Girinti başına 4 boşluk öneririz.**</span><span class="sxs-lookup"><span data-stu-id="308a8-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="308a8-117">Bu, programların girinti öznel bir konudur belirtti.</span><span class="sxs-lookup"><span data-stu-id="308a8-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="308a8-118">Çeşitlemeler edilir, ancak takip etmeniz gerekir ilk kural *girinti tutarlılığını*.</span><span class="sxs-lookup"><span data-stu-id="308a8-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="308a8-119">Girinti, genel olarak kabul edilen bir stil seçin ve temelinizde sistematik olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="308a8-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="308a8-120">Ayrılmış birleşim bildirimleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="308a8-120">Formatting discriminated union declarations</span></span>

<span data-ttu-id="308a8-121">Girinti `|` 4 boşluk tarafından türü tanımında:</span><span class="sxs-lookup"><span data-stu-id="308a8-121">Indent `|` in type definition by 4 spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

<span data-ttu-id="308a8-122">Örneklenen ayrılmış birden çok satıra yayılmış ayrılmış birleşimler içerdiği veri girinti ile yeni bir kapsam vermeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="308a8-122">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="308a8-123">Kapatma parantezi de yeni bir satıra olabilir:</span><span class="sxs-lookup"><span data-stu-id="308a8-123">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a><span data-ttu-id="308a8-124">Diziler biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="308a8-124">Formatting tuples</span></span>

<span data-ttu-id="308a8-125">Parantez içine alınmış bir tanımlama grubu örneklemesi olmalıdır ve sınırlandırma virgül içinde tek bir boşlukla örneğin gelmelidir: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="308a8-125">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="308a8-126">Diziler desen eşleştirme içinde parantez atlamak için yaygın olarak kabul edilen bir özel durumdur:</span><span class="sxs-lookup"><span data-stu-id="308a8-126">A commonly accepted exception is to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a><span data-ttu-id="308a8-127">Kayıtları biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="308a8-127">Formatting records</span></span>

<span data-ttu-id="308a8-128">Kısa kayıtları tek bir çizgi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="308a8-128">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="308a8-129">Uzun kayıtları yeni satırlar için etiketleri kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="308a8-129">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="308a8-130">Aynı satır ve yeni bir satıra kapatma belirteci açma belirteci yerleştirerek de uygundur:</span><span class="sxs-lookup"><span data-stu-id="308a8-130">Placing the opening token on the same line and the closing token on a new line is also fine:</span></span>

```fsharp
let rainbow = {
    Boss1 = "Jeffrey"
    Boss2 = "Jeffrey"
    Boss3 = "Jeffrey"
    Boss4 = "Jeffrey"
    Boss5 = "Jeffrey"
    Boss6 = "Jeffrey"
    Boss7 = "Jeffrey"
    Boss8 = "Jeffrey"
    Lackeys = ["Zippy"; "George"; "Bungle"]
}
```

<span data-ttu-id="308a8-131">Aynı kuralları dizisi ve liste öğeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="308a8-131">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="308a8-132">Biçimlendirme listeler ve diziler</span><span class="sxs-lookup"><span data-stu-id="308a8-132">Formatting lists and arrays</span></span>

<span data-ttu-id="308a8-133">Yazma `x :: l` boşluk ile `::` işleci (`::` bu nedenle boşluklarla çevrelenmiş bir iç işleci) ve `[1; 2; 3]` (`;` bu nedenle bir boşluk bırakarak bir sınırlayıcı).</span><span class="sxs-lookup"><span data-stu-id="308a8-133">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces) and `[1; 2; 3]` (`;` is a delimiter, hence followed by a space).</span></span>

<span data-ttu-id="308a8-134">Her zaman iki farklı küme parantezi benzeri işleç arasındaki en az bir boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="308a8-134">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="308a8-135">Örneğin, arasında boşluk bırakmak bir `[` ve `{`.</span><span class="sxs-lookup"><span data-stu-id="308a8-135">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="308a8-136">Kayıtları gibi listeler ve birden çok satıra yayılmış bölme diziler benzer bir kural izleyin:</span><span class="sxs-lookup"><span data-stu-id="308a8-136">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a><span data-ttu-id="308a8-137">Biçimlendirme IF ifadeleri</span><span class="sxs-lookup"><span data-stu-id="308a8-137">Formatting if expressions</span></span>

<span data-ttu-id="308a8-138">Koşulları girinti onları oluşturan ifadeler boyutlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="308a8-138">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="308a8-139">Varsa `cond`, `e1` ve `e2` küçük, yalnızca bunları tek satıra yazın:</span><span class="sxs-lookup"><span data-stu-id="308a8-139">If `cond`, `e1` and `e2` are small, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="308a8-140">Varsa `e1` ve `cond` küçük, ancak `e2` büyük:</span><span class="sxs-lookup"><span data-stu-id="308a8-140">If `e1` and `cond` are small, but `e2` is large:</span></span>

```fsharp
if cond then e1
else
    e2
```

<span data-ttu-id="308a8-141">Varsa `e1` ve `cond` büyük ve `e2` küçük:</span><span class="sxs-lookup"><span data-stu-id="308a8-141">If `e1` and `cond` are large and `e2` is small:</span></span>

```fsharp
if cond then
    e1
else e2
```

<span data-ttu-id="308a8-142">Tüm ifadeler büyükse:</span><span class="sxs-lookup"><span data-stu-id="308a8-142">If all the expressions are large:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="308a8-143">Birden çok koşulları ile `elif` ve `else` aynı kapsamda girintili `if`:</span><span class="sxs-lookup"><span data-stu-id="308a8-143">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="308a8-144">Desen eşleştirme yapıları</span><span class="sxs-lookup"><span data-stu-id="308a8-144">Pattern matching constructs</span></span>

<span data-ttu-id="308a8-145">Kullanım bir `|` her bir eşleşme yan tümcesinin hiçbir girinti ile.</span><span class="sxs-lookup"><span data-stu-id="308a8-145">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="308a8-146">İfade kısaysa, tek bir satır kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="308a8-146">If the expression is short, you can use a single line.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"

// OK
match l with [] -> false | _ :: _ -> true
```

<span data-ttu-id="308a8-147">Sağ ok eşleşen kalıbı tarafındaki ifade çok büyükse, taşıyabilir girintili bir adımda aşağıdaki satırı `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="308a8-147">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="308a8-148">Desen ile başlayan anonim işlevlerin eşleşen `function`, genellikle çok girinti değil.</span><span class="sxs-lookup"><span data-stu-id="308a8-148">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="308a8-149">Örneğin, aşağıdaki gibi bir kapsam girintileme uygundur:</span><span class="sxs-lookup"><span data-stu-id="308a8-149">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="308a8-150">Desen eşleştirme tarafından tanımlanan işlevlerinde `let` veya `let rec` girintili 4 boşluk, başlattıktan sonra olmalıdır `let`olsa bile `function` anahtar sözcüğü kullanılır:</span><span class="sxs-lookup"><span data-stu-id="308a8-150">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="308a8-151">Oklar hizalama önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="308a8-151">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="308a8-152">Biçimlendirme try / ifadelerle</span><span class="sxs-lookup"><span data-stu-id="308a8-152">Formatting try/with expressions</span></span>

<span data-ttu-id="308a8-153">Desen eşleştirme özel durum türüne girintili aynı düzeyde `with`.</span><span class="sxs-lookup"><span data-stu-id="308a8-153">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="308a8-154">İşlev parametresi uygulama biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="308a8-154">Formatting function parameter application</span></span>

<span data-ttu-id="308a8-155">Genel olarak, çoğu işlevi parametresi uygulama aynı çizgi üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="308a8-155">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="308a8-156">Yeni bir satıra bir işlev parametreleri uygulamak isterseniz, bunları bir kapsam tarafından girinti.</span><span class="sxs-lookup"><span data-stu-id="308a8-156">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="308a8-157">Anonim işlev bağımsız değişkenleri, bir sonraki satırdaki ya da bir sarkan ile olabilir `fun` bağımsız değişkeni satırında:</span><span class="sxs-lookup"><span data-stu-id="308a8-157">Anonymous function arguments can be either on next line or with a dangling `fun` on the argument line:</span></span>

```fsharp
// OK
let printListWithOffset a list1 =
    List.iter (fun elem ->
        printfn "%d" (a + elem)) list1

// OK, but prefer previous
let printListWithOffset a list1 =
    List.iter (
        fun elem ->
            printfn "%d" (a + elem)) list1
```

### <a name="formatting-infix-operators"></a><span data-ttu-id="308a8-158">Biçimlendirme iç işleçleri</span><span class="sxs-lookup"><span data-stu-id="308a8-158">Formatting infix operators</span></span>

<span data-ttu-id="308a8-159">Alanları ayrı işleçleriyle.</span><span class="sxs-lookup"><span data-stu-id="308a8-159">Separate operators by spaces.</span></span> <span data-ttu-id="308a8-160">Bu kural belirgin istisnaları `!` ve `.` işleçler.</span><span class="sxs-lookup"><span data-stu-id="308a8-160">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="308a8-161">İç ifadeleri serisi aynı sütunda Tamam üzeresiniz:</span><span class="sxs-lookup"><span data-stu-id="308a8-161">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="308a8-162">Ardışık Düzen operatörleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="308a8-162">Formatting pipeline operators</span></span>

<span data-ttu-id="308a8-163">Ardışık Düzen `|>` işleçleri çalışması üzerinde ifadeleri altında gitmesini.</span><span class="sxs-lookup"><span data-stu-id="308a8-163">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a><span data-ttu-id="308a8-164">Modülleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="308a8-164">Formatting modules</span></span>

<span data-ttu-id="308a8-165">Bir yerel modül kodda modülü göre girintili gerekir, ancak üst düzey bir modül kodda girintili.</span><span class="sxs-lookup"><span data-stu-id="308a8-165">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="308a8-166">Namespace öğeleri girintili gerekmez.</span><span class="sxs-lookup"><span data-stu-id="308a8-166">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="308a8-167">Nesne ifadeleri ve arabirimler biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="308a8-167">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="308a8-168">Nesne ifadeleri ve arabirimler hizalı ile aynı şekilde `member` sonra 4 boşluk girintili.</span><span class="sxs-lookup"><span data-stu-id="308a8-168">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a><span data-ttu-id="308a8-169">İfadelerde boşluk biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="308a8-169">Formatting whitespace in expressions</span></span>

<span data-ttu-id="308a8-170">F # ifadelerde yabancı boşluk kaçının.</span><span class="sxs-lookup"><span data-stu-id="308a8-170">Avoid extraneous whitespace in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="308a8-171">Adlandırılmış bağımsız değişkenler de olmamalıdır alanını çevreleyen `=`:</span><span class="sxs-lookup"><span data-stu-id="308a8-171">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="308a8-172">Boş satırlar biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="308a8-172">Formatting blank lines</span></span>

* <span data-ttu-id="308a8-173">Ayrı en üst düzey işlevi ve sınıf tanımları iki boş satırlar.</span><span class="sxs-lookup"><span data-stu-id="308a8-173">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="308a8-174">Yöntem tanımlarını bir sınıf içinde tek bir boş çizgi ile ayrılır.</span><span class="sxs-lookup"><span data-stu-id="308a8-174">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="308a8-175">Ek boş satırlar (tutumlu) ilgili işlevleri grupları ayırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="308a8-175">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="308a8-176">Boş satırlar ilgili one-liners (örneğin, sahte uygulamaları kümesi) arasında bir grup atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="308a8-176">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="308a8-177">Boş satırlar işlevlerde, gerektiğinde, mantıksal bölümleri belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="308a8-177">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="308a8-178">Açıklamalar Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="308a8-178">Formatting comments</span></span>

<span data-ttu-id="308a8-179">Genellikle birden çok çift eğik çizgi açıklamaları ML stil bloğu açıklamaları tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="308a8-179">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    Generally avoid these kinds of comments.
*)
```

<span data-ttu-id="308a8-180">Satır içi açıklamalar ilk harfini büyük.</span><span class="sxs-lookup"><span data-stu-id="308a8-180">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="308a8-181">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="308a8-181">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="308a8-182">Sınıf bağlı, ifade bağlı ve desen ilişkili değerleri ve işlevleri için camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="308a8-182">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="308a8-183">Yaygın bir durumdur ve yerel değişkenleri olarak veya desen eşleşmeleri ve işlev tanımları camelCase tüm adları için kabul edilen F # stili bağlanır.</span><span class="sxs-lookup"><span data-stu-id="308a8-183">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="308a8-184">Sınıflardaki yerel olarak bağlı işlevleri de camelCase kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="308a8-184">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="308a8-185">İç ve özel modülü sınır değerleri ve işlevleri için camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="308a8-185">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="308a8-186">CamelCase aşağıdakiler de dahil olmak üzere özel modülü sınır değerleri için kullanın:</span><span class="sxs-lookup"><span data-stu-id="308a8-186">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="308a8-187">Komut dosyalarında geçici işlevler</span><span class="sxs-lookup"><span data-stu-id="308a8-187">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="308a8-188">Bir modül veya türü iç uygulamasını yapmak değerleri</span><span class="sxs-lookup"><span data-stu-id="308a8-188">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="308a8-189">CamelCase parametrelerini kullanın</span><span class="sxs-lookup"><span data-stu-id="308a8-189">Use camelCase for parameters</span></span>

<span data-ttu-id="308a8-190">Tüm parametreleri camelCase .NET adlandırma kurallarına uygun olarak kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="308a8-190">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="308a8-191">Modüller için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="308a8-191">Use PascalCase for modules</span></span>

<span data-ttu-id="308a8-192">Tüm modülleri (üst düzey, iç, özel, iç içe geçmiş) PascalCase kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="308a8-192">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="308a8-193">Tür bildirimleri, üyeleri ve etiketler için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="308a8-193">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="308a8-194">Sınıflar, arabirimler, yapılar, numaralandırmalar, temsilciler, kaydeder ve ayrılmış birleşimler tüm ile PascalCase adlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="308a8-194">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="308a8-195">Üye türleri ve kaydeder ve ayrılmış birleşimler için etiketleri içinde ayrıca PascalCase kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="308a8-195">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="308a8-196">.NET için iç yapılar için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="308a8-196">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="308a8-197">Ad alanları, özel durumlar, olaylar ve proje /`.dll` adları PascalCase de kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="308a8-197">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="308a8-198">Yalnızca bu diğer .NET dilleri gelen tüketicilere daha doğal eşitleyerek tüketim yapar, ayrıca karşılaşma olasılığı olan .NET adlandırma kuralları ile tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="308a8-198">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="308a8-199">Alt çizgi adlarında kaçının</span><span class="sxs-lookup"><span data-stu-id="308a8-199">Avoid underscores in names</span></span>

<span data-ttu-id="308a8-200">Tarihsel olarak, bazı F # kitaplıkları adları alt çizgi kullandınız.</span><span class="sxs-lookup"><span data-stu-id="308a8-200">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="308a8-201">Kısmen .NET adlandırma kuralları ile çakışıyor çünkü ancak bu artık yaygın olarak, kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="308a8-201">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="308a8-202">Bu, bazı F # programcıları alt çizgi yoğun, kısmen geçmiş nedenlerle kullanın ve dayanıklılık ve saygı önemlidir da belirtti.</span><span class="sxs-lookup"><span data-stu-id="308a8-202">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="308a8-203">Ancak, bunu kullanıp kullanmayacağınızı hakkında seçmesini başkaları tarafından stili genellikle yanıtlamadığı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="308a8-203">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="308a8-204">Yerel, alt çizgi yaygın olduğu bileşenleriyle birlikte özel bazı durumlar içerir.</span><span class="sxs-lookup"><span data-stu-id="308a8-204">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="308a8-205">Standart F # işleçleri kullanın</span><span class="sxs-lookup"><span data-stu-id="308a8-205">Use standard F# operators</span></span>

<span data-ttu-id="308a8-206">Aşağıdaki işleçleri F # standart Kitaplığı'nda tanımlanır ve eşdeğerleri tanımlama yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="308a8-206">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="308a8-207">Kodunu daha okunabilir ve kullanılan deyimsel hale eğilimlidir gibi bu işleçlere kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="308a8-207">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="308a8-208">Arka plan OCaml veya diğer işlevsel programlama dili geliştiricilere farklı deyimleri alışkın olabilir.</span><span class="sxs-lookup"><span data-stu-id="308a8-208">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="308a8-209">Aşağıdaki liste, önerilen F # işleçleri özetler.</span><span class="sxs-lookup"><span data-stu-id="308a8-209">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Throwing away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="308a8-210">Genel türler için önek söz dizimini kullanın (`Foo<T>`) sonek sözdizimi yerine (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="308a8-210">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="308a8-211">F # genel türleri adlandırma hem sonek ML stili devralır (örneğin, `int list`) yanı sıra .NET stili önek (örneğin, `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="308a8-211">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="308a8-212">Dört belirli türleri dışında .NET stili tercih eder:</span><span class="sxs-lookup"><span data-stu-id="308a8-212">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="308a8-213">F # listeleri, sonek formu kullanın: `int list` yerine `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="308a8-213">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="308a8-214">F # seçenekleri için sonek formu kullanın: `int option` yerine `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="308a8-214">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="308a8-215">F # diziler için söz dizimi adı kullanmak `int[]` yerine `int array` veya `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="308a8-215">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="308a8-216">Başvuru hücreleri için kullanmak `int ref` yerine `ref<int>` veya `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="308a8-216">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="308a8-217">Diğer tüm türleri için önek formu kullanın.</span><span class="sxs-lookup"><span data-stu-id="308a8-217">For all other types, use the prefix form.</span></span>

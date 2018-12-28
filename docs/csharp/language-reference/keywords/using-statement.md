---
title: using deyimi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: df116a200795fd20405381fd71e82d1d6fe662bc
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614395"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="3f625-102">using deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3f625-102">using statement (C# Reference)</span></span>

<span data-ttu-id="3f625-103">Doğru kullanımını güvence altına kullanışlı bir söz dizimi sağlar <xref:System.IDisposable> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3f625-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="3f625-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f625-104">Example</span></span>

<span data-ttu-id="3f625-105">Aşağıdaki örnek nasıl kullanılacağını gösterir `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3f625-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

## <a name="remarks"></a><span data-ttu-id="3f625-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f625-106">Remarks</span></span>

<span data-ttu-id="3f625-107"><xref:System.IO.File> ve <xref:System.Drawing.Font> (içinde bu durum dosya tanıtıcıları ve cihaz bağlamları) yönetilmeyen kaynaklara erişen Yönetilen türlerin örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="3f625-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="3f625-108">Yönetilmeyen kaynakları bunları kapsayan sınıf kitaplığı türleri ve diğer birçok tür vardır.</span><span class="sxs-lookup"><span data-stu-id="3f625-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="3f625-109">Tüm türleri uygulamalıdır <xref:System.IDisposable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3f625-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="3f625-110">Zaman ömrünü bir `IDisposable` nesne tek bir yöntem sınırlıdır, bildirme ve içinde örneği `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3f625-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="3f625-111">`using` Deyim aramaları <xref:System.IDisposable.Dispose%2A> doğru bir şekilde ve (daha önce gösterildiği gibi kullandığınız zaman) nesnesi üzerinde yöntemi de neden nesne kapsam dışına çıkmadan kendisine hemen sonra <xref:System.IDisposable.Dispose%2A> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3f625-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="3f625-112">İçinde `using` blok, nesne, salt okunur ve yeniden atandığında veya değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="3f625-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="3f625-113">`using` Bildirimi sağlar <xref:System.IDisposable.Dispose%2A> bile içinde özel bir durum oluştuğunda çağrılır `using` blok.</span><span class="sxs-lookup"><span data-stu-id="3f625-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="3f625-114">Nesnenin içine koyarak aynı sonucu elde edebileceğiniz bir `try` blok ve ardından arama <xref:System.IDisposable.Dispose%2A> içinde bir `finally` engelle; aslında bu, nasıl `using` deyimi, derleyici tarafından çevrilir.</span><span class="sxs-lookup"><span data-stu-id="3f625-114">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="3f625-115">Kod örneği, daha önce aşağıdaki kodu derleme zamanında genişletir (nesne için sınırlı kapsamı oluşturmak için ek küme ayracı unutmayın):</span><span class="sxs-lookup"><span data-stu-id="3f625-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="3f625-116">Hakkında daha fazla bilgi için `try` - `finally` deyimi bkz [try-finally](try-finally.md) konu.</span><span class="sxs-lookup"><span data-stu-id="3f625-116">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="3f625-117">Birden fazla örneğini bir tür içinde bildirilebilir `using` aşağıdaki örnekte gösterildiği gibi deyimi:</span><span class="sxs-lookup"><span data-stu-id="3f625-117">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="3f625-118">Kaynak nesne örneği oluşturun ve ardından değişkenine geçirin `using` deyimi değildir, ancak bu en iyi uygulama.</span><span class="sxs-lookup"><span data-stu-id="3f625-118">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="3f625-119">Bu durumda, sonra Denetim leaves `using` engellemek, kapsam içinde nesne kalır ancak büyük olasılıkla kendi yönetilmeyen kaynaklara erişim yok.</span><span class="sxs-lookup"><span data-stu-id="3f625-119">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="3f625-120">Diğer bir deyişle, tam olarak artık başlatılır.</span><span class="sxs-lookup"><span data-stu-id="3f625-120">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="3f625-121">Nesne dışında kullanmayı denerseniz `using` bir özel durum oluşturulmasına neden risk engelleyin.</span><span class="sxs-lookup"><span data-stu-id="3f625-121">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="3f625-122">Bu nedenle, nesneyi oluşturmak genellikle daha iyi `using` deyimi ve sınırlandırmak için kapsamı `using` blok.</span><span class="sxs-lookup"><span data-stu-id="3f625-122">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="3f625-123">Atma hakkında daha fazla bilgi için `IDisposable` nesneleri bkz [IDisposable uygulayan nesneler kullanma](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="3f625-123">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3f625-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3f625-124">C# language specification</span></span>

<span data-ttu-id="3f625-125">Daha fazla bilgi için [using deyimi](~/_csharplang/spec/statements.md#the-using-statement) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f625-125">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="3f625-126">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="3f625-126">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f625-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f625-127">See also</span></span>

- [<span data-ttu-id="3f625-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3f625-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3f625-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3f625-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3f625-130">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3f625-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3f625-131">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="3f625-131">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="3f625-132">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="3f625-132">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="3f625-133">IDisposable uygulayan nesneler kullanma</span><span class="sxs-lookup"><span data-stu-id="3f625-133">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="3f625-134">IDisposable arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f625-134">IDisposable interface</span></span>](xref:System.IDisposable)
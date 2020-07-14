---
title: Öznitelikli Programlama Modeline Genel Bakış (MEF)
description: .NET 'teki Managed Extensibility Framework (MEF) için varsayılan programlama modeli olan öznitelikli programlama modeli ile çalışmaya başlayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
ms.openlocfilehash: aea3a19ffe6f177901e5c0839b618bb36f573beb
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281374"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="586e0-103">Öznitelikli Programlama Modeline Genel Bakış (MEF)</span><span class="sxs-lookup"><span data-stu-id="586e0-103">Attributed Programming Model Overview (MEF)</span></span>

<span data-ttu-id="586e0-104">Managed Extensibility Framework (MEF) içinde, bir *programlama MODELI* MEF 'in üzerinde çalıştığı kavramsal nesneler kümesini tanımlamaya yönelik belirli bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="586e0-104">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="586e0-105">Bu kavramsal nesneler parçalar, içeri aktarmalar ve dışarı aktarmaları içerir.</span><span class="sxs-lookup"><span data-stu-id="586e0-105">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="586e0-106">MEF bu nesneleri kullanır, ancak nasıl temsil edileceğini belirtmez.</span><span class="sxs-lookup"><span data-stu-id="586e0-106">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="586e0-107">Bu nedenle, özelleştirilmiş programlama modelleri de dahil olmak üzere çok çeşitli programlama modelleri mümkündür.</span><span class="sxs-lookup"><span data-stu-id="586e0-107">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>

<span data-ttu-id="586e0-108">MEF 'te kullanılan varsayılan programlama modeli, *öznitelikli programlama modelidir*.</span><span class="sxs-lookup"><span data-stu-id="586e0-108">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="586e0-109">Öznitelikli programlama modeli bölümlerinde, içeri aktarmalar, dışarı aktarımlar ve diğer nesneler, sıradan .NET Framework sınıfları süsleten öznitelikler ile tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="586e0-109">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="586e0-110">Bu konu başlığı altında, bir MEF uygulaması oluşturmak için Öznitelikli programlama modeli tarafından sunulan özniteliklerin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="586e0-110">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a><span data-ttu-id="586e0-111">İçeri ve dışarı aktarma temelleri</span><span class="sxs-lookup"><span data-stu-id="586e0-111">Import and Export Basics</span></span>

<span data-ttu-id="586e0-112">*Dışarı aktarma* , bir bölümün kapsayıcıdaki diğer bölümlere sağladığı bir değerdir ve *içeri aktarma* işlemi, kullanılabilir dışarı aktarımlardan doldurulacak bir bölümün kapsayıcının ifade olduğu gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="586e0-112">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="586e0-113">Öznitelikli programlama modelinde, içeri aktarmalar ve dışarı aktarımlar, ve öznitelikleri ile sınıflar veya Üyeler dekorasyon tarafından `Import` tanımlanır `Export` .</span><span class="sxs-lookup"><span data-stu-id="586e0-113">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="586e0-114">Özniteliği `Export` bir `Import` alanı, özelliği veya Oluşturucu parametresini süslemek için bir sınıfı, alanı, özelliği veya yöntemi süsedebilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-114">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>

<span data-ttu-id="586e0-115">İçeri aktarmanın bir dışarı aktarma işlemiyle eşleşmesi için, içeri ve dışarı aktarmanın aynı *sözleşmeye*sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="586e0-115">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="586e0-116">Sözleşme, sözleşme *adı*olarak adlandırılan bir dizeden ve verilen ya da içeri aktarılan nesnenin türü, *anlaşma türü*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="586e0-116">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="586e0-117">Yalnızca anlaşma adı ve anlaşma türü eşleşiyorsa, belirli bir içeri aktarma işlemini yerine getirmek için kabul edilen bir dışarı aktarma işlemi olur.</span><span class="sxs-lookup"><span data-stu-id="586e0-117">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>

<span data-ttu-id="586e0-118">Anlaşma parametrelerinden biri veya her ikisi örtük veya açık olabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-118">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="586e0-119">Aşağıdaki kod, temel bir içeri aktarma bildiren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="586e0-119">The following code shows a class that declares a basic import.</span></span>

```vb
Public Class MyClass1
    <Import()>
    Public Property MyAddin As IMyAddin
End Class
```

```csharp
public class MyClass
{
    [Import]
    public IMyAddin MyAddin { get; set; }
}
```

<span data-ttu-id="586e0-120">Bu içeri `Import` aktarımda, öznitelik bir anlaşma türüne veya bir anlaşma adı parametresine bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="586e0-120">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="586e0-121">Bu nedenle, her ikisi de düzenlenmiş özelliğinden çıkarsedilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-121">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="586e0-122">Bu durumda, sözleşme türü olur `IMyAddin` ve anlaşma adı Sözleşme türünden oluşturulan benzersiz bir dize olur.</span><span class="sxs-lookup"><span data-stu-id="586e0-122">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="586e0-123">(Başka bir deyişle, sözleşme adı yalnızca adları türden de çıkarılan dışarı aktarmalar ile eşleşir `IMyAddin` .)</span><span class="sxs-lookup"><span data-stu-id="586e0-123">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>

<span data-ttu-id="586e0-124">Aşağıda, önceki içeri aktarma ile eşleşen bir dışarı aktarma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="586e0-124">The following shows an export that matches the previous import.</span></span>

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="586e0-125">Bu dışarı aktarmada, sözleşme türü `IMyAddin` özniteliğin bir parametresi olarak belirtilmediği için olur `Export` .</span><span class="sxs-lookup"><span data-stu-id="586e0-125">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="586e0-126">İçe aktarılmış tür, anlaşma türüyle aynı olmalıdır, anlaşma türünden türetilir ya da bir arabirimteise sözleşme türünü uygular.</span><span class="sxs-lookup"><span data-stu-id="586e0-126">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="586e0-127">Bu dışa aktarmada gerçek tür `MyLogger` arabirimini uygular `IMyAddin` .</span><span class="sxs-lookup"><span data-stu-id="586e0-127">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="586e0-128">Sözleşme adı, Sözleşme türünden algılanır, bu da dışarı aktarmanın önceki içeri aktarma ile eşleşmeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="586e0-128">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>

> [!NOTE]
> <span data-ttu-id="586e0-129">Dışarı aktarmalar ve içeri aktarmalar genellikle ortak sınıflarda veya üyelerde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="586e0-129">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="586e0-130">Diğer bildirimler desteklenir, ancak özel, korumalı veya dahili bir üyenin dışa aktarılması veya içe aktarılması bölümün yalıtım modelini keser ve bu nedenle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="586e0-130">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>

<span data-ttu-id="586e0-131">Anlaşma türü, dışa aktarma ve içeri aktarma için tam olarak eşleşmelidir ve bir eşleşme olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-131">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="586e0-132">Aşağıdaki dışarı aktarmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="586e0-132">Consider the following export.</span></span>

```vb
<Export()> 'WILL NOT match the previous import!
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export] //WILL NOT match the previous import!
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="586e0-133">Bu dışarı aktarmada, bunun yerine anlaşma türü olur `MyLogger` `IMyAddin` .</span><span class="sxs-lookup"><span data-stu-id="586e0-133">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="586e0-134">`MyLogger` `IMyAddin` , Ve bu nedenle bir nesneye tür atama yapılabileceğinden, `IMyAddin` Bu dışarı aktarma önceki içeri aktarma ile eşleşmez, çünkü anlaşma türleri aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="586e0-134">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>

<span data-ttu-id="586e0-135">Genel olarak, Sözleşmenin adını belirtmek gerekli değildir ve çoğu sözleşme, anlaşma türü ve meta veriler bakımından tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="586e0-135">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="586e0-136">Ancak, belirli koşullarda, anlaşma adını doğrudan belirtmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="586e0-136">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="586e0-137">En yaygın durum, bir sınıfın temel öğeler gibi ortak bir türü paylaşan birkaç değeri dışarı aktardığı durumdur.</span><span class="sxs-lookup"><span data-stu-id="586e0-137">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="586e0-138">Sözleşme adı, veya özniteliğinin ilk parametresi olarak belirtilebilir `Import` `Export` .</span><span class="sxs-lookup"><span data-stu-id="586e0-138">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="586e0-139">Aşağıdaki kod, bir içeri aktarma ve belirtilen sözleşme adına sahip bir dışarı aktarma gösterir `MajorRevision` .</span><span class="sxs-lookup"><span data-stu-id="586e0-139">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>

```vb
Public Class MyExportClass

    'This one will match
    <Export("MajorRevision")>
    Public ReadOnly Property MajorRevision As Integer
        Get
            Return 4
        End Get
    End Property

    <Export("MinorRevision")>
    Public ReadOnly Property MinorRevision As Integer
        Get
            Return 16
        End Get
    End Property
End Class
```

```csharp
public class MyClass
{
    [Import("MajorRevision")]
    public int MajorRevision { get; set; }
}

public class MyExportClass
{
    [Export("MajorRevision")] //This one will match.
    public int MajorRevision = 4;

    [Export("MinorRevision")]
    public int MinorRevision = 16;
}
```

<span data-ttu-id="586e0-140">Anlaşma türü belirtilmemişse, hala içeri veya dışarı aktarma türünden çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="586e0-140">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="586e0-141">Ancak, anlaşma adı açıkça belirtilmiş olsa bile, aynı zamanda içeri aktarma ve dışarı aktarma için bir eşleşme olarak kabul edilmesi için anlaşma türü de tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="586e0-141">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="586e0-142">Örneğin, `MajorRevision` alan bir dize ise, çıkarılan anlaşma türleri eşleşmez ve dışarı aktarma, aynı anlaşma adına sahip olmasına rağmen içeri aktarma ile eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="586e0-142">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>

### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="586e0-143">Bir yöntemi içeri ve dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="586e0-143">Importing and Exporting a Method</span></span>

<span data-ttu-id="586e0-144">`Export`Özniteliği aynı zamanda bir yöntemi sınıf, özellik veya işlevle aynı şekilde süsde edebilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-144">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="586e0-145">Yöntem dışarı aktarmaları bir anlaşma türü veya sözleşme adı belirtmeli, çünkü tür çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="586e0-145">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="586e0-146">Belirtilen tür özel bir temsilci ya da gibi genel bir tür olabilir `Func` .</span><span class="sxs-lookup"><span data-stu-id="586e0-146">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="586e0-147">Aşağıdaki sınıf adlı bir yöntemi dışa aktarır `DoSomething` .</span><span class="sxs-lookup"><span data-stu-id="586e0-147">The following class exports a method named `DoSomething`.</span></span>

```vb
Public Class MyAddin

    'Explicitly specifying a generic type
    <Export(GetType(Func(Of Integer, String)))>
    Public Function DoSomething(ByVal TheParam As Integer) As String
        Return Nothing 'Function body goes here
    End Function

End Class
```

```csharp
public class MyAddin
{
    //Explicitly specifying a generic type.
    [Export(typeof(Func<int, string>))]
    public string DoSomething(int TheParam);
}
```

<span data-ttu-id="586e0-148">Bu sınıfta, `DoSomething` yöntemi tek bir `int` parametre alır ve döndürür `string` .</span><span class="sxs-lookup"><span data-stu-id="586e0-148">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="586e0-149">Bu dışarı aktarmayı eşleştirmek için, içeri aktarma bölümünde uygun bir üye bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="586e0-149">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="586e0-150">Aşağıdaki sınıf yöntemi içeri aktarır `DoSomething` .</span><span class="sxs-lookup"><span data-stu-id="586e0-150">The following class imports the `DoSomething` method.</span></span>

```vb
Public Class MyClass1

    'Contract name must match!
    <Import()>
    Public Property MajorRevision As Func(Of Integer, String)
End Class
```

```csharp
public class MyClass
{
    [Import] //Contract name must match!
    public Func<int, string> DoSomething { get; set; }
}
```

<span data-ttu-id="586e0-151">Nesnesinin kullanımı hakkında daha fazla bilgi için `Func<T, T>` bkz <xref:System.Func%602> ..</span><span class="sxs-lookup"><span data-stu-id="586e0-151">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a><span data-ttu-id="586e0-152">Içeri aktarmalar türleri</span><span class="sxs-lookup"><span data-stu-id="586e0-152">Types of Imports</span></span>

<span data-ttu-id="586e0-153">MEF, dinamik, geç, önkoşul ve isteğe bağlı olarak çeşitli içeri aktarma türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="586e0-153">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>

### <a name="dynamic-imports"></a><span data-ttu-id="586e0-154">Dinamik Içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="586e0-154">Dynamic Imports</span></span>

<span data-ttu-id="586e0-155">Bazı durumlarda, içeri aktarma sınıfı belirli bir sözleşme adına sahip olan her türlü dışarı aktarmaları eşleştirmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-155">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="586e0-156">Bu senaryoda, sınıfı *dinamik bir içeri aktarma*bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="586e0-156">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="586e0-157">Aşağıdaki içeri aktarma, sözleşme adı "TheString" olan tüm dışarı aktarma ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="586e0-157">The following import matches any export with contract name "TheString".</span></span>

```vb
Public Class MyClass1

    <Import("TheString")>
    Public Property MyAddin

End Class
```

```csharp
public class MyClass
{
    [Import("TheString")]
    public dynamic MyAddin { get; set; }
}
```

<span data-ttu-id="586e0-158">Anlaşma türü `dynamic` anahtar sözcükten çıkarıldığında, herhangi bir anlaşma türüyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="586e0-158">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="586e0-159">Bu durumda, bir içeri aktarmanın **her zaman** eşleştirilecek bir sözleşme adı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="586e0-159">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="586e0-160">(Sözleşme adı belirtilmemişse, içeri aktarma işlemi hiçbir dışarı Aktarımsız olacak şekilde değerlendirilir.) Aşağıdaki dışarı aktarımlar, önceki içeri aktarma ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="586e0-160">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>

```vb
<Export("TheString", GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class

<Export("TheString")>
Public Class MyToolbar

End Class
```

```csharp
[Export("TheString", typeof(IMyAddin))]
public class MyLogger : IMyAddin { }

[Export("TheString")]
public class MyToolbar { }
```

<span data-ttu-id="586e0-161">Açıkça içeri aktarma sınıfı, rastgele türdeki bir nesne ile başa çıkmak için hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="586e0-161">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>

### <a name="lazy-imports"></a><span data-ttu-id="586e0-162">Yavaş Içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="586e0-162">Lazy Imports</span></span>

<span data-ttu-id="586e0-163">Bazı durumlarda içeri aktarma sınıfı içeri aktarılan nesneye dolaylı bir başvuru gerektirebilir, böylece nesne hemen başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-163">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="586e0-164">Bu senaryoda, sınıfı bir anlaşma türü kullanarak bir *yavaş içeri aktarma* bildirebilir `Lazy<T>` .</span><span class="sxs-lookup"><span data-stu-id="586e0-164">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="586e0-165">Aşağıdaki içeri aktarma özelliği bir yavaş içeri aktarma bildirir.</span><span class="sxs-lookup"><span data-stu-id="586e0-165">The following importing property declares a lazy import.</span></span>

```vb
Public Class MyClass1

    <Import()>
    Public Property MyAddin As Lazy(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [Import]
    public Lazy<IMyAddin> MyAddin { get; set; }
}
```

<span data-ttu-id="586e0-166">Birleşim altyapısının bakış noktasından, bir sözleşme türü, `Lazy<T>` sözleşme türüyle aynı kabul edilir `T` .</span><span class="sxs-lookup"><span data-stu-id="586e0-166">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="586e0-167">Bu nedenle, önceki içeri aktarma aşağıdaki dışarı aktarma ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="586e0-167">Therefore, the previous import would match the following export.</span></span>

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="586e0-168">Sözleşme adı ve sözleşme türü, `Import` daha önce "temel Içeri aktarmalar ve dışarı aktarmalar" bölümünde açıklandığı gibi bir yavaş içeri aktarma özniteliğinde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-168">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>

### <a name="prerequisite-imports"></a><span data-ttu-id="586e0-169">Önkoşul Içeri aktarmaları</span><span class="sxs-lookup"><span data-stu-id="586e0-169">Prerequisite Imports</span></span>

<span data-ttu-id="586e0-170">Dışarı aktarılan MEF bölümleri genellikle doğrudan bir isteğe yanıt olarak veya eşleşen bir içeri aktarmayı doldurmanız gerektiğinde bileşim altyapısı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="586e0-170">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="586e0-171">Varsayılan olarak, bir bölüm oluştururken, bileşim altyapısı parametre-daha az oluşturucuyu kullanır.</span><span class="sxs-lookup"><span data-stu-id="586e0-171">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="586e0-172">Altyapının farklı bir Oluşturucu kullanmasını sağlamak için onu `ImportingConstructor` özniteliğiyle işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="586e0-172">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>

<span data-ttu-id="586e0-173">Her parçanın, bileşim altyapısı tarafından kullanılmak üzere yalnızca bir Oluşturucusu olabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-173">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="586e0-174">Parametresiz Oluşturucu ve öznitelik yok ya da birden `ImportingConstructor` fazla `ImportingConstructor` öznitelik sağlanması bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="586e0-174">Providing no parameterless constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>

<span data-ttu-id="586e0-175">Özniteliği ile işaretlenmiş bir oluşturucunun parametrelerini dolduracak şekilde `ImportingConstructor` , bu parametrelerin hepsi otomatik olarak içeri aktarmalar olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-175">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="586e0-176">Bu, kısmi başlatma sırasında kullanılan içeri aktarmaları bildirmek için kullanışlı bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="586e0-176">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="586e0-177">Aşağıdaki sınıf `ImportingConstructor` bir içeri aktarma bildirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="586e0-177">The following class uses `ImportingConstructor` to declare an import.</span></span>

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Parameterless constructor will NOT be used
    'because the ImportingConstructor
    'attribute is present.
    Public Sub New()

    End Sub

    'This constructor will be used.
    'An import with contract type IMyAddin
    'is declared automatically.
    <ImportingConstructor()>
    Public Sub New(ByVal MyAddin As IMyAddin)
        _theAddin = MyAddin
    End Sub

End Class
```

```csharp
public class MyClass
{
    private IMyAddin _theAddin;

    //Parameterless constructor will NOT be
    //used because the ImportingConstructor
    //attribute is present.
    public MyClass() { }

    //This constructor will be used.
    //An import with contract type IMyAddin is
    //declared automatically.
    [ImportingConstructor]
    public MyClass(IMyAddin MyAddin)
    {
        _theAddin = MyAddin;
    }
}
```

<span data-ttu-id="586e0-178">Varsayılan olarak, `ImportingConstructor` öznitelik, tüm parametre içeri aktarmaları için çıkarılan sözleşme türlerini ve sözleşme adlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="586e0-178">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="586e0-179">Parametreleri öznitelikleri ile süsleyerek bunu geçersiz kılmak mümkündür. Bu, `Import` daha sonra sözleşme türünü ve sözleşme adını açıkça tanımlayabilirler.</span><span class="sxs-lookup"><span data-stu-id="586e0-179">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="586e0-180">Aşağıdaki kod, bir üst sınıf yerine türetilmiş bir sınıfı içeri aktarmak için bu söz dizimini kullanan bir oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="586e0-180">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>

```vb
<ImportingConstructor()>
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)

End Sub
```

```csharp
[ImportingConstructor]
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)
{
    _theAddin = MyAddin;
}
```

<span data-ttu-id="586e0-181">Özellikle, koleksiyon parametreleriyle dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="586e0-181">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="586e0-182">Örneğin, `ImportingConstructor` türünde bir parametre içeren bir Oluşturucu üzerinde belirtirseniz, içeri aktarma türü bir dışarı aktarma `IEnumerable<int>` kümesi yerine, türü tek bir dışarı `IEnumerable<int>` aktarımdan eşleşir `int` .</span><span class="sxs-lookup"><span data-stu-id="586e0-182">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="586e0-183">Türünde bir dışarı aktarım kümesini eşleştirmek için `int` parametresini özniteliğiyle tasarlamanız gerekir `ImportMany` .</span><span class="sxs-lookup"><span data-stu-id="586e0-183">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>

<span data-ttu-id="586e0-184">Özniteliği tarafından içeri aktarmalar olarak belirtilen parametreler `ImportingConstructor` de *önkoşul içeri aktarmaları*olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="586e0-184">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="586e0-185">MEF, normalde dışarı aktarmalar ve içeri aktarmalar oluşturmak için bir *döngüye*izin verir.</span><span class="sxs-lookup"><span data-stu-id="586e0-185">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="586e0-186">Örneğin, bir döngüde nesne A 'nın, nesne a 'nın içe aktardığı, nesne a 'nın içe aktardığı yerdir. Normal koşullarda, bir döngüyle ilgili bir sorun değildir ve bileşim kapsayıcısı her iki nesneyi normal şekilde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="586e0-186">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>

<span data-ttu-id="586e0-187">Bir bölümün Oluşturucusu tarafından içeri aktarılan bir değer gerekliyse, bu nesne bir döngüye katılamaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-187">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="586e0-188">A nesnesi, nesne B 'nin oluşturulmadan önce oluşturulmasını gerektiriyorsa ve B nesnesi A nesnesini içeri aktardığında, bu durumda bir bileşim çözmeyecektir ve bir bileşim hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="586e0-188">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="586e0-189">Bu nedenle, Oluşturucu parametrelerine göre belirtilen içeri aktarmalar, tüm ön dışarı aktarımlardan önce kullanılması gereken herhangi bir dışarı aktarımdan önce doldurulmaları gereken önkoşul içeri aktarımlardır.</span><span class="sxs-lookup"><span data-stu-id="586e0-189">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>

### <a name="optional-imports"></a><span data-ttu-id="586e0-190">İsteğe bağlı Içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="586e0-190">Optional Imports</span></span>

<span data-ttu-id="586e0-191">`Import`Özniteliği, bölümün çalışması için bir gereksinim belirtir.</span><span class="sxs-lookup"><span data-stu-id="586e0-191">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="586e0-192">İçeri aktarma karşılanmıyorsa, bu bölümün kompozisyonu başarısız olur ve bölüm kullanılabilir olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="586e0-192">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>

<span data-ttu-id="586e0-193">Özelliğini kullanarak bir içeri aktarmanın *isteğe bağlı* olduğunu belirtebilirsiniz `AllowDefault` .</span><span class="sxs-lookup"><span data-stu-id="586e0-193">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="586e0-194">Bu durumda, içeri aktarma işlemi kullanılabilir herhangi bir dışarı aktarımlarla eşleşmediği halde içeri aktarma özelliği, özellik türü için varsayılan olarak ayarlanır ( `null` `false` Boolean Için, Boole değerleri veya sayısal özellikler için sıfır).) Aşağıdaki sınıf isteğe bağlı bir içeri aktarma kullanır.</span><span class="sxs-lookup"><span data-stu-id="586e0-194">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>

```vb
Public Class MyClass1

    <Import(AllowDefault:=True)>
    Public Property thePlugin As Plugin

    'If no matching export is available,
    'thePlugin will be set to null.
End Class
```

```csharp
public class MyClass
{
    [Import(AllowDefault = true)]
    public Plugin thePlugin { get; set; }

    //If no matching export is available,
    //thePlugin will be set to null.
}
```

### <a name="importing-multiple-objects"></a><span data-ttu-id="586e0-195">Birden çok nesne içeri aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="586e0-195">Importing Multiple Objects</span></span>

<span data-ttu-id="586e0-196">`Import`Özniteliği yalnızca bir ve yalnızca bir dışarı aktarma ile eşleştiğinde başarılı bir şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="586e0-196">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="586e0-197">Diğer durumlar, bir bileşim hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="586e0-197">Other cases will produce a composition error.</span></span> <span data-ttu-id="586e0-198">Aynı sözleşmeyle eşleşen birden fazla dışarı aktarmayı içeri aktarmak için `ImportMany` özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="586e0-198">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="586e0-199">Bu öznitelikle işaretlenen içeri aktarmalar her zaman isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="586e0-199">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="586e0-200">Örneğin, hiçbir eşleşen dışarı aktarma yoksa, bileşim başarısız olmaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-200">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="586e0-201">Aşağıdaki sınıf, türünde herhangi bir sayıda dışarı aktarma içeri aktarır `IMyAddin` .</span><span class="sxs-lookup"><span data-stu-id="586e0-201">The following class imports any number of exports of type `IMyAddin`.</span></span>

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<IMyAddin> MyAddin { get; set; }
}
```

<span data-ttu-id="586e0-202">İçeri aktarılan diziye, normal `IEnumerable<T>` sözdizimi ve yöntemleri kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-202">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="586e0-203">Bunun yerine sıradan bir Array () kullanmak da mümkündür `IMyAddin[]` .</span><span class="sxs-lookup"><span data-stu-id="586e0-203">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>

<span data-ttu-id="586e0-204">Bu model, söz dizimi ile birlikte kullandığınızda çok önemli olabilir `Lazy<T>` .</span><span class="sxs-lookup"><span data-stu-id="586e0-204">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="586e0-205">Örneğin,, ve kullanarak `ImportMany` , `IEnumerable<T>` `Lazy<T>` dolaylı başvuruları herhangi bir sayıda nesneye aktarabilir ve yalnızca gerekli olanları örnekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="586e0-205">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="586e0-206">Aşağıdaki sınıf bu kalıbı gösterir.</span><span class="sxs-lookup"><span data-stu-id="586e0-206">The following class shows this pattern.</span></span>

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }
}
```

<a name="avoiding_discovery"></a>

## <a name="avoiding-discovery"></a><span data-ttu-id="586e0-207">Bulmaktan kaçınma</span><span class="sxs-lookup"><span data-stu-id="586e0-207">Avoiding Discovery</span></span>

<span data-ttu-id="586e0-208">Bazı durumlarda, bir bölümün bir kataloğun parçası olarak bulunmasını engellemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="586e0-208">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="586e0-209">Örneğin, bölüm, öğesinden Devralınana yönelik bir temel sınıf olabilir, ancak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-209">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="586e0-210">Bunu yapmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="586e0-210">There are two ways to accomplish this.</span></span> <span data-ttu-id="586e0-211">İlk olarak, `abstract` bölüm sınıfında anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="586e0-211">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="586e0-212">Soyut sınıflar hiçbir şekilde dışa aktarma sağlamaz, ancak onlardan türetilen sınıflara devralınan dışarı aktarmalar sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-212">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>

<span data-ttu-id="586e0-213">Sınıf soyut hale getiril, özniteliği ile süslenebilir `PartNotDiscoverable` .</span><span class="sxs-lookup"><span data-stu-id="586e0-213">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="586e0-214">Bu öznitelikle donatılmış bir bölüm, hiçbir katalogda yer almaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-214">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="586e0-215">Aşağıdaki örnekte bu desenler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="586e0-215">The following example demonstrates these patterns.</span></span> <span data-ttu-id="586e0-216">`DataOne`, katalog tarafından keşfedilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-216">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="586e0-217">`DataTwo`Soyut olduğundan, bulunamayacaktır.</span><span class="sxs-lookup"><span data-stu-id="586e0-217">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="586e0-218">`DataThree`Özniteliği kullanılmasından bu yana `PartNotDiscoverable` bulunamayacaktır.</span><span class="sxs-lookup"><span data-stu-id="586e0-218">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>

```vb
<Export()>
Public Class DataOne
    'This part will be discovered
    'as normal by the catalog.
End Class

<Export()>
Public MustInherit Class DataTwo
    'This part will not be discovered
    'by the catalog.
End Class

<PartNotDiscoverable()>
<Export()>
Public Class DataThree
    'This part will also not be discovered
    'by the catalog.
End Class
```

```csharp
[Export]
public class DataOne
{
    //This part will be discovered
    //as normal by the catalog.
}

[Export]
public abstract class DataTwo
{
    //This part will not be discovered
    //by the catalog.
}

[PartNotDiscoverable]
[Export]
public class DataThree
{
    //This part will also not be discovered
    //by the catalog.
}
```

<a name="metadata_and_metadata_views"></a>

## <a name="metadata-and-metadata-views"></a><span data-ttu-id="586e0-219">Meta veriler ve meta veri görünümleri</span><span class="sxs-lookup"><span data-stu-id="586e0-219">Metadata and Metadata Views</span></span>

<span data-ttu-id="586e0-220">Dışarı aktarmalar, kendileri hakkında, *meta veri*olarak bilinen ek bilgiler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-220">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="586e0-221">Meta veriler, aktarılan nesnenin özelliklerini içeri aktarma bölümüne iletmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-221">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="586e0-222">İçeri aktarma bölümü bu verileri kullanarak hangi dışarı aktarımların kullanılacağını seçebilir veya onu oluşturmak zorunda kalmadan bir dışarı aktarma hakkında bilgi toplayabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-222">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="586e0-223">Bu nedenle, meta verilerin kullanılması için bir içeri aktarmanın yavaş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="586e0-223">For this reason, an import must be lazy to use metadata.</span></span>

<span data-ttu-id="586e0-224">Meta verileri kullanmak için genellikle meta veri *görünümü*olarak bilinen bir arabirim bildirirsiniz, bu da hangi meta verilerin kullanılabilir olacağını bildirir.</span><span class="sxs-lookup"><span data-stu-id="586e0-224">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="586e0-225">Meta veri görünümü arabiriminin yalnızca özellikleri olmalıdır ve bu özelliklerin `get` erişimcileri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="586e0-225">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="586e0-226">Aşağıdaki arabirim bir örnek meta veri görünümüdür.</span><span class="sxs-lookup"><span data-stu-id="586e0-226">The following interface is an example metadata view.</span></span>

```vb
Public Interface IPluginMetadata

    ReadOnly Property Name As String

    <DefaultValue(1)>
    ReadOnly Property Version As Integer

End Interface
```

```csharp
public interface IPluginMetadata
{
    string Name { get; }

    [DefaultValue(1)]
    int Version { get; }
}
```

<span data-ttu-id="586e0-227">Ayrıca, meta veri görünümü olarak genel bir koleksiyon kullanmak da mümkündür `IDictionary<string, object>` , ancak bu, tür denetimi avantajlarından yararlanır ve kaçınılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="586e0-227">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>

<span data-ttu-id="586e0-228">Normalde, meta veri görünümündeki adlı tüm özellikler zorunludur ve bunları sağlamayan tüm dışarı aktarımlar bir eşleşme olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="586e0-228">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="586e0-229">`DefaultValue`Özniteliği bir özelliğin isteğe bağlı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="586e0-229">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="586e0-230">Özellik dahil değilse, parametresi olarak belirtilen varsayılan değere atanır `DefaultValue` .</span><span class="sxs-lookup"><span data-stu-id="586e0-230">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="586e0-231">Aşağıdakiler meta verilerle donatılmış iki farklı sınıftır.</span><span class="sxs-lookup"><span data-stu-id="586e0-231">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="586e0-232">Bu sınıfların her ikisi de önceki meta veri görünümüyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="586e0-232">Both of these classes would match the previous metadata view.</span></span>

```vb
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class MyLogger
    Implements IPlugin

End Class

'Version is not required because of the DefaultValue
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Disk Writer")>
Public Class DWriter
    Implements IPlugin

End Class
```

```csharp
[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
}

[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Disk Writer")]
    //Version is not required because of the DefaultValue
public class DWriter : IPlugin
{
}
```

<span data-ttu-id="586e0-233">Meta veriler özniteliği `Export` kullanılarak öznitelikten sonra ifade edilir `ExportMetadata` .</span><span class="sxs-lookup"><span data-stu-id="586e0-233">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="586e0-234">Her meta veri parçası bir ad/değer çiftinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="586e0-234">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="586e0-235">Meta verilerin ad kısmı meta veri görünümündeki uygun özelliğin adıyla eşleşmelidir ve değer bu özelliğe atanır.</span><span class="sxs-lookup"><span data-stu-id="586e0-235">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>

<span data-ttu-id="586e0-236">Varsa, hangi meta veri görünümünün kullanımda olacağını belirten içeri aktarıcıdır.</span><span class="sxs-lookup"><span data-stu-id="586e0-236">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="586e0-237">Meta veri içeren bir içeri aktarma, için ikinci tür parametresi olarak meta veri arabirimi ile bir yavaş içeri aktarma olarak belirtilir `Lazy<T,T>` .</span><span class="sxs-lookup"><span data-stu-id="586e0-237">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="586e0-238">Aşağıdaki sınıf önceki bölümü meta verilerle içe aktarır.</span><span class="sxs-lookup"><span data-stu-id="586e0-238">The following class imports the previous part with metadata.</span></span>

```vb
Public Class Addin

    <Import()>
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)
End Class
```

```csharp
public class Addin
{
    [Import]
    public Lazy<IPlugin, IPluginMetadata> plugin;
}
```

<span data-ttu-id="586e0-239">Birçok durumda, `ImportMany` kullanılabilir içeri aktarmalar aracılığıyla ayrıştırılacak ve yalnızca bir tane seçip örnekleyerek veya bir koleksiyonu belirli bir koşulla eşleşecek şekilde filtreleyecek şekilde meta verileri özniteliğiyle birleştirmek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="586e0-239">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="586e0-240">Aşağıdaki sınıf yalnızca `IPlugin` `Name` "günlükçü" değerine sahip nesneleri örnekleyen.</span><span class="sxs-lookup"><span data-stu-id="586e0-240">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>

```vb
Public Class User

    <ImportMany()>
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))

    Public Function InstantiateLogger() As IPlugin

        Dim logger As IPlugin
        logger = Nothing

        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins
            If Plugin.Metadata.Name = "Logger" Then
                logger = Plugin.Value
            End If
        Next
        Return logger
    End Function

End Class
```

```csharp
public class User
{
    [ImportMany]
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;

    public IPlugin InstantiateLogger()
    {
        IPlugin logger = null;

        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)
        {
            if (plugin.Metadata.Name == "Logger")
                logger = plugin.Value;
        }
        return logger;
    }
}
```

<a name="import_and_export_inheritance"></a>

## <a name="import-and-export-inheritance"></a><span data-ttu-id="586e0-241">Devralmayı içeri ve dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="586e0-241">Import and Export Inheritance</span></span>

<span data-ttu-id="586e0-242">Bir sınıf bir bölümden devralırsa, bu sınıf da bir parça olabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-242">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="586e0-243">İçeri aktarmalar her zaman alt sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="586e0-243">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="586e0-244">Bu nedenle, bir parçanın bir alt sınıfı her zaman üst sınıfı ile aynı içeri aktarmaları olan bir bölüm olacaktır.</span><span class="sxs-lookup"><span data-stu-id="586e0-244">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>

<span data-ttu-id="586e0-245">Özniteliği kullanılarak belirtilen dışarı aktarmalar, alt `Export` sınıflar tarafından devralınmaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-245">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="586e0-246">Ancak, bir bölüm özniteliğini kullanarak kendisini dışarı aktarabilir `InheritedExport` .</span><span class="sxs-lookup"><span data-stu-id="586e0-246">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="586e0-247">Bölümün alt sınıfları, sözleşme adı ve anlaşma türü dahil olmak üzere aynı dışarı aktarmayı alır ve verir.</span><span class="sxs-lookup"><span data-stu-id="586e0-247">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="586e0-248">Bir `Export` özniteliğin aksine, `InheritedExport` üye düzeyinde değil yalnızca sınıf düzeyinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-248">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="586e0-249">Bu nedenle, üye düzeyinde dışarı aktarımlar hiçbir şekilde devralınmaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-249">Therefore, member-level exports can never be inherited.</span></span>

<span data-ttu-id="586e0-250">Aşağıdaki dört sınıf içeri ve dışarı aktarma devralma ilkelerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="586e0-250">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="586e0-251">`NumTwo`öğesinden devraldığından `NumOne` `NumTwo` içeri aktarma işlemi yapılır `IMyData` .</span><span class="sxs-lookup"><span data-stu-id="586e0-251">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="586e0-252">Sıradan dışarı aktarmalar devralınmaz, `NumTwo` Bu nedenle hiçbir şeyi dışarı aktarmaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-252">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="586e0-253">`NumFour`öğesinden devralır `NumThree` .</span><span class="sxs-lookup"><span data-stu-id="586e0-253">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="586e0-254">`NumThree`Kullanıldığı için `InheritedExport` , `NumFour` sözleşme türünde bir dışarı aktarma işlemi vardır `NumThree` .</span><span class="sxs-lookup"><span data-stu-id="586e0-254">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="586e0-255">Üye düzeyinde dışarı aktarımlar hiçbir şekilde devralınmaz, bu nedenle `IMyData` dışarı aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-255">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>

```vb
<Export()>
Public Class NumOne
    <Import()>
    Public Property MyData As IMyData
End Class

Public Class NumTwo
    Inherits NumOne

    'Imports are always inherited, so NumTwo will
    'Import IMyData

    'Ordinary exports are not inherited, so
    'NumTwo will NOT export anything.  As a result it
    'will not be discovered by the catalog!

End Class

<InheritedExport()>
Public Class NumThree

    <Export()>
    Public Property MyData As IMyData

    'This part provides two exports, one of
    'contract type NumThree, and one of
    'contract type IMyData.

End Class

Public Class NumFour
    Inherits NumThree

    'Because NumThree used InheritedExport,
    'this part has one export with contract
    'type NumThree.

    'Member-level exports are never inherited,
    'so IMyData is not exported.

End Class
```

```csharp
[Export]
public class NumOne
{
    [Import]
    public IMyData MyData { get; set; }
}

public class NumTwo : NumOne
{
    //Imports are always inherited, so NumTwo will
    //import IMyData.

    //Ordinary exports are not inherited, so
    //NumTwo will NOT export anything. As a result it
    //will not be discovered by the catalog!
}

[InheritedExport]
public class NumThree
{
    [Export]
    Public IMyData MyData { get; set; }

    //This part provides two exports, one of
    //contract type NumThree, and one of
    //contract type IMyData.
}

public class NumFour : NumThree
{
    //Because NumThree used InheritedExport,
    //this part has one export with contract
    //type NumThree.

    //Member-level exports are never inherited,
    //so IMyData is not exported.
}
```

<span data-ttu-id="586e0-256">Bir öznitelikle ilişkili meta veriler varsa `InheritedExport` , bu meta veriler de devralınacaktır.</span><span class="sxs-lookup"><span data-stu-id="586e0-256">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="586e0-257">(Daha fazla bilgi için önceki "meta veriler ve meta veri görünümleri" bölümüne bakın.) Devralınan meta veriler alt sınıf tarafından değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="586e0-257">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="586e0-258">Ancak, `InheritedExport` aynı sözleşme adı ve anlaşma türüyle özniteliği yeniden bildirerek, ancak yeni meta veriler ile, alt sınıf devralınan meta verileri yeni meta verilerle değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-258">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="586e0-259">Aşağıdaki sınıf bu ilkeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="586e0-259">The following class demonstrates this principle.</span></span> <span data-ttu-id="586e0-260">`MegaLogger`Bölüm öğesinden devralır `Logger` ve `InheritedExport` özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="586e0-260">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="586e0-261">`MegaLogger`Durum adlı yeni meta verileri yeniden bildirdiğinden, ' den adı ve sürüm meta verilerini içermez `Logger` .</span><span class="sxs-lookup"><span data-stu-id="586e0-261">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>

```vb
<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class Logger
    Implements IPlugin

    'Exports with contract type IPlugin
    'and metadata "Name" and "Version".
End Class

Public Class SuperLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Name" and "Version", exactly the same
    'as the Logger class.

End Class

<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Status", "Green")>
Public Class MegaLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Status" only. Re-declaring
    'the attribute replaces all metadata.

End Class
```

```csharp
[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version".
}

public class SuperLogger : Logger
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version", exactly the same
    //as the Logger class.
}

[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Status", "Green")]
public class MegaLogger : Logger        {
    //Exports with contract type IPlugin and
    //metadata "Status" only. Re-declaring
    //the attribute replaces all metadata.
}
```

<span data-ttu-id="586e0-262">`InheritedExport`Meta verileri geçersiz kılmak için özniteliği yeniden bildirirken, anlaşma türlerinin aynı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="586e0-262">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="586e0-263">(Önceki örnekte, `IPlugin` Sözleşme türüdür.) Farklıysa, ikinci öznitelik bölümden ikinci bir bağımsız dışarı aktarma işlemi oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="586e0-263">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="586e0-264">Genellikle bu, `InheritedExport` Önceki örnekte gösterildiği gibi bir özniteliği geçersiz kıldığınızda anlaşma türünü açıkça belirtmeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="586e0-264">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>

<span data-ttu-id="586e0-265">Arabirimler doğrudan oluşturulamadıklarından, genellikle veya öznitelikleriyle birlikte tasarlanamazlar `Export` `Import` .</span><span class="sxs-lookup"><span data-stu-id="586e0-265">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="586e0-266">Bununla birlikte, bir arabirim, `InheritedExport` arabirim düzeyinde bir öznitelikle ilişkilendirilebilir ve ilgili tüm meta verilerle birlikte dışarı aktarma işlemi herhangi bir uygulama sınıfı tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="586e0-266">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="586e0-267">Ancak, arabirim bir bölüm olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-267">The interface itself will not be available as a part, however.</span></span>

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a><span data-ttu-id="586e0-268">Özel dışarı aktarma öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="586e0-268">Custom Export Attributes</span></span>

<span data-ttu-id="586e0-269">Temel dışa aktarma öznitelikleri `Export` ve `InheritedExport` , meta verileri öznitelik özellikleri olarak içerecek şekilde genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-269">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="586e0-270">Bu teknik, benzer meta verileri birçok parçaya uygulamak veya meta veri özniteliklerinin devralma ağacını oluşturmak için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="586e0-270">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>

<span data-ttu-id="586e0-271">Özel bir öznitelik, anlaşma türünü, anlaşma adını veya diğer meta verileri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-271">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="586e0-272">Özel bir öznitelik tanımlamak için, (veya) öğesinden devralan bir sınıf, `ExportAttribute` `InheritedExportAttribute` özniteliğiyle birlikte tasarlanmalıdır `MetadataAttribute` .</span><span class="sxs-lookup"><span data-stu-id="586e0-272">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="586e0-273">Aşağıdaki sınıf özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="586e0-273">The following class defines a custom attribute.</span></span>

```vb
<MetadataAttribute()>
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>
Public Class MyAttribute
    Inherits ExportAttribute

    Public Property MyMetadata As String

    Public Sub New(ByVal myMetadata As String)
        MyBase.New(GetType(IMyAddin))

        myMetadata = myMetadata
    End Sub

End Class
```

```csharp
[MetadataAttribute]
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]
public class MyAttribute : ExportAttribute
{
    public MyAttribute(string myMetadata)
        : base(typeof(IMyAddin))
    {
        MyMetadata = myMetadata;
    }

    public string MyMetadata { get; private set; }
}
```

<span data-ttu-id="586e0-274">Bu sınıf, `MyAttribute` anlaşma türü ile adlı özel bir özniteliği `IMyAddin` ve adında bazı meta verileri tanımlar `MyMetadata` .</span><span class="sxs-lookup"><span data-stu-id="586e0-274">This class defines a custom attribute named `MyAttribute` with contract type `IMyAddin` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="586e0-275">Özniteliği ile işaretlenmiş bir sınıftaki tüm özellikler `MetadataAttribute` özel özniteliğinde tanımlanmış meta veriler olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-275">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="586e0-276">Aşağıdaki iki bildirim eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="586e0-276">The following two declarations are equivalent.</span></span>

```vb
<Export(GetType(IMyAddin))>
<ExportMetadata("MyMetadata", "theData")>
Public Property myAddin As MyAddin
```

```vb
<MyAttribute("theData")>
Public Property myAddin As MyAddin
```

```csharp
[Export(typeof(IMyAddin)),
    ExportMetadata("MyMetadata", "theData")]
public MyAddin myAddin { get; set; }
```

```csharp
[MyAttribute("theData")]
public MyAddin myAddin { get; set; }
```

<span data-ttu-id="586e0-277">İlk bildirimde, anlaşma türü ve meta veriler açıkça tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="586e0-277">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="586e0-278">İkinci bildirimde, anlaşma türü ve meta veriler, özelleştirilmiş öznitelikte örtülü olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="586e0-278">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="586e0-279">Özellikle, büyük miktarda özdeş meta verilerin birçok parçaya uygulanması gerektiği durumlarda (örneğin, yazar veya telif hakkı bilgileri), özel bir öznitelik kullanmak çok fazla zaman ve çoğaltma kazandırabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-279">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="586e0-280">Ayrıca, çeşitlere izin vermek için özel özniteliklerin devralma ağaçları oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-280">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>

<span data-ttu-id="586e0-281">Özel bir öznitelikte isteğe bağlı meta veri oluşturmak için `DefaultValue` özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="586e0-281">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="586e0-282">Bu öznitelik özel öznitelik sınıfındaki bir özelliğe uygulandığında, düzenlenmiş özelliğin isteğe bağlı olduğunu ve bir dışarı aktarma tarafından sağlanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="586e0-282">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="586e0-283">Özelliği için bir değer sağlanmadığında, özellik türü (genellikle `null` , `false` , veya 0) için varsayılan değer atanır.</span><span class="sxs-lookup"><span data-stu-id="586e0-283">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>

<a name="creation_policies"></a>

## <a name="creation-policies"></a><span data-ttu-id="586e0-284">Oluşturma Ilkeleri</span><span class="sxs-lookup"><span data-stu-id="586e0-284">Creation Policies</span></span>

<span data-ttu-id="586e0-285">Bir parça bir içeri aktarma belirttiğinde ve bileşim gerçekleştirildiğinde, bileşim kapsayıcısı eşleşen bir dışarı aktarma bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="586e0-285">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="586e0-286">İçeri aktarma işlemi başarıyla dışarı aktarma ile eşleşiyorsa, içeri aktarma üyesi dışa aktarılan nesnenin bir örneğine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="586e0-286">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="586e0-287">Bu örneğin nereden geldiği, dışa aktarılan bölümün *oluşturma ilkesi*tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="586e0-287">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>

<span data-ttu-id="586e0-288">Olası iki oluşturma ilkesi *paylaşılır* ve *paylaşılmaz*.</span><span class="sxs-lookup"><span data-stu-id="586e0-288">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="586e0-289">Paylaşılan bir oluşturma ilkesinin bulunduğu bir bölüm, söz konusu sözleşmenin bir parçası için kapsayıcıdaki her içeri aktarma arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="586e0-289">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="586e0-290">Bileşim altyapısı bir eşleşme bulduğunda ve bir içeri aktarma özelliği ayarlamaya sahipse, yalnızca bir tane yoksa, bölümün yeni bir kopyasını oluşturur. Aksi takdirde, mevcut kopyayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="586e0-290">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="586e0-291">Bu, birçok nesnenin aynı bölüme başvurmuş olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="586e0-291">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="586e0-292">Bu tür parçalar birçok yerden değiştirilebilen iç duruma dayanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="586e0-292">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="586e0-293">Bu ilke statik bölümler, hizmet sağlayan parçalar ve çok fazla bellek veya diğer kaynakları kullanan parçalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="586e0-293">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>

<span data-ttu-id="586e0-294">Dışarı aktarmalarından biri için eşleşen bir içeri aktarma bulunduğunda, paylaşılmayan oluşturma ilkesini içeren bir bölüm oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="586e0-294">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="586e0-295">Bu nedenle, kapsayıcının dışarı aktarılan sözleşmelerinden biriyle eşleşen kapsayıcıdaki her içeri aktarma işlemi için yeni bir kopya oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="586e0-295">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="586e0-296">Bu kopyaların iç durumu paylaşılmayacak.</span><span class="sxs-lookup"><span data-stu-id="586e0-296">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="586e0-297">Bu ilke, her içeri aktarmanın kendi iç durumunu gerektirdiği parçalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="586e0-297">This policy is appropriate for parts where each import requires its own internal state.</span></span>

<span data-ttu-id="586e0-298">İçeri aktarma ve dışarı aktarma, bir bölümün oluşturma ilkesini, veya değerlerinin arasından belirtebilir `Shared` `NonShared` `Any` .</span><span class="sxs-lookup"><span data-stu-id="586e0-298">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="586e0-299">Varsayılan değer `Any` içeri ve dışarı aktarma içindir.</span><span class="sxs-lookup"><span data-stu-id="586e0-299">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="586e0-300">`Shared` `NonShared` Yalnızca aynısını belirten veya belirten bir içeri aktarma ile eşleşen bir dışarı aktarma işlemi `Any` .</span><span class="sxs-lookup"><span data-stu-id="586e0-300">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="586e0-301">Benzer şekilde, veya belirten bir içeri aktarma `Shared` `NonShared` yalnızca aynısını belirten veya belirten bir dışarı aktarma ile eşleşir `Any` .</span><span class="sxs-lookup"><span data-stu-id="586e0-301">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="586e0-302">Uyumsuz oluşturma ilkelerine sahip içeri aktarmalar ve dışarı aktarmalar, sözleşme adı veya sözleşme türü eşleşme olmayan bir içeri ve dışarı aktarma ile aynı şekilde bir eşleşme olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="586e0-302">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="586e0-303">Hem içeri ve dışarı aktarma hem de `Any` bir oluşturma ilkesi ve için varsayılan değer belirtmez, `Any` oluşturma ilkesi varsayılan olarak paylaşılacaktır.</span><span class="sxs-lookup"><span data-stu-id="586e0-303">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>

<span data-ttu-id="586e0-304">Aşağıdaki örnek, oluşturma ilkelerini belirten içeri ve dışarı aktarmaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="586e0-304">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="586e0-305">`PartOne`bir oluşturma ilkesi belirtmez, bu nedenle varsayılan olur `Any` .</span><span class="sxs-lookup"><span data-stu-id="586e0-305">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="586e0-306">`PartTwo`bir oluşturma ilkesi belirtmez, bu nedenle varsayılan olur `Any` .</span><span class="sxs-lookup"><span data-stu-id="586e0-306">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="586e0-307">Hem içeri hem de dışarı aktarma varsayılan `Any` olarak `PartOne` paylaşılacak.</span><span class="sxs-lookup"><span data-stu-id="586e0-307">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="586e0-308">`PartThree`bir `Shared` oluşturma ilkesi belirtir, `PartTwo` Bu nedenle `PartThree` aynı kopyasını paylaşır `PartOne` .</span><span class="sxs-lookup"><span data-stu-id="586e0-308">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="586e0-309">`PartFour`bir `NonShared` oluşturma ilkesi belirtir, `PartFour` Bu nedenle içinde paylaşılmayacak `PartFive` .</span><span class="sxs-lookup"><span data-stu-id="586e0-309">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="586e0-310">`PartSix`bir `NonShared` oluşturma ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="586e0-310">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="586e0-311">`PartFive`ve `PartSix` her biri ayrı birer kopyasını alır `PartFour` .</span><span class="sxs-lookup"><span data-stu-id="586e0-311">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="586e0-312">`PartSeven`bir `Shared` oluşturma ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="586e0-312">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="586e0-313">Oluşturma ilkesiyle dışarı aktarılmış olmadığından `PartFour` `Shared` , `PartSeven` içeri aktarma hiçbir şeyle eşleşmez ve doldurulmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="586e0-313">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>

```vb
<Export()>
Public Class PartOne
    'The default creation policy for an export is Any.
End Class

Public Class PartTwo

    <Import()>
    Public Property partOne As PartOne

    'The default creation policy for an import is Any.
    'If both policies are Any, the part will be shared.

End Class

Public Class PartThree

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partOne As PartOne

    'The Shared creation policy is explicitly specified.
    'PartTwo and PartThree will receive references to the
    'SAME copy of PartOne.

End Class

<Export()>
<PartCreationPolicy(CreationPolicy.NonShared)>
Public Class PartFour
    'The NonShared creation policy is explicitly specified.
End Class

Public Class PartFive

    <Import()>
    Public Property partFour As PartFour

    'The default creation policy for an import is Any.
    'Since the export's creation policy was explicitly
    'defined, the creation policy for this property will
    'be non-shared.

End Class

Public Class PartSix

    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>
    Public Property partFour As PartFour

    'Both import and export specify matching creation
    'policies.  PartFive and PartSix will each receive
    'SEPARATE copies of PartFour, each with its own
    'internal state.

End Class

Public Class PartSeven

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partFour As PartFour

    'A creation policy mismatch.  Because there is no
    'exported PartFour with a creation policy of Shared,
    'this import does not match anything and will not be
    'filled.

End Class
```

```csharp
[Export]
public class PartOne
{
    //The default creation policy for an export is Any.
}

public class PartTwo
{
    [Import]
    public PartOne partOne { get; set; }

    //The default creation policy for an import is Any.
    //If both policies are Any, the part will be shared.
}

public class PartThree
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartOne partOne { get; set; }

    //The Shared creation policy is explicitly specified.
    //PartTwo and PartThree will receive references to the
    //SAME copy of PartOne.
}

[Export]
[PartCreationPolicy(CreationPolicy.NonShared)]
public class PartFour
{
    //The NonShared creation policy is explicitly specified.
}

public class PartFive
{
    [Import]
    public PartFour partFour { get; set; }

    //The default creation policy for an import is Any.
    //Since the export's creation policy was explicitly
    //defined, the creation policy for this property will
    //be non-shared.
}

public class PartSix
{
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]
    public PartFour partFour { get; set; }

    //Both import and export specify matching creation
    //policies.  PartFive and PartSix will each receive
    //SEPARATE copies of PartFour, each with its own
    //internal state.
}

public class PartSeven
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartFour partFour { get; set; }

    //A creation policy mismatch.  Because there is no
    //exported PartFour with a creation policy of Shared,
    //this import does not match anything and will not be
    //filled.
}
```

<a name="life_cycle_and_disposing"></a>

## <a name="life-cycle-and-disposing"></a><span data-ttu-id="586e0-314">Yaşam döngüsü ve elden atma</span><span class="sxs-lookup"><span data-stu-id="586e0-314">Life Cycle and Disposing</span></span>

<span data-ttu-id="586e0-315">Parçalar bileşim kapsayıcısında barındırıldığından, bunların yaşam döngüsü sıradan nesnelerden daha karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-315">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="586e0-316">Parçalar, iki önemli yaşam döngüyle ilgili arabirimler uygulayabilir: `IDisposable` ve `IPartImportsSatisfiedNotification` .</span><span class="sxs-lookup"><span data-stu-id="586e0-316">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>

<span data-ttu-id="586e0-317">Çalışma veya kaynakların serbest bırakılması gereken `IDisposable` , .NET Framework nesneler için her zamanki gibi, çalışması gereken bölümlerin uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="586e0-317">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="586e0-318">Ancak, kapsayıcı parçalar için başvuruları oluşturduğundan ve sakladığı için, yalnızca bir bölüme sahip olan kapsayıcı `Dispose` üzerinde yöntemi çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="586e0-318">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="586e0-319">Kapsayıcının kendisi `IDisposable` ve içindeki temizleme işleminin bir kısmı, `Dispose` `Dispose` sahip olduğu tüm bölümleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="586e0-319">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="586e0-320">Bu nedenle, derleme kapsayıcısını her zaman ve sahip olduğu tüm parçalar artık gerekli olmadığında atmalısınız.</span><span class="sxs-lookup"><span data-stu-id="586e0-320">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>

<span data-ttu-id="586e0-321">Uzun süreli oluşturma kapsayıcıları için, paylaşılmayan bir oluşturma ilkesiyle bölümlere göre bellek tüketimi bir sorun olabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-321">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="586e0-322">Bu paylaşılmayan bölümler birden çok kez oluşturulabilir ve kapsayıcının kendisi atılana kadar atılamaz.</span><span class="sxs-lookup"><span data-stu-id="586e0-322">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="586e0-323">Bu sorunu ele almak için kapsayıcı `ReleaseExport` yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="586e0-323">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="586e0-324">Bu yöntemi paylaşılmayan bir dışarı aktarma üzerinde çağırmak, bu dışarı aktarmayı bileşim kapsayıcısından kaldırır ve bunu ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="586e0-324">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="586e0-325">Yalnızca kaldırılan dışarı aktarma tarafından kullanılan ve bu nedenle ağacın üzerinde kullanılan parçalar da kaldırılır ve silinir.</span><span class="sxs-lookup"><span data-stu-id="586e0-325">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="586e0-326">Bu şekilde, kaynaklar bileşim kapsayıcısının kendisini elden çıkarmadan geri kazanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="586e0-326">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>

<span data-ttu-id="586e0-327">`IPartImportsSatisfiedNotification`adlı bir yöntemi içerir `OnImportsSatisfied` .</span><span class="sxs-lookup"><span data-stu-id="586e0-327">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="586e0-328">Bu yöntem, oluşturma işlemi tamamlandığında ve bölümün içeri aktarmaları kullanıma hazırlandığında arabirimini uygulayan herhangi bir bölümde bileşim kapsayıcısı tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="586e0-328">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="586e0-329">Bölümler, diğer parçaların içeri aktarmalarını dolduracak şekilde bileşim altyapısı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="586e0-329">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="586e0-330">Bir bölümün içeri aktarmaları bir şekilde ayarlanmadan önce, bu değerler öznitelik kullanılarak önkoşul olarak belirtilmediği sürece, Bölüm oluşturucusunda içeri aktarılan değerleri kullanan veya bunları değiştiren herhangi bir başlatma gerçekleştiremezsiniz `ImportingConstructor` .</span><span class="sxs-lookup"><span data-stu-id="586e0-330">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="586e0-331">Bu normal olarak tercih edilen yöntemdir, ancak bazı durumlarda, Oluşturucu Ekleme kullanılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="586e0-331">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="586e0-332">Bu durumlarda, ' de başlatma gerçekleştirilebilir `OnImportsSatisfied` ve bölümünün uygulanması gerekir `IPartImportsSatisfiedNotification` .</span><span class="sxs-lookup"><span data-stu-id="586e0-332">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>

## <a name="see-also"></a><span data-ttu-id="586e0-333">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="586e0-333">See also</span></span>

- [<span data-ttu-id="586e0-334">Channel 9 videosu: uygulamalarınızı Managed Extensibility Framework açın</span><span class="sxs-lookup"><span data-stu-id="586e0-334">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [<span data-ttu-id="586e0-335">Channel 9 videosu: Managed Extensibility Framework (MEF) 2,0</span><span class="sxs-lookup"><span data-stu-id="586e0-335">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)

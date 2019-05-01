---
title: Öznitelikli Programlama Modeline Genel Bakış (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09eb37fd2c1bf77e981a2eb7952b1fff5110e977
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872384"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="5cc86-102">Öznitelikli Programlama Modeline Genel Bakış (MEF)</span><span class="sxs-lookup"><span data-stu-id="5cc86-102">Attributed Programming Model Overview (MEF)</span></span>

<span data-ttu-id="5cc86-103">İçinde Yönetilen Genişletilebilirlik Çerçevesi (MEF), bir *programlama modeli* MEF çalıştığı kavramsal nesne kümesini tanımlayan belirli bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-103">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="5cc86-104">Kavramsal bu nesneler, bölümleri, içeri aktarmalar ve dışarı aktarmaları içerir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-104">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="5cc86-105">MEF bu nesneleri kullanan, ancak nasıl temsil belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="5cc86-105">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="5cc86-106">Bu nedenle, çok çeşitli programlama modellerini programlama modelleri de dahil olmak üzere özelleştirilmiş mümkün.</span><span class="sxs-lookup"><span data-stu-id="5cc86-106">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>

<span data-ttu-id="5cc86-107">MEF kullanılan programlama modeli varsayılan *öznitelikli programlama modeli*.</span><span class="sxs-lookup"><span data-stu-id="5cc86-107">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="5cc86-108">Öznitelikli Programlama modeli bölümleri, sıradan bir .NET Framework sınıf süslemek özniteliklerle içeri aktarmalar, dışarı aktarma ve diğer nesneleri tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-108">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="5cc86-109">Bu konuda, bir MEF uygulaması oluşturmak için öznitelikli programlama modeli tarafından sağlanan özniteliklerin kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="5cc86-109">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a><span data-ttu-id="5cc86-110">İçeri ve dışarı aktarma temelleri</span><span class="sxs-lookup"><span data-stu-id="5cc86-110">Import and Export Basics</span></span>

<span data-ttu-id="5cc86-111">Bir *dışarı* diğer bölümlerinde kapsayıcı bir bölümü sağlayan bir değerdir ve *alma* erişilebilir dışarı doldurulması kapsayıcıya, bir bölümü ifade bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-111">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="5cc86-112">Öznitelikli programlama modelinde, içeri ve dışarı aktarmalar sınıfları ve üyeleri ile tasarlayarak bildirilen `Import` ve `Export` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="5cc86-112">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="5cc86-113">`Export` Özniteliği donatmak bir sınıf, alan, özelliği veya yöntemi sırasında `Import` öznitelik, bir alan, özelliği veya Oluşturucu parametresi süslemek.</span><span class="sxs-lookup"><span data-stu-id="5cc86-113">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>

<span data-ttu-id="5cc86-114">Bir dışarı aktarma ile eşleştirilecek bir içeri aktarma, içeri ve dışarı aktarma aynı olması gerekir *sözleşme*.</span><span class="sxs-lookup"><span data-stu-id="5cc86-114">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="5cc86-115">Anlaşma adı verilen bir dizenin oluşur *sözleşme adı*ve adlı dışarı aktarılan veya içeri aktarılan nesnenin türü *sözleşme türü*.</span><span class="sxs-lookup"><span data-stu-id="5cc86-115">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="5cc86-116">Yalnızca sözleşme adı ve sözleşme türü eşleşmesi durumunda bir dışarı aktarma belirli bir içeri aktarma yerine getirmek için değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-116">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>

<span data-ttu-id="5cc86-117">Sözleşme parametrelerinin her ikisini ya da örtük veya açık olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-117">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="5cc86-118">Aşağıdaki kod, temel bir içeri aktarma bildiren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-118">The following code shows a class that declares a basic import.</span></span>

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

<span data-ttu-id="5cc86-119">Bu içeri aktarma `Import` özniteliğine sahip bir sözleşme türü ya da bağlı bir sözleşme adı parametresi.</span><span class="sxs-lookup"><span data-stu-id="5cc86-119">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="5cc86-120">Bu nedenle, her ikisi de düzenlenmiş özellikten.</span><span class="sxs-lookup"><span data-stu-id="5cc86-120">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="5cc86-121">Bu durumda, sözleşme türü olacaktır `IMyAddin`, ve anlaşma türü ile oluşturulan benzersiz bir dize sözleşme adı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-121">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="5cc86-122">(Diğer bir deyişle, yalnızca, adları da türünden çıkarsanan dışarı aktarmaları sözleşme adı eşleşir `IMyAddin`.)</span><span class="sxs-lookup"><span data-stu-id="5cc86-122">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>

<span data-ttu-id="5cc86-123">Önceki alma eşleşen bir dışarı aktarma gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-123">The following shows an export that matches the previous import.</span></span>

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

<span data-ttu-id="5cc86-124">Sözleşme türü bu dışarı aktarma, `IMyAddin` bir parametresi olarak belirtildiğinden `Export` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-124">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="5cc86-125">Dışarı aktarılan tür ya da aynı anlaşma türü olması gerekir, Sözleşme türünden türetilmesi veya sözleşme türü bir arabirim ise uygulama.</span><span class="sxs-lookup"><span data-stu-id="5cc86-125">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="5cc86-126">Bu dışarı aktarma, gerçek tür içinde `MyLogger` arabirimi uygulayan `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-126">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="5cc86-127">Sözleşme adı, bu dışarı aktarma önceki alma eşleştiğini anlamına gelir. anlaşma türü ile algılanır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-127">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>

> [!NOTE]
> <span data-ttu-id="5cc86-128">Dışarı ve içeri aktarmalar, genel bir sınıf veya üye üzerinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-128">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="5cc86-129">Diğer bildirimler desteklenir, ancak dışarı aktarma veya özel bir içeri aktarma, korumalı veya iç üye bölümü ayırma modeli ayırır ve bu nedenle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="5cc86-129">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>

<span data-ttu-id="5cc86-130">Sözleşme türü dışarı ve içeri aktarma için bir eşleşme olarak kabul edilmesi için tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-130">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="5cc86-131">Aşağıdaki dışa aktarım göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5cc86-131">Consider the following export.</span></span>

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

<span data-ttu-id="5cc86-132">Sözleşme türü bu dışarı aktarma, `MyLogger` yerine `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-132">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="5cc86-133">Olsa da `MyLogger` uygulayan `IMyAddin`ve bu nedenle dönüştürülebilir bir `IMyAddin` nesnesi, bu dışarı aktarma anlaşması türleri aynı olmadığından önceki alma eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="5cc86-133">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>

<span data-ttu-id="5cc86-134">Genel olarak, sözleşme adı belirtmeniz gerekli değildir ve anlaşma türü ve meta verileri açısından çoğu sözleşmeleri tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-134">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="5cc86-135">Ancak, belirli koşullar altında doğrudan sözleşme adı belirtmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-135">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="5cc86-136">Bir sınıf temelleri gibi bir ortak türü değerlerden verdiğinde en yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-136">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="5cc86-137">Sözleşme adı, ilk parametresi olarak belirtilebilir `Import` veya `Export` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-137">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="5cc86-138">Aşağıdaki kod, alma ve verme belirtilen sözleşme adıyla gösterir `MajorRevision`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-138">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>

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

<span data-ttu-id="5cc86-139">Sözleşme türü belirtilmediği takdirde, yine de içeri veya dışarı aktarmayı türünden çıkarılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-139">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="5cc86-140">Ancak, sözleşme adı açıkça belirtilmiş olsa bile, sözleşme türü de içeri aktarma ve bir eşleşme olarak kabul edilmesi için dışarı aktarma için tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-140">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="5cc86-141">Örneğin, varsa `MajorRevision` alan bir dize olan, çıkarsanan anlaşması türleri eşleşmiyor ve dışarı aktarma, alma, aynı sözleşme adına sahip olmasına rağmen aynı olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-141">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>

### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="5cc86-142">İçeri ve dışarı aktarma yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cc86-142">Importing and Exporting a Method</span></span>

<span data-ttu-id="5cc86-143">`Export` Özniteliği de tasarlamanız bir yöntem bir sınıf, özellik veya işlev aynı şekilde.</span><span class="sxs-lookup"><span data-stu-id="5cc86-143">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="5cc86-144">Türü çıkarsanamıyor olarak yöntemi dışarı bir sözleşme türü veya sözleşme adı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-144">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="5cc86-145">Belirtilen tür gibi özel bir temsilci ya da genel bir tür olabilir `Func`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-145">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="5cc86-146">Aşağıdaki sınıf adlı bir yöntem dışarı aktarır `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-146">The following class exports a method named `DoSomething`.</span></span>

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

<span data-ttu-id="5cc86-147">Bu sınıftaki `DoSomething` yöntemi tek bir alan `int` parametresi ve döndürür bir `string`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-147">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="5cc86-148">Bu dışarı aktarma eşleştirmek için içeri aktarma bölümü uygun bir üye bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-148">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="5cc86-149">Sınıfına aşağıdaki içeri aktarmaları `DoSomething` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cc86-149">The following class imports the `DoSomething` method.</span></span>

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

<span data-ttu-id="5cc86-150">Nasıl kullanıldığı hakkında daha fazla bilgi için `Func<T, T>` nesne, bkz: <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="5cc86-150">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a><span data-ttu-id="5cc86-151">İçeri aktarmalar türleri</span><span class="sxs-lookup"><span data-stu-id="5cc86-151">Types of Imports</span></span>

<span data-ttu-id="5cc86-152">Yavaş, gerekli ve isteğe bağlı dinamik dahil olmak üzere birkaç içeri aktarma, MEF destek türleri.</span><span class="sxs-lookup"><span data-stu-id="5cc86-152">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>

### <a name="dynamic-imports"></a><span data-ttu-id="5cc86-153">Dinamik içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="5cc86-153">Dynamic Imports</span></span>

<span data-ttu-id="5cc86-154">Bazı durumlarda, içeri aktarma sınıfı sözleşmeye ada sahip dışarı aktarma herhangi bir türde eşleşen isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-154">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="5cc86-155">Bu senaryoda sınıf bildirebilir bir *dinamik içeri aktarma*.</span><span class="sxs-lookup"><span data-stu-id="5cc86-155">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="5cc86-156">Aşağıdaki içeri aktarma, hiçbir dışarı aktarma sözleşme adı "Width" ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-156">The following import matches any export with contract name "TheString".</span></span>

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

<span data-ttu-id="5cc86-157">Ne zaman anlaşma türü çıkarılan gelen `dynamic` anahtar sözcüğü, herhangi bir sözleşme türü eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-157">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="5cc86-158">Bu durumda, bir içeri aktarma gereken **her zaman** eşleştirmek için bir sözleşme adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="5cc86-158">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="5cc86-159">(Hiçbir sözleşme adı belirtilmezse, içeri aktarma hiçbir dışarı eşleşecek şekilde kabul edilir.) Aşağıdaki dışarı aktarmaları her ikisi de önceki alma eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-159">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>

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

<span data-ttu-id="5cc86-160">Kuşkusuz, içeri aktarma sınıfı rastgele türünde bir nesne ile dağıtılacak hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-160">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>

### <a name="lazy-imports"></a><span data-ttu-id="5cc86-161">İçeri aktarmaları</span><span class="sxs-lookup"><span data-stu-id="5cc86-161">Lazy Imports</span></span>

<span data-ttu-id="5cc86-162">Nesneyi hemen oluşturulmadı, bazı durumlarda, içeri aktarılan nesneye dolaylı bir başvuru alma sınıfı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-162">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="5cc86-163">Bu senaryoda sınıf bildirebilir bir *yavaş alma* anlaşma türünü kullanarak `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-163">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="5cc86-164">Aşağıdaki içeri aktarma özelliği, yavaş bir içeri aktarma bildirir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-164">The following importing property declares a lazy import.</span></span>

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

<span data-ttu-id="5cc86-165">Bakış açısıyla bileşim motoru, bir sözleşme türü `Lazy<T>` anlaşma türü ile aynı olarak kabul edilir `T`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-165">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="5cc86-166">Bu nedenle, önceki alma aşağıdaki dışa aktarım eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-166">Therefore, the previous import would match the following export.</span></span>

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

<span data-ttu-id="5cc86-167">Sözleşme adı ve anlaşma türü belirtilebilir `Import` "Temel alır ve dışarı aktarma" bölümünde daha önce açıklandığı gibi yavaş bir alma işlemi için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-167">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>

### <a name="prerequisite-imports"></a><span data-ttu-id="5cc86-168">Önkoşul İçeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="5cc86-168">Prerequisite Imports</span></span>

<span data-ttu-id="5cc86-169">Dışarı aktarılan MEF bölümleri genellikle yanıt olarak doğrudan bir istek veya eşleşen bir içeri aktarma doldurmak için gereken bileşim motoru tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-169">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="5cc86-170">Bir bölüm oluşturulduğunda varsayılan olarak, parametresiz oluşturucuya bileşim motoru kullanır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-170">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="5cc86-171">Farklı bir oluşturucu kullanın altyapısı sağlamak için birlikte işaretleyebilirsiniz `ImportingConstructor` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-171">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>

<span data-ttu-id="5cc86-172">Yalnızca bir yapıcısı bileşim motoru tarafından kullanılmak üzere her bir bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-172">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="5cc86-173">Varsayılan oluşturucu yok ve Hayır sağlayarak `ImportingConstructor` özniteliği veya birden fazla sağlama `ImportingConstructor` öznitelik, bir hata üretecektir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-173">Providing no default constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>

<span data-ttu-id="5cc86-174">İşaretli bir oluşturucuda parametrelerinin doldurmak için `ImportingConstructor` özniteliği, tüm bu parametreler otomatik olarak bildirilir alır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-174">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="5cc86-175">Bu bölümü başlatma sırasında kullanılan içeri aktarmalar bildirmek için kullanışlı bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-175">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="5cc86-176">Aşağıdaki sınıf kullandığı `ImportingConstructor` alma bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="5cc86-176">The following class uses `ImportingConstructor` to declare an import.</span></span>

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Default constructor will NOT be used
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

    //Default constructor will NOT be
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

<span data-ttu-id="5cc86-177">Varsayılan olarak, `ImportingConstructor` özniteliğini kullanır anlaşması türleri ve sözleşme adları tüm parametre alır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-177">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="5cc86-178">Parametrelerle tasarlayarak bunu geçersiz kılmak mümkündür `Import` öznitelikleri, sözleşme adı ve anlaşma türü daha sonra açıkça tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-178">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="5cc86-179">Aşağıdaki kod, bir üst sınıf yerine türetilmiş bir sınıf içeri aktarmak için şu söz dizimini kullanan bir oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-179">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>

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

<span data-ttu-id="5cc86-180">Özellikle, koleksiyon parametrelerle dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-180">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="5cc86-181">Örneğin belirtirseniz, `ImportingConstructor` türünde bir parametreye sahip bir Oluşturucuda `IEnumerable<int>`, içeri aktarma türünde tek bir dışarı aktarım eşleşecektir `IEnumerable<int>`, dışarı aktarma türü bir dizi yerine `int`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-181">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="5cc86-182">Bir dışarı aktarma türü eşleşecek şekilde `int`, parametresiyle donatmak sahip olduğunuz `ImportMany` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-182">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>

<span data-ttu-id="5cc86-183">Alınanlar tarafından bildirilen parametreler `ImportingConstructor` özniteliği olarak da işaretlenir *önkoşul aktarır*.</span><span class="sxs-lookup"><span data-stu-id="5cc86-183">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="5cc86-184">MEF normalde dışarı aktarmaları sağlar ve forma alır bir *döngüsü*.</span><span class="sxs-lookup"><span data-stu-id="5cc86-184">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="5cc86-185">Örneğin, bir döngü nesne A içeri aktarmalar sırayla nesne A. aktarır B, nesne olur. Normal koşullar altında bir döngü bir sorun değildir ve kapsayıcının normalde iki nesneleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-185">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>

<span data-ttu-id="5cc86-186">Bir bölüm Oluşturucu tarafından içeri aktarılan bir değer gerektiğinde, o nesnenin bir döngü alamaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-186">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="5cc86-187">Nesne A B Bu nesne, oluşturduğu önce oluşturulmasını gerektiriyorsa, kendisi ve nesne B alır nesne A, sonra döngüsü çözemez ve bir birleştirme hatası meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-187">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="5cc86-188">İçeri aktarmalar Oluşturucu parametrelere bildirilen olan bu nedenle önkoşul alır, tüm önce doldurulmalıdır herhangi dışarı gerektirdiği nesne kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-188">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>

### <a name="optional-imports"></a><span data-ttu-id="5cc86-189">İsteğe bağlı içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="5cc86-189">Optional Imports</span></span>

<span data-ttu-id="5cc86-190">`Import` Özniteliği bölümü işlevi için bir gereksinim belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-190">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="5cc86-191">Bir içeri aktarma yerine getirilemiyor, bu bölümü olarak başarısız olur ve bölümü kullanılabilir olmaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-191">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>

<span data-ttu-id="5cc86-192">Bir içeri aktarma olduğunu belirtebilirsiniz *isteğe bağlı* kullanarak `AllowDefault` özelliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-192">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="5cc86-193">Bu durumda, bileşim alma mevcut dışarı eşleşmiyor ve içeri aktarma özelliği, kendi özellik türü için varsayılan ayarlanacak bile başarılı olur (`null` nesne özelliklerini `false` Boole değerlerini veya sayısal sıfır Özellikler.) Aşağıdaki sınıf isteğe bağlı bir içeri aktarma kullanır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-193">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>

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

### <a name="importing-multiple-objects"></a><span data-ttu-id="5cc86-194">Birden çok nesne alma</span><span class="sxs-lookup"><span data-stu-id="5cc86-194">Importing Multiple Objects</span></span>

<span data-ttu-id="5cc86-195">`Import` Özniteliği yalnızca başarıyla oluşan bir ve yalnızca bir dışarı aktarma eşleştiğinde.</span><span class="sxs-lookup"><span data-stu-id="5cc86-195">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="5cc86-196">Diğer durumlarda, bir birleştirme hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-196">Other cases will produce a composition error.</span></span> <span data-ttu-id="5cc86-197">Aynı anlaşmaya eşleşen birden fazla dışarı aktarmak için kullanın `ImportMany` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-197">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="5cc86-198">İçeri aktarmalar bu özniteliği ile işaretlenmiş her zaman isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-198">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="5cc86-199">Örneğin, eşleşen dışarı aktarımlar mevcut değilse birleştirme başarısız olmaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-199">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="5cc86-200">Aşağıdaki sınıf herhangi bir sayıda tür dışarı aktarır `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-200">The following class imports any number of exports of type `IMyAddin`.</span></span>

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

<span data-ttu-id="5cc86-201">İçeri aktarılan dizi sıradan kullanarak erişilebilir `IEnumerable<T>` sözdizimi ve yöntem.</span><span class="sxs-lookup"><span data-stu-id="5cc86-201">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="5cc86-202">Bir sıradan dizi kullanmak da mümkündür (`IMyAddin[]`) bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="5cc86-202">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>

<span data-ttu-id="5cc86-203">İle birlikte kullandığınızda bu desen çok önemli olabilir `Lazy<T>` söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="5cc86-203">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="5cc86-204">Kullanarak örneğin, `ImportMany`, `IEnumerable<T>`, ve `Lazy<T>`, istediğiniz sayıda nesne dolaylı başvuru içeri aktarabilir ve yalnızca gerekli olanları örneği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-204">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="5cc86-205">Bu düzen aşağıdaki sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-205">The following class shows this pattern.</span></span>

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

## <a name="avoiding-discovery"></a><span data-ttu-id="5cc86-206">Keşif Önleme</span><span class="sxs-lookup"><span data-stu-id="5cc86-206">Avoiding Discovery</span></span>

<span data-ttu-id="5cc86-207">Bazı durumlarda, bir katalog bir parçası olarak bulunan bir bölümünün engellemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-207">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="5cc86-208">Örneğin, parça öğesinden devralındı amaçlandı, ancak kullanılmayan bir temel sınıf olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-208">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="5cc86-209">Bunu yapmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-209">There are two ways to accomplish this.</span></span> <span data-ttu-id="5cc86-210">İlk olarak kullanabileceğiniz `abstract` bölümü sınıfı anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5cc86-210">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="5cc86-211">Devralınan dışarı aktarımlar sınıfları sağlasa soyut sınıfları dışarı aktarma, hiçbir zaman sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cc86-211">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>

<span data-ttu-id="5cc86-212">Sınıfı soyut olarak yapılamaz, kendisiyle tasarlayabilirsiniz `PartNotDiscoverable` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-212">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="5cc86-213">Bu özniteliği ile donatılmış bir bölümü herhangi bir katalogda dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="5cc86-213">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="5cc86-214">Aşağıdaki örnek, bu desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-214">The following example demonstrates these patterns.</span></span> <span data-ttu-id="5cc86-215">`DataOne` katalog tarafından bulunacaktır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-215">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="5cc86-216">Bu yana `DataTwo` olan soyut, bu bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-216">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="5cc86-217">Bu yana `DataThree` kullanılan `PartNotDiscoverable` özniteliği, bu bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-217">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>

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

## <a name="metadata-and-metadata-views"></a><span data-ttu-id="5cc86-218">Meta verileri ve meta veri görünümleri</span><span class="sxs-lookup"><span data-stu-id="5cc86-218">Metadata and Metadata Views</span></span>

<span data-ttu-id="5cc86-219">Dışarı aktarmalar kendileri olarak bilinen hakkında ek bilgiler sağlayabilir *meta verileri*.</span><span class="sxs-lookup"><span data-stu-id="5cc86-219">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="5cc86-220">Meta verileri içeri aktarma bölümü dışarı aktarılan nesnenin özelliklerini belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-220">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="5cc86-221">İçeri aktarma bölümünü kullanın veya bu oluşturmak zorunda kalmadan bir dışarı aktarma hakkında bilgi toplamak için dışarı aktarır karar vermek için bu verileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-221">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="5cc86-222">Bu nedenle, bir içeri aktarma meta verileri kullanmak için yavaş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-222">For this reason, an import must be lazy to use metadata.</span></span>

<span data-ttu-id="5cc86-223">Meta veri kullanmak için tipik olarak bilinen bir arabirim bildirmelidir bir *meta veri görünümü*, hangi meta verileri kullanıma sunulacak bildirir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-223">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="5cc86-224">Meta veri görünümü arabirimi yalnızca özelliklere sahip olması gerekir ve bu özelliklere sahip olması gerekir `get` erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="5cc86-224">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="5cc86-225">Aşağıdaki örnek bir meta veri görünümü arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-225">The following interface is an example metadata view.</span></span>

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

<span data-ttu-id="5cc86-226">Bir genel koleksiyon kullanmak da mümkündür `IDictionary<string, object>`olarak meta veri görünümü, ancak bu tür denetimi kulanmanız ve kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-226">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>

<span data-ttu-id="5cc86-227">Normalde, gerekli olan tüm meta veri görünümü'nde adlı özellikleri ve bunları sağlamayan hiçbir dışarı aktarma işlemini bir eşleşme değerlendirilmeyecek.</span><span class="sxs-lookup"><span data-stu-id="5cc86-227">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="5cc86-228">`DefaultValue` Özniteliği, bir özelliğin isteğe bağlı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-228">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="5cc86-229">Özellik dahil edilmezse, bir parametre olarak belirtilen varsayılan değerin atanacak `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-229">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="5cc86-230">Meta veri ile tasarlanmış iki farklı sınıfları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5cc86-230">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="5cc86-231">Bu sınıfların her ikisi de önceki meta veri görünümü eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-231">Both of these classes would match the previous metadata view.</span></span>

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

<span data-ttu-id="5cc86-232">Meta veri sonra ifade edilir `Export` kullanarak özniteliği `ExportMetadata` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-232">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="5cc86-233">Her bir meta veri parçası bir ad/değer çiftinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-233">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="5cc86-234">Meta veri adı kısmı meta veri görünümü'nde uygun özellik adıyla eşleşmelidir ve değeri, bu özelliğe atanır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-234">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>

<span data-ttu-id="5cc86-235">Herhangi biri, olacaksa kullanımda hangi meta veri görünümü belirten alıcısı var.</span><span class="sxs-lookup"><span data-stu-id="5cc86-235">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="5cc86-236">Meta veri alma ikinci tür parametresi olarak meta veriler arabirimi ile yavaş bir içeri aktarma bildirilmiş `Lazy<T,T>`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-236">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="5cc86-237">Aşağıdaki sınıf önceki bölümünde meta verilerle içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-237">The following class imports the previous part with metadata.</span></span>

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

<span data-ttu-id="5cc86-238">Çoğu durumda, meta verilerle birleştirmek istersiniz `ImportMany` kullanılabilir Imports ayrıştırmak ve seçin ve yalnızca bir örneği veya belirli bir koşulla eşleşecek şekilde bir koleksiyonu filtrelemek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-238">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="5cc86-239">Aşağıdaki sınıf yalnızca başlatır `IPlugin` sahip nesneleri `Name` "Günlükçüsü" değeri.</span><span class="sxs-lookup"><span data-stu-id="5cc86-239">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>

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

## <a name="import-and-export-inheritance"></a><span data-ttu-id="5cc86-240">İçeri ve dışarı aktarma devralma</span><span class="sxs-lookup"><span data-stu-id="5cc86-240">Import and Export Inheritance</span></span>

<span data-ttu-id="5cc86-241">Bir sınıf bir bölümünden devralınırsa, bu sınıf ayrıca bir bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-241">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="5cc86-242">İçeri aktarmalar her zaman alt sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-242">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="5cc86-243">Bu nedenle, bir parça öğesinin her zaman üst sınıfıyla aynı Alınanlarla bir parçası olur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-243">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>

<span data-ttu-id="5cc86-244">Dışarı aktarmalar kullanarak bildirilen `Export` özniteliği alt sınıflar tarafından devralınmaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-244">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="5cc86-245">Ancak, bir kendisini kullanarak dışarı aktarabilir `InheritedExport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-245">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="5cc86-246">Adornerset'in alt bölümü devralır ve sözleşme adı ve anlaşma türü de dahil olmak üzere aynı dışarı aktarma da sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cc86-246">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="5cc86-247">Farklı bir `Export` özniteliği `InheritedExport` yalnızca sınıf düzeyinde ve üye düzeyinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-247">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="5cc86-248">Bu nedenle, hiçbir üye düzeyinde dışarı aktarmaları devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-248">Therefore, member-level exports can never be inherited.</span></span>

<span data-ttu-id="5cc86-249">Aşağıdaki dört sınıflar, içeri aktarma sürecin prensiplerini göstermek ve devralma dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="5cc86-249">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="5cc86-250">`NumTwo` devralınan `NumOne`, bu nedenle `NumTwo` içeri aktaracak `IMyData`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-250">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="5cc86-251">Sıradan dışarı aktarmaları devralınmaz, bu nedenle `NumTwo` herhangi bir şey aktarmaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-251">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="5cc86-252">`NumFour` devralınan `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-252">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="5cc86-253">Çünkü `NumThree` kullanılan `InheritedExport`, `NumFour` sözleşme türü ile bir dışarı aktarma yok `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-253">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="5cc86-254">Üye düzeyinde dışarı aktarmaları hiçbir zaman devralınır, bu nedenle `IMyData` aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-254">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>

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

<span data-ttu-id="5cc86-255">İle ilişkili meta veri varsa bir `InheritedExport` özniteliği, bu meta verileri de devralınır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-255">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="5cc86-256">(Daha fazla bilgi için önceki "Meta verileri ve meta veri görünümleri" bölümüne bakın.) Alt sınıf tarafından devralınan meta verileri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="5cc86-256">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="5cc86-257">Ancak, yeniden bildirme tarafından `InheritedExport` özniteliği aynı anlaşma ve sözleşme yazın, ancak yeni meta veriler, alt sınıfın yeni meta verileriyle devralınan meta verileri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-257">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="5cc86-258">Aşağıdaki sınıf, bu ilkeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-258">The following class demonstrates this principle.</span></span> <span data-ttu-id="5cc86-259">`MegaLogger` Bölümü devraldığı `Logger` ve içerir `InheritedExport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-259">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="5cc86-260">Bu yana `MegaLogger` durumu adlı yeniden bildirir yeni meta devralmaz adı ve sürümü meta verilerine `Logger`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-260">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>

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

<span data-ttu-id="5cc86-261">Yeniden bildirirken `InheritedExport` öznitelik meta verileri geçersiz kılma, anlaşması türleri aynı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5cc86-261">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="5cc86-262">(Önceki örnekte, `IPlugin` anlaşma türü.) İkinci öznitelik bunlar geçersiz kılmak yerine, farklıysa ikinci bağımsız bir dışarı aktarma bölümünden oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="5cc86-262">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="5cc86-263">Genellikle, bu sözleşme türü, geçersiz kıldığınızda açıkça belirtmek olacağı anlamına gelir bir `InheritedExport` , önceki örnekte gösterildiği gibi öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5cc86-263">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>

<span data-ttu-id="5cc86-264">Arabirimler doğrudan oluşturulamaz olduğundan, bunlar genellikle ile donatılmış olmalıdır olamaz `Export` veya `Import` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="5cc86-264">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="5cc86-265">Ancak, bir arabirim ile tasarlanabilir bir `InheritedExport` özniteliği arabirim düzeyinde ve dışarı aktarma herhangi yanı sıra meta veri ilişkili tüm sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-265">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="5cc86-266">Bir parçası olarak, ancak arabirim kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-266">The interface itself will not be available as a part, however.</span></span>

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a><span data-ttu-id="5cc86-267">Özel dışarı aktarma öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="5cc86-267">Custom Export Attributes</span></span>

<span data-ttu-id="5cc86-268">Temel dışarı aktarma öznitelik `Export` ve `InheritedExport`, meta veri öznitelik özellikleri içerecek şekilde genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-268">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="5cc86-269">Bu teknik, birçok bölüme benzer meta veri uygulamak veya meta veri öznitelikleri, bir devralma ağacı oluşturma için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-269">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>

<span data-ttu-id="5cc86-270">Sözleşme türü, sözleşme adı veya diğer meta verileri özel bir öznitelik belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-270">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="5cc86-271">Özel bir öznitelik öğesinden devralan bir sınıf tanımlamak için `ExportAttribute` (veya `InheritedExportAttribute`) ile belirtilmiş olmalıdır `MetadataAttribute` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-271">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="5cc86-272">Aşağıdaki sınıf özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5cc86-272">The following class defines a custom attribute.</span></span>

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

<span data-ttu-id="5cc86-273">Bu sınıf adlı özel bir öznitelik tanımlar `MyAttribute` sözleşme türüyle `IMyData` ve bazı meta veriler adlı `MyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-273">This class defines a custom attribute named `MyAttribute` with contract type `IMyData` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="5cc86-274">Bir sınıftaki tüm özellikler ile işaretlenen `MetadataAttribute` özniteliği özel özniteliğinde tanımlanan meta veriler olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-274">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="5cc86-275">Aşağıdaki iki bildirimi eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-275">The following two declarations are equivalent.</span></span>

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

<span data-ttu-id="5cc86-276">İlk bildiriminde sözleşme türü ve meta verileri açıkça tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-276">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="5cc86-277">İkinci bildiriminde anlaşma türü ve meta veri özelleştirilmiş özniteliğinde örtüktür.</span><span class="sxs-lookup"><span data-stu-id="5cc86-277">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="5cc86-278">Burada aynı meta verilerinin büyük bir miktarını birçok bölümü (örneğin, yazar veya telif hakkı bilgileri) uygulanması gereken durumlarda özellikle çok fazla zaman ve çoğaltma özel özniteliğini kullanarak kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-278">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="5cc86-279">Daha fazla özel özniteliklerin devralma ağacı farklılıklara izin vermek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-279">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>

<span data-ttu-id="5cc86-280">İsteğe bağlı meta veri özel bir öznitelik oluşturmak için kullanabileceğiniz `DefaultValue` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-280">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="5cc86-281">Bu öznitelik, bir özel öznitelik sınıftaki bir özelliğe uygulandığında, düzenlenmiş özellik isteğe bağlıdır ve bir dışarı Aktarıcı tarafından sağlanması gerekmez belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-281">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="5cc86-282">Özellik için bir değer sağlanmazsa, bu özellik türü için varsayılan değer atanır (genellikle `null`, `false`, veya 0.)</span><span class="sxs-lookup"><span data-stu-id="5cc86-282">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>

<a name="creation_policies"></a>

## <a name="creation-policies"></a><span data-ttu-id="5cc86-283">İlkeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5cc86-283">Creation Policies</span></span>

<span data-ttu-id="5cc86-284">Bir bölümü bir içeri aktarma ve oluşturma işlemi gerçekleştirildiğinde belirttiğinde, kapsayıcının eşleşen bir dışarı aktarım bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-284">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="5cc86-285">Bir dışarı aktarma ile içeri aktarma başarıyla eşleşirse, içeri aktarma üye dışarı aktarılan nesne örneğine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-285">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="5cc86-286">Bu örnek nereden geldiğini dışarı aktarılan bölümün tarafından denetlenir *oluşturma ilkesi*.</span><span class="sxs-lookup"><span data-stu-id="5cc86-286">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>

<span data-ttu-id="5cc86-287">İki olası oluşturma ilke *paylaşılan* ve *paylaşılmayan*.</span><span class="sxs-lookup"><span data-stu-id="5cc86-287">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="5cc86-288">Paylaşılan bir oluşturma ilkesiyle parçası sözleşme ile bir bölümü için kapsayıcıdaki her bir içeri aktarma arasında paylaştırılır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-288">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="5cc86-289">Bileşim motoru eşleşme bulur ve içeri aktarılırken bir özelliği ayarlamak yalnızca biri zaten mevcut değilse yeni bir kopya bölümünün örneği oluşturulmaz; Aksi takdirde, mevcut kopyalama kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="5cc86-289">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="5cc86-290">Bu, çok sayıda nesne aynı bölüme başvuruları olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-290">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="5cc86-291">Bu bölümleri, birçok yerde değiştirilebilir; iç durumu dayanarak doğrulamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="5cc86-291">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="5cc86-292">Bu ilke, statik bölümleri, hizmetleri sağlamak bölümleri ve çok fazla bellek veya diğer kaynakları tüketen bölümleri için uygundur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-292">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>

<span data-ttu-id="5cc86-293">Aktarımlarından biri için eşleşen bir içeri aktarma bulunan her zaman bir parçası oluşturma ilkesine paylaşılmayan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-293">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="5cc86-294">Parçanın dışarı aktarılan sözleşme biriyle eşleşen bir kapsayıcıdaki her bir içeri aktarma için yeni bir kopyasını dolayısıyla örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-294">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="5cc86-295">Bu kopyalar iç durumu paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-295">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="5cc86-296">Bu ilke, burada kendi iç durumu her içeri aktarma gerektirir bölümleri için uygundur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-296">This policy is appropriate for parts where each import requires its own internal state.</span></span>

<span data-ttu-id="5cc86-297">Hem içeri aktarma ve dışarı aktarma değerleri arasından bir bölümü oluşturma ilkesi belirleyebilirsiniz `Shared`, `NonShared`, veya `Any`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-297">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="5cc86-298">Varsayılan değer `Any` hem içeri ve dışarı aktarımların.</span><span class="sxs-lookup"><span data-stu-id="5cc86-298">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="5cc86-299">Belirten bir dışarı aktarma `Shared` veya `NonShared` yalnızca aynı belirtir ya da belirten bir içeri aktarma eşleşecektir `Any`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-299">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="5cc86-300">Benzer şekilde, belirten alma `Shared` veya `NonShared` yalnızca aynı belirtir ya da belirten bir dışarı aktarma eşleşecektir `Any`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-300">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="5cc86-301">İçeri ve dışarı aktarmalar uyumsuz oluşturma ilkeleri ile bir eşleşme aynı şekilde bir içeri aktarma ve dışarı aktarma, sözleşme adı ya da sözleşme türü bir eşleşme değil olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="5cc86-301">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="5cc86-302">İçeri aktarma ve dışarı aktarma hem de belirtirseniz `Any`, değil oluşturma ilkesi belirtin veya varsayılan `Any`, paylaşılan oluşturma ilkesi varsayılan olur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-302">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>

<span data-ttu-id="5cc86-303">Aşağıdaki örnek, içeri aktarmalar hem oluşturma ilkeleri belirtme dışarı aktarmaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-303">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="5cc86-304">`PartOne` Varsayılan olarak, bu nedenle, bir oluşturma ilkesi belirtmiyor `Any`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-304">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="5cc86-305">`PartTwo` Varsayılan olarak, bu nedenle, bir oluşturma ilkesi belirtmiyor `Any`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-305">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="5cc86-306">Her ikisi de içeri ve dışarı aktarmak için varsayılan olduğundan `Any`, `PartOne` paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-306">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="5cc86-307">`PartThree` belirtir bir `Shared` oluşturma ilkesi, bu nedenle `PartTwo` ve `PartThree` aynı kopyasını paylaşır `PartOne`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-307">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="5cc86-308">`PartFour` belirtir bir `NonShared` oluşturma ilkesi, bu nedenle `PartFour` içinde paylaşılmayan olacaktır `PartFive`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-308">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="5cc86-309">`PartSix` belirtir bir `NonShared` oluşturma ilkesi.</span><span class="sxs-lookup"><span data-stu-id="5cc86-309">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="5cc86-310">`PartFive` ve `PartSix` her ayrı kopyası alırsınız `PartFour`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-310">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="5cc86-311">`PartSeven` belirtir bir `Shared` oluşturma ilkesi.</span><span class="sxs-lookup"><span data-stu-id="5cc86-311">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="5cc86-312">Olduğundan dışarı aktarılan `PartFour` oluşturma ilkesi ile `Shared`, `PartSeven` alma herhangi bir şey eşleşmiyor ve doldurulmaz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-312">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>

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

## <a name="life-cycle-and-disposing"></a><span data-ttu-id="5cc86-313">Yaşam döngüsü ve atma</span><span class="sxs-lookup"><span data-stu-id="5cc86-313">Life Cycle and Disposing</span></span>

<span data-ttu-id="5cc86-314">Kapsayıcının içinde bölümleri barındırıldığından, yaşam döngüsü sıradan nesnelerden daha karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-314">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="5cc86-315">Bölümleri iki önemli yaşam döngüsü ile ilgili arabirimler uygulayabilirsiniz: `IDisposable` ve `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-315">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>

<span data-ttu-id="5cc86-316">Aşağı kapatma sırasında gerçekleştirilecek işin gerektiren veya kaynakları serbest bırakmak gereken bölümleri uygulamanız gerekir `IDisposable`, .NET Framework nesneleri için her zamanki gibi.</span><span class="sxs-lookup"><span data-stu-id="5cc86-316">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="5cc86-317">Ancak, kapsayıcı oluşturur ve bölümleri başvuruları korur olduğundan, yalnızca bir bölüm kapsayıcı çağırmalıdır `Dispose` yöntemini.</span><span class="sxs-lookup"><span data-stu-id="5cc86-317">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="5cc86-318">Kapsayıcı uygulayan `IDisposable`ve kendisinin temizleme bölümü olarak `Dispose` çağırır `Dispose` sahip olduğu tüm bölümleri.</span><span class="sxs-lookup"><span data-stu-id="5cc86-318">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="5cc86-319">Ve sahip olduğu herhangi bir bölümü artık gerekli değilse bu nedenle, her zaman kapsayıcının silmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-319">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>

<span data-ttu-id="5cc86-320">Uzun süreli bileşim kapsayıcılar için bellek tüketimi paylaşılmayan oluşturma ilkesi ile parçaları tarafından bir sorun olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-320">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="5cc86-321">Bu paylaşılmayan bölümler birden çok kez oluşturulabilir ve kapsayıcı atılana kadar elden değil.</span><span class="sxs-lookup"><span data-stu-id="5cc86-321">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="5cc86-322">Bu işlemel için kapsayıcı sağlar. `ReleaseExport` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cc86-322">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="5cc86-323">Bu yöntemin çağrılması bir paylaşılmayan dışarı aktarma, dışarı aktarma kaldırır ve siler.</span><span class="sxs-lookup"><span data-stu-id="5cc86-323">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="5cc86-324">Yalnızca vb. ağaç aşağı kaldırılan dışarı aktarma tarafından kullanılan bölümleri de kaldırılır ve atıldı.</span><span class="sxs-lookup"><span data-stu-id="5cc86-324">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="5cc86-325">Bu şekilde, kaynakları bileşim kapsayıcı disposing olmadan kazanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-325">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>

<span data-ttu-id="5cc86-326">`IPartImportsSatisfiedNotification` adlı bir yöntem içerir `OnImportsSatisfied`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-326">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="5cc86-327">Bu yöntem, kapsayıcının oluşturma tamamlandı ve parça içeri aktarmalar kullanım için hazır olduğunuzda arabirimi uygulayan herhangi bir bölümü şirket tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5cc86-327">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="5cc86-328">Bölümleri aktarımlarının diğer bölümlerini doldurmak için bileşim motoru tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5cc86-328">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="5cc86-329">Imports bölümünün ayarlamadan önce kullanır veya bu değerleri kullanarak önkoşul olarak belirtilmedi sürece bölümü oluşturucuda içeri aktarılan değerlerini işleyen başlatma gerçekleştirilemiyor `ImportingConstructor` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5cc86-329">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="5cc86-330">Bu genellikle tercih edilen yöntemdir, ancak bazı durumlarda, oluşturucu ekleme kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc86-330">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="5cc86-331">Bu gibi durumlarda, başlatma gerçekleştirilebilir `OnImportsSatisfied`, ve bölümü uygulamalıdır `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="5cc86-331">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5cc86-332">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cc86-332">See also</span></span>

- [<span data-ttu-id="5cc86-333">Kanal 9 Video: Yönetilen Genişletilebilirlik Çerçevesi ile uygulamalarınızı açın</span><span class="sxs-lookup"><span data-stu-id="5cc86-333">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [<span data-ttu-id="5cc86-334">Kanal 9 Video: Yönetilen Genişletilebilirlik Çerçevesi (MEF) 2.0</span><span class="sxs-lookup"><span data-stu-id="5cc86-334">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)

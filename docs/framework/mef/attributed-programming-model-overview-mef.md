---
title: "Öznitelikli Programlama Modeline Genel Bakış (MEF)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16ffe789635ee13c118c63c30ef255cc9b264a9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="59b80-102">Öznitelikli Programlama Modeline Genel Bakış (MEF)</span><span class="sxs-lookup"><span data-stu-id="59b80-102">Attributed Programming Model Overview (MEF)</span></span>
<span data-ttu-id="59b80-103">İçinde Yönetilen Genişletilebilirlik Çerçevesi (MEF), bir *programlama modeli* MEF faaliyet kavramsal nesneler kümesini tanımlayan belirli bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="59b80-103">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="59b80-104">Bu kavramsal nesneler bölümleri, içeri aktarmalar ve dışarı aktarma içerir.</span><span class="sxs-lookup"><span data-stu-id="59b80-104">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="59b80-105">MEF bu nesneleri kullanır, ancak nasıl temsil belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="59b80-105">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="59b80-106">Bu nedenle, çok çeşitli programlama modelleri programlama modelleri de dahil olmak üzere özelleştirilebilir mümkün.</span><span class="sxs-lookup"><span data-stu-id="59b80-106">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>  
  
 <span data-ttu-id="59b80-107">Programlama modeli MEF kullanılan varsayılan *öznitelikli programlama modeli*.</span><span class="sxs-lookup"><span data-stu-id="59b80-107">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="59b80-108">Öznitelikli Programlama modeli bölümleri, içeri aktarmalar, dışa aktarır ve diğer nesneleri sıradan .NET Framework sınıflarını tasarlayan öznitelikler ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="59b80-108">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="59b80-109">Bu konu öznitelikli programlama modeli tarafından sağlanan özniteliklerin bir MEF uygulaması oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="59b80-109">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a><span data-ttu-id="59b80-110">İçeri ve dışarı aktarma temelleri</span><span class="sxs-lookup"><span data-stu-id="59b80-110">Import and Export Basics</span></span>  
 <span data-ttu-id="59b80-111">Bir *verme* kapsayıcı diğer bölümlerinde bir bölümü sağlayan bir değerdir ve bir *alma* erişilebilir dışarı doldurulması için bu kapsayıcıya aktarımlardan açıklayan bir bölüm bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="59b80-111">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="59b80-112">Öznitelikli Programlama modeli içeri ve dışarı aktarmalar sınıflar ve üyeleri ile tasarlayarak bildirilir `Import` ve `Export` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="59b80-112">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="59b80-113">`Export` Özniteliği işaretleme sınıf, alan, özellik veya yöntem sırada `Import` özniteliği bir alan, özelliği veya oluşturucusu parametre tasarlamanız.</span><span class="sxs-lookup"><span data-stu-id="59b80-113">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>  
  
 <span data-ttu-id="59b80-114">Bir verme ile eşleştirilmesini alma, içeri ve dışarı aktarma aynı olması gerekir *sözleşme*.</span><span class="sxs-lookup"><span data-stu-id="59b80-114">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="59b80-115">Anlaşma adı verilen bir dize türünden oluşur *sözleşme adı*, çağrılan dışarı aktarılan ya da içeri aktarılan nesne türünü *sözleşme türü*.</span><span class="sxs-lookup"><span data-stu-id="59b80-115">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="59b80-116">Yalnızca sözleşme adı ve sözleşme türü eşleşmesi verme belirli bir alma işlemi gerçekleştirmek için değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-116">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>  
  
 <span data-ttu-id="59b80-117">Ya da sözleşme parametrelerinin her ikisi de kapalı veya açık olabilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-117">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="59b80-118">Aşağıdaki kod temel alma bildiren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="59b80-118">The following code shows a class that declares a basic import.</span></span>  
  
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
  
 <span data-ttu-id="59b80-119">Bu içeri `Import` öznitelik türünün bir sözleşme veya iliştirilmiş bir sözleşme adı parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="59b80-119">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="59b80-120">Bu nedenle, her ikisi de tasarlanmış özellikten.</span><span class="sxs-lookup"><span data-stu-id="59b80-120">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="59b80-121">Bu durumda, anlaşma türü olacak `IMyAddin`, ve sözleşme adı anlaşma türünden oluşturulan benzersiz bir dize olacaktır.</span><span class="sxs-lookup"><span data-stu-id="59b80-121">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="59b80-122">(Diğer bir deyişle, sözleşme adı yalnızca, adları türünden de çıkartılan dışarı aktarma ile eşleşir `IMyAddin`.)</span><span class="sxs-lookup"><span data-stu-id="59b80-122">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>  
  
 <span data-ttu-id="59b80-123">Önceki içeri eşleşen bir dışarı aktarma gösterir.</span><span class="sxs-lookup"><span data-stu-id="59b80-123">The following shows an export that matches the previous import.</span></span>  
  
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
  
 <span data-ttu-id="59b80-124">Bu dışarı aktarma sözleşme türüdür `IMyAddin` bir parametresi olarak belirtildiğinden `Export` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-124">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="59b80-125">Dışarı aktarılan tür ya da aynı sözleşme türü olması gerekir, sözleşme türden türetilmiş veya arabirim ise sözleşme türü uygulamak.</span><span class="sxs-lookup"><span data-stu-id="59b80-125">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="59b80-126">Bu dışarı aktarma, gerçek tür içinde `MyLogger` arabirimini uygulayan `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="59b80-126">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="59b80-127">Sözleşme adı bu dışarı aktarma önceki içeri eşleşir anlamına gelir anlaşma türü ile sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="59b80-127">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59b80-128">Dışarı ve içeri aktarmalar, ortak sınıf veya üye üzerinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="59b80-128">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="59b80-129">Diğer bildirimler desteklenir, ancak veya özel verme, korumalı veya dahili bir üyeyi bölümü için yalıtım modelini keser ve bu nedenle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="59b80-129">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>  
  
 <span data-ttu-id="59b80-130">Sözleşme türü dışarı ve içeri aktarma bir eşleşme olarak kabul edilmesi için için tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="59b80-130">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="59b80-131">Aşağıdaki dışarı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="59b80-131">Consider the following export.</span></span>  
  
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
  
 <span data-ttu-id="59b80-132">Bu dışarı aktarma sözleşme türüdür `MyLogger` yerine `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="59b80-132">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="59b80-133">Olsa bile `MyLogger` uygulayan `IMyAddin`ve bu nedenle dönüştürülebilir bir `IMyAddin` nesnesi, bu dışarı aktarma sözleşme türleri aynı olmadığından önceki içeri eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="59b80-133">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>  
  
 <span data-ttu-id="59b80-134">Genel olarak, sözleşme adı belirtmek gerekli değildir ve çoğu sözleşmeleri sözleşme türü ve meta veri bakımından tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="59b80-134">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="59b80-135">Ancak, belirli koşullar altında doğrudan sözleşme adı belirtmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="59b80-135">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="59b80-136">Bir sınıf temelleri gibi ortak bir türü paylaşan değerlerden verdiğinde en yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="59b80-136">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="59b80-137">Sözleşme adı ilk parametresi belirtilebilir `Import` veya `Export` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-137">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="59b80-138">Aşağıdaki kod bir alma ve verme belirtilen sözleşme adıyla gösterir `MajorRevision`.</span><span class="sxs-lookup"><span data-stu-id="59b80-138">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>  
  
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
  
 <span data-ttu-id="59b80-139">Anlaşma türü belirtilmezse, bunu hala içe veya dışa aktarma türünden çıkarılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="59b80-139">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="59b80-140">Ancak, sözleşme adı açıkça belirtilmiş olsa bile, anlaşma türü de tam olarak alma ve verme bir eşleşme olarak kabul edilmesi için eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="59b80-140">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="59b80-141">Örneğin, varsa `MajorRevision` alanı bir dize olsaydı, çıkarılan anlaşma türleri eşleşmiyor ve dışarı aktarma, aynı sözleşme adına sahip olmasına rağmen alma, aynı olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="59b80-141">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>  
  
### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="59b80-142">İçeri ve dışarı aktarma yöntemi</span><span class="sxs-lookup"><span data-stu-id="59b80-142">Importing and Exporting a Method</span></span>  
 <span data-ttu-id="59b80-143">`Export` Özniteliği de tasarlamanız bir yöntem aynı şekilde bir sınıf, özellik veya işlev.</span><span class="sxs-lookup"><span data-stu-id="59b80-143">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="59b80-144">Türü çıkarsanamıyor gibi yöntemi dışarı sözleşme türü veya sözleşme adı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="59b80-144">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="59b80-145">Belirtilen tür gibi özel bir temsilci ya da genel bir tür olabilir `Func`.</span><span class="sxs-lookup"><span data-stu-id="59b80-145">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="59b80-146">Aşağıdaki sınıf adlı bir yöntem verir `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="59b80-146">The following class exports a method named `DoSomething`.</span></span>  
  
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
    [Export(typeof(Func<int, string>)]  
    public string DoSomething(int TheParam);  
}  
```  
  
 <span data-ttu-id="59b80-147">Bu sınıftaki `DoSomething` yöntemi alır tek bir `int` parametre ve döndürür bir `string`.</span><span class="sxs-lookup"><span data-stu-id="59b80-147">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="59b80-148">Bu dışarı aktarma eşleştirmek için içeri aktarılan bölüm uygun bir üye bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="59b80-148">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="59b80-149">Aşağıdaki sınıf içeri aktarmalar `DoSomething` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="59b80-149">The following class imports the `DoSomething` method.</span></span>  
  
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
  
 <span data-ttu-id="59b80-150">Kullanımı hakkında daha fazla bilgi için `Func<T, T>` nesne için bkz: <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="59b80-150">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a><span data-ttu-id="59b80-151">İçeri aktarmalar türleri</span><span class="sxs-lookup"><span data-stu-id="59b80-151">Types of Imports</span></span>  
 <span data-ttu-id="59b80-152">Yavaş, önkoşul ve isteğe bağlı dinamik dahil olmak üzere birkaç alma MEF destek türleri.</span><span class="sxs-lookup"><span data-stu-id="59b80-152">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>  
  
### <a name="dynamic-imports"></a><span data-ttu-id="59b80-153">Dinamik içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="59b80-153">Dynamic Imports</span></span>  
 <span data-ttu-id="59b80-154">Bazı durumlarda, içeri aktarma sınıfı belirli sözleşme adına sahip dışarı herhangi bir türde eşleşen isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59b80-154">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="59b80-155">Bu senaryoda sınıf bildirebilir bir *dinamik alma*.</span><span class="sxs-lookup"><span data-stu-id="59b80-155">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="59b80-156">Aşağıdaki içeri aktarma tüm verme sözleşme adı "Width" ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="59b80-156">The following import matches any export with contract name "TheString".</span></span>  
  
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
  
 <span data-ttu-id="59b80-157">Ne zaman anlaşma türü sözcüğünden çıkarıldığında `dynamic` anahtar sözcüğü, herhangi bir sözleşme türü ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="59b80-157">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="59b80-158">Bu durumda, bir içeri aktarma gereken **her zaman** eşleştirilecek bir sözleşme adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="59b80-158">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="59b80-159">(Hiçbir sözleşme adı belirtilirse, alma işlemi hiçbir dışarı aktarma eşleşecek şekilde kabul edilir.) Aşağıdaki dışarı her ikisi de önceki içeri eşleşir.</span><span class="sxs-lookup"><span data-stu-id="59b80-159">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>  
  
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
  
 <span data-ttu-id="59b80-160">Belli ki, içeri aktarma sınıfı rasgele türünde bir nesne mücadele etmek için hazırlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="59b80-160">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>  
  
### <a name="lazy-imports"></a><span data-ttu-id="59b80-161">Yavaş içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="59b80-161">Lazy Imports</span></span>  
 <span data-ttu-id="59b80-162">Böylece nesne hemen oluşturulmadı bazı durumlarda, içeri aktarılan nesne için dolaylı bir başvuru alma sınıfı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-162">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="59b80-163">Bu senaryoda sınıf bildirebilir bir *yavaş alma* anlaşma türünü kullanarak `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="59b80-163">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="59b80-164">Aşağıdaki içeri aktarma özelliği bir yavaş alma bildirir.</span><span class="sxs-lookup"><span data-stu-id="59b80-164">The following importing property declares a lazy import.</span></span>  
  
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
  
 <span data-ttu-id="59b80-165">Bir sözleşme açısından bakıldığında bileşim motoru, türü `Lazy<T>` anlaşma türü ile aynı olarak kabul edilir `T`.</span><span class="sxs-lookup"><span data-stu-id="59b80-165">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="59b80-166">Bu nedenle, önceki içeri aşağıdaki dışarı eşleşir.</span><span class="sxs-lookup"><span data-stu-id="59b80-166">Therefore, the previous import would match the following export.</span></span>  
  
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
  
 <span data-ttu-id="59b80-167">Sözleşme türü ve sözleşme adı belirtilebilir `Import` daha önce "Temel alır ve dışarı aktarma" bölümünde açıklandığı gibi yavaş bir alma işlemi için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="59b80-167">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>  
  
### <a name="prerequisite-imports"></a><span data-ttu-id="59b80-168">Önkoşul İçeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="59b80-168">Prerequisite Imports</span></span>  
 <span data-ttu-id="59b80-169">Dışarı aktarılan MEF bölümleri genellikle doğrudan bir istek veya eşleşen bir içeri aktarımı doldurma gerek yanıt olarak bileşim motoru tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59b80-169">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="59b80-170">Bir bölümü oluştururken, varsayılan olarak, oluşturucu birleşim altyapısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="59b80-170">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="59b80-171">Farklı bir oluşturucu kullanın altyapısı yapma ile işaretleyebilirsiniz `ImportingConstructor` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-171">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>  
  
 <span data-ttu-id="59b80-172">Her bölümü bileşim motoru tarafından kullanım için yalnızca bir oluşturucuya sahip.</span><span class="sxs-lookup"><span data-stu-id="59b80-172">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="59b80-173">Varsayılan oluşturucu yok ve no sağlama `ImportingConstructor` özniteliği veya birden fazla sağlama `ImportingConstructor` öznitelik, bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59b80-173">Providing no default constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>  
  
 <span data-ttu-id="59b80-174">İle işaretlenmiş bir oluşturucunun parametrelerini doldurmak için `ImportingConstructor` özniteliği, bu parametrelerin tümü otomatik olarak bildirildiğinden alır.</span><span class="sxs-lookup"><span data-stu-id="59b80-174">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="59b80-175">Bu bölümü başlatma sırasında kullanılan içeri aktarmalar bildirmek için kullanışlı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="59b80-175">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="59b80-176">Aşağıdaki sınıf kullanır `ImportingConstructor` alma bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="59b80-176">The following class uses `ImportingConstructor` to declare an import.</span></span>  
  
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
  
 <span data-ttu-id="59b80-177">Varsayılan olarak, `ImportingConstructor` özniteliğini kullanır anlaşma türleri ve sözleşme adları tüm parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="59b80-177">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="59b80-178">Parametrelerle tasarlayarak bunu geçersiz kılmak mümkündür `Import` anlaşma türü ve sözleşme adı daha sonra açıkça tanımlayabilirsiniz öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="59b80-178">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="59b80-179">Aşağıdaki kod, bir üst sınıf yerine türetilmiş bir sınıf içeri aktarmak için bu söz dizimini kullanır bir oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="59b80-179">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>  
  
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
  
 <span data-ttu-id="59b80-180">Özellikle, koleksiyon parametrelerle dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="59b80-180">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="59b80-181">Belirtirseniz, örneğin, `ImportingConstructor` türünde bir parametre ile bir oluşturucu üzerinde `IEnumerable<int>`, içe aktarma türü tek bir verme eşleşir `IEnumerable<int>`, dışarı aktarma türü bir dizi yerine `int`.</span><span class="sxs-lookup"><span data-stu-id="59b80-181">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="59b80-182">Dışarı aktarımlar türünü eşlemek için `int`, parametresiyle tasarlamanız gerekir `ImportMany` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-182">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>  
  
 <span data-ttu-id="59b80-183">İçeri aktarmalar tarafından bildirilen parametreler `ImportingConstructor` özniteliği olarak da işaretlenir *önkoşul alır*.</span><span class="sxs-lookup"><span data-stu-id="59b80-183">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="59b80-184">MEF normalde dışarı sağlar ve forma alır bir *döngüsü*.</span><span class="sxs-lookup"><span data-stu-id="59b80-184">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="59b80-185">Örneğin, bir döngü nereye nesne A içeri aktarmalar sırayla nesne A. alır B nesne. Normal koşullar altında bir döngü bir sorun değildir ve kapsayıcının hem nesneleri normal olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59b80-185">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>  
  
 <span data-ttu-id="59b80-186">İçeri aktarılan bir değer bir bölümü oluşturucusu tarafından istendiğinde bu nesne bir döngüde yer alamaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-186">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="59b80-187">Nesne A oluşturulması önce o nesnenin B oluşturulmasını gerektiriyorsa, kendisi ve nesne B alır nesne A, sonra döngüsü çözmek mümkün olmayacaktır ve bir birleşim hatası ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="59b80-187">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="59b80-188">Oluşturucu parametrelerinde bildirilen içeri aktarmalar olan bu nedenle önkoşul içeri aktarmalar, tüm önce doldurulan olmalıdır dışarı gerektirmesi nesne hiçbirini kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-188">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>  
  
### <a name="optional-imports"></a><span data-ttu-id="59b80-189">İsteğe bağlı içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="59b80-189">Optional Imports</span></span>  
 <span data-ttu-id="59b80-190">`Import` Özniteliği bölümü işlevi için bir gereksinim belirtir.</span><span class="sxs-lookup"><span data-stu-id="59b80-190">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="59b80-191">Alma karşılanamazsa, bu bölümün bileşimi başarısız olur ve bölümü kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-191">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>  
  
 <span data-ttu-id="59b80-192">Alma olduğunu belirtebilirsiniz *isteğe bağlı* kullanarak `AllowDefault` özelliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-192">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="59b80-193">Bu durumda, bileşim mevcut dışarı eşleşmiyor içe aktarın ve alma özelliği, özellik türü için varsayılan ayarlanmış olsa bile başarılı olur (`null` nesne özelliklerini `false` Boole değerlerini veya sayısal sıfır özellikleri.) Aşağıdaki sınıf isteğe bağlı alma kullanır.</span><span class="sxs-lookup"><span data-stu-id="59b80-193">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>  
  
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
  
    //If no matching export is avaliable,  
    //thePlugin will be set to null.  
}  
```  
  
### <a name="importing-multiple-objects"></a><span data-ttu-id="59b80-194">Birden çok nesne içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="59b80-194">Importing Multiple Objects</span></span>  
 <span data-ttu-id="59b80-195">`Import` Özniteliği yalnızca başarıyla oluşan tek bir verme eşleştiğinde.</span><span class="sxs-lookup"><span data-stu-id="59b80-195">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="59b80-196">Diğer durumlarda, bir birleşim hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="59b80-196">Other cases will produce a composition error.</span></span> <span data-ttu-id="59b80-197">Aynı anlaşmayla eşleşen birden fazla dışarı aktarmak için kullanın `ImportMany` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-197">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="59b80-198">Bu özniteliği ile işaretlenmiş içeri aktarımlar her zaman isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="59b80-198">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="59b80-199">Örneğin, eşleşen hiçbir dışarı aktarma mevcut olup olmadığını birleşim neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-199">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="59b80-200">Aşağıdaki sınıf herhangi bir sayıda türü dışarı aktarır `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="59b80-200">The following class imports any number of exports of type `IMyAddin`.</span></span>  
  
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
  
 <span data-ttu-id="59b80-201">İçeri aktarılan dizine sıradan kullanarak erişilebilir `IEnumerable<T>` sözdizimi ve yöntem.</span><span class="sxs-lookup"><span data-stu-id="59b80-201">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="59b80-202">Sıradan bir dizi kullanmak da mümkündür (`IMyAddin[]`) yerine.</span><span class="sxs-lookup"><span data-stu-id="59b80-202">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>  
  
 <span data-ttu-id="59b80-203">İle birlikte kullandığınızda bu deseni oldukça önemli olabilir `Lazy<T>` sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="59b80-203">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="59b80-204">Kullanarak örneğin, `ImportMany`, `IEnumerable<T>`, ve `Lazy<T>`, istediğiniz sayıda nesne başvuruları dolaylı içe aktarabilir ve yalnızca gerekli olanları örneği.</span><span class="sxs-lookup"><span data-stu-id="59b80-204">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="59b80-205">Aşağıdaki sınıf bu deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="59b80-205">The following class shows this pattern.</span></span>  
  
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
## <a name="avoiding-discovery"></a><span data-ttu-id="59b80-206">Keşif Önleme</span><span class="sxs-lookup"><span data-stu-id="59b80-206">Avoiding Discovery</span></span>  
 <span data-ttu-id="59b80-207">Bazı durumlarda, bir katalog bir parçası olarak bulunan bir bölümü önlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59b80-207">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="59b80-208">Örneğin, bir parçası kaynağından devralındı düşünülen ama kullanılmayan bir temel sınıf olabilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-208">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="59b80-209">Bunu yapmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="59b80-209">There are two ways to accomplish this.</span></span> <span data-ttu-id="59b80-210">İlk olarak, kullanabileceğiniz `abstract` bölümü sınıfı anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="59b80-210">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="59b80-211">Bunlardan türeyen sınıflar devralınan dışarı sağlayabilirse soyut sınıflar dışarı aktarmalar, hiçbir zaman sağlar.</span><span class="sxs-lookup"><span data-stu-id="59b80-211">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>  
  
 <span data-ttu-id="59b80-212">Sınıfı Özet yapılamazsa, kendisiyle tasarlayabilirsiniz `PartNotDiscoverable` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-212">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="59b80-213">Bu öznitelik ile donatılmış bir bölümü hiçbir katalog içine dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="59b80-213">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="59b80-214">Aşağıdaki örnekte bu düzenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="59b80-214">The following example demonstrates these patterns.</span></span> <span data-ttu-id="59b80-215">`DataOne`katalog tarafından bulunacaktır.</span><span class="sxs-lookup"><span data-stu-id="59b80-215">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="59b80-216">Bu yana `DataTwo` olan Özet, onu bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-216">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="59b80-217">Bu yana `DataThree` kullanılan `PartNotDiscoverable` özniteliği değil bulunacaktır.</span><span class="sxs-lookup"><span data-stu-id="59b80-217">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>  
  
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
## <a name="metadata-and-metadata-views"></a><span data-ttu-id="59b80-218">Meta veri ve meta veri görünümleri</span><span class="sxs-lookup"><span data-stu-id="59b80-218">Metadata and Metadata Views</span></span>  
 <span data-ttu-id="59b80-219">Dışarı aktarma kendileri olarak bilinen hakkında ek bilgiler sağlayabilir *meta verileri*.</span><span class="sxs-lookup"><span data-stu-id="59b80-219">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="59b80-220">Meta veri alma bölümü için dışarı aktarılan nesnenin özelliklerini iletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59b80-220">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="59b80-221">İçeri aktarılan bölüm kullanın ya da onu oluşturmak zorunda kalmadan bir dışarı aktarma hakkında bilgi toplamak için aktarır karar vermek için bu verileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59b80-221">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="59b80-222">Bu nedenle, bir içeri aktarma meta veriyi kullanmak için yavaş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="59b80-222">For this reason, an import must be lazy to use metadata.</span></span>  
  
 <span data-ttu-id="59b80-223">Meta veri kullanmak için tipik olarak bilinen bir arayüz bildirmelidir bir *meta veri görünümü*, hangi meta verinin kullanılabilir olacağını bildirir.</span><span class="sxs-lookup"><span data-stu-id="59b80-223">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="59b80-224">Meta veri görünüm arayüzü yalnızca özelliklere sahip olmalıdır ve bu özellikler içermelidir `get` erişimciler.</span><span class="sxs-lookup"><span data-stu-id="59b80-224">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="59b80-225">Bir örnek meta veri görünümü arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="59b80-225">The following interface is an example metadata view.</span></span>  
  
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
  
 <span data-ttu-id="59b80-226">Bir genel koleksiyon kullanmak da mümkündür `IDictionary<string, object>`, meta veri görünümü ancak bu tür denetlemesi kulanmanız ve kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59b80-226">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>  
  
 <span data-ttu-id="59b80-227">Normalde, meta veri görünümünde adlı özelliklerin tümü gereklidir ve bunları sağlamayan dışarı bir eşleşme dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-227">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="59b80-228">`DefaultValue` Özniteliği belirtir. bir özellik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="59b80-228">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="59b80-229">Özellik dahil değilse, onu bir parametresi olarak belirtilen varsayılan değeri atanacak `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="59b80-229">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="59b80-230">Meta verileri ile donatılmış farklı iki sınıf şunlardır:</span><span class="sxs-lookup"><span data-stu-id="59b80-230">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="59b80-231">Bu sınıfların her ikisi de önceki meta veri görünümü eşleşir.</span><span class="sxs-lookup"><span data-stu-id="59b80-231">Both of these classes would match the previous metadata view.</span></span>  
  
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
  
 <span data-ttu-id="59b80-232">Meta veri ifade sonra `Export` kullanarak özniteliği `ExportMetadata` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-232">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="59b80-233">Meta veriler her parçasının bir ad/değer çiftinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="59b80-233">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="59b80-234">Meta veri adı kısmını meta veri görünümünde uygun özellik adıyla eşleşmelidir ve değeri bu özelliğe atanır.</span><span class="sxs-lookup"><span data-stu-id="59b80-234">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>  
  
 <span data-ttu-id="59b80-235">Herhangi biri, olacaksa kullanımda hangi meta veri görünümü belirtir içeri Aktarıcı var.</span><span class="sxs-lookup"><span data-stu-id="59b80-235">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="59b80-236">Meta veri alma ikinci tür parametre olarak meta veriler arabirimiyle yavaş bir alma bildirilmiş `Lazy<T,T>`.</span><span class="sxs-lookup"><span data-stu-id="59b80-236">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="59b80-237">Aşağıdaki sınıf meta verileri önceki bölümüyle içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="59b80-237">The following class imports the previous part with metadata.</span></span>  
  
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
  
 <span data-ttu-id="59b80-238">Çoğu durumda, meta verileri ile birleştirmek istersiniz `ImportMany` kullanılabilir içeri aktarmalar ayrıştırma ve seçin ve yalnızca bir örneği veya belirli bir koşulla eşleşecek şekilde bir koleksiyonu filtrelemek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="59b80-238">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="59b80-239">Aşağıdaki sınıf yalnızca başlatır `IPlugin` nesneleri `Name` "Günlükçü" değeri.</span><span class="sxs-lookup"><span data-stu-id="59b80-239">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>  
  
```vb  
Public Class User  
  
    <ImportMany()>  
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))  
  
    Public Function InstantiateLogger() As IPlugin  
  
        Dim logger As IPlugin  
        logger = Nothing  
  
        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins  
            If (Plugin.Metadata.Name = "Logger") Then  
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
  
    public IPlugin InstantiateLogger ()  
    {  
        IPlugin logger = null;  
  
        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)  
        {  
            if (plugin.Metadata.Name = "Logger") logger = plugin.Value;  
        }  
        return logger;  
    }  
}  
```  
  
<a name="import_and_export_inheritance"></a>   
## <a name="import-and-export-inheritance"></a><span data-ttu-id="59b80-240">İçeri ve dışarı aktarma devralma</span><span class="sxs-lookup"><span data-stu-id="59b80-240">Import and Export Inheritance</span></span>  
 <span data-ttu-id="59b80-241">Bir sınıf bir bölümünden devralıyorsa Bu sınıf ayrıca bir bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-241">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="59b80-242">İçeri aktarmalar her zaman alt sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="59b80-242">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="59b80-243">Bu nedenle, bir bölümü öğesinin bir alt her zaman kendi üst sınıfı olarak aynı içeri aktarmalar ile bir parçası olur.</span><span class="sxs-lookup"><span data-stu-id="59b80-243">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>  
  
 <span data-ttu-id="59b80-244">Dışarı aktarma bildirilen kullanarak `Export` özniteliği olmayan alt sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="59b80-244">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="59b80-245">Ancak, bir kendisini kullanarak dışarı aktarabilir `InheritedExport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-245">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="59b80-246">Alt sınıfların bölümünün devralır ve sözleşme adı ve sözleşme türü dahil olmak üzere aynı verme sağlayın.</span><span class="sxs-lookup"><span data-stu-id="59b80-246">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="59b80-247">Farklı bir `Export` özniteliği `InheritedExport` yalnızca sınıf düzeyinde ve üye düzeyinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-247">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="59b80-248">Bu nedenle, hiçbir zaman üye düzeyi dışarı devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-248">Therefore, member-level exports can never be inherited.</span></span>  
  
 <span data-ttu-id="59b80-249">Aşağıdaki dört sınıfları alma ilkeleri göstermek ve devralma verin.</span><span class="sxs-lookup"><span data-stu-id="59b80-249">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="59b80-250">`NumTwo`öğesinden devralınan `NumOne`, bu nedenle `NumTwo` alacak `IMyData`.</span><span class="sxs-lookup"><span data-stu-id="59b80-250">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="59b80-251">Sıradan dışarı devralınmaz, bu nedenle `NumTwo` herhangi bir şey aktarmaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-251">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="59b80-252">`NumFour`öğesinden devralınan `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="59b80-252">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="59b80-253">Çünkü `NumThree` kullanılan `InheritedExport`, `NumFour` sözleşme türüne sahip bir dışa aktarma sahip `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="59b80-253">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="59b80-254">Üye düzeyi dışarı hiçbir zaman devralınan, bu nedenle `IMyData` aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-254">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>  
  
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
  
 <span data-ttu-id="59b80-255">İle ilişkili meta veri varsa bir `InheritedExport` özniteliği, bu meta veri de devralınır.</span><span class="sxs-lookup"><span data-stu-id="59b80-255">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="59b80-256">(Daha fazla bilgi için önceki "Meta veri ve meta veri görünümleri" bölümüne bakın.) Devralınan meta alt sınıf tarafından değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="59b80-256">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="59b80-257">Ancak, ile yeniden bildirerek `InheritedExport` özniteliğinin anlaşma türü ve aynı sözleşme adı ile ancak yeni meta veriler, alt sınıf yeni meta veri ile devralınan meta değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59b80-257">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="59b80-258">Aşağıdaki sınıf Bu ilkeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="59b80-258">The following class demonstrates this principle.</span></span> <span data-ttu-id="59b80-259">`MegaLogger` Bölümü devraldığı `Logger` ve içerir `InheritedExport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-259">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="59b80-260">Bu yana `MegaLogger` durum adlı tekrar bildirdiğinden yeni meta devralmaz adı ve sürümü meta verileri `Logger`.</span><span class="sxs-lookup"><span data-stu-id="59b80-260">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>  
  
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
  
 <span data-ttu-id="59b80-261">Yeniden bildirirken `InheritedExport` özniteliği meta veriyi geçersiz kılmak için anlaşma türleri aynı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="59b80-261">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="59b80-262">(Önceki örnekte, `IPlugin` sözleşme türüdür.) Bunlar, geçersiz kılma yerine farklıysa ikinci öznitelik ikinci, bağımsız bir verme bölümünden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="59b80-262">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="59b80-263">Genellikle, bu, geçersiz kıldığınızda anlaşma türünü açıkça belirtmek olacağı anlamına gelir bir `InheritedExport` özniteliği, önceki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="59b80-263">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>  
  
 <span data-ttu-id="59b80-264">Arabirimleri doğrudan başlatılamaz olduğundan, bunlar genellikle ile tasarlanır `Export` veya `Import` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="59b80-264">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="59b80-265">Ancak, bir arabirim ile tasarlanabilir bir `InheritedExport` özniteliği arabirimi düzeyinde ve ilişkili meta verileri dışarı aktarma herhangi yanı sıra tüm sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="59b80-265">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="59b80-266">Arabirim ancak bir parçası olarak kullanılabilir olmaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-266">The interface itself will not be available as a part, however.</span></span>  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a><span data-ttu-id="59b80-267">Özel dışarı aktarım öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="59b80-267">Custom Export Attributes</span></span>  
 <span data-ttu-id="59b80-268">Temel dışarı aktarım öznitelikleri `Export` ve `InheritedExport`, meta verileri öznitelik özellikleri olarak eklemek için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-268">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="59b80-269">Bu teknik benzer meta verileri birçok bölüme uygulamak veya meta veri özniteliklerinin kalıtım ağacını oluşturmak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="59b80-269">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>  
  
 <span data-ttu-id="59b80-270">Özel bir öznitelik anlaşma türü, sözleşme adı veya diğer meta verileri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59b80-270">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="59b80-271">İçinden devralma sınıfı özel bir öznitelik tanımlamak için `ExportAttribute` (veya `InheritedExportAttribute`) ile tasarlanmalıdır `MetadataAttribute` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-271">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="59b80-272">Aşağıdaki sınıf özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59b80-272">The following class defines a custom attribute.</span></span>  
  
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
  
 <span data-ttu-id="59b80-273">Bu sınıf adlı özel bir öznitelik tanımlar `MyAttribute` sözleşme türüyle `IMyData` ve adlı bazı meta verileri `MyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="59b80-273">This class defines a custom attribute named `MyAttribute` with contract type `IMyData` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="59b80-274">Bir sınıftaki tüm özellikler işaretlenmiş `MetadataAttribute` özniteliği özel özniteliğinde tanımlanan meta veriler olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-274">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="59b80-275">Aşağıdaki iki bildirim eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="59b80-275">The following two declarations are equivalent.</span></span>  
  
```vb  
<Export(GetType(IMyAddin))>  
<ExportMetadata("MyMetadata", "theData")>  
Public Property myAddin As MyAddin  
  
<MyAttribute("theData")>  
Public Property myAddin As MyAddin  
```  
  
```csharp  
[Export(typeof(IMyAddin)),   
    ExportMetadata("MyMetadata", "theData")]  
public MyAddin myAddin { get; set; }  
```  
  
```  
[MyAttribute("theData")]  
public MyAddin myAddin { get; set; }  
```  
  
 <span data-ttu-id="59b80-276">İlk bildiriminde sözleşme türü ve meta veriler açık olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="59b80-276">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="59b80-277">İkinci bildiriminde anlaşma türü ve meta veri özelleştirilmiş özniteliğinde örtük.</span><span class="sxs-lookup"><span data-stu-id="59b80-277">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="59b80-278">Aynı meta verilerinin büyük bir miktarını birçok bölümleri (örneğin, yazar veya telif hakkı bilgileri) burada uygulanması gereken durumlarda özellikle çok fazla zaman ve çoğaltma özel bir öznitelik kullanarak kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59b80-278">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="59b80-279">Ayrıca, özel özniteliklerin kalıtım ağaçları farklılıklara izin vermek için oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-279">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>  
  
 <span data-ttu-id="59b80-280">İsteğe bağlı meta veriler özel bir öznitelik oluşturmak için kullanabileceğiniz `DefaultValue` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-280">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="59b80-281">Bu öznitelik, bir özel öznitelik sınıftaki bir özelliğe uygulandığında düzenlenmiş özellik isteğe bağlıdır ve bir dışarı aktarma tarafından sağlanması gerekmez belirtir.</span><span class="sxs-lookup"><span data-stu-id="59b80-281">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="59b80-282">Özelliği için bir değer sağlanmazsa, bu özellik türü için varsayılan değer atanacak (genellikle `null`, `false`, ya da 0.)</span><span class="sxs-lookup"><span data-stu-id="59b80-282">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a><span data-ttu-id="59b80-283">Oluşturma ilkeleri</span><span class="sxs-lookup"><span data-stu-id="59b80-283">Creation Policies</span></span>  
 <span data-ttu-id="59b80-284">Bir bölümü bir içeri aktarma ve birleşim gerçekleştirildiğinde, kapsayıcının eşleşen bir dışarı aktarım bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="59b80-284">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="59b80-285">Bir verme içeri aktarmaya başarıyla eşleşirse, içeri aktarma üye dışarı aktarılan nesnenin örneğine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="59b80-285">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="59b80-286">Bu örnek nereden geldiğini dışarı aktarılan bölümün tarafından denetlenir *oluşturma ilkesi*.</span><span class="sxs-lookup"><span data-stu-id="59b80-286">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>  
  
 <span data-ttu-id="59b80-287">İki olası oluşturma ilke *paylaşılan* ve *paylaşılmayan*.</span><span class="sxs-lookup"><span data-stu-id="59b80-287">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="59b80-288">Bir parçası oluşturma ilkesi ile paylaşılan sözleşme sahip bir bölüm için kapsayıcıdaki her içeri aktarma arasında paylaştırılır.</span><span class="sxs-lookup"><span data-stu-id="59b80-288">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="59b80-289">Bileşim motoru bir eşleşme bulur ve içeri aktarma özelliğini ayarlamak sahip olduğunda yalnızca bir zaten mevcut değilse yeni bir kopya bölümünün örneği; Aksi takdirde, varolan kopyayı kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="59b80-289">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="59b80-290">Bu, birçok nesne başvuruları aynı bölüm için olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="59b80-290">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="59b80-291">Bu tür bölümleri birçok yerden değiştirilebilir iç durumu güvenmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="59b80-291">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="59b80-292">Bu ilke, statik bölümleri, hizmetler sağlayan bölümler ve çok miktarda bellek veya diğer kaynakları tüketen bölümleri için uygundur.</span><span class="sxs-lookup"><span data-stu-id="59b80-292">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>  
  
 <span data-ttu-id="59b80-293">Eşleşen bir içeri aktarma, dışarı aktarma biri için bulunan her zaman bir parçası oluşturma ilkesiyle paylaşılmayan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59b80-293">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="59b80-294">Yeni bir kopyasını, bu nedenle bölümün dışarı aktarılan sözleşmeleri biriyle eşleşen kapsayıcıdaki her bir içeri aktarma için oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="59b80-294">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="59b80-295">Bu kopyalar iç durumu paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-295">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="59b80-296">Bu ilke, burada her alma iç durumuna ihtiyaç duyduğu bölümler için uygundur.</span><span class="sxs-lookup"><span data-stu-id="59b80-296">This policy is appropriate for parts where each import requires its own internal state.</span></span>  
  
 <span data-ttu-id="59b80-297">İçeri aktarma ve dışarı aktarma değerlerinden bir bölümün oluşturma ilkesi belirleyebilirsiniz `Shared`, `NonShared`, veya `Any`.</span><span class="sxs-lookup"><span data-stu-id="59b80-297">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="59b80-298">Varsayılan değer `Any` her ikisi için alır ve verir.</span><span class="sxs-lookup"><span data-stu-id="59b80-298">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="59b80-299">Belirleyen bir dışarı aktarım `Shared` veya `NonShared` yalnızca aynısını belirten ya da belirten bir içeri aktarma ile eşleşir `Any`.</span><span class="sxs-lookup"><span data-stu-id="59b80-299">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="59b80-300">Benzer şekilde, belirten alma `Shared` veya `NonShared` yalnızca aynısını belirten ya da belirten bir dışarı aktarma ile eşleşir `Any`.</span><span class="sxs-lookup"><span data-stu-id="59b80-300">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="59b80-301">İçeri ve dışarı aktarmalar uyumsuz oluşturma ilkeleri ile bir eşleşme bir içeri aktarma ve dışarı aktarma, sözleşme adı veya sözleşme türü bir eşleşme olmayan aynı şekilde dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-301">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="59b80-302">İçeri ve dışarı aktarma belirtirseniz, `Any`, değil oluşturma ilkesi belirtin veya varsayılan `Any`, oluşturma ilkesi paylaşılan varsayılan olur.</span><span class="sxs-lookup"><span data-stu-id="59b80-302">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>  
  
 <span data-ttu-id="59b80-303">Aşağıdaki örnek, içeri ve dışarı aktarma oluşturma ilkeleri belirtme gösterir.</span><span class="sxs-lookup"><span data-stu-id="59b80-303">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="59b80-304">`PartOne`Varsayılan değer olacak şekilde bir oluşturma ilkesi belirtmiyor `Any`.</span><span class="sxs-lookup"><span data-stu-id="59b80-304">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="59b80-305">`PartTwo`Varsayılan değer olacak şekilde bir oluşturma ilkesi belirtmiyor `Any`.</span><span class="sxs-lookup"><span data-stu-id="59b80-305">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="59b80-306">Her ikisi de içeri ve varsayılan olarak dışarı aktarma beri `Any`, `PartOne` paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="59b80-306">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="59b80-307">`PartThree`belirten bir `Shared` oluşturma ilkesi, bu nedenle `PartTwo` ve `PartThree` aynı kopyasını paylaşır `PartOne`.</span><span class="sxs-lookup"><span data-stu-id="59b80-307">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="59b80-308">`PartFour`belirten bir `NonShared` oluşturma ilkesi, bu nedenle `PartFour` içinde paylaşılmayan olacaktır `PartFive`.</span><span class="sxs-lookup"><span data-stu-id="59b80-308">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="59b80-309">`PartSix`belirten bir `NonShared` oluşturma ilkesi.</span><span class="sxs-lookup"><span data-stu-id="59b80-309">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="59b80-310">`PartFive`ve `PartSix` her ayrı kopyası alacak `PartFour`.</span><span class="sxs-lookup"><span data-stu-id="59b80-310">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="59b80-311">`PartSeven`belirten bir `Shared` oluşturma ilkesi.</span><span class="sxs-lookup"><span data-stu-id="59b80-311">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="59b80-312">Olduğundan dışarı aktarılan `PartFour` oluşturma ilkesi ile `Shared`, `PartSeven` alma şeyle eşleşmez ve doldurulmaz.</span><span class="sxs-lookup"><span data-stu-id="59b80-312">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>  
  
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
    'Since the export's creation policy was explictly  
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
    //Since the export's creation policy was explictly  
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
## <a name="life-cycle-and-disposing"></a><span data-ttu-id="59b80-313">Yaşam döngüsü ve atma</span><span class="sxs-lookup"><span data-stu-id="59b80-313">Life Cycle and Disposing</span></span>  
 <span data-ttu-id="59b80-314">Bölümleri bileşim kapsayıcıda barındırıldığından, yaşam döngüsü sıradan nesnelerden daha karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-314">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="59b80-315">Bölümleri iki önemli yaşam döngüsü ile ilgili arabirimler uygulayabilirsiniz: `IDisposable` ve `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="59b80-315">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>  
  
 <span data-ttu-id="59b80-316">Kapatma sırasında aşağı yapılması iş gerektiren veya kaynakları serbest bırakmak gereken bölümleri uygulamanız gerekir `IDisposable`, .NET Framework nesneleri için normal.</span><span class="sxs-lookup"><span data-stu-id="59b80-316">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="59b80-317">Ancak, kapsayıcıyı oluşturur ve bölümlere referanslar bulundurur olduğundan, yalnızca bir bölüm kapsayıcı çağırmalıdır `Dispose` yöntemini.</span><span class="sxs-lookup"><span data-stu-id="59b80-317">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="59b80-318">Kapsayıcı uygulayan `IDisposable`ve kendi temizleme bölümü olarak `Dispose` çağırır `Dispose` sahip olduğu tüm bölümleri.</span><span class="sxs-lookup"><span data-stu-id="59b80-318">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="59b80-319">Ve sahip olduğu tüm parçaları artık gerekli değildir, bu nedenle, her zaman kapsayıcının silmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="59b80-319">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>  
  
 <span data-ttu-id="59b80-320">Uzun dönemli bileşim kapsayıcılar için paylaşılmayan oluşturma ilkesi ile bölümleri bellek tüketimi bir sorun olabilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-320">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="59b80-321">Paylaşılmayan bölümleri birden çok kez oluşturulabilir ve kapsayıcı bırakılana kadar silinecek değil.</span><span class="sxs-lookup"><span data-stu-id="59b80-321">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="59b80-322">Bu işlem için kapsayıcı sağlar `ReleaseExport` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="59b80-322">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="59b80-323">Paylaşılmayan bir dışarı aktarma üzerinde bu yöntemi çağırmadan birleşim kapsayıcıdan bu dışarı kaldırır ve siler.</span><span class="sxs-lookup"><span data-stu-id="59b80-323">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="59b80-324">Yalnızca ağaç aşağı ve benzeri kaldırılan dışarı aktarım tarafından kullanılan bölümleri da kaldırılır ve atıldı.</span><span class="sxs-lookup"><span data-stu-id="59b80-324">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="59b80-325">Bu şekilde, kapsayıcının kendisini atma olmadan kaynakları istenemiyor.</span><span class="sxs-lookup"><span data-stu-id="59b80-325">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>  
  
 <span data-ttu-id="59b80-326">`IPartImportsSatisfiedNotification`adlı bir yöntem içerir `OnImportsSatisfied`.</span><span class="sxs-lookup"><span data-stu-id="59b80-326">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="59b80-327">Bu yöntem, kapsayıcının birleşim tamamlandı ve bölümünün içeri aktarmalar kullanıma hazır olduğunda arabirimini uygulayan tüm bölümleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="59b80-327">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="59b80-328">Bölümleri diğer bölümleri Imports doldurmak için bileşim motoru tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59b80-328">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="59b80-329">İçeri aktarmalar bir bölümü ayarlamadan önce dayanan veya bu değerleri kullanarak önkoşul olarak belirtilmiş sürece bölüm oluşturucusu içerisinde içeri aktarılan değerlerini işleyen hiçbir başlangıç gerçekleştiremezsiniz `ImportingConstructor` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59b80-329">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="59b80-330">Bu genellikle tercih edilen yöntemdir, ancak bazı durumlarda Oluşturucu ekleme kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="59b80-330">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="59b80-331">Bu gibi durumlarda başlatma gerçekleştirilebilecek `OnImportsSatisfied`, ve bölümü uygulamalıdır `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="59b80-331">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b80-332">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59b80-332">See Also</span></span>  
 [<span data-ttu-id="59b80-333">Kanal 9 Video: Yönetilen Genişletilebilirlik Çerçevesi uygulamalarınızla açın</span><span class="sxs-lookup"><span data-stu-id="59b80-333">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](http://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)  
 [<span data-ttu-id="59b80-334">Kanal 9 Video: Yönetilen Genişletilebilirlik Çerçevesi (MEF) 2.0</span><span class="sxs-lookup"><span data-stu-id="59b80-334">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](http://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)

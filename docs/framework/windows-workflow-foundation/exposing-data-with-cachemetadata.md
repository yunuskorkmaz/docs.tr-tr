---
title: CacheMetadata ile verileri gösterme
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: a044c896e56541ee954fc33853376eb8293c6ede
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482684"
---
# <a name="exposing-data-with-cachemetadata"></a><span data-ttu-id="5667b-102">CacheMetadata ile verileri gösterme</span><span class="sxs-lookup"><span data-stu-id="5667b-102">Exposing data with CacheMetadata</span></span>

<span data-ttu-id="5667b-103">Bir etkinlik çalıştırmadan önce iş akışı çalışma zamanı yürütme sürdürmek için gereken etkinlik hakkında tüm bilgiler alır.</span><span class="sxs-lookup"><span data-stu-id="5667b-103">Before executing an activity, the workflow runtime obtains all of the information about the activity that it needs in order to maintain its execution.</span></span> <span data-ttu-id="5667b-104">İş akışı çalışma zamanı yürütme sırasında bu bilgileri alır <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5667b-104">The workflow runtime gets this information during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="5667b-105">Varsayılan uygulama bu yöntemin tüm genel bağımsız değişkenler, değişkenler ve çocuk etkinliklerinin zamanında yürütülür etkinlik tarafından sunulan çalışma zamanı sağlar; Etkinlik daha fazla bilgi için çalışma zamanı bu (örneğin, özel üyeler veya etkinlikleri etkinlik tarafından zamanlanması) vermeniz gerekiyorsa, bunu sağlamak için bu yöntem geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="5667b-105">The default implementation of this method provides the runtime with all of the public arguments, variables, and child activities exposed by the activity at the time it is executed; if the activity needs to give more information to the runtime than this (such as private members, or activities to be scheduled by the activity), this method can be overridden to provide it.</span></span>

## <a name="default-cachemetadata-behavior"></a><span data-ttu-id="5667b-106">Varsayılan CacheMetadata davranışı</span><span class="sxs-lookup"><span data-stu-id="5667b-106">Default CacheMetadata behavior</span></span>

<span data-ttu-id="5667b-107">Varsayılan uygulaması <xref:System.Activities.NativeActivity.CacheMetadata%2A> öğesinden türetilen etkinlikler için <xref:System.Activities.NativeActivity> aşağıdaki yöntemi türleri aşağıdaki yollarla işler:</span><span class="sxs-lookup"><span data-stu-id="5667b-107">The default implementation of <xref:System.Activities.NativeActivity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.NativeActivity> processes the following method types in the following ways:</span></span>

- <span data-ttu-id="5667b-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, veya <xref:System.Activities.InOutArgument%601> (Genel değişkenler): Bu bağımsız değişkenler, çalışma zamanı için bir ada sahip bağımsız değişken olarak sunulur ve açık özellik adı ve türü, uygun bağımsız değişken yönünü ve bazı doğrulama verileri eşit yazın.</span><span class="sxs-lookup"><span data-stu-id="5667b-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, or <xref:System.Activities.InOutArgument%601> (generic arguments): These arguments are exposed to the runtime as arguments with a name and type equal to the exposed property name and type, the appropriate argument direction, and some validation data.</span></span>

- <span data-ttu-id="5667b-109"><xref:System.Activities.Variable> veya tüm alt yapanın: Bu üyeleri çalışma zamanının genel değişkenleri olarak kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="5667b-109"><xref:System.Activities.Variable> or any subclass thereof: These members are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="5667b-110"><xref:System.Activities.Activity> veya tüm alt yapanın: Bu üyeleri çalışma zamanının Genel alt etkinlikler kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="5667b-110"><xref:System.Activities.Activity> or any subclass thereof: These members are exposed to the runtime as public child activities.</span></span> <span data-ttu-id="5667b-111">Varsayılan davranış çağrılarak açıkça uygulanabilir <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, geçen alt etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5667b-111">The default behavior can be implemented explicitly by calling <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passing in the child activity.</span></span>

- <span data-ttu-id="5667b-112"><xref:System.Activities.ActivityDelegate> veya tüm alt yapanın: Bu üyeleri çalışma zamanının genel temsilciler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="5667b-112"><xref:System.Activities.ActivityDelegate> or any subclass thereof: These members are exposed to the runtime as public delegates.</span></span>

- <span data-ttu-id="5667b-113"><xref:System.Collections.ICollection> tür <xref:System.Activities.Variable>: Koleksiyondaki tüm öğeler için çalışma zamanı, genel değişkenleri olarak kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="5667b-113"><xref:System.Collections.ICollection> of type <xref:System.Activities.Variable>: All elements in the collection are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="5667b-114"><xref:System.Collections.ICollection> tür <xref:System.Activities.Activity>: Koleksiyondaki tüm öğeler için çalışma zamanı ortak bir alt öğe olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="5667b-114"><xref:System.Collections.ICollection> of type <xref:System.Activities.Activity>: All elements in the collection are exposed to the runtime as public children.</span></span>

- <span data-ttu-id="5667b-115"><xref:System.Collections.ICollection> tür <xref:System.Activities.ActivityDelegate>: Koleksiyondaki tüm öğeleri çalışma zamanına genel temsilciler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="5667b-115"><xref:System.Collections.ICollection> of type <xref:System.Activities.ActivityDelegate>: All elements in the collection are exposed to the runtime as public delegates.</span></span>

<span data-ttu-id="5667b-116"><xref:System.Activities.Activity.CacheMetadata%2A> Öğesinden türetilen etkinlikler için <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, ve <xref:System.Activities.AsyncCodeActivity> da işlev yukarıda gerçekleştirildiği gibi aşağıdaki farklar dışında:</span><span class="sxs-lookup"><span data-stu-id="5667b-116">The <xref:System.Activities.Activity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, and <xref:System.Activities.AsyncCodeActivity> also function as above, except for the following differences:</span></span>

- <span data-ttu-id="5667b-117">Öğesinden türetilen sınıfları <xref:System.Activities.Activity> çocuk etkinliklerinin veya Temsilciler, tür üyeleri, içeri aktarılan alt öğeleri ve temsilcileri; sunulur. Bu nedenle zamanlayamazsınız</span><span class="sxs-lookup"><span data-stu-id="5667b-117">Classes that derive from <xref:System.Activities.Activity> cannot schedule child activities or delegates, so such members are exposed as imported children and delegates; the</span></span>

- <span data-ttu-id="5667b-118">Öğesinden türetilen sınıfları <xref:System.Activities.CodeActivity> ve <xref:System.Activities.AsyncCodeActivity> yalnızca bağımsız değişkenler kullanıma sunulacak şekilde değişkenleri, alt ve temsilciler desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5667b-118">Classes that derive from <xref:System.Activities.CodeActivity> and <xref:System.Activities.AsyncCodeActivity> do not support variables, children, or delegates, so only arguments will be exposed.</span></span>

## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a><span data-ttu-id="5667b-119">CacheMetadata çalışma zamanı bilgileri sağlamak için geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="5667b-119">Overriding CacheMetadata to provide information to the runtime</span></span>

<span data-ttu-id="5667b-120">Aşağıdaki kod parçacığı üyeleri hakkında bilgi yürütülmesi sırasında bir etkinliğe ilişkin meta verileri eklemek gösterilmiştir <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5667b-120">The following code snippet demonstrates how to add information about members to an activity’s metadata during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="5667b-121">Etkinlikle ilgili tüm genel verileri önbelleğe almak için temel yöntemin çağrıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5667b-121">Note that the base of the method is called to cache all public data about the activity.</span></span>

```csharp
protected override void CacheMetadata(NativeActivityMetadata metadata)
{
    base.CacheMetadata(metadata);
    metadata.AddImplementationChild(this._writeLine);
    metadata.AddVariable(this._myVariable);
    metadata.AddImplementationVariable(this._myImplementationVariable);

    RuntimeArgument argument = new RuntimeArgument("MyArgument", ArgumentDirection.In, typeof(SomeType));
    metadata.Bind(argument, this.SomeName);
    metadata.AddArgument(argument);
}
```

## <a name="using-cachemetadata-to-expose-implementation-children"></a><span data-ttu-id="5667b-122">CacheMetadata uygulama alt öğeleri göstermek için kullanma</span><span class="sxs-lookup"><span data-stu-id="5667b-122">Using CacheMetadata to expose implementation children</span></span>

<span data-ttu-id="5667b-123">Değişkenleri kullanarak bir etkinlik tarafından zamanlanması gereken alt etkinliklere veri geçirmek için değişkenleri uygulama değişkenleri olarak eklemek gereklidir. Genel değişkenler bu şekilde değerlerine sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="5667b-123">In order to pass data to child activities that are to be scheduled by an activity using variables, it is necessary to add the variables as implementation variables; public variables cannot have their values set this way.</span></span> <span data-ttu-id="5667b-124">Bunun nedeni, etkinlikleri (hangi özelliklere sahip) kapsüllenmiş sınıfları yerine (Bu parametrelere sahip) işlevleri uygulamaları daha yürütülecek yöneliktir ' dir.</span><span class="sxs-lookup"><span data-stu-id="5667b-124">The reason for this is that activities are intended to be executed more as implementations of functions (which have parameters), rather than encapsulated classes (which have properties).</span></span> <span data-ttu-id="5667b-125">Bununla birlikte, bağımsız değişkenleri açıkça ayarlanması gerekir, ne zaman gibi durumlar vardır kullanarak <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, zamanlanan etkinlikten bir alt etkinlik olduğu gibi üst etkinliğin bağımsız değişken erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5667b-125">However, there are situations in which the arguments must be explicitly set, such as when using <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, since the scheduled activity doesn't have access to the parent activity's arguments in the way a child activity would.</span></span>

<span data-ttu-id="5667b-126">Aşağıdaki kod parçacığını kullanarak bir zamanlanan etkinlik yerel etkinlik bağımsız değişkeni form geçirilecek gösterilmiştir <xref:System.Activities.Activity.CacheMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="5667b-126">The following code snippet demonstrates how to pass an argument form a native activity into a scheduled activity using <xref:System.Activities.Activity.CacheMetadata%2A>.</span></span>

```csharp
public sealed class ChildActivity : NativeActivity
{
    public WriteLine _writeLine;
    public InArgument<string> Message { get; set; }
    private Variable<string> MessageVariable { get; set; }
    public ChildActivity()
    {
        MessageVariable = new Variable<string>();
        _writeLine = new WriteLine
        {
            Text = new InArgument<string>(MessageVariable),
        };
    }
    protected override void CacheMetadata(NativeActivityMetadata metadata)
    {
        base.CacheMetadata(metadata);
        metadata.AddImplementationVariable(this.MessageVariable);
        metadata.AddImplementationChild(this._writeLine);
    }
    protected override void Execute(NativeActivityContext context)
    {
        string configuredMessage = context.GetValue(Message);
        context.SetValue(MessageVariable, configuredMessage);
        context.ScheduleActivity(this._writeLine);
    }
}
```

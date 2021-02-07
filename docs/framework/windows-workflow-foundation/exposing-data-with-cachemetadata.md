---
description: 'Hakkında daha fazla bilgi edinin: CacheMetadata ile verileri gösterme'
title: CacheMetadata ile verileri kullanıma sunma
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: ac4623881ebd76270f773a3b7acfe205ad365118
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742348"
---
# <a name="exposing-data-with-cachemetadata"></a><span data-ttu-id="8c22f-103">CacheMetadata ile verileri kullanıma sunma</span><span class="sxs-lookup"><span data-stu-id="8c22f-103">Exposing data with CacheMetadata</span></span>

<span data-ttu-id="8c22f-104">Bir etkinliği yürütmeden önce, iş akışı çalışma zamanı, çalışmasını sürdürmek için ihtiyacı olan etkinlik hakkındaki tüm bilgileri edinir.</span><span class="sxs-lookup"><span data-stu-id="8c22f-104">Before executing an activity, the workflow runtime obtains all of the information about the activity that it needs in order to maintain its execution.</span></span> <span data-ttu-id="8c22f-105">İş akışı çalışma zamanı, yöntemin yürütülmesi sırasında bu bilgileri alır <xref:System.Activities.Activity.CacheMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="8c22f-105">The workflow runtime gets this information during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="8c22f-106">Bu yöntemin varsayılan uygulamasının çalışma zamanını, yürütüldüğü sırada etkinliğin açığa çıkarılan tüm genel bağımsız değişkenler, değişkenler ve alt etkinlikleri sağlar; etkinliğin çalışma zamanına bu kadar daha fazla bilgi vermesi gerekiyorsa (özel Üyeler veya etkinlik tarafından zamanlanacak etkinlikler gibi), bu yöntem sağlamak için geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="8c22f-106">The default implementation of this method provides the runtime with all of the public arguments, variables, and child activities exposed by the activity at the time it is executed; if the activity needs to give more information to the runtime than this (such as private members, or activities to be scheduled by the activity), this method can be overridden to provide it.</span></span>

## <a name="default-cachemetadata-behavior"></a><span data-ttu-id="8c22f-107">Varsayılan CacheMetadata davranışı</span><span class="sxs-lookup"><span data-stu-id="8c22f-107">Default CacheMetadata behavior</span></span>

<span data-ttu-id="8c22f-108"><xref:System.Activities.NativeActivity.CacheMetadata%2A>' Den türetilen etkinlikler için varsayılan uygulama, aşağıdaki <xref:System.Activities.NativeActivity> yöntemlerle aşağıdaki yöntem türlerini işler:</span><span class="sxs-lookup"><span data-stu-id="8c22f-108">The default implementation of <xref:System.Activities.NativeActivity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.NativeActivity> processes the following method types in the following ways:</span></span>

- <span data-ttu-id="8c22f-109"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> veya <xref:System.Activities.InOutArgument%601> (genel bağımsız değişkenler): Bu bağımsız değişkenler, çalışma zamanına, sunulan özellik adı ve türüne, uygun bağımsız değişken yönüne ve bazı doğrulama verilerine eşit bir ad ve tür olan bağımsız değişkenler olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8c22f-109"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, or <xref:System.Activities.InOutArgument%601> (generic arguments): These arguments are exposed to the runtime as arguments with a name and type equal to the exposed property name and type, the appropriate argument direction, and some validation data.</span></span>

- <span data-ttu-id="8c22f-110"><xref:System.Activities.Variable> veya herhangi bir alt sınıf: Bu Üyeler çalışma zamanına genel değişkenler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="8c22f-110"><xref:System.Activities.Variable> or any subclass thereof: These members are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="8c22f-111"><xref:System.Activities.Activity> veya herhangi bir alt sınıf: Bu Üyeler çalışma zamanına genel alt etkinlikler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="8c22f-111"><xref:System.Activities.Activity> or any subclass thereof: These members are exposed to the runtime as public child activities.</span></span> <span data-ttu-id="8c22f-112">Varsayılan davranış çağırarak <xref:System.Activities.ActivityMetadata.AddImportedChild%2A> , alt etkinliği geçirerek açıkça uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8c22f-112">The default behavior can be implemented explicitly by calling <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passing in the child activity.</span></span>

- <span data-ttu-id="8c22f-113"><xref:System.Activities.ActivityDelegate> veya herhangi bir alt sınıf: Bu Üyeler çalışma zamanına Genel Temsilciler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="8c22f-113"><xref:System.Activities.ActivityDelegate> or any subclass thereof: These members are exposed to the runtime as public delegates.</span></span>

- <span data-ttu-id="8c22f-114"><xref:System.Collections.ICollection> türü <xref:System.Activities.Variable> : koleksiyondaki tüm öğeler çalışma zamanına ortak değişkenler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="8c22f-114"><xref:System.Collections.ICollection> of type <xref:System.Activities.Variable>: All elements in the collection are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="8c22f-115"><xref:System.Collections.ICollection> türü <xref:System.Activities.Activity> : koleksiyondaki tüm öğeler çalışma zamanına ortak alt öğeler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="8c22f-115"><xref:System.Collections.ICollection> of type <xref:System.Activities.Activity>: All elements in the collection are exposed to the runtime as public children.</span></span>

- <span data-ttu-id="8c22f-116"><xref:System.Collections.ICollection> türü <xref:System.Activities.ActivityDelegate> : koleksiyondaki tüm öğeler, çalışma zamanına Genel Temsilciler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="8c22f-116"><xref:System.Collections.ICollection> of type <xref:System.Activities.ActivityDelegate>: All elements in the collection are exposed to the runtime as public delegates.</span></span>

<span data-ttu-id="8c22f-117"><xref:System.Activities.Activity.CacheMetadata%2A> <xref:System.Activities.Activity> <xref:System.Workflow.Activities.CodeActivity> Aşağıdaki farklar dışında, ve ' den türetilen etkinlikler için <xref:System.Activities.AsyncCodeActivity> :</span><span class="sxs-lookup"><span data-stu-id="8c22f-117">The <xref:System.Activities.Activity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, and <xref:System.Activities.AsyncCodeActivity> also function as above, except for the following differences:</span></span>

- <span data-ttu-id="8c22f-118">Öğesinden türetilen sınıflar <xref:System.Activities.Activity> alt etkinlikleri veya temsilcileri zamanlayamaz, bu nedenle bu Üyeler, içeri aktarılan alt öğeler ve temsilciler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="8c22f-118">Classes that derive from <xref:System.Activities.Activity> cannot schedule child activities or delegates, so such members are exposed as imported children and delegates; the</span></span>

- <span data-ttu-id="8c22f-119">Ve ' den türetilen <xref:System.Activities.CodeActivity> ve <xref:System.Activities.AsyncCodeActivity> değişkenleri, alt öğeleri veya temsilcileri desteklemeyen sınıflar, bu nedenle yalnızca bağımsız değişkenler sunulur.</span><span class="sxs-lookup"><span data-stu-id="8c22f-119">Classes that derive from <xref:System.Activities.CodeActivity> and <xref:System.Activities.AsyncCodeActivity> do not support variables, children, or delegates, so only arguments will be exposed.</span></span>

## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a><span data-ttu-id="8c22f-120">Çalışma zamanına bilgi sağlamak için CacheMetadata geçersiz kılınıyor</span><span class="sxs-lookup"><span data-stu-id="8c22f-120">Overriding CacheMetadata to provide information to the runtime</span></span>

<span data-ttu-id="8c22f-121">Aşağıdaki kod parçacığı, yöntemin yürütülmesi sırasında bir etkinliğin meta verilerine Üyeler hakkında nasıl bilgi ekleneceğini gösterir <xref:System.Activities.Activity.CacheMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="8c22f-121">The following code snippet demonstrates how to add information about members to an activity’s metadata during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="8c22f-122">Yöntemin temelini, etkinlikle ilgili tüm genel verileri önbelleğe almak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="8c22f-122">Note that the base of the method is called to cache all public data about the activity.</span></span>

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

## <a name="using-cachemetadata-to-expose-implementation-children"></a><span data-ttu-id="8c22f-123">Uygulama alt öğelerini göstermek için CacheMetadata kullanma</span><span class="sxs-lookup"><span data-stu-id="8c22f-123">Using CacheMetadata to expose implementation children</span></span>

<span data-ttu-id="8c22f-124">Değişkenleri kullanarak bir etkinlik tarafından zamanlanacak alt etkinliklere veri geçirmek için, değişkenleri uygulama değişkenleri olarak eklemek gerekir; ortak değişkenlerin değerleri bu şekilde ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="8c22f-124">In order to pass data to child activities that are to be scheduled by an activity using variables, it is necessary to add the variables as implementation variables; public variables cannot have their values set this way.</span></span> <span data-ttu-id="8c22f-125">Bunun nedeni, etkinliklerin (özellikleri olan) kapsüllenmiş sınıflar yerine işlevlerin (parametrelere sahip) uygulamalar olarak daha fazla yürütülmesi amacını taşımaktadır.</span><span class="sxs-lookup"><span data-stu-id="8c22f-125">The reason for this is that activities are intended to be executed more as implementations of functions (which have parameters), rather than encapsulated classes (which have properties).</span></span> <span data-ttu-id="8c22f-126">Ancak, <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> zamanlanan etkinliğin bir alt etkinliğin olduğu şekilde üst etkinliğin bağımsız değişkenlerine erişimi olmadığından bağımsız değişkenlerin açıkça ayarlanması gerektiği durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="8c22f-126">However, there are situations in which the arguments must be explicitly set, such as when using <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, since the scheduled activity doesn't have access to the parent activity's arguments in the way a child activity would.</span></span>

<span data-ttu-id="8c22f-127">Aşağıdaki kod parçacığı, kullanarak bir bağımsız değişkenin bir yerel etkinlik olarak zamanlanan bir etkinliğe nasıl geçirileceğini gösterir <xref:System.Activities.Activity.CacheMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="8c22f-127">The following code snippet demonstrates how to pass an argument form a native activity into a scheduled activity using <xref:System.Activities.Activity.CacheMetadata%2A>.</span></span>

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

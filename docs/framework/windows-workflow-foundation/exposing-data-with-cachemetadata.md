---
title: CacheMetadata verilerle gösterme
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: 386bbb8734e26eff8079f2913284668125a8a774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515258"
---
# <a name="exposing-data-with-cachemetadata"></a><span data-ttu-id="c7224-102">CacheMetadata verilerle gösterme</span><span class="sxs-lookup"><span data-stu-id="c7224-102">Exposing data with CacheMetadata</span></span>
<span data-ttu-id="c7224-103">Bir etkinliği yürütmeden önce iş akışı çalışma zamanı tüm yürütülmesinin korumak için gereken etkinliği hakkında bilgi edinir.</span><span class="sxs-lookup"><span data-stu-id="c7224-103">Before executing an activity, the workflow runtime obtains all of the information about the activity that it needs in order to maintain its execution.</span></span> <span data-ttu-id="c7224-104">İş akışı çalışma zamanı yürütme işlemi sırasında bu bilgileri alır <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c7224-104">The workflow runtime gets this information during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="c7224-105">Bu yöntem varsayılan uygulamasını tüm ortak bağımsız değişkenleri, değişkenler ve yürütülür aynı anda etkinlik tarafından sunulan alt etkinlikleri ile çalışma zamanı sağlar; Etkinlik daha fazla bilgi için çalışma zamanı bu (örneğin, özel üyelerin veya etkinlikleri etkinlik tarafından zamanlanacak) vermek gerekirse, bunu sağlamak için bu yöntem geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="c7224-105">The default implementation of this method provides the runtime with all of the public arguments, variables, and child activities exposed by the activity at the time it is executed; if the activity needs to give more information to the runtime than this (such as private members, or activities to be scheduled by the activity), this method can be overridden to provide it.</span></span>  
  
## <a name="default-cachemetadata-behavior"></a><span data-ttu-id="c7224-106">Varsayılan CacheMetadata davranışı</span><span class="sxs-lookup"><span data-stu-id="c7224-106">Default CacheMetadata behavior</span></span>  
 <span data-ttu-id="c7224-107">Varsayılan uygulaması <xref:System.Activities.NativeActivity.CacheMetadata%2A> öğesinden türetilen etkinlikler için <xref:System.Activities.NativeActivity> aşağıdaki yöntemi türleri aşağıdaki yollarla işler:</span><span class="sxs-lookup"><span data-stu-id="c7224-107">The default implementation of <xref:System.Activities.NativeActivity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.NativeActivity> processes the following method types in the following ways:</span></span>  
  
-   <span data-ttu-id="c7224-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, veya <xref:System.Activities.InOutArgument%601> (Genel değişkenler): Bu bağımsız değişkenler çalışma bir adı olan bağımsız değişkenler olarak sunulur ve sunulan özellik adı ve türü, uygun değişken yön ve bazı doğrulama veriler eşit yazın.</span><span class="sxs-lookup"><span data-stu-id="c7224-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, or <xref:System.Activities.InOutArgument%601> (generic arguments): These arguments are exposed to the runtime as arguments with a name and type equal to the exposed property name and type, the appropriate argument direction, and some validation data.</span></span>  
  
-   <span data-ttu-id="c7224-109"><xref:System.Activities.Variable> veya bunların herhangi bir alt: Bu üyeleri çalışma zamanına genel değişkenleri olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="c7224-109"><xref:System.Activities.Variable> or any subclass thereof: These members are exposed to the runtime as public variables.</span></span>  
  
-   <span data-ttu-id="c7224-110"><xref:System.Activities.Activity> veya bunların herhangi bir alt: Bu üyeleri çalışma zamanına Genel alt etkinlikler sunulur.</span><span class="sxs-lookup"><span data-stu-id="c7224-110"><xref:System.Activities.Activity> or any subclass thereof: These members are exposed to the runtime as public child activities.</span></span> <span data-ttu-id="c7224-111">Varsayılan davranış çağırarak uygulanan açıkça olabilir <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, alt etkinliğinde geçen.</span><span class="sxs-lookup"><span data-stu-id="c7224-111">The default behavior can be implemented explicity by calling <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passing in the child activity.</span></span>  
  
-   <span data-ttu-id="c7224-112"><xref:System.Activities.ActivityDelegate> veya bunların herhangi bir alt: Bu üyeleri çalışma zamanına Genel temsilci olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="c7224-112"><xref:System.Activities.ActivityDelegate> or any subclass thereof: These members are exposed to the runtime as public delegates.</span></span>  
  
-   <span data-ttu-id="c7224-113"><xref:System.Collections.ICollection> tür <xref:System.Activities.Variable>: koleksiyondaki tüm öğeleri çalışma zamanına genel değişkenleri olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="c7224-113"><xref:System.Collections.ICollection> of type <xref:System.Activities.Variable>: All elements in the collection are exposed to the runtime as public variables.</span></span>  
  
-   <span data-ttu-id="c7224-114"><xref:System.Collections.ICollection> tür <xref:System.Activities.Activity>: koleksiyondaki tüm öğeleri çalışma zamanına Genel alt öğesi olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="c7224-114"><xref:System.Collections.ICollection> of type <xref:System.Activities.Activity>: All elements in the collection are exposed to the runtime as public children.</span></span>  
  
-   <span data-ttu-id="c7224-115"><xref:System.Collections.ICollection> tür <xref:System.Activities.ActivityDelegate>: koleksiyondaki tüm öğeleri çalışma zamanına Genel temsilci olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="c7224-115"><xref:System.Collections.ICollection> of type <xref:System.Activities.ActivityDelegate>: All elements in the collection are exposed to the runtime as public delegates.</span></span>  
  
 <span data-ttu-id="c7224-116"><xref:System.Activities.Activity.CacheMetadata%2A> Öğesinden türetilen etkinlikler için <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, ve <xref:System.Activities.AsyncCodeActivity> da işlev olarak yukarıdaki aşağıdaki farklar dışında:</span><span class="sxs-lookup"><span data-stu-id="c7224-116">The <xref:System.Activities.Activity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, and <xref:System.Activities.AsyncCodeActivity> also function as above, except for the following differences:</span></span>  
  
-   <span data-ttu-id="c7224-117">Öğesinden türetilen sınıflar <xref:System.Activities.Activity> alt etkinlikler veya Temsilciler, bu tür üyeler alınan alt ve temsilciler; gösterilen şekilde zamanlayamazsınız</span><span class="sxs-lookup"><span data-stu-id="c7224-117">Classes that derive from <xref:System.Activities.Activity> cannot schedule child activities or delegates, so such members are exposed as imported children and delegates; the</span></span>  
  
-   <span data-ttu-id="c7224-118">Öğesinden türetilen sınıflar <xref:System.Activities.CodeActivity> ve <xref:System.Activities.AsyncCodeActivity> yalnızca bağımsız değişken gösterilen şekilde değişkenleri, alt öğelerini veya temsilciler desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c7224-118">Classes that derive from <xref:System.Activities.CodeActivity> and <xref:System.Activities.AsyncCodeActivity> do not support variables, children, or delegates, so only arguments will be exposed.</span></span>  
  
## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a><span data-ttu-id="c7224-119">Çalışma zamanı bilgileri sağlamak için CacheMetadata geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="c7224-119">Overriding CacheMetadata to provide information to the runtime</span></span>  
 <span data-ttu-id="c7224-120">Aşağıdaki kod parçacığını üyeleri hakkında bilgi için bir etkinliğe ilişkin meta verileri yürütülmesi sırasında ekleneceği gösterilmektedir <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c7224-120">The following code snippet demonstrates how to add information about members to an activity’s metadata during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="c7224-121">Yöntem tabanı etkinlikle ilgili tüm genel verileri önbelleğe almak için çağrılır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c7224-121">Note that the base of the method is called to cache all public data about the activity.</span></span>  
  
```  
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
  
## <a name="using-cachemetadata-to-expose-implementation-children"></a><span data-ttu-id="c7224-122">Uygulama alt kullanıma sunmak için CacheMetadata kullanma</span><span class="sxs-lookup"><span data-stu-id="c7224-122">Using CacheMetadata to expose implementation children</span></span>  
 <span data-ttu-id="c7224-123">Değişkenler kullanarak bir etkinlik tarafından zamanlanacak alt etkinlikleri için veri iletmek için uygulama değişkenleri olarak değişkenleri eklemek gereklidir; Genel değişkenler bu şekilde ayarlamak değerlerine sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="c7224-123">In order to pass data to child activities that are to be scheduled by an activity using variables, it is necessary to add the variables as implementation variables; public variables cannot have their values set this way.</span></span> <span data-ttu-id="c7224-124">Bunun nedeni, etkinlikler (özelliklerine sahip) kapsüllenmiş sınıflarını yerine (parametrelere sahip) işlevlerini uygulamaları daha yürütülmek üzere tasarlanmıştır ' dir.</span><span class="sxs-lookup"><span data-stu-id="c7224-124">The reason for this is that activities are intended to be executed more as implementations of functions (which have parameters), rather than encapsulated classes (which have properties).</span></span> <span data-ttu-id="c7224-125">Bununla birlikte, bağımsız değişkenler açıkça ayarlanmalıdır, zaman gibi durumlar vardır kullanarak <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, zamanlanan etkinlikten bir alt etkinlik olduğu gibi üst etkinliğin bağımsız değişken erişimi olmadığından.</span><span class="sxs-lookup"><span data-stu-id="c7224-125">However, there are situations in which the arguments must be explicitly set, such as when using <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, since the scheduled activity doesn't have access to the parent activity's arguments in the way a child activity would.</span></span>  
  
 <span data-ttu-id="c7224-126">Aşağıdaki kod parçacığını bir zamanlanan etkinlik kullanarak yerel bir etkinlik bir bağımsız değişken form geçmesine gösterilmiştir <xref:System.Activities.Activity.CacheMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7224-126">The following code snippet demonstrates how to pass an argument form a native activity into a scheduled activity using <xref:System.Activities.Activity.CacheMetadata%2A>.</span></span>  
  
```  
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

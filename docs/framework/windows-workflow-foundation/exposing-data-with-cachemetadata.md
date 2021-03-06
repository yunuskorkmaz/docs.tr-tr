---
description: 'Hakkında daha fazla bilgi edinin: CacheMetadata ile verileri gösterme'
title: CacheMetadata ile verileri kullanıma sunma
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: e3f4dc83a0e268ae548c904a714753fa025c77ae
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259791"
---
# <a name="exposing-data-with-cachemetadata"></a>CacheMetadata ile verileri kullanıma sunma

Bir etkinliği yürütmeden önce, iş akışı çalışma zamanı, çalışmasını sürdürmek için ihtiyacı olan etkinlik hakkındaki tüm bilgileri edinir. İş akışı çalışma zamanı, yöntemin yürütülmesi sırasında bu bilgileri alır <xref:System.Activities.Activity.CacheMetadata%2A> . Bu yöntemin varsayılan uygulamasının çalışma zamanını, yürütüldüğü sırada etkinliğin açığa çıkarılan tüm genel bağımsız değişkenler, değişkenler ve alt etkinlikleri sağlar; etkinliğin çalışma zamanına bu kadar daha fazla bilgi vermesi gerekiyorsa (özel Üyeler veya etkinlik tarafından zamanlanacak etkinlikler gibi), bu yöntem sağlamak için geçersiz kılınabilir.

## <a name="default-cachemetadata-behavior"></a>Varsayılan CacheMetadata davranışı

<xref:System.Activities.NativeActivity.CacheMetadata%2A>' Den türetilen etkinlikler için varsayılan uygulama, aşağıdaki <xref:System.Activities.NativeActivity> yöntemlerle aşağıdaki yöntem türlerini işler:

- <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> veya <xref:System.Activities.InOutArgument%601> (genel bağımsız değişkenler): Bu bağımsız değişkenler, çalışma zamanına, sunulan özellik adı ve türüne, uygun bağımsız değişken yönüne ve bazı doğrulama verilerine eşit bir ad ve tür olan bağımsız değişkenler olarak gösterilir.

- <xref:System.Activities.Variable> veya herhangi bir alt sınıf: Bu Üyeler çalışma zamanına genel değişkenler olarak sunulur.

- <xref:System.Activities.Activity> veya herhangi bir alt sınıf: Bu Üyeler çalışma zamanına genel alt etkinlikler olarak sunulur. Varsayılan davranış çağırarak <xref:System.Activities.ActivityMetadata.AddImportedChild%2A> , alt etkinliği geçirerek açıkça uygulanabilir.

- <xref:System.Activities.ActivityDelegate> veya herhangi bir alt sınıf: Bu Üyeler çalışma zamanına Genel Temsilciler olarak sunulur.

- <xref:System.Collections.ICollection> türü <xref:System.Activities.Variable> : koleksiyondaki tüm öğeler çalışma zamanına ortak değişkenler olarak sunulur.

- <xref:System.Collections.ICollection> türü <xref:System.Activities.Activity> : koleksiyondaki tüm öğeler çalışma zamanına ortak alt öğeler olarak sunulur.

- <xref:System.Collections.ICollection> türü <xref:System.Activities.ActivityDelegate> : koleksiyondaki tüm öğeler, çalışma zamanına Genel Temsilciler olarak sunulur.

<xref:System.Activities.Activity.CacheMetadata%2A> <xref:System.Activities.Activity> <xref:System.Workflow.Activities.CodeActivity> Aşağıdaki farklar dışında, ve ' den türetilen etkinlikler için <xref:System.Activities.AsyncCodeActivity> :

- Öğesinden türetilen sınıflar <xref:System.Activities.Activity> alt etkinlikleri veya temsilcileri zamanlayamaz, bu nedenle bu Üyeler, içeri aktarılan alt öğeler ve temsilciler olarak sunulur.

- Ve ' den türetilen <xref:System.Activities.CodeActivity> ve <xref:System.Activities.AsyncCodeActivity> değişkenleri, alt öğeleri veya temsilcileri desteklemeyen sınıflar, bu nedenle yalnızca bağımsız değişkenler sunulur.

## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a>Çalışma zamanına bilgi sağlamak için CacheMetadata geçersiz kılınıyor

Aşağıdaki kod parçacığı, yöntemin yürütülmesi sırasında bir etkinliğin meta verilerine Üyeler hakkında nasıl bilgi ekleneceğini gösterir <xref:System.Activities.Activity.CacheMetadata%2A> . Yöntemin temelini, etkinlikle ilgili tüm genel verileri önbelleğe almak için çağırılır.

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

## <a name="using-cachemetadata-to-expose-implementation-children"></a>Uygulama alt öğelerini göstermek için CacheMetadata kullanma

Değişkenleri kullanarak bir etkinlik tarafından zamanlanacak alt etkinliklere veri geçirmek için, değişkenleri uygulama değişkenleri olarak eklemek gerekir; ortak değişkenlerin değerleri bu şekilde ayarlanamaz. Bunun nedeni, etkinliklerin (özellikleri olan) kapsüllenmiş sınıflar yerine işlevlerin (parametrelere sahip) uygulamalar olarak daha fazla yürütülmesi amacını taşımaktadır. Ancak, <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> zamanlanan etkinliğin bir alt etkinliğin olduğu şekilde üst etkinliğin bağımsız değişkenlerine erişimi olmadığından bağımsız değişkenlerin açıkça ayarlanması gerektiği durumlar vardır.

Aşağıdaki kod parçacığı, kullanarak bir bağımsız değişkenin yerel etkinlikten zamanlanan bir etkinliğe nasıl geçirileceğini gösterir <xref:System.Activities.Activity.CacheMetadata%2A> .

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

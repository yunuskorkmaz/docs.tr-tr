---
title: CacheMetadata ile verileri kullanıma sunma
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: a044c896e56541ee954fc33853376eb8293c6ede
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945710"
---
# <a name="exposing-data-with-cachemetadata"></a>CacheMetadata ile verileri kullanıma sunma

Bir etkinlik çalıştırmadan önce iş akışı çalışma zamanı yürütme sürdürmek için gereken etkinlik hakkında tüm bilgiler alır. İş akışı çalışma zamanı yürütme sırasında bu bilgileri alır <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi. Varsayılan uygulama bu yöntemin tüm genel bağımsız değişkenler, değişkenler ve çocuk etkinliklerinin zamanında yürütülür etkinlik tarafından sunulan çalışma zamanı sağlar; Etkinlik daha fazla bilgi için çalışma zamanı bu (örneğin, özel üyeler veya etkinlikleri etkinlik tarafından zamanlanması) vermeniz gerekiyorsa, bunu sağlamak için bu yöntem geçersiz kılınabilir.

## <a name="default-cachemetadata-behavior"></a>Varsayılan CacheMetadata davranışı

Varsayılan uygulaması <xref:System.Activities.NativeActivity.CacheMetadata%2A> öğesinden türetilen etkinlikler için <xref:System.Activities.NativeActivity> aşağıdaki yöntemi türleri aşağıdaki yollarla işler:

- <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, veya <xref:System.Activities.InOutArgument%601> (Genel değişkenler): Bu bağımsız değişkenler, çalışma zamanı için bir ada sahip bağımsız değişken olarak sunulur ve açık özellik adı ve türü, uygun bağımsız değişken yönünü ve bazı doğrulama verileri eşit yazın.

- <xref:System.Activities.Variable> veya tüm alt yapanın: Bu üyeleri çalışma zamanının genel değişkenleri olarak kullanıma sunulur.

- <xref:System.Activities.Activity> veya tüm alt yapanın: Bu üyeleri çalışma zamanının Genel alt etkinlikler kullanıma sunulur. Varsayılan davranış çağrılarak açıkça uygulanabilir <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, geçen alt etkinlik.

- <xref:System.Activities.ActivityDelegate> veya tüm alt yapanın: Bu üyeleri çalışma zamanının genel temsilciler olarak sunulur.

- <xref:System.Collections.ICollection> tür <xref:System.Activities.Variable>: Koleksiyondaki tüm öğeler için çalışma zamanı, genel değişkenleri olarak kullanıma sunulur.

- <xref:System.Collections.ICollection> tür <xref:System.Activities.Activity>: Koleksiyondaki tüm öğeler için çalışma zamanı ortak bir alt öğe olarak sunulur.

- <xref:System.Collections.ICollection> tür <xref:System.Activities.ActivityDelegate>: Koleksiyondaki tüm öğeleri çalışma zamanına genel temsilciler olarak sunulur.

<xref:System.Activities.Activity.CacheMetadata%2A> Öğesinden türetilen etkinlikler için <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, ve <xref:System.Activities.AsyncCodeActivity> da işlev yukarıda gerçekleştirildiği gibi aşağıdaki farklar dışında:

- Öğesinden türetilen sınıfları <xref:System.Activities.Activity> çocuk etkinliklerinin veya Temsilciler, tür üyeleri, içeri aktarılan alt öğeleri ve temsilcileri; sunulur. Bu nedenle zamanlayamazsınız

- Öğesinden türetilen sınıfları <xref:System.Activities.CodeActivity> ve <xref:System.Activities.AsyncCodeActivity> yalnızca bağımsız değişkenler kullanıma sunulacak şekilde değişkenleri, alt ve temsilciler desteklemez.

## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a>CacheMetadata çalışma zamanı bilgileri sağlamak için geçersiz kılma

Aşağıdaki kod parçacığı üyeleri hakkında bilgi yürütülmesi sırasında bir etkinliğe ilişkin meta verileri eklemek gösterilmiştir <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi. Etkinlikle ilgili tüm genel verileri önbelleğe almak için temel yöntemin çağrıldığını unutmayın.

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

## <a name="using-cachemetadata-to-expose-implementation-children"></a>CacheMetadata uygulama alt öğeleri göstermek için kullanma

Değişkenleri kullanarak bir etkinlik tarafından zamanlanması gereken alt etkinliklere veri geçirmek için değişkenleri uygulama değişkenleri olarak eklemek gereklidir. Genel değişkenler bu şekilde değerlerine sahip olamaz. Bunun nedeni, etkinlikleri (hangi özelliklere sahip) kapsüllenmiş sınıfları yerine (Bu parametrelere sahip) işlevleri uygulamaları daha yürütülecek yöneliktir ' dir. Bununla birlikte, bağımsız değişkenleri açıkça ayarlanması gerekir, ne zaman gibi durumlar vardır kullanarak <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, zamanlanan etkinlikten bir alt etkinlik olduğu gibi üst etkinliğin bağımsız değişken erişimi yoktur.

Aşağıdaki kod parçacığını kullanarak bir zamanlanan etkinlik yerel etkinlik bağımsız değişkeni form geçirilecek gösterilmiştir <xref:System.Activities.Activity.CacheMetadata%2A>.

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

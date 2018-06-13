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
# <a name="exposing-data-with-cachemetadata"></a>CacheMetadata verilerle gösterme
Bir etkinliği yürütmeden önce iş akışı çalışma zamanı tüm yürütülmesinin korumak için gereken etkinliği hakkında bilgi edinir. İş akışı çalışma zamanı yürütme işlemi sırasında bu bilgileri alır <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi. Bu yöntem varsayılan uygulamasını tüm ortak bağımsız değişkenleri, değişkenler ve yürütülür aynı anda etkinlik tarafından sunulan alt etkinlikleri ile çalışma zamanı sağlar; Etkinlik daha fazla bilgi için çalışma zamanı bu (örneğin, özel üyelerin veya etkinlikleri etkinlik tarafından zamanlanacak) vermek gerekirse, bunu sağlamak için bu yöntem geçersiz kılınabilir.  
  
## <a name="default-cachemetadata-behavior"></a>Varsayılan CacheMetadata davranışı  
 Varsayılan uygulaması <xref:System.Activities.NativeActivity.CacheMetadata%2A> öğesinden türetilen etkinlikler için <xref:System.Activities.NativeActivity> aşağıdaki yöntemi türleri aşağıdaki yollarla işler:  
  
-   <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, veya <xref:System.Activities.InOutArgument%601> (Genel değişkenler): Bu bağımsız değişkenler çalışma bir adı olan bağımsız değişkenler olarak sunulur ve sunulan özellik adı ve türü, uygun değişken yön ve bazı doğrulama veriler eşit yazın.  
  
-   <xref:System.Activities.Variable> veya bunların herhangi bir alt: Bu üyeleri çalışma zamanına genel değişkenleri olarak sunulur.  
  
-   <xref:System.Activities.Activity> veya bunların herhangi bir alt: Bu üyeleri çalışma zamanına Genel alt etkinlikler sunulur. Varsayılan davranış çağırarak uygulanan açıkça olabilir <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, alt etkinliğinde geçen.  
  
-   <xref:System.Activities.ActivityDelegate> veya bunların herhangi bir alt: Bu üyeleri çalışma zamanına Genel temsilci olarak sunulur.  
  
-   <xref:System.Collections.ICollection> tür <xref:System.Activities.Variable>: koleksiyondaki tüm öğeleri çalışma zamanına genel değişkenleri olarak sunulur.  
  
-   <xref:System.Collections.ICollection> tür <xref:System.Activities.Activity>: koleksiyondaki tüm öğeleri çalışma zamanına Genel alt öğesi olarak sunulur.  
  
-   <xref:System.Collections.ICollection> tür <xref:System.Activities.ActivityDelegate>: koleksiyondaki tüm öğeleri çalışma zamanına Genel temsilci olarak sunulur.  
  
 <xref:System.Activities.Activity.CacheMetadata%2A> Öğesinden türetilen etkinlikler için <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, ve <xref:System.Activities.AsyncCodeActivity> da işlev olarak yukarıdaki aşağıdaki farklar dışında:  
  
-   Öğesinden türetilen sınıflar <xref:System.Activities.Activity> alt etkinlikler veya Temsilciler, bu tür üyeler alınan alt ve temsilciler; gösterilen şekilde zamanlayamazsınız  
  
-   Öğesinden türetilen sınıflar <xref:System.Activities.CodeActivity> ve <xref:System.Activities.AsyncCodeActivity> yalnızca bağımsız değişken gösterilen şekilde değişkenleri, alt öğelerini veya temsilciler desteklemez.  
  
## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a>Çalışma zamanı bilgileri sağlamak için CacheMetadata geçersiz kılma  
 Aşağıdaki kod parçacığını üyeleri hakkında bilgi için bir etkinliğe ilişkin meta verileri yürütülmesi sırasında ekleneceği gösterilmektedir <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi. Yöntem tabanı etkinlikle ilgili tüm genel verileri önbelleğe almak için çağrılır unutmayın.  
  
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
  
## <a name="using-cachemetadata-to-expose-implementation-children"></a>Uygulama alt kullanıma sunmak için CacheMetadata kullanma  
 Değişkenler kullanarak bir etkinlik tarafından zamanlanacak alt etkinlikleri için veri iletmek için uygulama değişkenleri olarak değişkenleri eklemek gereklidir; Genel değişkenler bu şekilde ayarlamak değerlerine sahip olamaz. Bunun nedeni, etkinlikler (özelliklerine sahip) kapsüllenmiş sınıflarını yerine (parametrelere sahip) işlevlerini uygulamaları daha yürütülmek üzere tasarlanmıştır ' dir. Bununla birlikte, bağımsız değişkenler açıkça ayarlanmalıdır, zaman gibi durumlar vardır kullanarak <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, zamanlanan etkinlikten bir alt etkinlik olduğu gibi üst etkinliğin bağımsız değişken erişimi olmadığından.  
  
 Aşağıdaki kod parçacığını bir zamanlanan etkinlik kullanarak yerel bir etkinlik bir bağımsız değişken form geçmesine gösterilmiştir <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
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

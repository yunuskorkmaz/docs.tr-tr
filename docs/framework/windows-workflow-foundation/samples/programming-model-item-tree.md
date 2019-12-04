---
title: Programlama Modeli Öğe Ağacı
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: efda69ac568b0ad9c5fdcf4d42722c5b7dadd3f3
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715674"
---
# <a name="programming-model-item-tree"></a>Programlama Modeli Öğe Ağacı
Bu örnek, Windows Presentation Foundation (WPF) ağaç görünümünden bildirim temelli veri bağlamayı kullanarak <xref:System.Activities.Presentation.Model.ModelItem> ağacının nasıl gezindiğini gösterir.

## <a name="sample-details"></a>Örnek Ayrıntılar
 <xref:System.Activities.Presentation.Model.ModelItem> ağacı, Windows İş Akışı Tasarımcısı altyapısı tarafından düzenlenmekte olan temeldeki örnekle ilgili verileri açığa çıkarmak için kullanılan soyutlamadır. Aşağıdaki çizim İş Akışı Tasarımcısı içindeki çeşitli altyapı katmanlarının bir gösterimi.

 ![İş Akışı Tasarımcısı mimarisini gösteren diyagram.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <xref:System.Activities.Presentation.Model.ModelItem>, temel alınan değerin bir işaretçisinin yanı sıra <xref:System.Activities.Presentation.Model.ModelProperty> nesneleri koleksiyonu içerir. Sırasıyla bir <xref:System.Activities.Presentation.Model.ModelProperty> nesnesi, özelliğin adı ve türü gibi verilerden oluşur ve sonra, daha sonra başka bir <xref:System.Activities.Presentation.Model.ModelItem>bir değer işaretçisi olur. Bir değer Dönüştürücüsü, ağaç görünümünde doğru görünmesini sağlamak için bir <xref:System.Activities.Presentation.Model.ModelProperty> döndürülen <xref:System.Activities.Presentation.Model.ModelItem>bazılarını işlemek üzere kullanılır. Örnek daha sonra aşağıdaki örnekte görüldüğü gibi, zorunlu sözdizimini kullanarak programın <xref:System.Activities.Presentation.Model.ModelItem> ağacına nasıl imperatively gösterir.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 ' de Studio. sln çözümünü açın.

2. **Build** menüsünden **Build Solution** ' i seçerek çözümü oluşturun.

3. Uygulamayı çalıştırmak için F5 tuşuna basın. WPF formu daha sonra görüntülenir.

4. <xref:System.Activities.Presentation.Model.ModelItem> yüklemek ve ağaç görünümüne bağlamak için **WF yükle** düğmesine tıklayın.

5. **Model öğe ağacını Değiştir** düğmesine tıklamak, bir öğeyi ağaca eklemek ve bir özelliği ayarlamak için yukarıdaki kodu yürütür.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.IValueConverter>

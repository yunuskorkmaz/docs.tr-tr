---
title: Programlama Modeli Öğe Ağacı
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 059bb3edcfe41f52e2244ff6f5bf3fc78a4262bb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235811"
---
# <a name="programming-model-item-tree"></a>Programlama Modeli Öğe Ağacı

Bu örnek, <xref:System.Activities.Presentation.Model.ModelItem> Windows Presentation Foundation (WPF) ağaç görünümünden bildirim temelli veri bağlamayı kullanarak ağaçta nasıl gezineceğinizi gösterir.

## <a name="sample-details"></a>Örnek Ayrıntılar

 <xref:System.Activities.Presentation.Model.ModelItem>Ağaç, düzenlenen temeldeki örnekle ilgili verileri göstermek Için Windows iş akışı Tasarımcısı altyapısı tarafından kullanılan soyutlamadır. Aşağıdaki çizim İş Akışı Tasarımcısı içindeki çeşitli altyapı katmanlarının bir gösterimi.

 ![İş Akışı Tasarımcısı mimarisini gösteren diyagram.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <xref:System.Activities.Presentation.Model.ModelItem>, Temel alınan değerin bir işaretçisinin yanı sıra bir nesne koleksiyonu içerir <xref:System.Activities.Presentation.Model.ModelProperty> . <xref:System.Activities.Presentation.Model.ModelProperty>Sırasıyla bir nesne, özelliğin adı ve türü gibi verilerden oluşur ve sonra değer için bir işaretçi, diğeri de olur <xref:System.Activities.Presentation.Model.ModelItem> . Bir değer Dönüştürücüsü, <xref:System.Activities.Presentation.Model.ModelItem> <xref:System.Activities.Presentation.Model.ModelProperty> ağaç görünümünde doğru görünmesini sağlamak için bir öğesinden döndürülen bazı öğeleri işlemek için kullanılır. Örnek daha sonra, <xref:System.Activities.Presentation.Model.ModelItem> Aşağıdaki örnekte görüldüğü gibi, zorunlu sözdizimini kullanarak nasıl imperatively program ağacına karşılık gelen gösterilmektedir.

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

3. Uygulamayı çalıştırmak için F5'e basın. WPF formu daha sonra görüntülenir.

4. Yüklemek ve ağaç görünümüne bağlamak için **WF yükle** düğmesine tıklayın <xref:System.Activities.Presentation.Model.ModelItem> .

5. **Model öğe ağacını Değiştir** düğmesine tıklamak, bir öğeyi ağaca eklemek ve bir özelliği ayarlamak için yukarıdaki kodu yürütür.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.IValueConverter>

---
title: Programlama Modeli Öğe Ağacı
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f2d89cb2a3b0f6167f043148ea793ec1c264a556
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038179"
---
# <a name="programming-model-item-tree"></a>Programlama Modeli Öğe Ağacı
Bu örnek, <xref:System.Activities.Presentation.Model.ModelItem> Windows Presentation Foundation (WPF) ağaç görünümünden bildirim temelli veri bağlamayı kullanarak ağaçta nasıl gezineceğinizi gösterir.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Ağaç, düzenlenmekte olan temeldeki örnekle ilgili verileri göstermek için [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] altyapı tarafından kullanılan soyutlamadır. <xref:System.Activities.Presentation.Model.ModelItem> Aşağıdaki çizim, [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]içindeki çeşitli altyapı katmanlarının bir gösterimi.

 ![İş Akışı Tasarımcısı mimarisini gösteren diyagram.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 , Temel alınan değerin bir işaretçisinin yanı sıra bir <xref:System.Activities.Presentation.Model.ModelProperty> nesne koleksiyonu içerir.<xref:System.Activities.Presentation.Model.ModelItem> Sırasıyla <xref:System.Activities.Presentation.Model.ModelProperty> bir nesne, özelliğin adı ve türü gibi verilerden oluşur ve sonra değer için bir işaretçi, diğeri <xref:System.Activities.Presentation.Model.ModelItem>de olur. Bir değer Dönüştürücüsü, ağaç görünümünde doğru görünmesini sağlamak için <xref:System.Activities.Presentation.Model.ModelItem>bir <xref:System.Activities.Presentation.Model.ModelProperty> öğesinden döndürülen bazı öğeleri işlemek için kullanılır. Örnek daha sonra, aşağıdaki örnekte görüldüğü gibi, zorunlu <xref:System.Activities.Presentation.Model.ModelItem> sözdizimini kullanarak nasıl imperatively program ağacına karşılık gelen gösterilmektedir.

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

4. Yüklemek<xref:System.Activities.Presentation.Model.ModelItem> ve ağaç görünümüne bağlamak için **WF yükle** düğmesine tıklayın.

5. **Model öğe ağacını Değiştir** düğmesine tıklamak, bir öğeyi ağaca eklemek ve bir özelliği ayarlamak için yukarıdaki kodu yürütür.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.IValueConverter>

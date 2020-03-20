---
title: Programlama Modeli Öğe Ağacı
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f14b140fdac95f3763cc5625841a725793876fa4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142699"
---
# <a name="programming-model-item-tree"></a>Programlama Modeli Öğe Ağacı
Bu örnek, Windows Sunu <xref:System.Activities.Presentation.Model.ModelItem> Temeli (WPF) Ağaç Görünümü'nden bildirimsel veri bağlamakullanarak ağaçta nasıl gezinilince gösterilmektedir.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Ağaç, <xref:System.Activities.Presentation.Model.ModelItem> Windows İş Akışı Tasarımcısı altyapısı tarafından, düzenlenen temel örnekle ilgili verileri ortaya çıkarmak için kullanılan soyutlamadır. Aşağıdaki resimde, İş Akışı Tasarımcısı içindeki çeşitli altyapı katmanlarının bir tasviri ve

 ![İş Akışı Tasarımcısı mimarisini gösteren diyagram.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 A, <xref:System.Activities.Presentation.Model.ModelItem> temel değere işaretçi nin yanı sıra <xref:System.Activities.Presentation.Model.ModelProperty> nesneler koleksiyonundan oluşur. Sırayla bir <xref:System.Activities.Presentation.Model.ModelProperty> nesne, adı ve özelliğinin türü gibi verilerden oluşur ve sonra değer için <xref:System.Activities.Presentation.Model.ModelItem>bir işaretçi, sırayla, başka bir . Değer dönüştürücü, a'dan <xref:System.Activities.Presentation.Model.ModelItem> <xref:System.Activities.Presentation.Model.ModelProperty> döndürülen bazı s'leri işlemek için kullanılır ve ağaç görünümünde doğru görünmelerini sağlamak için kullanılır. Örnek daha sonra aşağıdaki örnekte görüldüğü <xref:System.Activities.Presentation.Model.ModelItem> gibi, zorunlu sözdizimini kullanarak ağaca karşı zorunlu olarak nasıl programlanırgösteriz.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010'da ProgrammingModelItemTree.sln çözümlerini açın.

2. **Yapı** menüsünden **Çözüm Oluştur'u** seçerek çözümü oluşturun.

3. Uygulamayı çalıştırmak için F5'e basın. WPF formu daha sonra görüntülenir.

4. Yüklemek <xref:System.Activities.Presentation.Model.ModelItem> ve ağaç görünümüne bağlamak için **WF** Yükle düğmesini tıklatın.

5. **Model Öğesi Ağacını Değiştir** düğmesini tıklattığınızda, ağaca bir öğe eklemek ve bir özellik ayarlamak için önceki kodu çalıştırın.

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.IValueConverter>

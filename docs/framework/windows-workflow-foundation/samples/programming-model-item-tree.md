---
title: Programlama modeli öğe ağacı
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: a24e52ec2b7cab10471d756a721611c6dd10516e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521976"
---
# <a name="programming-model-item-tree"></a>Programlama modeli öğe ağacı
Bu örnek nasıl gidileceğini gösteren <xref:System.Activities.Presentation.Model.ModelItem> Windows Presentation Foundation (WPF) ağaç görünümünden bildirim temelli veriler bağlama kullanarak ağaç.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 <xref:System.Activities.Presentation.Model.ModelItem> Ağacıdır tarafından kullanılan soyutlama [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] düzenlenmekte olan temel örneği hakkındaki verileri göstermek için altyapı. Aşağıdaki çizimde bir altyapı dahilinde çeşitli katmanları bir gösterimi olan [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].  
  
 ![İş Akışı Tasarımcısı mimarisi](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")  
  
 A <xref:System.Activities.Presentation.Model.ModelItem> koleksiyonunu yanı sıra, temeldeki değeri için bir işaretçi oluşur <xref:System.Activities.Presentation.Model.ModelProperty> nesneleri. A <xref:System.Activities.Presentation.Model.ModelProperty> nesnesi sırayla oluşur adı ve türü özelliği ve buna karşılık, başka değeri için bir işaretçi gibi veri <xref:System.Activities.Presentation.Model.ModelItem>. Bazılarını işlemek için kullanılan bir değer dönüştürücü <xref:System.Activities.Presentation.Model.ModelItem>s öğesinden döndürülen bir <xref:System.Activities.Presentation.Model.ModelProperty> hale getirmek için bunları doğru ağaç görünümünde görünür. Örnek daha sonra kesin karşı programlamak nasıl gösterir <xref:System.Activities.Presentation.Model.ModelItem> aşağıdaki örnekte görüldüğü gibi kesinlik temelli sözdizimi kullanılarak ağaç.  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  ProgrammingModelItemTree.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözüm seçerek yapı **Çözümü Derle** gelen **derleme** menüsü.  
  
3.  Uygulamayı çalıştırmak için F5 tuşuna basın. [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Formu görüntülenir.  
  
4.  Tıklayın **yük WF** yüklemek için düğmeye <xref:System.Activities.Presentation.Model.ModelItem> ve ağaç görünümüne bağlayın.  
  
5.  Tıklayarak **değişiklik modeli öğe ağacı** düğmesi ağacına bir öğe ekleyin ve bir özelliği ayarlamak için yukarıdaki kodu yürütür.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.IValueConverter>

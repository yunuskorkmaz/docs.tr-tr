---
title: "Programlama modeli öğesi ağacı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83e804a3ede525510b5c46b494882656c74591b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="programming-model-item-tree"></a>Programlama modeli öğesi ağacı
Bu örnek gitmek gösterilmiştir <xref:System.Activities.Presentation.Model.ModelItem> bildirim temelli veri bağlamasını kullanma ağaç [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] ağaç görünümü.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 <xref:System.Activities.Presentation.Model.ModelItem> Ağacıdır tarafından kullanılan soyutlama [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] düzenlenmekte olan temeldeki örnek hakkındaki verileri kullanıma sunmak için altyapı. Aşağıdaki çizimde altyapısı içinde çeşitli katmanlarına bir gösterimi olan [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].  
  
 ![İş Akışı Tasarımcısı mimarisi](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")  
  
 A <xref:System.Activities.Presentation.Model.ModelItem> koleksiyonu yanı sıra temel alınan değer için bir işaretçi oluşan <xref:System.Activities.Presentation.Model.ModelProperty> nesneleri. A <xref:System.Activities.Presentation.Model.ModelProperty> nesnesi sırayla oluşur adı ve türü özelliği ve buna karşılık, başka değeri için bir işaretçi gibi veri <xref:System.Activities.Presentation.Model.ModelItem>. Değer Dönüştürücüsü Bazı işlemek için kullanılan <xref:System.Activities.Presentation.Model.ModelItem>döndürülen s bir <xref:System.Activities.Presentation.Model.ModelProperty> bunları doğru ağaç görünümünde görünür hale getirmek için. Örnek sonra imperatively karşı programlamayı gösteren <xref:System.Activities.Presentation.Model.ModelItem> kesinlik temelli söz dizimini kullanarak aşağıdaki örnekte görüldüğü gibi ağacı.  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  ProgrammingModelItemTree.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Seçerek çözümü derleme **yapı çözümü** gelen **yapı** menüsü.  
  
3.  Uygulamayı çalıştırmak için F5 tuşuna basın. [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Form sonra görüntülenir.  
  
4.  Tıklatın **yük WF** yüklemek için düğmeyi <xref:System.Activities.Presentation.Model.ModelItem> ve ağaç görünümüne bağlayın.  
  
5.  Tıklatarak **değişiklik Model öğesi ağacı** düğmesi ağacına bir öğe ekleyin ve bir özelliği ayarlamak için yukarıdaki kodu yürütür.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.IValueConverter>

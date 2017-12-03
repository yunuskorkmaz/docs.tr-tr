---
title: "Kapsamı düzenlenirken kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd0752502bdbd7da9d749ae4f71ea869a4c1ec95
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-editing-scope"></a>Kapsamı düzenlenirken kullanma
Bu örnek, böylece tek bir atomik biriminde geri değişiklik kümesi toplu olarak gösterilmiştir. Varsayılan olarak, bir etkinlik Tasarımcısı yazar tarafından gerçekleştirilen eylemleri otomatik olarak geri alma/yineleme sistemiyle tümleşiktir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Kapsam ve geri alma ve yineleme düzenleme.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek için değişiklik kümesi toplu olarak gösterilmiştir <xref:System.Activities.Presentation.Model.ModelItem> ağacı tek bir iş birimine içinde. İçin bağlama sırasında unutmayın <xref:System.Activities.Presentation.Model.ModelItem> değerleri doğrudan bir WPF Tasarımcısı'ndan, değişiklikler otomatik olarak uygulanır. Bu örnek, toplu için birden fazla değişiklik tek bir değişiklik yerine kesinlik temelli kodu yapıldığını olduğunda ne yapılmalıdır gösterir.  
  
 Bu örnekte, üç etkinlikleri eklenir. Düzenleme işlemi başladığında, <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> örneğinde adlı <xref:System.Activities.Presentation.Model.ModelItem>. Yapılan değişiklikler <xref:System.Activities.Presentation.Model.ModelItem> ağaç düzenleme bu kapsam içinde toplu. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> Komutu döndürür bir <xref:System.Activities.Presentation.Model.EditingScope>, bu örnek denetlemek için kullanılabilir. Ya da <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> veya <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> ya da uygulanmak üzere çağrılabilir veya düzenleme kapsamı geri döndür.  
  
 Ayrıca geçirebilmenize <xref:System.Activities.Presentation.Model.EditingScope> büyük düzenleme bir parçası olarak izlenmesi için birden fazla değişiklik kümeleri için verir nesneleri kapsam ve tek tek kontrol. Bu özelliği kullanan bir senaryo, birden çok iletişim kutuları değişikliklerden kaydedilmiş veya ayrı olarak, tek bir atomik işlemle kabul ediliyor tüm değişikliklerle geri olacaktır. Bu örnekte, düzenleme kapsamları kullanarak yığılmış bir <xref:System.Collections.ObjectModel.ObservableCollection%601> türü <xref:System.Activities.Presentation.Model.ModelEditingScope>. <xref:System.Collections.ObjectModel.ObservableCollection%601> İç içe geçirme derinliği Tasarımcı yüzeyine uyulması böylece kullanılır.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Yapı örneğini çalıştırın ve ardından iş akışını değiştirmek için soldaki düğmelerini kullanın.  
  
2.  Tıklatın **açık kapsamı düzenleme**.  
  
    1.  Bu komutu çağıran <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> düzenleme bir kapsam oluşturur ve düzenleme yığına iter.  
  
    2.  Üç etkinlikleri sonra eklenmiş olan seçili <xref:System.Activities.Presentation.Model.ModelItem>. Düzenleme kapsamı ile açılmış değil gerçekleştiriyorsanız <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, üç yeni etkinlikler Tasarımcı tuvalde görünür. Çünkü bu işlemi hala beklemede içinde <xref:System.Activities.Presentation.Model.EditingScope>, Tasarımcı henüz güncelleştirilmemiş.  
  
3.  Tuşuna **Kapat düzenleme kapsamı** düzenleme kapsamı kaydedilemedi. Üç Etkinlik Tasarımcısı'nda görünür.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`

---
title: Düzenleme Kapsamını Kullanma
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 3e99610fda78e50f6d6eb72c38ecc82bdc96b5a2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715547"
---
# <a name="using-editing-scope"></a>Düzenleme Kapsamını Kullanma
Bu örnek, tek bir atomik birimde geri alınabilmeleri için bir değişiklik kümesinin toplu olarak nasıl yapılacağını gösterir. Varsayılan olarak, bir etkinlik Tasarımcısı yazarı tarafından gerçekleştirilen eylemler, geri al/yinele sistemiyle otomatik olarak tümleştirilir.  
  
## <a name="demonstrates"></a>Gösterir  
 Kapsam düzenleniyor ve geri al ve Yinele.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, tek bir iş birimi içinde <xref:System.Activities.Presentation.Model.ModelItem> ağacına bir değişiklik kümesinin nasıl toplu olarak yapılacağını gösterir. <xref:System.Activities.Presentation.Model.ModelItem> değerlerine doğrudan bir WPF tasarımcısından bağlarken, değişikliklerin otomatik olarak uygulandığını unutmayın. Bu örnek, tek bir değişiklik yerine, toplu olarak birden çok değişiklik yapılması zorunlu kodla yapıldığında ne yapılması gerektiğini gösterir.  
  
 Bu örnekte, üç etkinlik eklenmiştir. Düzenlenmek başladığında <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> bir <xref:System.Activities.Presentation.Model.ModelItem>örneğinde çağrılır. Bu düzen kapsamındaki <xref:System.Activities.Presentation.Model.ModelItem> ağaçta yapılan değişiklikler toplu olarak sunulur. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> komutu, bu örneği denetlemek için kullanılabilecek bir <xref:System.Activities.Presentation.Model.EditingScope>döndürür. <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> veya <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A>, düzenlemenin kapsamını yürütmek ya da almak için çağrılabilir.  
  
 Ayrıca, birden fazla değişiklik kümesinin daha büyük bir düzen kapsamının parçası olarak izlenmesini sağlayan ve tek tek denetlenebileceği <xref:System.Activities.Presentation.Model.EditingScope> nesneleri iç içe geçirebilirsiniz. Bu özelliği kullanan bir senaryo, birden fazla iletişim kutusunun değişikliklerinin tek bir atomik işlem olarak kabul edildiği şekilde ayrı ayrı yürütülmesi veya geri döndürülmesi gerektiği durumdur. Bu örnekte, düzen kapsamları <xref:System.Activities.Presentation.Model.ModelEditingScope>türünde bir <xref:System.Collections.ObjectModel.ObservableCollection%601> kullanılarak yığıldılar. <xref:System.Collections.ObjectModel.ObservableCollection%601>, iç içe geçme derinliğinin tasarımcı yüzeyinde gözlemlenebilir olması için kullanılır.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Örneği derleyin ve çalıştırın ve ardından, sol taraftaki düğmeleri kullanarak iş akışını değiştirin.  
  
2. **Düzen kapsamını aç**' a tıklayın.  
  
    1. Bu komut, bir düzen kapsamı oluşturan <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> çağırır ve bunu düzenlenen yığın üzerine gönderir.  
  
    2. Üç etkinlik seçili <xref:System.Activities.Presentation.Model.ModelItem>eklenir. Düzen kapsamı <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>ile açılmadıysa, tasarımcı tuvalinde üç yeni etkinliğin görüneceğini unutmayın. Bu işlem hala <xref:System.Activities.Presentation.Model.EditingScope>içinde beklediğinden, tasarımcı henüz güncelleştirilmedi.  
  
3. Düzen kapsamını yürütmek için, **Düzen kapsamını kapat** ' a basın. Tasarımcıda üç etkinlik görüntülenir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`

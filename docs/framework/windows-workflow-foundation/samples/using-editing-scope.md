---
title: Düzenleme Kapsamını Kullanma
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 386c94e5c6761bb704efc9e48723d0e91a4aaf6b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037793"
---
# <a name="using-editing-scope"></a>Düzenleme Kapsamını Kullanma
Bu örnek, tek bir atomik birimde geri alınabilmeleri için bir değişiklik kümesinin toplu olarak nasıl yapılacağını gösterir. Varsayılan olarak, bir etkinlik Tasarımcısı yazarı tarafından gerçekleştirilen eylemler, geri al/yinele sistemiyle otomatik olarak tümleştirilir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Kapsam düzenleniyor ve geri al ve Yinele.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, <xref:System.Activities.Presentation.Model.ModelItem> tek bir iş birimi içindeki ağaçta bir değişiklik kümesinin toplu olarak nasıl yapılacağını gösterir. Doğrudan bir WPF tasarımcısından <xref:System.Activities.Presentation.Model.ModelItem> değerlere bağlandığınızda, değişikliklerin otomatik olarak uygulandığını unutmayın. Bu örnek, tek bir değişiklik yerine, toplu olarak birden çok değişiklik yapılması zorunlu kodla yapıldığında ne yapılması gerektiğini gösterir.  
  
 Bu örnekte, üç etkinlik eklenmiştir. ' <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> In<xref:System.Activities.Presentation.Model.ModelItem>başladığı zaman bir örneğinde çağrılır. Bu düzen kapsamındaki <xref:System.Activities.Presentation.Model.ModelItem> ağaçta yapılan değişiklikler toplu hale getirilir. Komutu, bu örneği <xref:System.Activities.Presentation.Model.EditingScope>denetlemek için kullanılabilecek bir döndürür. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> Ya<xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> da, düzenlemenin kapsamını yürütmek ya da almak için çağrılabilir.  
  
 Ayrıca, birden fazla <xref:System.Activities.Presentation.Model.EditingScope> değişiklik kümesinin daha büyük bir düzen kapsamının parçası olarak izlenmesini sağlayan ve tek tek denetlenebileceği nesneleri iç içe geçirebilirsiniz. Bu özelliği kullanan bir senaryo, birden fazla iletişim kutusunun değişikliklerinin tek bir atomik işlem olarak kabul edildiği şekilde ayrı ayrı yürütülmesi veya geri döndürülmesi gerektiği durumdur. Bu örnekte, düzen kapsamları türü <xref:System.Collections.ObjectModel.ObservableCollection%601> <xref:System.Activities.Presentation.Model.ModelEditingScope>kullanılarak yığınlanilir. , <xref:System.Collections.ObjectModel.ObservableCollection%601> İç içe geçme derinliğinin tasarımcı yüzeyinde gözlemlenebilir olması için kullanılır.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Örneği derleyin ve çalıştırın ve ardından, sol taraftaki düğmeleri kullanarak iş akışını değiştirin.  
  
2. **Düzen kapsamını aç**' a tıklayın.  
  
    1. Bu komut, <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> bir düzen kapsamı oluşturduğunu ve bunu düzenleyen yığınına ilettiğinde çağırır.  
  
    2. Ardından seçili <xref:System.Activities.Presentation.Model.ModelItem>üç etkinlik eklenir. Düzen kapsamı ile <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>açılmadıysa, tasarımcı tuvalinde üç yeni etkinliğin görüneceğini unutmayın. Bu işlem içinde <xref:System.Activities.Presentation.Model.EditingScope>hala beklemede olduğundan, tasarımcı henüz güncelleştirilmedi.  
  
3. Düzen kapsamını yürütmek için, **Düzen kapsamını kapat** ' a basın. Tasarımcıda üç etkinlik görüntülenir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`

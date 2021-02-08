---
description: 'Hakkında daha fazla bilgi edinin: düzen kapsamını kullanma'
title: Düzenleme Kapsamını Kullanma
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 9d91c787bb1b44d5cd07245fe48bd31ed2ccab3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787779"
---
# <a name="using-editing-scope"></a>Düzenleme Kapsamını Kullanma

Bu örnek, tek bir atomik birimde geri alınabilmeleri için bir değişiklik kümesinin toplu olarak nasıl yapılacağını gösterir. Varsayılan olarak, bir etkinlik Tasarımcısı yazarı tarafından gerçekleştirilen eylemler, geri al/yinele sistemiyle otomatik olarak tümleştirilir.  
  
## <a name="demonstrates"></a>Gösteriler  

 Kapsam düzenleniyor ve geri al ve Yinele.  
  
## <a name="discussion"></a>Tartışma  

 Bu örnek, <xref:System.Activities.Presentation.Model.ModelItem> tek bir iş birimi içindeki ağaçta bir değişiklik kümesinin toplu olarak nasıl yapılacağını gösterir. <xref:System.Activities.Presentation.Model.ModelItem>Doğrudan BIR WPF tasarımcısından değerlere bağlandığınızda, değişikliklerin otomatik olarak uygulandığını unutmayın. Bu örnek, tek bir değişiklik yerine, toplu olarak birden çok değişiklik yapılması zorunlu kodla yapıldığında ne yapılması gerektiğini gösterir.  
  
 Bu örnekte, üç etkinlik eklenmiştir. ' In başladığı zaman <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> bir örneğinde çağrılır <xref:System.Activities.Presentation.Model.ModelItem> . <xref:System.Activities.Presentation.Model.ModelItem>Bu düzen kapsamındaki ağaçta yapılan değişiklikler toplu hale getirilir. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>Komutu <xref:System.Activities.Presentation.Model.EditingScope> , bu örneği denetlemek için kullanılabilecek bir döndürür. <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A>Ya da <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> , düzenlemenin kapsamını yürütmek ya da almak için çağrılabilir.  
  
 Ayrıca <xref:System.Activities.Presentation.Model.EditingScope> , birden fazla değişiklik kümesinin daha büyük bir düzen kapsamının parçası olarak izlenmesini sağlayan ve tek tek denetlenebileceği nesneleri iç içe geçirebilirsiniz. Bu özelliği kullanan bir senaryo, birden fazla iletişim kutusunun değişikliklerinin tek bir atomik işlem olarak kabul edildiği şekilde ayrı ayrı yürütülmesi veya geri döndürülmesi gerektiği durumdur. Bu örnekte, düzen kapsamları türü kullanılarak yığınlanilir <xref:System.Collections.ObjectModel.ObservableCollection%601> <xref:System.Activities.Presentation.Model.ModelEditingScope> . , <xref:System.Collections.ObjectModel.ObservableCollection%601> İç içe geçme derinliğinin tasarımcı yüzeyinde gözlemlenebilir olması için kullanılır.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Örneği derleyin ve çalıştırın ve ardından, sol taraftaki düğmeleri kullanarak iş akışını değiştirin.  
  
2. **Düzen kapsamını aç**' a tıklayın.  
  
    1. Bu komut <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> , bir düzen kapsamı oluşturduğunu ve bunu düzenleyen yığınına ilettiğinde çağırır.  
  
    2. Ardından seçili üç etkinlik eklenir <xref:System.Activities.Presentation.Model.ModelItem> . Düzen kapsamı ile açılmadıysa <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> , tasarımcı tuvalinde üç yeni etkinliğin görüneceğini unutmayın. Bu işlem içinde hala beklemede olduğundan <xref:System.Activities.Presentation.Model.EditingScope> , tasarımcı henüz güncelleştirilmedi.  
  
3. Düzen kapsamını yürütmek için, **Düzen kapsamını kapat** ' a basın. Tasarımcıda üç etkinlik görüntülenir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`

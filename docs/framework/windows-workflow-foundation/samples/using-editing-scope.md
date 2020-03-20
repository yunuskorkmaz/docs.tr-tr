---
title: Düzenleme Kapsamını Kullanma
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 13f23289f0b764b80f971d3e514f3b12acfbfffc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142660"
---
# <a name="using-editing-scope"></a>Düzenleme Kapsamını Kullanma
Bu örnek, tek bir atomik birimde geri alınabilmeleri için bir dizi değişikliğin nasıl toplu olarak yapılacağını gösterir. Varsayılan olarak, bir etkinlik tasarımcısı yazarı tarafından gerçekleştirilen eylemler otomatik olarak Geri Al/Yeniden Yap sistemine entegre edilir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Düzenleme kapsamı ve Geri ve Redo.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, tek bir çalışma birimi <xref:System.Activities.Presentation.Model.ModelItem> içinde ağaçta bir dizi değişikliğin nasıl toplu olarak yapılacağını gösterir. Değerlere <xref:System.Activities.Presentation.Model.ModelItem> doğrudan bir WPF tasarımcısından bağlanırken, değişikliklerin otomatik olarak uygulandığını unutmayın. Bu örnek, toplu olarak yapılacak birden çok değişiklik tek bir değişiklik yerine zorunlu kod aracılığıyla yapıldığında ne yapılması gerektiğini gösterir.  
  
 Bu örnekte üç etkinlik eklenir. Düzenleme başladığında, <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> bir örnek <xref:System.Activities.Presentation.Model.ModelItem>çağrılır. Bu düzenleme <xref:System.Activities.Presentation.Model.ModelItem> kapsamında ağaçta yapılan değişiklikler toplu olarak toplu olarak yapılır. Komut, <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> bu <xref:System.Activities.Presentation.Model.EditingScope>örneği denetlemek için kullanılabilecek bir , döndürür. Düzenleme <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> kapsamını işlemek veya geri almak için çağrılabilir veya çağrılabilir.  
  
 Ayrıca, birden <xref:System.Activities.Presentation.Model.EditingScope> çok değişiklik kümesinin daha büyük bir düzenleme kapsamının parçası olarak izlenmesine ve tek tek denetlenebilen nesneleri de yuvaya çekebilirsiniz. Bu özelliği kullanabilecek bir senaryo, birden çok iletişim kutusundan gelen değişikliklerin ayrı olarak kaydedilmesi veya geri alınması ve tüm değişikliklerin tek bir atomik işlem olarak ele alınması dır. Bu örnekte, düzenleme kapsamları bir <xref:System.Collections.ObjectModel.ObservableCollection%601> tür <xref:System.Activities.Presentation.Model.ModelEditingScope>kullanılarak istiflenir. İç <xref:System.Collections.ObjectModel.ObservableCollection%601> içe geçme derinliği tasarımcı yüzeyinde gözlemlenebilir şekilde kullanılır.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Örneği oluşturun ve çalıştırın ve ardından iş akışını değiştirmek için soldaki düğmeleri kullanın.  
  
2. **Düzenleme Kapsamını Aç'ı**tıklatın.  
  
    1. Bu komut, düzenleme kapsamı oluşturan ve düzenleme yığınına iten çağrıları. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>  
  
    2. Daha sonra seçili <xref:System.Activities.Presentation.Model.ModelItem>olana üç etkinlik eklenir. Düzenleme kapsamı tasarımcı tuvalinde üç <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>yeni etkinlikle açılmamış olsaydı, üç yeni etkinlik görüneceğini unutmayın. Bu işlem hala içinde <xref:System.Activities.Presentation.Model.EditingScope>bekleyen olduğundan, tasarımcı henüz güncelleştirilmesin.  
  
3. Düzenleme kapsamını işlemek için **Düzenleme Kapsamını Kapat'a** basın. Tasarımcıda üç etkinlik görünür.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`

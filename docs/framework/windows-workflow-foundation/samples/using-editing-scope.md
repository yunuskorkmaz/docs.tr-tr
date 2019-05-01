---
title: Düzenleme Kapsamını Kullanma
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 6417e51a29215ce2da22fa4c655642a5fe9b7d18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004776"
---
# <a name="using-editing-scope"></a>Düzenleme Kapsamını Kullanma
Bu örnek, tek bir atomik birim alınabilir olacak şekilde bir değişiklik kümesini toplu gösterilmiştir. Varsayılan olarak, bir etkinlik Tasarımcısı yazarı tarafından gerçekleştirilen eylemler otomatik olarak geri al/Yinele sisteme tümleşiktir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Kapsam ve Geri Al ve Yinele düzenleme.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, bir grup için değişiklik toplu gösterilmiştir <xref:System.Activities.Presentation.Model.ModelItem> ağacı içinde tek bir iş birimi. Bağlama sırasında dikkat <xref:System.Activities.Presentation.Model.ModelItem> değerleri doğrudan bir WPF Tasarımcısı'ndan, değişiklikleri otomatik olarak uygulanır. Bu örnek, toplanacak birden çok değişiklik kesinlik temelli Kodun kullanmak yerine tek bir değişiklik yapıldığını, nelerin yapılmalıdır gösterir.  
  
 Bu örnekte, üç faaliyetin eklenir. Düzenleme başladığında <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> örneğinde adlı <xref:System.Activities.Presentation.Model.ModelItem>. Yapılan değişiklikler <xref:System.Activities.Presentation.Model.ModelItem> ağacı düzenleme bu kapsam içinde toplu. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> Komutu tarafından döndürülen bir <xref:System.Activities.Presentation.Model.EditingScope>, bu örneği denetlemek için kullanılabilir. Ya da <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> veya <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> ya da işlemeye çağrılabilir veya düzenleme kapsamına geri döndür.  
  
 Ayrıca yuvalayabilirsiniz <xref:System.Activities.Presentation.Model.EditingScope> daha büyük bir düzenleme bir parçası olarak izlenmesi için birden çok değişiklik kümeleri sağlayan nesneler, kapsam ve ayrı olarak denetlenebilir. Bu özelliği kullanan bir senaryo, birden fazla iletişim kutuları değişiklikler kaydedilmiş veya ayrı olarak, tek bir atomik işlem olarak kabul tüm değişiklikler geri olacaktır. Bu örnekte, düzenleme kapsamları kullanarak yığılmış bir <xref:System.Collections.ObjectModel.ObservableCollection%601> türü <xref:System.Activities.Presentation.Model.ModelEditingScope>. <xref:System.Collections.ObjectModel.ObservableCollection%601> İç içe geçme derinliği Tasarımcı yüzeyinde gözlenecek böylece kullanılır.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Derleme örneği çalıştırın ve ardından iş akışını değiştirmek için sol taraftaki düğmelerini kullanın.  
  
2. Tıklayın **açık kapsamı düzenleme**.  
  
    1. Bu komutu çağıran <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> düzenleme bir kapsam oluşturur ve düzenleme da yığına iter.  
  
    2. Üç etkinlikleri daha sonra eklenen seçili <xref:System.Activities.Presentation.Model.ModelItem>. Düzenleme kapsamına ile açılmış değil gerçekleştiriyorsanız <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, üç yeni etkinlik Tasarımcısı tuvalinde görüneceği. Bu işlemi olduğundan içinde hala beklemede <xref:System.Activities.Presentation.Model.EditingScope>, Tasarımcı henüz güncelleştirilmemiş.  
  
3. Tuşuna **Kapat düzenleme kapsamı** düzenleme kapsamına tamamlanamadı. Üç Etkinlik Tasarımcısı'nda görünür.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`

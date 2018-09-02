---
title: Araç kutusu hizmeti
ms.date: 03/30/2017
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
ms.openlocfilehash: 0b21f10c763f3f82591f947eb4cc48cf90f4ac79
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406468"
---
# <a name="toolbox-service"></a>Araç kutusu hizmeti
Bu örnek nasıl güncelleştirilebileceğini gösterir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] etkinlikler araç kutusu temel iş akışı bağlama. Özel bir etkinlik seçili olduğundan bağlı olarak toolbox içeriklerin değiştiren bir iş akışı örneği içerir.  
  
## <a name="discussion"></a>Tartışma  
 İş akışı yazma sırasında müşteriler genellikle bir bağlama duyarlı olacak şekilde kendi araç kutusu istersiniz. Örneğin, kullanıcı iş akışını belirli bir etkinlik eklendiğinde birkaç ek etkinlikler araç kutusunu göstermesini sağlamak isteyebilirsiniz. Etkinlikleri akışından kaldırılırsa, araç uygun etki alanı gereksinimlerine göre tepki.  
  
 Yeniden barındırılan iş akışı tasarımcısında, araç kutusu denetim ve iş akışı modeli değişikliklere dayalı işaretlenmesini sağlayabilir, araç kutusu denetimi uygun değişiklikleri ana tetikler. Bununla birlikte, [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], araç çubuğu kullanıcı tarafından denetlenen ve bu nedenle bir arabirim içeriğini değiştirmek için gereklidir. `IActivityToolboxService` Bu arabirimidir.  
  
 API'si aşağıdaki dört yöntemi sağlar.  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WorkflowSimulator.sln çözüm dosyasını açın.  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  Workflow.xaml dosyası açın.  
  
4.  Ekleme bir **CustomActivity** bunu araç kutusundan sürükleyip bırakarak. Bir ek araç kutusu kategorisi adlı dikkat edin: **yeni WF kategori** ek bir etkinlikle **atama**.  
  
5.  Artık seçimini kaldırın **CustomActivity** başka bir etkinlik içine sürükleyerek.  
  
6.  Öğe **atama** kategorisinde **yeni WF kategori** araç kutusu altında artık kaldırılır. Ayrıca, kategorisinde başka bir öğe yok olduğundan, kategori de kaldırılır.  
  
7.  Seçin **CustomActivity** yeniden ve kategori ve **atama** etkinlik yeniden eklenir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`

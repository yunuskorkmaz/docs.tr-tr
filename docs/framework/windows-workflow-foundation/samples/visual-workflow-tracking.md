---
title: Görsel İş Akışı İzleme
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 22c91a12bba148e1fa823bb2bf9b3eaf16704c46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182756"
---
# <a name="visual-workflow-tracking"></a>Görsel İş Akışı İzleme
Bu örnek, [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]hata ayıklama işlevini kullanarak görsel bir iş akışı izleme uygulamasının nasıl yazılabildiğini gösterir.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Uygulama basit bir akış şeması iş akışı yürütür (Workflow.xaml'de tanımlanan) ve şu anda çalıştırılan iş akışını görüntülemek için iş akışı tasarımcısını yeniden barındırır. İş akışı yürütüldükçe, şu anda yürütülen etkinlik sarı bir anahat ve hata ayıklama okuyla gösterilir. Ayrıca, iş akışı tarafından oluşturulan izleme kayıtları da uygulama penceresinde görüntülenir. İş akışı izleme hakkında daha fazla bilgi için [bkz.](../workflow-tracking-and-tracing.md) İş akışı tasarımcısını yeniden barındırma hakkında daha fazla bilgi [için](../rehosting-the-workflow-designer.md)bkz.

 İş akışı simülatörü iki sözlük tutarak çalışır. Bunlardan biri, şu anda çalıştırılan etkinlik nesnesi ile etkinliğin anlık olarak bulunduğu XAML satır numarası arasında bir eşleme içerir. Diğer etkinlik örnek kimliği ve etkinlik nesnesi arasında bir eşleme içerir. İzleme kayıtları özel bir izleme profili kullanılarak yayımlandığında, uygulama şu anda çalıştırılan etkinliğin örnek kimliğini belirler ve anında alan XAML dosyasıyla yeniden eşlenir. Yeniden barındırılan iş akışı tasarımcısı, tasarımcı yüzeyindeki etkinliği vurgulamak ve iş akışı hata ayıklayıcıyla aynı yöntemi kullanması, özellikle etkinliğin etrafında sarı bir kenarlık çizmesi ve sol tarafı boyunca sarı bir ok göstermesi talimatı nı Tasarımcısı.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010'daki örnek dizinden WorkflowSimulator.sln dosyasını açın.

2. Çözümü derlemek için CTRL+SHIFT+B'ye basın.

3. Örneği çalıştırmak için CTRL + F5 tuşuna basın. Bu, yeniden barındırılan iş akışı tasarımcısı penceresinde Workflow.xaml dosyasını görüntüler.

4. **Dosya** menüsüne tıklayın ve **İş Akışını Çalıştır'ı seçin... seçeneğini belirleyin.**

5. Şu anda yürütülen etkinliğin daha önce açıklandığı gibi vurgulandığına ve izleme kayıtlarının uygulama penceresinin sağ tarafında görüntülendiğine dikkat edin.

6. İş akışı tamamlandığında, hangi faaliyete karşılık geldiğini denetlemek için izleme kayıtlarından herhangi birini tıklatabilirsiniz.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`

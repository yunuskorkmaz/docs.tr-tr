---
title: Wait For Input etkinliği
ms.date: 03/30/2017
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
ms.openlocfilehash: 2e878e8c91c5da12a68da848694ce790896517c7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741178"
---
# <a name="wait-for-input-activity"></a>Wait For Input etkinliği
Bu örnek, bir iş akışında adlandırılmış yer işaretleri oluşturulacağını gösterir. Windows Workflow Foundation (WF), bildirim temelli bir yer işareti oluşturmak için bir etkinlik sağlamaz. Bu nedenle, iş akışınızda yer işareti oluşturmak istediğinizde, oluşturduğu özel bir etkinlik yazmanız gerekir. `WaitForInput` Bu örnekte tanımlanan etkinlik, kullanıcıların bir iş akışı içinde bildirimli olarak yer işaretleri oluşturabilirsiniz böylece bu işlevselliği sağlar.  
  
## <a name="projects-in-this-sample"></a>Bu örnekte projeleri  
  
|**Proje adı**|**Açıklama**|**Ana dosyaları**|  
|-|-|-|  
|WaitForInput|İçeren `WaitForInput` etkinlik ve iş Tasarımcısı|WaitForInput.cs<br /><br /> `WaitForInput` Etkinlik tanımı.|  
|||WaitForInputDesigner.xaml<br /><br /> Özel tasarımcısını `WaitForInput` etkinlik.|  
|||TypeToFirstGenericArgumentConverter.cs<br /><br /> WPF tür dönüştürücüsü genel tür etkinlik Tasarımcısı'nda güncelleştirmek için kullanılır.|  
|WaitForInputTestClient|Yapılandırır ve iş akışı Tasarımcısı'nı kullanarak birkaç WaitForInput etkinliği kullanarak iş akışını çalıştıran örnek istemci uygulaması.|Sequence1.xaml<br /><br /> Kullanan bir sıralı iş akışı `WaitForInput` etkinlik.|  
|||Program.cs<br /><br /> Sequence1.xaml içinde tanımlanan iş akışı örneğini çalıştırır.|  
  
## <a name="waitforinput-activity"></a>WaitForInput etkinliği  
 `WaitForInput` Etkinliğini bir iş akışında adlandırılmış bir yer işareti oluşturur. Yer işareti, bir sinyal için bekler ve yapılandırılmış türüne verilerini alır. Yer işareti çıktıktan sonra iş akışına geçirilen veriler aracılığıyla `Result` özelliği.  
  
 `WaitForInput` Etkinlik türetilir <xref:System.Activities.NativeActivity> yalnızca üzerinden erişilebilir olan yer işaretleri oluşturmanız gerekir çünkü <xref:System.Activities.NativeActivityContext> sınıfı.  
  
 Etkinlik için bir tasarımcı bağlama, güncelleştirilebilir genel bağımsız değişkene özellik eklemek ve varsayılan genel türün dize olarak ayarlanması için uygulanan üç özniteliğe sahiptir. Etkinlik, ayrıca aşağıdaki tabloda listelenen bağımsız değişkenlere sahiptir.  
  
|**Ad**|**Türü**|**Açıklama**|  
|-|-|-|  
|TResult|Genel bağımsız değişken (TResult)|Yer işareti türü. Yer işaretine sürdürüldü olduğunda geçirilecek veri türüdür.|  
|YerİşaretiAdı|InArgument\<dizesi >|Yer işaretinin adı.|  
|Sonuç|InArgument\<TResult >|Yer işareti devam ettirildiğinde veriler etkinliği geçirildi.|  
  
## <a name="waitforinput-activity-designer"></a>WaitForInput etkinlik Tasarımcısı  
 `WaitForInput` Etkinlik Tasarımcısı WaitForInputDesigner.xaml dosyasında gerçekleştirilir. `WaitForInput` Etkinlik ve iş Tasarımcısı aynı derlemede de dahil edilir. Aşağıdaki grafik gösterildiği `WaitForInput` araç kutusunda derleme olarak aynı ada sahip bir kategoride etkinlik.  
  
 ![Araç kutusu ekran WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")  
  
 Aşağıdaki grafik gösterildiği `WaitForInput` Tasarımcısı. Çünkü, `WaitForInput` etkinlik çok basit, tüm bağımsız değişkenler doğrudan tasarım yüzeyinde ayarı tasarımcı sağlar.  
  
 ![WaitForInput etkinlik Tasarımcısı](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WaitForInput.sln dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Hata ayıklama olmadan örneği başlatmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`
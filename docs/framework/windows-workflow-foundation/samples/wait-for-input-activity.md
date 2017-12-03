---
title: "Giriş etkinliği bekle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d877c147a19635782b652d96031644b3be42448a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wait-for-input-activity"></a>Giriş etkinliği bekle
Bu örnek bir iş akışında adlandırılmış yer işaretleri oluşturulacağını gösterir. [!INCLUDE[wf](../../../../includes/wf-md.md)]bir etkinlik bildirim temelli yer işareti oluşturmak için sağlamaz. Bu nedenle, iş akışında yer işareti oluşturmak istediğinizde, oluşturduğu özel bir aktivite yazmanız gerekir. `WaitForInput` Bu örnekte tanımlanan faaliyet, kullanıcılar bir iş akışındaki bildirimli olarak yer işaretleri oluşturabilmesi için bu işlevselliği sağlar.  
  
## <a name="projects-in-this-sample"></a>Bu örnek proje  
  
|**Proje adı**|**Açıklama**|**Ana dosyaları**|  
|-|-|-|  
|WaitForInput|İçeren `WaitForInput` etkinliği ve onun Tasarımcısı|WaitForInput.cs<br /><br /> `WaitForInput`Etkinlik tanımı.|  
|||WaitForInputDesigner.xaml<br /><br /> İçin özel Tasarımcısı `WaitForInput` etkinlik.|  
|||TypeToFirstGenericArgumentConverter.cs<br /><br /> Etkinlik Tasarımcısı'nda genel türü güncelleştirmek için kullanılan WPF türü dönüştürücü.|  
|WaitForInputTestClient|Yapılandırır ve iş akışı Tasarımcısı'nı kullanarak birkaç WaitForInput etkinlikleri kullanarak bir iş akışı çalıştıran örnek istemci uygulaması.|Sequence1.xaml<br /><br /> Kullanan bir sıralı iş akışı `WaitForInput` etkinlik.|  
|||Program.cs<br /><br /> Sequence1.xaml içinde tanımlanan iş akışı örneğini çalıştırır.|  
  
## <a name="waitforinput-activity"></a>WaitForInput etkinliği  
 `WaitForInput` Etkinliğini bir iş akışında adlandırılmış bir yer işareti oluşturur. Yer işareti sinyal bekler ve yapılandırılmış türüne verilerini alır. Yer işareti çıktıktan sonra iş akışına geçirilen verileri aracılığıyla kullanılabilir `Result` özelliği.  
  
 `WaitForInput` Etkinlik türer <xref:System.Activities.NativeActivity> yalnızca üzerinden erişilebilir yer işaretleri oluşturmanız gerekir çünkü sınıfı <xref:System.Activities.NativeActivityContext> sınıfı.  
  
 Etkinlik bir tasarımcı bağlama, güncelleştirilebilir genel bağımsız değişken özellik ekleme ve varsayılan genel tür dize olarak ayarlamak için uygulanan üç özniteliklere sahiptir. Etkinlik, aynı zamanda aşağıdaki tabloda listelenen bağımsız değişkenlere sahiptir.  
  
|**Ad**|**Türü**|**Açıklama**|  
|-|-|-|  
|TResult|Genel bağımsız değişken (TResult)|Yer işareti türü. Yer işaretine sürdürüldü zaman geçirilecek veri türüdür.|  
|YerİşaretiAdı|InArgument\<dize >|Yer işareti adı.|  
|Sonuç|InArgument\<TResult >|Yer işareti devam ettirildiğinde veri faaliyete geçirildi.|  
  
## <a name="waitforinput-activity-designer"></a>WaitForInput etkinlik Tasarımcısı  
 `WaitForInput` Etkinlik Tasarımcısı WaitForInputDesigner.xaml dosyasında uygulanır. `WaitForInput` Etkinlik ve onun Tasarımcısı aynı bütünleştirilmiş kodda dahil edilir. Aşağıdaki grafik gösterir `WaitForInput` etkinlik araç çubuğundaki derleme aynı ada sahip bir kategoride.  
  
 ![WaitForInput araç kutusu ekran](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")  
  
 Aşağıdaki grafik gösterir `WaitForInput` Tasarımcısı. Çünkü, `WaitForInput` etkinlik çok basit, doğrudan Tasarımcı yüzeyine tüm bağımsız değişkenler ayarlamayı tasarımcı sağlar.  
  
 ![WaitForInput etkinlik Tasarımcısı](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WaitForInput.sln dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Hata ayıklama olmadan örnek başlatmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`
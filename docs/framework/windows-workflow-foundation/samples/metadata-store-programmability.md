---
title: Meta veri deposu ile programlama
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 6efcb86e29f19a29d6ef382afa336d0ca2ce4306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517443"
---
# <a name="metadata-store-programmability"></a>Meta veri deposu ile programlama
Meta veri deposu bir [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] CLR öznitelikleri biçiminde rasgele meta verileri ilişkilendirme için olanak tanıyan özelliği çalışma zamanında türleri. Bu çalışma zamanı bileşenleri ve tasarım zamanı dekiler yanı sıra, çalışma zamanı etkilemeden tasarım zamanı bileşenleri değiştirme yeteneğini arasında gevşek bir bağlantı sağlar. Örnek, bir çalışma zamanı türü için hiçbir denetim üzerinden sahibiz kaynak özniteliklerini uygulayarak karşı meta veri deposu program gösterilmektedir. Genellikle kullanılan terminolojiyi barındırma uygulama türleri kümesi için meta verileri kaydeder ' dir.  
  
 Çıktısı bir ek, beklenmeyen öznitelik karşılaşabilirsiniz <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`. Bu meta verileri API'si kullanılırken eklenir ve örnek çalışan üzerinde hiçbir etkisi olmaz.  
  
 Bu örnek gösterilmektedir:  
  
## <a name="demonstrates"></a>Gösteriler  
  
-   Meta verileri kullanarak özniteliği ekleme API depolar.  
  
-   Meta veri kaydı ertelemek için bir geri dönüş mekanizması kullanıyor.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ProgrammingMetadataStore.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`
---
title: Meta veri Store programlama
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 4ea6117686b985a9ea18ce4e5cc4ea2b5c25524c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423291"
---
# <a name="metadata-store-programmability"></a>Meta veri Store programlama
Meta veri deposu bir [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] türlerini çalışma zamanında CLR öznitelikleri biçiminde rastgele meta veriler ilişkisini olanak tanıyan özellik. Bu çalışma zamanı bileşenlerini ve tasarım zamanı karşılıkları yanı sıra, çalışma zamanı etkilemeden tasarım saati bileşenlerini değiştirme olanağı arasında gevşek bir bağlantı sağlar. Örnek, bir çalışma zamanı türü, biz denetimi içinde olan kaynak öznitelikleri uygulayarak meta veri deposuna karşı programlamak gösterilmektedir. Genellikle kullanılan terimler, barındırma uygulaması türleri kümesi için meta verileri kaydeder ' dir.  
  
 Çıktısı, beklenmeyen ek bir öznitelik fark edebilirsiniz <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`. Bu meta veri API'si kullanılırken eklenir ve örnek çalışmasını etkilemez.  
  
 Bu örnek gösterir:  
  
## <a name="demonstrates"></a>Gösteriler  
  
-   Öznitelik ekleme meta verileri kullanarak API depolayın.  
  
-   Meta veri kaydı ertelemek için bir geri dönüş mekanizması kullanıyor.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ProgrammingMetadataStore.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`
---
title: "Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd89a3333ab68b7d580c813a4b7741686b46c5b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma
Uygun bir barındırma modu seçtikten sonra Web Hizmetleri olarak ifşa edilip uygulama arabirimleri yapılandırmak için COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe) kullanın.  
  
> [!NOTE]
>  Aşağıdaki görevleri gerçekleştirmek için makinede yönetici olması gerekir.  
  
 ComSvcConfig.exe en son hizmet modeli sürümü (şu anda v4.5) kullanmak için bir web hizmeti yapılandırmak için bir Windows 7 makinede kullanırken, aşağıdaki adımları gerçekleştirin:  
  
1.  Kayıt defteri anahtarını ayarlayın `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` 0x00000001 bir DWORD değeri için  
  
2.  ComSvcConfig.exe Çalıştır  
  
3.  Özgün değeri dön 1. adımda eklenen kayıt defteri anahtarını geri veya varsa silme yoktu.  
  
> [!IMPORTANT]
>  Bu kayıt defteri anahtarı geri döndürmeyi önemlidir. Bu uyumluluk anahtarıdır. Bu değişikliği geri döndürmeyi olmayan sorunlar makinede çalışan diğer .NET uygulamaları neden olabilir).  
  
> [!WARNING]
>  ComSvcConfig.exe kullanırken bir Windows 8 makinede bir iletişim kutusu/install belirten görüntülenir "aşağıdaki Windows özelliği, bilgisayarınızdaki bir uygulama gerekiyor: .NET Framework 3.5 (.NET 2.0 ve 3.0 içerir".NET Framework 3.5 yüklü değilse. Bu iletişim kutusunu yok sayılabilir. Alternatif olarak azaltılabilir 0x00000001 DWORD değerini OnlyUseLatestCLR kayıt defteri anahtarına olabilir  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>COM + modu barındırma kullanarak Web Hizmetleri açığa çıkarılması olan arabirimler kümesi için bir arabirim eklemek için  
  
-   ComSvcConfig / kullanarak çalışan `/install` ve `/hosting:complus` , aşağıdaki örnekte gösterildiği gibi seçenekleri.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     Komut ekler `IFinances` arabiriminin `ItemOrders.IFinancial` bileşeninden (OnlineStore COM + uygulaması) için Web Hizmetleri olarak sunulan arabirimleri kümesi. Hizmet COM + modu barındırma kullanır ve bu nedenle açık uygulama etkinleştirmesi gerekir.  
  
     Yıldız işareti (*) joker karakterini bileşeni ve arabirim için kullanılabilir, ancak yalnızca seçilen işlevleri bir Web hizmeti olarak kullanıma sunmak istediğiniz çünkü bunu kullanmaktan kaçının. Bu bileşen gelecek bir sürümünde çalıştırırsanız, joker karakter kullanılması yapılandırma sözdizimi belirlendi olduğunda mevcut olmayabilen arabirimler kasıtsız olarak sunabilir.  
  
     / Verbose seçeneği hataları ek olarak uyarıları görüntülemek için aracı bildirir.  
  
     Sunulan hizmet sözleşmesini yöntemlerden tümünde içerecek `IFinances` arabirimi.  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Yalnızca belirli yöntemler kullanarak COM + modu barındırma Web Hizmetleri açığa çıkarılması olan arabirimler kümesi arabirimden eklemek için  
  
-   ComSvcConfig / kullanarak çalışan `/install` ve `/hosting:complus` aşağıdaki örnekte gösterildiği gibi gerekli yöntemleri açık adlandırma ile seçenekleri.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     Komut yalnızca ekler `Credit` ve `Debit` yöntemleri `IFinances` arabirimi olarak sunulan hizmet sözleşmesi işlemleri. Diğer tüm yöntemleri arabirimde sözleşmeden atlanacak ve Web hizmeti istemcilerden aranabilir olmaz.  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a>Web barındırma modunu kullanan Web Hizmetleri açığa çıkarılması olan arabirimler kümesi için bir arabirim eklemek için  
  
-   ComSvcConfig / kullanarak çalışan `/install` seçeneği ve `/hosting:was` , aşağıdaki örnekte gösterildiği gibi seçeneği.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     Komut ekler `IStockLevels` üzerinde arabirim `ItemInventory.Warehouse` bileşeninden (OnlineWarehouse COM + uygulaması) için Web Hizmetleri olarak sunulan arabirimleri kümesi. Böylece uygulama otomatik olarak etkinleştirilir ve IIS OnlineWarehouse sanal dizinin yerine COM +'da barındırılan Web hizmetidir gerektiği gibi.  
  
     Web barındırılan işlem dışı yapılandırmayı kullanmak için COM + uygulaması Bileşen Hizmetleri yönetim konsolunu kullanarak bir sunucu uygulaması yerine bir kitaplık uygulaması olarak çalıştırmak için yapılandırılmalıdır. Sunucu uygulamaları yapılandırılan uygulamalar standart Web barındırılan modunu kullanın ve her isteği işlemek için bir işlem atlama doğurur.  
  
     `/mex` Seçeneği, aynı aktarım hizmetinden bir sözleşme tanımı almak istediğiniz istemcileri desteklemek için uygulamanın hizmet uç noktası olarak kullanan bir ek meta veri değişimi (MEX) Hizmeti uç noktası ekler.  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a>Belirtilen bir arabirim için bir Web hizmetini kaldırmak için  
  
-   ComSvcConfig / kullanarak çalıştırmanız `/uninstall` , aşağıdaki örnekte gösterildiği gibi seçeneği.  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     Komut kaldırır `IFinances` üzerinde arabirim `ItemOrders.Financial` bileşen (uygulamadan OnlineStore COM +).  
  
### <a name="to-list-currently-exposed-interfaces"></a>Şu anda arabirimleri listelemek için  
  
-   ComSvcConfig / kullanarak çalıştırmanız `/list` , aşağıdaki örnekte gösterildiği gibi seçeneği.  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     Komut şu anda arabirimleri, ilgili adres ve yerel makineye kapsamlı bağlama ayrıntıları ile birlikte listeler.  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a>Şu anda belirli listelemek için sergilenen arabirimleri  
  
-   ComSvcConfig / kullanarak çalıştırmanız `/list` , aşağıdaki örnekte gösterildiği gibi seçeneği.  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     Komut listeleri şu anda COM + kullanıma sunulan-arabirimi, yerel makinede OnlineStore COM + uygulaması için bağlama ayrıntıları ve karşılık gelen adresi ile barındırılan.  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>Yardımcı programı ile kullanılabilir seçenekler hakkında Yardım görüntülemek için  
  
-   ComSvcConfig / kullanarak Çalıştır /? Aşağıdaki örnekte gösterildiği gibi seçeneği.  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM+ Uygulamaları ile Tümleştirme Genel Bakış](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)

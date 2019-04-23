---
title: "Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma"
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 5b330a727c0a4a20de13f43fd2844d0b745e5060
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322595"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma
Uygun bir barındırma modu seçtikten sonra COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe) Web Hizmetleri olarak kullanıma sunulacak bir uygulama arabirimleri yapılandırmak için kullanın.  
  
> [!NOTE]
>  Aşağıdaki görevleri gerçekleştirmek için makinede bir yönetici olması gerekir.  
  
 En son hizmet modeli sürümü (şu anda v4.5) kullanmak için bir web hizmeti yapılandırmak için bir Windows 7 makinesinde ComSvcConfig.exe kullanırken aşağıdaki adımları gerçekleştirin:  
  
1. Kayıt defteri anahtarını ayarlayın `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` 0x00000001 DWORD değerini  
  
2. ComSvcConfig.exe çalıştırın  
  
3. Özgün değeri geri dön 1. adımda eklenen kayıt defteri anahtarı geri veya varsa silin yoktu.  
  
> [!IMPORTANT]
>  Bu kayıt defteri anahtarı dönüştürme önemlidir. Bu uyumluluk anahtarıdır. Bu değişikliği geri döndürülürken değil sorunları makine üzerinde çalışan diğer .NET uygulamaları neden olabilir).  
  
> [!WARNING]
>  ComSvcConfig.exe kullanırken Windows 8 makinesinde bir iletişim kutusu/Install belirten görüntülenen "bilgisayarınızda bir uygulama aşağıdaki Windows özellik gerekiyor: .NET Framework 3.5 (.NET 2.0 ve 3.0 içerir".NET Framework 3.5 yüklü değilse. Bu iletişim kutusunu yok sayılabilir. Alternatif olarak sed OnlyUseLatestCLR kayıt defteri anahtarı DWORD değerini 0x00000001 yapabilecekleriniz  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Bir arabirim kullanarak COM + modu barındırma Web Hizmetleri olarak açığa olan arabirimler kümesi eklemek için  
  
-   ComSvcConfig / kullanarak çalıştırma `/install` ve `/hosting:complus` , aşağıdaki örnekte gösterildiği gibi seçenekleri.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     Komut ekler `IFinances` arabiriminin `ItemOrders.IFinancial` Web Hizmetleri olarak kullanıma sunulacak arabirimleri kümesine (OnlineStore COM + uygulaması) bileşeni. Hizmet, COM + modu barındırma kullanır ve bu nedenle açık uygulama etkinleştirme gerektirir.  
  
     Yıldız işareti (*) joker karakterini bileşeni ve arabirimi için kullanılabilse de, yalnızca seçilen işlevleri bir Web hizmeti olarak kullanıma sunmak isteyebilirsiniz, çünkü kullanmaya özen gösterin. Bu bileşen gelecek bir sürümünde çalıştırırsanız, joker karakter kullanılması yanlışlıkla yapılandırma sözdizimi belirlendi olduğunda mevcut olmuş olabilir arabirimler sunabilir.  
  
     / Verbose seçeneği hataları ek olarak uyarıları görüntülemek için araç bildirir.  
  
     Kullanıma sunulan hizmet sözleşmesini tüm yöntemleri içerecek `IFinances` arabirimi.  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Yalnızca belirli yöntemleri kullanarak COM + modu barındırma Web Hizmetleri olarak açığa olan arabirimler kümesi bir arabirimden eklemek için  
  
-   ComSvcConfig / kullanarak çalıştırma `/install` ve `/hosting:complus` ile aşağıdaki örnekte gösterildiği gibi gerekli yöntemlerden açık adlandırma seçenekleri.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     Komutu yalnızca ekler `Credit` ve `Debit` yöntemlerinden `IFinances` arabirimi olarak kullanıma sunulan hizmet sözleşmesi işlemleri. Tüm diğer yöntemler arabirimde sözleşmeden atlanacak ve Web hizmeti istemcilerden çağrılabilir olmayacaktır.  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a>Web barındırma modunu kullanarak Web Hizmetleri olarak açığa olan arabirimler kümesi için bir arabirim eklemek için  
  
-   ComSvcConfig / kullanarak çalıştırma `/install` seçeneği ve `/hosting:was` seçeneği, aşağıdaki örnekte gösterildiği gibi.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     Komut ekler `IStockLevels` üzerinde arabirim `ItemInventory.Warehouse` Web Hizmetleri olarak kullanıma sunulacak arabirimleri kümesine (OnlineWarehouse COM + uygulaması) bileşeni. IIS sanal dizini OnlineWarehouse yerine COM +'da barındırılan Web hizmeti ve böylece uygulama otomatik olarak etkinleştirilir gerektiğinde.  
  
     Web barındırılan işlem içi yapılandırmayı kullanmak için COM + uygulaması Bileşen Hizmetleri yönetim konsolunu kullanarak bir sunucu uygulaması yerine bir kitaplık uygulaması olarak çalıştırmak için yapılandırılmalıdır. Sunucu uygulamaları yapılandırılan uygulamalar standart Web barındırılan modunu kullanın ve her isteği işlemek için bir işlem atlama doğurur.  
  
     `/mex` Seçeneği, aynı taşıma, hizmetten bir sözleşme tanımı almak istediğiniz istemcileri desteklemek için uygulamanın hizmet uç noktası olarak kullanan bir ek meta veri değişimi (MEX) hizmet uç noktası ekler.  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a>Belirtilen bir arabirim için bir Web hizmeti kaldırmak için  
  
-   ComSvcConfig / kullanarak çalıştırma `/uninstall` seçeneği, aşağıdaki örnekte gösterildiği gibi.  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     Komut kaldırır `IFinances` üzerinde arabirim `ItemOrders.Financial` (OnlineStore COM + uygulaması) bileşenini.  
  
### <a name="to-list-currently-exposed-interfaces"></a>Şu anda arabirimleri listelemek için  
  
-   ComSvcConfig / kullanarak çalıştırma `/list` seçeneği, aşağıdaki örnekte gösterildiği gibi.  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     Komut şu anda arabirimleri, bağlama ayrıntıları, yerel makineye kapsamlı ve karşılık gelen adresi birlikte listeler.  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a>Şu anda belirli listelemek için arabirimleri kullanıma sunulan  
  
-   ComSvcConfig / kullanarak çalıştırma `/list` seçeneği, aşağıdaki örnekte gösterildiği gibi.  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     Komut listeleri şu anda COM + kullanıma sunulan-arabirimi, yerel makinede OnlineStore COM + uygulaması bağlama ayrıntıları ve karşılık gelen adresi ile barındırılan.  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>Yardımcı programı ile kullanılabilecek Seçenekleri Yardımı görüntülemek için  
  
-   Kullanarak ComSvcConfig / çalışan /? seçeneği, aşağıdaki örnekte gösterildiği gibi.  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM+ Uygulamaları ile Tümleştirme Genel Bakış](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)

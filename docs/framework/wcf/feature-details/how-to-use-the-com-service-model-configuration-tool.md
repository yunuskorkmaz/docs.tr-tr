---
title: "Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma"
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: f9e761bafd84726b51a2010a932c68c67c37f899
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595290"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma
Uygun bir barındırma modu seçtikten sonra, Web Hizmetleri olarak kullanıma sunulacak uygulama arabirimlerini yapılandırmak için COM+ hizmet modeli yapılandırma komut satırı aracını (ComSvcConfig. exe) kullanın.  
  
> [!NOTE]
> Aşağıdaki görevlerden herhangi birini gerçekleştirmek için makinede yönetici olmanız gerekir.  
  
 Bir Web hizmetini en son hizmet modeli sürümünü (Şu anda v 4.5) kullanacak şekilde yapılandırmak için Windows 7 makinesinde ComSvcConfig. exe ' yi kullanırken aşağıdaki adımları gerçekleştirin:  
  
1. Kayıt defteri anahtarını `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` 0x00000001 DWORD değerine ayarlayın  
  
2. ComSvcConfig. exe dosyasını çalıştır  
  
3. Adım 1 ' de eklenen kayıt defteri anahtarını özgün değerine geri dönün veya yoksa silin.  
  
> [!IMPORTANT]
> Bu kayıt defteri anahtarının geri döndürülmesi önemlidir. Bu bir uyumluluk anahtarıdır. Bu değişikliğin geri döndürülmesi, makinede çalışan diğer .NET uygulamalarıyla ilgili sorunlara neden olabilir).  
  
> [!WARNING]
> Bir Windows 8 makinesinde ComSvcConfig. exe/install kullanırken bir iletişim kutusu görüntülenir. "bilgisayarınızdaki bir uygulama şu Windows özelliğine ihtiyaç duyuyor: .NET Framework 3,5 (.NET 2,0 ve .NET 3,0 içerir) .NET Framework 3,5 yüklü değilse. Bu iletişim kutusu yoksayılabilir. Alternatif olarak, OnlyUseLatestCLR kayıt defteri anahtarını 0x00000001 DWORD değerine bağlayabilirsiniz.  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a>Web Hizmetleri olarak sunulan arabirimler kümesine, COM+ barındırma modunu kullanarak bir arabirim eklemek için  
  
- `/install`Aşağıdaki örnekte gösterildiği gibi, ve seçeneklerini kullanarak ComSvcConfig komutunu çalıştırın `/hosting:complus` .  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     Komut, `IFinances` `ItemOrders.IFinancial` bileşen arabirimini (ONLINESBIR com+ uygulamasından) Web Hizmetleri olarak kullanıma sunulacak arabirimler kümesine ekler. Hizmet COM+ barındırma modunu kullanır ve bu nedenle açık uygulama etkinleştirmesi gerektirir.  
  
     \*Bir Web hizmeti olarak yalnızca seçili işlevselliği göstermek isteyebileceğiniz için, joker karakter yıldız () karakteri bileşen ve arabirim için kullanılabilir ancak kullanmaktan kaçının. Bu bileşenin gelecek bir sürümüyle çalıştırırsanız, joker karakteri kullanmak, yapılandırma sözdizimi belirleniyorsa, yanlışlıkla mevcut olmayan arabirimler sunabilir.  
  
     /Verbose seçeneği, aracının hatalara ek olarak uyarıları görüntülemesini sağlar.  
  
     Gösterilen hizmet sözleşmesi, arabirimdeki tüm yöntemleri içerir `IFinances` .  
  
## <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a>Bir arabirimden, Web Hizmetleri olarak sunulan arabirimler kümesine, COM+ barındırma modunu kullanarak yalnızca belirli yöntemler eklemek için  
  
- `/install` `/hosting:complus` Aşağıdaki örnekte gösterildiği gibi, gerekli yöntemlerin açık adlandırması ile ve seçeneklerini kullanarak ComSvcConfig komutunu çalıştırın.  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     Komutu, `Credit` `Debit` `IFinances` sunulan hizmet sözleşmesine yalnızca işlemler olarak arabirimden ve yöntemlerini ekler. Arabirimdeki diğer tüm yöntemler sözleşmede atlanacak ve Web hizmeti istemcilerinden çağrılabilir olmayacaktır.  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-web-hosting-mode"></a>Web hizmeti olarak sunulan arabirimler kümesine Web barındırma modunu kullanarak arabirim ekleme  
  
- `/install`Aşağıdaki örnekte gösterildiği gibi seçeneğini ve seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/hosting:was` .  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     Bu komut, `IStockLevels` `ItemInventory.Warehouse` bileşeni bileşenini (OnlineWarehouse com+ uygulamasından) Web Hizmetleri olarak kullanıma sunulacak arabirim kümesine ekler. Hizmet, COM+ yerine IIS 'nin OnlineWarehouse sanal dizininde barındırılır ve bu nedenle uygulama gerektiği şekilde otomatik olarak etkinleştirilir.  
  
     Web 'de barındırılan işlem içi yapılandırmayı kullanmak için COM+ uygulaması, Bileşen Hizmetleri yönetim konsolunu kullanarak bir sunucu uygulaması yerine bir kitaplık uygulaması olarak çalışacak şekilde yapılandırılmalıdır. Sunucu uygulamaları olarak yapılandırılan uygulamalar, standart Web 'de barındırılan modu kullanır ve her isteği işlemek için bir işlem atlaması sağlar.  
  
     `/mex`Seçeneği, hizmetten bir sözleşme tanımı almak isteyen istemcileri desteklemek için uygulamanın hizmet uç noktasıyla aynı aktarımı kullanan bir ek meta veri değişimi (MEX) hizmet uç noktası ekler.  
  
## <a name="to-remove-a-web-service-for-a-specified-interface"></a>Belirtilen bir arabirim için bir Web hizmetini kaldırmak için  
  
- Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/uninstall` .  
  
    ```console  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     Komut, `IFinances` Bileşen üzerindeki arabirimini kaldırır `ItemOrders.Financial` (onlines, com+ uygulamasından).  
  
## <a name="to-list-currently-exposed-interfaces"></a>Şu anda gösterilen arabirimleri listelemek için  
  
- Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/list` .  
  
    ```console  
    ComSvcConfig.exe /list  
    ```  
  
     Bu komut, şu anda kullanıma sunulan arabirimleri ve yerel makine kapsamındaki ilgili adres ve bağlama ayrıntılarını listeler.  
  
## <a name="to-list-specific-currently-exposed-interfaces"></a>Şu anda kullanıma sunulan belirli arabirimleri listelemek için  
  
- Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/list` .  
  
    ```console  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     Bu komut, yerel makinedeki Onlinesbir COM+ uygulaması için ilgili adres ve bağlama ayrıntılarının yanı sıra, şu anda COM+ barındırılan arabirimlerini listeler.  
  
## <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>Yardımcı programıyla kullanılabilecek seçeneklerle ilgili yardım görüntüleme  
  
- /? Kullanarak ComSvcConfig komutunu çalıştırın seçeneğini, aşağıdaki örnekte gösterildiği gibi.  
  
    ```console  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM+ uygulamaları ile tümleştirme genel bakış](integrating-with-com-plus-applications-overview.md)

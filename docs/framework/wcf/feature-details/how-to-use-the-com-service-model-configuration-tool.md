---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: COM+ hizmet modeli yapılandırma aracını kullanma'
title: "Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma"
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 2047604f327cd871629bbdac403e9acd816bbdb1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734093"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma

Uygun bir barındırma modu seçtikten sonra, Web Hizmetleri olarak kullanıma sunulacak uygulama arabirimlerini yapılandırmak için COM+ hizmet modeli yapılandırma komut satırı aracını (ComSvcConfig.exe) kullanın.

> [!NOTE]
> Aşağıdaki görevlerden herhangi birini gerçekleştirmek için makinede yönetici olmanız gerekir.

 Bir Web hizmetini en son hizmet modeli sürümünü (Şu anda v 4.5) kullanacak şekilde yapılandırmak için bir Windows 7 makinesinde ComSvcConfig.exe kullanırken, aşağıdaki adımları gerçekleştirin:

1. Kayıt defteri anahtarını  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` 0x00000001 DWORD değerine ayarlayın

2. comsvcconfig.exe Çalıştır

3. Adım 1 ' de eklenen kayıt defteri anahtarını özgün değerine geri dönün veya yoksa silin.

> [!IMPORTANT]
> Bu kayıt defteri anahtarının geri döndürülmesi önemlidir. Bu bir uyumluluk anahtarıdır. Bu değişikliğin geri döndürülmesi, makinede çalışan diğer .NET uygulamalarıyla ilgili sorunlara neden olabilir).

> [!WARNING]
> Bir Windows 8 makinesinde ComSvcConfig.exe/install kullanırken, ".NET Framework 3,5 yüklenmemişse," bilgisayarınızdaki bir uygulamanın şu Windows özelliğine ihtiyacı vardır: .NET Framework 3,5 (.NET 2,0 ve .NET 3,0 içerir) iletişim kutusu görüntülenir. Bu iletişim kutusu yoksayılabilir. Alternatif olarak, OnlyUseLatestCLR kayıt defteri anahtarını 0x00000001 DWORD değerine bağlayabilirsiniz.

## <a name="add-an-interface-using-the-com-hosting-mode"></a>COM+ barındırma modunu kullanarak arabirim ekleme

- `/install`Aşağıdaki örnekte gösterildiği gibi, ve seçeneklerini kullanarak ComSvcConfig komutunu çalıştırın `/hosting:complus` .

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose
    ```

     Komut, `IFinances` `ItemOrders.IFinancial` bileşen arabirimini (ONLINESBIR com+ uygulamasından) Web Hizmetleri olarak kullanıma sunulacak arabirimler kümesine ekler. Hizmet COM+ barındırma modunu kullanır ve bu nedenle açık uygulama etkinleştirmesi gerektirir.

     \*Bir Web hizmeti olarak yalnızca seçili işlevselliği göstermek isteyebileceğiniz için, joker karakter yıldız () karakteri bileşen ve arabirim için kullanılabilir ancak kullanmaktan kaçının. Bu bileşenin gelecek bir sürümüyle çalıştırırsanız, joker karakteri kullanmak, yapılandırma sözdizimi belirleniyorsa, yanlışlıkla mevcut olmayan arabirimler sunabilir.

     /Verbose seçeneği, aracının hatalara ek olarak uyarıları görüntülemesini sağlar.

     Gösterilen hizmet sözleşmesi, arabirimdeki tüm yöntemleri içerir `IFinances` .

## <a name="add-specific-methods-from-an-interface-using-the-com-hosting-mode"></a>COM+ barındırma modunu kullanarak bir arabirimden belirli yöntemler ekleme

- `/install` `/hosting:complus` Aşağıdaki örnekte gösterildiği gibi, gerekli yöntemlerin açık adlandırması ile ve seçeneklerini kullanarak ComSvcConfig komutunu çalıştırın.

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose
    ```

     Komutu, `Credit` `Debit` `IFinances` sunulan hizmet sözleşmesine yalnızca işlemler olarak arabirimden ve yöntemlerini ekler. Arabirimdeki diğer tüm yöntemler sözleşmede atlanacak ve Web hizmeti istemcilerinden çağrılabilir olmayacaktır.

## <a name="add-an-interface-using-the-web-hosting-mode"></a>Web barındırma modunu kullanarak arabirim ekleme

- `/install`Aşağıdaki örnekte gösterildiği gibi seçeneğini ve seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/hosting:was` .

    ```console
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose
    ```

     Bu komut, `IStockLevels` `ItemInventory.Warehouse` bileşeni bileşenini (OnlineWarehouse com+ uygulamasından) Web Hizmetleri olarak kullanıma sunulacak arabirim kümesine ekler. Hizmet, COM+ yerine IIS 'nin OnlineWarehouse sanal dizininde barındırılır ve bu nedenle uygulama gerektiği şekilde otomatik olarak etkinleştirilir.

     Web 'de barındırılan işlem içi yapılandırmayı kullanmak için COM+ uygulaması, Bileşen Hizmetleri yönetim konsolunu kullanarak bir sunucu uygulaması yerine bir kitaplık uygulaması olarak çalışacak şekilde yapılandırılmalıdır. Sunucu uygulamaları olarak yapılandırılan uygulamalar, standart Web 'de barındırılan modu kullanır ve her isteği işlemek için bir işlem atlaması sağlar.

     `/mex`Seçeneği, hizmetten bir sözleşme tanımı almak isteyen istemcileri desteklemek için uygulamanın hizmet uç noktasıyla aynı aktarımı kullanan bir ek meta veri değişimi (MEX) hizmet uç noktası ekler.

## <a name="remove-a-web-service-for-a-specified-interface"></a>Belirtilen arabirim için bir Web hizmetini kaldır

- Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/uninstall` .

    ```console
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus
    ```

     Komut, `IFinances` Bileşen üzerindeki arabirimini kaldırır `ItemOrders.Financial` (onlines, com+ uygulamasından).

## <a name="list-currently-exposed-interfaces"></a>Şu anda gösterilen arabirimleri Listele

- Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/list` .

    ```console
    ComSvcConfig.exe /list
    ```

     Bu komut, şu anda kullanıma sunulan arabirimleri ve yerel makine kapsamındaki ilgili adres ve bağlama ayrıntılarını listeler.

## <a name="list-specific-currently-exposed-interfaces"></a>Şu anda kullanıma sunulan belirli arabirimleri listeleyin

- Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/list` .

    ```console
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus
    ```

     Bu komut, yerel makinedeki Onlinesbir COM+ uygulaması için ilgili adres ve bağlama ayrıntılarının yanı sıra, şu anda COM+ barındırılan arabirimlerini listeler.

## <a name="display-help-for-options"></a>Seçenekler için yardımı görüntüle

- /? Kullanarak ComSvcConfig komutunu çalıştırın seçeneğini, aşağıdaki örnekte gösterildiği gibi.

    ```console
    ComSvcConfig.exe /?
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [COM+ uygulamaları ile tümleştirme genel bakış](integrating-with-com-plus-applications-overview.md)

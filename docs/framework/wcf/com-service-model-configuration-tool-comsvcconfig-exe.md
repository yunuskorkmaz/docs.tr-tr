---
title: "COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 322268f5b11a5078545ae120440f91d327d6a615
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)
COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe), Web Hizmetleri olarak açığa çıkarılması COM + arabirimleri yapılandırmanıza olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  ComSvcConfig.exe kullanmak için yerel bilgisayarda yönetici olması gerekir.  
  
 Aracı şu konumda bulunabilir.  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows iletişim Foundation\  
  
 ComSvcConfig.exe hakkında daha fazla bilgi için bkz: [nasıl yapılır: COM + hizmet modeli yapılandırma aracını kullanma](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilen modları açıklanır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`install`|Arabirimin bir COM + hizmet modeli tümleştirmesi için yapılandırma yükler.<br /><br /> Kısa form `/i`.|  
|`uninstall`|COM + arabirimi için bir yapılandırma hizmet modeli entegrasyonunu kaldırır.<br /><br /> Kısa form `/u`.|  
|`list`|COM + uygulamaları ve hizmet modeli tümleştirmesi için yapılandırılmış arabirimine sahip bileşenleri hakkında bilgileri listeler.<br /><br /> Kısa form `/l`.|  
  
 Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilir bayrakları açıklanmaktadır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/application:`\< *ApplicationId* &#124; *ApplicationName*\>|Yapılandırmak için COM + uygulamasını belirtir.<br /><br /> Kısa form `/a`.|  
|`/contract:`\< *ClassID* &#124; *ProgID* &#124; \*,*InterfaceId* &#124; *InterfaceName* &#124;\*\>|COM + bileşeni ve hizmet sözleşmesini olarak yapılandırılacak arabirimi belirtir.<br /><br /> Kısa form `/c`.<br /><br /> While joker karakter (\*) bileşeni ve arabirim adlarını belirttiğinizde kullanılabilir, istemediğiniz arabirimleri doğurabilir, kullanmamanızı öneririz.|  
|`/hosting:`\< *complus* &#124; *edildi*\>|COM + modu veya Web barındırma modu barındırma kullanılıp kullanılmayacağını belirtir.<br /><br /> Kısa form `/h`.<br /><br /> COM + kullanma modu barındırma COM + uygulamasının açık etkinleştirme gerektirir. Web barındırma modu otomatik olarak etkinleştirilecek COM + uygulaması verir kullanarak gerekli. COM + uygulaması bir kitaplık uygulaması varsa, Internet Information Services (IIS) işleminde çalışır. COM + uygulaması bir sunucu uygulaması ise, Dllhost.exe işleminde çalışır.|  
|`/webSite:`\< *WebsiteName*\>|Ne zaman modu barındırma Web barındırma için Web sitesi kullanılır belirtir (bkz `/hosting` bayrağı).<br /><br /> Kısa form `/w`.<br /><br /> Web sitesi belirtilmezse, varsayılan Web sitesi kullanılır.|  
|`/webDirectory:`\< *WebDirectoryName*\>|Web barındırma kullanıldığında barındırmak için sanal dizini belirtir (bkz `/hosting` bayrağı).<br /><br /> Kısa form `/d`.|  
|`/mex`|Bir sözleşme tanımı hizmetinden almak istediğiniz istemcileri desteklemek için varsayılan hizmet yapılandırması için bir meta veri değişimi (MEX) Hizmeti uç noktası ekler.<br /><br /> Kısa form `/x`.|  
|`/id`|Uygulama bileşeni ve arabirim bilgilerini kimlikleri olarak görüntüler.<br /><br /> Kısa form `/k`.|  
|`/nologo`|ComSvcConfig.exe kendi logo görüntülemesini engeller.<br /><br /> Kısa form `/n`.|  
|`/verbose`|Tüm uyarı veya bilgilendirme metin karşılaşılan hataları yanı sıra çıkarır.<br /><br /> Kısa form `/v`.|  
|`/help`|Kullanım iletisini görüntüler.<br /><br /> Kısa form `/?`.|  
|`/partial`|Belirtilen arabirim kullanıma sunulabilecek bir veya daha fazla yöntem imzaları içerdiğinde bir hizmet yapılandırması oluşturur. Hizmeti başlatma sırasında uyumlu yöntemlerini hizmet sözleşmesi işlemler olarak görünür ve uyumlu olmayan yöntemleri göz ardı edilir ve hizmet sözleşmeden yok.<br /><br /> Bu bayrak eksikse, belirtilen arabirimi bir veya daha fazla uyumsuz yöntemleri içerdiğinde aracı bir hizmet yapılandırması oluşturmaz.|  
  
## <a name="examples"></a>Örnekler  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, `IFinances` arabiriminin `ItemOrders.IFinancial` bileşeninden (OnlineStore COM + uygulaması) COM + barındırma modunu kullanarak Web hizmetleri sunulan arabirimleri kümesi için. Tüm uyarıları karşılaşılan hataları yanı sıra çıkarır.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, `IStockLevels` arabiriminin `ItemInventory.Warehouse` bileşeninden (OnlineWarehouse COM + uygulaması) Web modu barındırma kullanarak Web hizmetleri sunulan arabirimleri kümesi için. IIS OnlineWarehouse sanal dizinde Web barındırılan Web hizmetidir.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kaldırır `IFinances` arabiriminin `ItemOrders.Financial` bileşeninden (OnlineStore COM + uygulaması) Web Hizmetleri olarak sunulan arabirimleri kümesi.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek listeler, COM + barındırılan arabirimi, yerel makinede OnlineStore COM + uygulaması için bağlama ayrıntıları ve karşılık gelen adresi ile şu anda açık.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: COM + hizmet modeli yapılandırma aracını kullanın](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)

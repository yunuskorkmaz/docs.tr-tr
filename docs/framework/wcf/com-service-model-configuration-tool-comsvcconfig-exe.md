---
title: COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 6d0967355e64640e0fd5c81f04a5bf4f33c7b3f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158671"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)
COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe) Web Hizmetleri olarak açığa COM arabirimleri yapılandırmanızı sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  ComSvcConfig.exe kullanmak için yerel bilgisayarda yönetici olması gerekir.  
  
 Aracı şu konumda bulunabilir.  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
 ComSvcConfig.exe hakkında daha fazla bilgi için bkz: [nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilen modları açıklanmaktadır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`install`|Yapılandırma hizmet modeli tümleştirme için bir COM + arabirimini yükler.<br /><br /> Kısa form `/i`.|  
|`uninstall`|Bir COM arabirimi için bir yapılandırma hizmet modeli tümleştirmeden kaldırır.<br /><br /> Kısa form `/u`.|  
|`list`|COM + uygulamaları ve hizmet modeli tümleştirmesi için yapılandırılmış arabirimlere sahip bileşenler hakkında bilgi listeler.<br /><br /> Kısa form `/l`.|  
  
 Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilecek bayrakları açıklanmaktadır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/application:` \<*ApplicationID* &#124; *ApplicationName*\>|Yapılandırmak için COM + uygulamasını belirtir.<br /><br /> Kısa form `/a`.|  
|`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\>|Hizmet sözleşmesini olarak yapılandırılacak arabirimi ve COM + bileşeni belirtir.<br /><br /> Kısa form `/c`.<br /><br /> While joker karakter (\*) bileşeni ve arabirim adı belirttiğinizde kullanılabilir siz istediniz olmayan arabirimleri sunabileceğinize olduğundan, kullanmamanızı öneririz.|  
|`/hosting:` \<*complus*  &#124; *was*\>|COM + modunda veya Web barındırma modunda barındırma kullanılıp kullanılmayacağını belirtir.<br /><br /> Kısa form `/h`.<br /><br /> COM + kullanarak modu barındırma, COM + uygulamasının açık etkinleştirme gerektirir. Barındırma mod, otomatik olarak etkinleştirilecek COM + uygulaması sağlar. Web kullanarak gereklidir. COM + uygulaması bir kitaplık uygulaması ise, Internet Information Services (IIS) işleminde çalışır. Sunucu uygulaması COM + uygulamasını Dllhost.exe işleminde çalışır.|  
|`/webSite:` \<*WebsiteName*\>|Web sitesi, ne zaman modu barındırma Web barındırma için kullanılan belirtir (bkz `/hosting` bayrağı).<br /><br /> Kısa form `/w`.<br /><br /> Web sitesi belirtilmezse, varsayılan Web sitesi kullanılır.|  
|`/webDirectory:` \<*WebDirectoryName*\>|Web barındırma kullanıldığında barındırmak için sanal dizin belirtir (bkz `/hosting` bayrağı).<br /><br /> Kısa form `/d`.|  
|`/mex`|Meta veri değişimi (MEX) hizmet uç noktası, hizmetten bir sözleşme tanımı almak istediğiniz istemcileri desteklemek için varsayılan hizmet yapılandırması ekler.<br /><br /> Kısa form `/x`.|  
|`/id`|Uygulama, bileşen ve arabirim bilgilerini kimlikleri görüntüler.<br /><br /> Kısa form `/k`.|  
|`/nologo`|ComSvcConfig.exe kendi logosu görüntülenmesini engeller.<br /><br /> Kısa form `/n`.|  
|`/verbose`|Tüm uyarıları veya bilgilendirici metin karşılaşılan hataları yanı sıra çıkarır.<br /><br /> Kısa form `/v`.|  
|`/help`|Kullanım iletisini görüntüler.<br /><br /> Kısa form `/?`.|  
|`/partial`|Belirtilen arabirim kullanıma sunulabilecek bir veya daha fazla yöntem imzaları içeren bir hizmet yapılandırması oluşturur. Hizmet başlatma zaman uyumlu yöntemleri hizmet sözleşmesi işlemleri olarak görünür ve uyumlu olmayan yöntemleri göz ardı edilir ve hizmet sözleşme yok.<br /><br /> Bu bayrak yoksa, belirtilen arabirim bir veya daha fazla uyumsuz yöntemleri içerdiğinde aracı bir hizmet yapılandırması oluşturmaz.|  
  
## <a name="examples"></a>Örnekler  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek ekler `IFinances` arabiriminin `ItemOrders.IFinancial` bileşeninden (OnlineStore COM + uygulaması) COM + barındırma modunu kullanarak Web Hizmetleri olarak sunulan arabirimler dizi. Tüm uyarıları karşılaşılan hataları yanı sıra çıkarır.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek ekler `IStockLevels` arabiriminin `ItemInventory.Warehouse` Web barındırma modu kullanarak Web Hizmetleri olarak sunulan arabirimler kümesine (OnlineWarehouse COM + uygulaması) bileşeni. IIS OnlineWarehouse sanal dizine Web barındırılan Web hizmetidir.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kaldırır `IFinances` arabiriminin `ItemOrders.Financial` Web Hizmetleri olarak sunulan arabirimler kümesinden (OnlineStore COM + uygulaması) bileşeni.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte liste, COM + barındırılan arabirimi, yerel makinede OnlineStore COM + uygulaması bağlama ayrıntıları ve karşılık gelen adresi ile şu anda açık.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)

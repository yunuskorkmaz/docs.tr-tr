---
title: Paylaşılan Web Barındırma için İyileştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: affdbb357cac14f258822591c3817c93ce6077f8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915909"
---
# <a name="optimization-for-shared-web-hosting"></a>Paylaşılan Web Barındırma için İyileştirme
Birkaç küçük Web sitesini barındırarak paylaşılan bir sunucunun yöneticisiyseniz, .net 'teki Aspnet. config dosyasındaki `gcTrimCommitOnLowMemory` `runtime` düğümüne aşağıdaki ayarı ekleyerek performansı iyileştirir ve site kapasitesini artırabilirsiniz. dizinden  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> Bu ayar yalnızca paylaşılan web barındırma senaryolarında önerilir.  
  
 Çöp toplayıcı gelecek ayırmalar için belleği koruduğundan, onun ayrılan alanı kesinlikle gerekenden daha fazla olabilir. Sistem belleğinde ağır bir yük olduğunda bu alanı azaltabilirsiniz. Bu ayrılan alanın azaltılması performansı iyileştirir ve daha fazla siteyi barındırmak için kapasiteyi genişletir.  
  
 `gcTrimCommitOnLowMemory` Ayar etkinleştirildiğinde, çöp toplayıcı sistem belleği yükünü değerlendirir ve yük% 90 ' a ulaştığında bir kırpma modu girer. Yük% 85 altına düşene kadar kırpma modunu korur.  
  
 Koşulların izin vermesi durumunda çöp toplayıcı, `gcTrimCommitOnLowMemory` ayarın geçerli uygulamayı ve yok saymasını sağlamamasına karar verebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML parçası, `gcTrimCommitOnLowMemory` ayarı nasıl etkinleştireceğinizi gösterir. Üç nokta, `runtime` düğümde yer alan diğer ayarları gösterir.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)

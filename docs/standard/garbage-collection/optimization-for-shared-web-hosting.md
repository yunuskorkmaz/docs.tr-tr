---
description: 'Daha fazla bilgi edinin: Paylaşılan Web barındırma için Iyileştirme'
title: Paylaşılan Web Barındırma için İyileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 80627aba90825fe08f891672da4d598edb6f5686
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782448"
---
# <a name="optimization-for-shared-web-hosting"></a>Paylaşılan Web Barındırma için İyileştirme

Birkaç küçük Web sitesini barındırarak paylaşılan bir sunucunun yöneticisiyseniz, `gcTrimCommitOnLowMemory` `runtime` .net dizinindeki Aspnet.config dosyasındaki düğümüne aşağıdaki ayarı ekleyerek performansı iyileştirir ve site kapasitesini artırabilirsiniz:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> Bu ayar yalnızca paylaşılan web barındırma senaryolarında önerilir.  
  
 Çöp toplayıcı gelecek ayırmalar için belleği koruduğundan, onun ayrılan alanı kesinlikle gerekenden daha fazla olabilir. Sistem belleğinde ağır bir yük olduğunda bu alanı azaltabilirsiniz. Bu ayrılan alanın azaltılması performansı iyileştirir ve daha fazla siteyi barındırmak için kapasiteyi genişletir.  
  
 `gcTrimCommitOnLowMemory`Ayar etkinleştirildiğinde, çöp toplayıcı sistem belleği yükünü değerlendirir ve yük %90 ' a ulaştığında bir kırpma modu girer. Yük %85 altına düşene kadar kırpma modunu korur.  
  
 Koşulların izin vermesi durumunda çöp toplayıcı, `gcTrimCommitOnLowMemory` ayarın geçerli uygulamayı ve yok saymasını sağlamamasına karar verebilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki XML parçası, ayarı nasıl etkinleştireceğinizi gösterir `gcTrimCommitOnLowMemory` . Üç nokta, düğümde yer alan diğer ayarları gösterir `runtime` .  
  
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

- [Çöp toplama](index.md)

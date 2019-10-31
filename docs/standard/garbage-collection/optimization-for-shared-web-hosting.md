---
title: Paylaşılan Web Barındırma için İyileştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 07a100e2cd6aaff2b54b99144c9d762c8979fb47
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140275"
---
# <a name="optimization-for-shared-web-hosting"></a>Paylaşılan Web Barındırma için İyileştirme
Birkaç küçük Web sitesini barındırmakla paylaşılan bir sunucunun yöneticisiyseniz, .NET dizinindeki Aspnet. config dosyasındaki `runtime` düğümüne aşağıdaki `gcTrimCommitOnLowMemory` ayarını ekleyerek performansı iyileştirir ve site kapasitesini artırabilirsiniz. :  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> Bu ayar yalnızca paylaşılan web barındırma senaryolarında önerilir.  
  
 Çöp toplayıcı gelecek ayırmalar için belleği koruduğundan, onun ayrılan alanı kesinlikle gerekenden daha fazla olabilir. Sistem belleğinde ağır bir yük olduğunda bu alanı azaltabilirsiniz. Bu ayrılan alanın azaltılması performansı iyileştirir ve daha fazla siteyi barındırmak için kapasiteyi genişletir.  
  
 `gcTrimCommitOnLowMemory` ayarı etkinleştirildiğinde, atık Toplayıcısı sistem belleği yükünü değerlendirir ve yük %90 ' a ulaştığında bir kırpma modu girer. Yük %85 altına düşene kadar kırpma modunu korur.  
  
 Koşulların izin vermesi durumunda çöp toplayıcı, `gcTrimCommitOnLowMemory` ayarının geçerli uygulamayı ve yok saymasını sağlamamasına karar verebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML parçasında `gcTrimCommitOnLowMemory` ayarının nasıl etkinleştirileceği gösterilmektedir. Üç nokta, `runtime` düğümünde olacak diğer ayarları gösterir.  
  
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

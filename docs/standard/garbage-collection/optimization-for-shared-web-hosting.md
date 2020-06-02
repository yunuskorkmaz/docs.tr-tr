---
title: Paylaşılan Web Barındırma için İyileştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: ccaacd44f8aaed9c3178cb94f98b0f58d4d3c7d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285995"
---
# <a name="optimization-for-shared-web-hosting"></a>Paylaşılan Web Barındırma için İyileştirme
Birkaç küçük Web sitesini barındırarak paylaşılan bir sunucunun yöneticisiyseniz, `gcTrimCommitOnLowMemory` `runtime` .NET dizinindeki Aspnet. config dosyasındaki düğümüne aşağıdaki ayarı ekleyerek performansı iyileştirir ve site kapasitesini artırabilirsiniz:  
  
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

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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140275"
---
# <a name="optimization-for-shared-web-hosting"></a>Paylaşılan Web Barındırma için İyileştirme
Birkaç küçük Web sitesini barındırarak paylaşılan bir sunucunun yöneticisiyseniz, .NET dizinindeki Aspnet.config dosyasındaki `gcTrimCommitOnLowMemory` `runtime` düğüme aşağıdaki ayarı ekleyerek performansı en iyi duruma getirebilir ve site kapasitesini artırabilirsiniz:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> Bu ayar yalnızca paylaşılan Web barındırma senaryoları için önerilir.  
  
 Çöp toplayıcı gelecekteki ayırmalar için bellek sakladığından, taahhüt edilen alanı kesinlikle gerekenden daha fazla olabilir. Sistem belleğinde ağır bir yük olduğu zamanları karşılamak için bu alanı azaltabilirsiniz. Bu taahhüt edilen alanı azaltmak performansı artırır ve daha fazla siteyi barındırma kapasitesini artırır.  
  
 `gcTrimCommitOnLowMemory` Ayar etkinleştirildiğinde, çöp toplayıcı sistem bellek yükünü değerlendirir ve yük %90'a ulaştığında bir kırpma moduna girer. Yük %85'in altına düşene kadar kesme modunu korur.  
  
 Koşullar izin verdiğinde, çöp toplayıcı `gcTrimCommitOnLowMemory` ayarın geçerli uygulamaya yardımcı olmadığına karar verebilir ve bunu yoksayabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML parçası `gcTrimCommitOnLowMemory` ayarı nasıl etkinleştirecek lerini gösterir. Elipsler `runtime` düğümde olacak diğer ayarları gösterir.  
  
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

- [Çöp Toplama](../../../docs/standard/garbage-collection/index.md)

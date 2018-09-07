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
ms.openlocfilehash: 7831e383a3048523909b79ac5a4706f3c1c48371
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066704"
---
# <a name="optimization-for-shared-web-hosting"></a>Paylaşılan Web Barındırma için İyileştirme
Birkaç küçük Web sitesi barındırma tarafından paylaşılan bir sunucu yöneticisiyseniz performansı iyileştirmek ve aşağıdakileri ekleyerek site kapasitesini artırmak `gcTrimCommitOnLowMemory` ayarını `runtime` .NET Aspnet.config dosyasında düğümü dizini:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  Bu ayar, yalnızca paylaşılan Web barındırma senaryolarında önerilir.  
  
 Çöp toplayıcı belleği gelecekteki ayırmalar için koruyacağından, onun kaydedilmiş alan birden çok kesinlikle gerekli olabilir. Saatleri gerçekleştirmek için bu alan azaltabilir sistem belleği üzerinde ağır bir yük olduğunda. Bu taahhüt alanını azaltma, performansı geliştirir ve daha fazla siteyi barındırma kapasitesi genişletir.  
  
 Zaman `gcTrimCommitOnLowMemory` ayarı etkinse, çöp toplayıcı sistem bellek yükü değerlendirir ve yük % 90'ını ulaştığında bir kesme moduna girer. Yük altında % 85'lik düşene kadar kesme modu tutar.  
  
 Koşullar izin, çöp toplayıcı, karar verebilirsiniz `gcTrimCommitOnLowMemory` ayar değil geçerli uygulamanın yardımcı olmak ve onu yok sayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML parçası nasıl etkinleştirileceğini göstermektedir `gcTrimCommitOnLowMemory` ayarı. Üç nokta içinde olabilecek diğer ayarları belirtmek `runtime` düğümü.  
  
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

---
title: "Paylaşılan Web Barındırma için İyileştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7525ca263449da77b4b6364fd6bcfd51dcba145d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="optimization-for-shared-web-hosting"></a>Paylaşılan Web Barındırma için İyileştirme
Birkaç küçük Web sitesi barındırma tarafından paylaşılan bir sunucu yöneticisiyseniz, performansı iyileştirmek ve aşağıdakileri ekleyerek site kapasitesini artırmak `gcTrimCommitOnLowMemory` ayarını `runtime` .NET Aspnet.config dosyasında düğümü dizini:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  Bu ayar, yalnızca paylaşılan Web barındırma senaryolarında önerilir.  
  
 Çöp toplayıcı gelecekteki ayırmaları için bellek koruyacağından, kaydedilmiş alan birden çok kesinlikle gerekli olabilir. Kez yerleştirmek için bu alanı azaltabilir sistem belleği üzerinde ağır bir yük olduğunda. Bu kaydedilmiş alanını azaltma performansını artırır ve daha fazla siteleri barındırmak için kapasite genişletir.  
  
 Zaman `gcTrimCommitOnLowMemory` ayarı etkinleştirildiğinde, atık toplayıcı sistem bellek yükü değerlendirir ve yük % 90 ulaştığında kırpma moduna girer. % 85 yük altında düşene kadar kırpma modunu korur.  
  
 Koşullar izin, atık toplayıcı, karar verebilirsiniz `gcTrimCommitOnLowMemory` ayarı değil geçerli uygulama Yardımı ve yok sayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML parçası nasıl etkinleştirileceği gösterilmiştir `gcTrimCommitOnLowMemory` ayarı. Üç nokta içinde olacak diğer ayarları belirtmek `runtime` düğümü.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Atık Toplama](../../../docs/standard/garbage-collection/index.md)

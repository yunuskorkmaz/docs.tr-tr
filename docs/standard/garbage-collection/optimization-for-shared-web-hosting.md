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
ms.openlocfilehash: c3c979477f0928c9c3d2a393042867c84df33ecf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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

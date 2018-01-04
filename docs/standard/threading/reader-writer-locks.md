---
title: "Okuyucu-Yazıcı Kilitleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d005442ee74b46a0ecb1eaafe214e7190330cfe7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="reader-writer-locks"></a>Okuyucu-Yazıcı Kilitleri
<xref:System.Threading.ReaderWriterLockSlim> Sınıfı bir kaynak eşzamanlı olarak okumak birden çok iş parçacığı sağlar, ancak özel bir kilit için kaynağa yazma için beklenecek bir iş parçacığı gerektirir.  
  
 Kullanabileceğinize bir <xref:System.Threading.ReaderWriterLockSlim> bir paylaşılan kaynağa erişim iş parçacıkları arasında işbirlikçi eşitleme sağlamak için uygulamanızda. Kilitleri alınır <xref:System.Threading.ReaderWriterLockSlim> kendisi.  
  
 Hiçbir iş parçacığı eşitleme mekanizması ile iş parçacığı tarafından sağlanan kilitleme atlama sağlamalısınız gibi <xref:System.Threading.ReaderWriterLockSlim>. Bunu sağlamak için bir paylaşılan kaynağa yalıtan bir sınıf tasarlamak için yoludur. Bu sınıf özel paylaşılan kaynağa erişme ve özel kullanma üyeleri sağlayacak <xref:System.Threading.ReaderWriterLockSlim> eşitleme için. Örneğin, kod örneğine bakın <xref:System.Threading.ReaderWriterLockSlim> sınıfı. <xref:System.Threading.ReaderWriterLockSlim>ayrı ayrı nesneleri eşitlemek için kullanılacak verimli olur.  
  
 Uygulamanızın Okuma süresini en aza indirmek ve yazma işlemleri yapılandırın. Yazma kilidi özel olduğundan uzun yazma işlemleri işleme doğrudan etkiler. Uzun işlemleri blok bekleme yazıcılarının okuma ve yazma erişimi için en az bir iş parçacığı bekliyorsa okuma erişimi isteği iş parçacığı de engellenir.  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] İki Okuyucu-Yazıcı kilitleri sahip <xref:System.Threading.ReaderWriterLockSlim> ve <xref:System.Threading.ReaderWriterLock>. <xref:System.Threading.ReaderWriterLockSlim>tüm yeni geliştirme projeleri için önerilir. <xref:System.Threading.ReaderWriterLockSlim>benzer <xref:System.Threading.ReaderWriterLock>, ancak kurallar ve yükseltme ve kilitleme durumu eski sürüme düşürmeyi özyineleme için basitleştirilmiştir. <xref:System.Threading.ReaderWriterLockSlim>olası kilitlenme birçok örneklerini önler. Ayrıca, performansını <xref:System.Threading.ReaderWriterLockSlim> daha önemli ölçüde iyidir <xref:System.Threading.ReaderWriterLock>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)

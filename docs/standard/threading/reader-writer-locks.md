---
title: Okuyucu-Yazıcı Kilitleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8be9b4eef30333fbbdc26915635d17157176d6fc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079194"
---
# <a name="reader-writer-locks"></a>Okuyucu-Yazıcı Kilitleri
<xref:System.Threading.ReaderWriterLockSlim> Sınıfı için bir kaynak eş zamanlı olarak okumak birden çok iş parçacığı sağlar, ancak bu kaynağa yazmak üzere özel bir kilit için beklenecek bir iş parçacığı gerektirir.  
  
 Kullanabileceğinize bir <xref:System.Threading.ReaderWriterLockSlim> uygulamanızda paylaşılan bir kaynağa erişmeye iş parçacıkları arasında işbirliği halinde eşitleme sağlar. Kilitleri alınır <xref:System.Threading.ReaderWriterLockSlim> kendisi.  
  
 Tüm iş parçacığı eşitleme mekanizması ile iş parçacığı tarafından sağlanan kilitleme atlama sağlamalısınız gibi <xref:System.Threading.ReaderWriterLockSlim>. Bunu sağlamak için bir paylaşılan kaynağı kapsülleyen bir sınıf tasarlamak için yoludur. Bu sınıf üyeleri özel paylaşılan kaynağa erişmek ve özel kullanan sağlayacağını <xref:System.Threading.ReaderWriterLockSlim> eşitleme. Örneğin, kod örneği için bkz. <xref:System.Threading.ReaderWriterLockSlim> sınıfı. <xref:System.Threading.ReaderWriterLockSlim> ayrı ayrı nesneleri eşitlemek için kullanılacak verimli olur.  
  
 Okuma süresi en aza indirmek ve yazma işlemleri için uygulamanızı yapılandırın. Özel bir yazma kilidi olduğundan uzun yazma işlemleri aktarım hızı doğrudan etkiler. Uzun işlemler blok bekleme yazıcılar okuyun ve yazma erişimi için en az bir iş parçacığı bekliyorsa, okuma erişimi gerektiren iş parçacıkları de engellenir.  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] İki Okuyucu-Yazıcı kilitleri sahip <xref:System.Threading.ReaderWriterLockSlim> ve <xref:System.Threading.ReaderWriterLock>. <xref:System.Threading.ReaderWriterLockSlim> tüm yeni geliştirme projeleri için tavsiye edilir. <xref:System.Threading.ReaderWriterLockSlim> benzer <xref:System.Threading.ReaderWriterLock>, ancak kuralları ve yükseltme ve kilitleme durumu eski sürüme düşürme özyineleme için basitleştirilmiştir. <xref:System.Threading.ReaderWriterLockSlim> Çoğu durumda, olası kilitlenme önler. Ayrıca, performansı <xref:System.Threading.ReaderWriterLockSlim> önemli ölçüde daha iyidir <xref:System.Threading.ReaderWriterLock>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ReaderWriterLockSlim>  
- <xref:System.Threading.ReaderWriterLock>  
- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)

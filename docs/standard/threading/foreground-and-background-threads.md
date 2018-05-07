---
title: Ön Plan ve Arka Plan İş Parçacıklarını Seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 476dc75a569224db405eb7498ecb35eb6bda24d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="foreground-and-background-threads"></a>Ön Plan ve Arka Plan İş Parçacıklarını Seçme
Yönetilen iş parçacığı, arka plan iş parçacığı ya da bir ön plan iş parçacığı değil. Arka plan iş parçacıkları bir özel durumla ön plan iş parçacıkları aynı: arka plan iş parçacığı çalıştıran yönetilen yürütme ortamını korumaz. Tüm ön plan iş parçacıkları (.exe dosyası bir yönetilen derlemesi olduğu) yönetilen bir işlemde durdurulan sonra sistem tüm arka plan iş parçacıkları durdurur ve kapanır.  
  
> [!NOTE]
>  Çalışma zamanı işlem kapanmakta olduğundan bir arka plan iş parçacığı durduğunda, iş parçacığı hiçbir özel durum atılır. Ancak, ne zaman iş parçacığı durdurulur çünkü <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi bellekten uygulama etki alanı bir <xref:System.Threading.ThreadAbortException> ön ve arka plan iş parçacığı oluşturulur.  
  
 Kullanım <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> özelliğini bir iş parçacığı bir arka plan ya da bir ön plan iş parçacığı olup olmadığını belirlemek veya durumunu değiştirin. Bir iş parçacığı bir arka plan iş parçacığı için herhangi bir zamanda ayarlayarak değiştirilebilir kendi <xref:System.Threading.Thread.IsBackground%2A> özelliğine `true`.  
  
> [!IMPORTANT]
>  Bir iş parçacığı ön plan veya arka plan durumunu bir iş parçacığı işlenmeyen bir özel durum sonucunu etkilemez. .NET Framework sürüm 2. 0'da, uygulamanın sonlandırılmasıyla ön plan veya arka plan iş parçacığı işlenmeyen bir özel durum oluşur. Bkz: [yönetilen iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Yönetilen iş parçacığı havuzuna ait iş parçacıkları (diğer bir deyişle, iş parçacıkları <xref:System.Threading.Thread.IsThreadPoolThread%2A> özelliği `true`) arka plan iş parçacıkları şunlardır. Yönetilmeyen koddan yönetilen yürütme ortamını girin tüm iş parçacıklarının arka plan iş parçacığı olarak işaretlenir. Oluşturma ve yeni bir başlangıç tarafından oluşturulan tüm iş parçacıklarının <xref:System.Threading.Thread> nesne olan varsayılan ön plan iş parçacıkları tarafından.  
  
 Bir yuva bağlantısı gibi bir etkinliğini izlemek için bir iş parçacığı kullanırsanız ayarlamanız kendi <xref:System.Threading.Thread.IsBackground%2A> özelliğine `true` böylece iş parçacığı işleminizin sonlandırılıyor gelen engellemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>

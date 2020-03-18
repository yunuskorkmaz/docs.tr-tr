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
ms.openlocfilehash: 9e93f07b3b84264373db0317919b6ee519c8127c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138047"
---
# <a name="foreground-and-background-threads"></a>Ön Plan ve Arka Plan İş Parçacıklarını Seçme
Yönetilen iş parçacığı, arka plan iş parçacığı veya ön plan iş parçacığıdır. Arka plan iş parçacıkları, bir istisna dışında ön plan iş parçacıklarıyla aynıdır: arka plan iş parçacığı yönetilen yürütme ortamını çalışır durumda tutmaz. Tüm ön plan iş parçacıkları yönetilen bir işlemde durdurulduktan sonra (.exe dosyasının yönetilen bir derleme olduğu yerde), sistem tüm arka plan iş parçacıklarını durdurur ve kapanır.  
  
> [!NOTE]
> İşlem kapandığı için çalışma zamanı arka plan iş parçacığı durduğunda, iş parçacığına özel bir durum atılmaz. Ancak, <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntem uygulama etki alanını boşalttığı için iş <xref:System.Threading.ThreadAbortException> parçacıkları durdurulduğunda, hem ön plana hem de arka plan iş parçacığına bir a atılır.  
  
 İş <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> parçacığının arka plan mı yoksa ön plan iş parçacığı mı olduğunu belirlemek veya durumunu değiştirmek için özelliği kullanın. Bir iş parçacığı, özelliğini <xref:System.Threading.Thread.IsBackground%2A> . `true`  
  
> [!IMPORTANT]
> Bir iş parçacığının ön plan veya arka plan durumu iş parçacığındaki işlenmemiş bir özel durumun sonucunu etkilemez. .NET Framework sürüm 2.0'da, ön planda veya arka plan iş parçacığında işlenmemiş bir özel durum, uygulamanın sonlandırılmasıyla sonuçlanır. [Yönetilen İş Parçacıklarındaki Özel Durumlara](../../../docs/standard/threading/exceptions-in-managed-threads.md)Bakın.  
  
 Yönetilen iş parçacığı havuzuna ait iş parçacıkları <xref:System.Threading.Thread.IsThreadPoolThread%2A> (diğer `true`bir şekilde, özelliği olan iş parçacıkları) arka plan iş parçacıklarıdır. Yönetilmeyen koddan yönetilen yürütme ortamına giren tüm iş parçacıkları arka plan iş parçacığı olarak işaretlenir. Yeni <xref:System.Threading.Thread> bir nesne oluşturulup başlatılarak oluşturulan tüm iş parçacıkları varsayılan olarak ön plan iş parçacıklarıdır.  
  
 Soket bağlantısı gibi bir etkinliği izlemek için bir iş <xref:System.Threading.Thread.IsBackground%2A> parçacığı `true` kullanıyorsanız, iş parçacığıişleminizin sonlandırmasını engellemeyecek şekilde özelliğini ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>

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
ms.openlocfilehash: 8dbad5da42f5ed4e03751534a3a183615a9757cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960029"
---
# <a name="foreground-and-background-threads"></a>Ön Plan ve Arka Plan İş Parçacıklarını Seçme
Yönetilen iş parçacığı, bir arka plan iş parçacığı veya bir ön plan iş parçacığıdır. Arka plan iş parçacıkları tek bir özel durum içeren ön plan iş parçacıklarıyla aynıdır: arka plan iş parçacığı yönetilen yürütme ortamını çalışır durumda tutar. Yönetilen bir işlemde (. exe dosyasının yönetilen bir derleme olduğu) tüm ön plan iş parçacıkları durdurulduktan sonra, sistem tüm arka plan iş parçacıklarını durduruyor ve kapatır.  
  
> [!NOTE]
> Çalışma zamanı bir arka plan iş parçacığını durdurduğundan, iş parçacığında hiçbir özel durum oluşturulmaz. Ancak, <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> Yöntem uygulama etki alanını kaldırdığından iş parçacıkları durdurulduğunda, hem ön planda <xref:System.Threading.ThreadAbortException> hem de arka plan iş parçacıklarında bir oluşturulur.  
  
 Bir iş parçacığının arka plan veya ön plan iş parçacığı olduğunu veya durumunu değiştirmek için özelliğinikullanın.<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> Bir iş parçacığı, <xref:System.Threading.Thread.IsBackground%2A> özelliği olarak `true`ayarlanarak herhangi bir zamanda arka plan iş parçacığına değiştirilebilir.  
  
> [!IMPORTANT]
> Bir iş parçacığının ön plan veya arka plan durumu, iş parçacığında işlenmeyen bir özel durumun sonucunu etkilemez. .NET Framework sürüm 2,0 ' de, ön planda veya arka plan iş parçacıklarında işlenmeyen bir özel durum uygulamanın sonlandırmasına neden olur. Bkz. [yönetilen Iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Yönetilen iş parçacığı havuzuna ait olan iş parçacıkları (diğer bir deyişle, <xref:System.Threading.Thread.IsThreadPoolThread%2A> `true`özelliği olan iş parçacıkları) arka plan iş parçacığıdır. Yönetilmeyen koddan yönetilen yürütme ortamına giriş yapan tüm iş parçacıkları arka plan iş parçacıkları olarak işaretlenir. Yeni <xref:System.Threading.Thread> bir nesne oluşturup başlattıktan sonra oluşturulan tüm iş parçacıkları varsayılan ön plan iş parçacıklarından oluşur.  
  
 Yuva bağlantısı gibi bir etkinliği izlemek için bir iş parçacığı kullanıyorsanız, iş parçacığının sonlandırmasını önleyememesi <xref:System.Threading.Thread.IsBackground%2A> için `true` özelliğini olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>

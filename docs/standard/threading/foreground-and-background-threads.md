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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138047"
---
# <a name="foreground-and-background-threads"></a>Ön Plan ve Arka Plan İş Parçacıklarını Seçme
Yönetilen iş parçacığı, bir arka plan iş parçacığı veya bir ön plan iş parçacığıdır. Arka plan iş parçacıkları tek bir özel durum içeren ön plan iş parçacıklarıyla aynıdır: arka plan iş parçacığı yönetilen yürütme ortamını çalışır durumda tutar. Yönetilen bir işlemde (. exe dosyasının yönetilen bir derleme olduğu) tüm ön plan iş parçacıkları durdurulduktan sonra, sistem tüm arka plan iş parçacıklarını durduruyor ve kapatır.  
  
> [!NOTE]
> Çalışma zamanı bir arka plan iş parçacığını durdurduğundan, iş parçacığında hiçbir özel durum oluşturulmaz. Ancak, <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi uygulama etki alanını kaldırdığından iş parçacıkları durdurulduğunda, hem ön planda hem de arka plan iş parçacıklarında bir <xref:System.Threading.ThreadAbortException> oluşturulur.  
  
 Bir iş parçacığının arka plan veya ön plan iş parçacığı olduğunu veya durumunu değiştirmek için <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> özelliğini kullanın. Bir iş parçacığı, <xref:System.Threading.Thread.IsBackground%2A> özelliği `true`olarak ayarlanarak herhangi bir zamanda arka plan iş parçacığına değiştirilebilir.  
  
> [!IMPORTANT]
> Bir iş parçacığının ön plan veya arka plan durumu, iş parçacığında işlenmeyen bir özel durumun sonucunu etkilemez. .NET Framework sürüm 2,0 ' de, ön planda veya arka plan iş parçacıklarında işlenmeyen bir özel durum uygulamanın sonlandırmasına neden olur. Bkz. [yönetilen Iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Yönetilen iş parçacığı havuzuna ait olan iş parçacıkları (yani, <xref:System.Threading.Thread.IsThreadPoolThread%2A> özelliği `true`olan iş parçacıkları) arka plan iş parçacığıdır. Yönetilmeyen koddan yönetilen yürütme ortamına giriş yapan tüm iş parçacıkları arka plan iş parçacıkları olarak işaretlenir. Yeni bir <xref:System.Threading.Thread> nesnesi oluşturup başlattıktan sonra oluşturulan tüm iş parçacıkları varsayılan ön plan iş parçacıklarından oluşur.  
  
 Yuva bağlantısı gibi bir etkinliği izlemek için bir iş parçacığı kullanıyorsanız, iş parçacığının işlemin sonlandırılmasını önleyememesi için <xref:System.Threading.Thread.IsBackground%2A> özelliğini `true` olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>

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
ms.openlocfilehash: 5e7ec9e2c2a5ba3de1b4518cea15eb5f512640d3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279691"
---
# <a name="foreground-and-background-threads"></a>Ön Plan ve Arka Plan İş Parçacıklarını Seçme
Yönetilen iş parçacığı, bir arka plan iş parçacığı veya bir ön plan iş parçacığıdır. Arka plan iş parçacıkları tek bir özel durum içeren ön plan iş parçacıklarıyla aynıdır: arka plan iş parçacığı yönetilen yürütme ortamını çalışır durumda tutar. Yönetilen bir işlemde (. exe dosyasının yönetilen bir derleme olduğu) tüm ön plan iş parçacıkları durdurulduktan sonra, sistem tüm arka plan iş parçacıklarını durduruyor ve kapatır.  
  
> [!NOTE]
> Çalışma zamanı bir arka plan iş parçacığını durdurduğundan, iş parçacığında hiçbir özel durum oluşturulmaz. Ancak, yöntem uygulama etki alanını kaldırdığından iş parçacıkları durdurulduğunda, <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> <xref:System.Threading.ThreadAbortException> hem ön planda hem de arka plan iş parçacıklarında bir oluşturulur.  
  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>Bir iş parçacığının arka plan veya ön plan iş parçacığı olduğunu veya durumunu değiştirmek için özelliğini kullanın. Bir iş parçacığı, özelliği olarak ayarlanarak herhangi bir zamanda arka plan iş parçacığına değiştirilebilir <xref:System.Threading.Thread.IsBackground%2A> `true` .  
  
> [!IMPORTANT]
> Bir iş parçacığının ön plan veya arka plan durumu, iş parçacığında işlenmeyen bir özel durumun sonucunu etkilemez. .NET Framework sürüm 2,0 ' de, ön planda veya arka plan iş parçacıklarında işlenmeyen bir özel durum uygulamanın sonlandırmasına neden olur. Bkz. [yönetilen Iş parçacıklarında özel durumlar](exceptions-in-managed-threads.md).  
  
 Yönetilen iş parçacığı havuzuna ait olan iş parçacıkları (diğer bir deyişle, özelliği olan iş parçacıkları <xref:System.Threading.Thread.IsThreadPoolThread%2A> `true` ) arka plan iş parçacığıdır. Yönetilmeyen koddan yönetilen yürütme ortamına giriş yapan tüm iş parçacıkları arka plan iş parçacıkları olarak işaretlenir. Yeni bir nesne oluşturup başlattıktan sonra oluşturulan tüm iş parçacıkları <xref:System.Threading.Thread> varsayılan ön plan iş parçacıklarından oluşur.  
  
 Yuva bağlantısı gibi bir etkinliği izlemek için bir iş parçacığı kullanıyorsanız, <xref:System.Threading.Thread.IsBackground%2A> `true` iş parçacığının sonlandırmasını önleyememesi için özelliğini olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>

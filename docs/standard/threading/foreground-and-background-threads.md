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
ms.openlocfilehash: c6605fa1923dc4fdaf4f12a7c8fc7c1e344673b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925378"
---
# <a name="foreground-and-background-threads"></a>Ön Plan ve Arka Plan İş Parçacıklarını Seçme
Yönetilen iş parçacığı veya bir arka plan iş parçacığı, hem de ön plan iş parçacığı değil. Arka plan iş parçacığı bir özel durumla aynı ön plan iş parçacığı: arka plan iş parçacığı çalıştıran yönetilen yürütme ortamında korumaz. (Burada .exe dosyasını, yönetilen bir derleme adıdır) yönetilen bir işlemde tüm ön plan iş parçacığı üzere durdurduktan sonra sistem tüm arka plan iş parçacığı durdurur ve kapanır.  
  
> [!NOTE]
>  İşlem kapatıldığından, çalışma zamanı arka plan iş parçacığı sona erdiğinde, iş parçacığında hiçbir özel durum oluşturulur. Ancak, iş parçacığı durduruldu çünkü <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi kaldırır uygulama etki alanının bir <xref:System.Threading.ThreadAbortException> ön ve arka plan iş parçacığı oluşturulur.  
  
 Kullanım <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> özelliği bir iş parçacığı bir arka plan ya da bir ön plan iş parçacığı olup olmadığını belirlemek için ya da kendi durumunu değiştirmek için. Bir iş parçacığı bir arka plan iş parçacığı herhangi bir zamanda ayarlayarak değiştirilebilir, <xref:System.Threading.Thread.IsBackground%2A> özelliğini `true`.  
  
> [!IMPORTANT]
>  Bir iş parçacığı durumunu ön plan veya arka plan iş parçacığı işlenmeyen bir özel durum sonucunu etkilemez. .NET Framework sürüm 2. 0'da, uygulamanın sonlandırılmasıyla ön plan veya arka plan iş parçacığı işlenmeyen bir özel durum oluşur. Bkz: [yönetilen iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Yönetilen iş parçacığı havuzuna ait iş parçacıkları (diğer bir deyişle, ayarlanmış iş parçacıkları <xref:System.Threading.Thread.IsThreadPoolThread%2A> özelliği `true`) arka plan iş parçacıklarının. Tüm iş parçacıklarını yönetilmeyen koddan yönetilen yürütme ortamında girdiğiniz arka plan iş parçacığı işaretlenir. Tüm iş parçacıkları oluşturma ve yeni bir başlangıç tarafından oluşturulan <xref:System.Threading.Thread> nesne olan varsayılan ön plan iş parçacıkları tarafından.  
  
 Bir yuva bağlantısı gibi bir etkinliği izlemek için bir iş parçacığı kullanırsanız ayarlayın, <xref:System.Threading.Thread.IsBackground%2A> özelliğini `true` böylece iş parçacığı, işlem sonlandırılıyor gelen engellemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>

---
title: "Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
ms.openlocfilehash: f52a844284cf46bcace3f54f8b320d336050a64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138041"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme
<xref:System.Threading.SpinLock?displayProperty=nameWithType>çok kısa bekleme süreleri olan senaryolar için kullanabileceğiniz düşük düzeyli bir karşılıklı dışlama kilididir. <xref:System.Threading.SpinLock>yeniden giren değildir. Bir iş parçacığı kilidi girdikten sonra, yeniden girebilmeleri için kilidi niçin doğru bir şekilde çıkarması gerekir. Genellikle, kilidi yeniden girmeye yönelik herhangi bir girişim kilitlenmeye neden olur ve kilitlenmeleri hata ayıklamak çok zor olabilir. Geliştirmeye yardımcı olarak, <xref:System.Threading.SpinLock?displayProperty=nameWithType> bir iş parçacığı zaten tuttuğu bir kilidi yeniden girmeye çalıştığında bir özel durum atılmasına neden olan bir iş parçacığı izleme modunu destekler. Bu, kilidin doğru şekilde çıkarılmayan noktayı daha kolay bulmanızı sağlar. Boolean giriş parametresi alan <xref:System.Threading.SpinLock> oluşturucuyu kullanarak ve ''nin `true`bir bağımsız değişkeninde geçerek iş parçacığı izleme modunu açabilirsiniz. Geliştirme ve test aşamalarını tamamladıktan sonra, daha iyi performans için iş parçacığı izleme modunu kapatın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iş parçacığı izleme modunu gösterir. Kilitten doğru çıkan satırlar, aşağıdaki sonuçlardan birine neden olan bir kodlama hatasının benzetimi için yorumlanır:  
  
- (Visual Basic'te) bağımsız değişkeni kullanılarak`True` oluşturulan bir özel durum atılır. <xref:System.Threading.SpinLock> `true`  
  
- Kilitlenme eğer <xref:System.Threading.SpinLock> `false` bir`False` argüman kullanılarak oluşturuldu ( Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SpinLock](../../../docs/standard/threading/spinlock.md)

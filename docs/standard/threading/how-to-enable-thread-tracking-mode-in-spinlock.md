---
description: "Daha fazla bilgi edinin: nasıl yapılır: SpinLock 'ta Thread-Tracking modunu etkinleştirme"
title: "Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
ms.openlocfilehash: 376582c7ccde999bd010753819159f6f8da92bf3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666907"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme

<xref:System.Threading.SpinLock?displayProperty=nameWithType> , çok kısa bekleme süreleriyle ilgili senaryolar için kullanabileceğiniz alt düzey bir karşılıklı dışlama kilidindedir. <xref:System.Threading.SpinLock> yeniden entrant. Bir iş parçacığı kilidi girdikten sonra, yeniden girmeden önce kilidi doğru bir şekilde çıkmalıdır. Genellikle kilidi yeniden girmeye yönelik her türlü girişim kilitlenmeye neden olur ve kilitlenmeleri hata ayıklama için çok zor olabilir. Geliştirmeye yardımcı olarak, <xref:System.Threading.SpinLock?displayProperty=nameWithType> bir iş parçacığı zaten tuttuğu bir kilidi yeniden girmeye çalıştığında bir özel durumun oluşturulmasına neden olan bir iş parçacığı izleme modunu destekler. Bu, kilidin doğru bir şekilde çıkış yapılmadığını daha kolay bir şekilde bulmanızı sağlar. <xref:System.Threading.SpinLock>Bir Boole giriş parametresi alan ve bağımsız değişkenini geçirerek iş parçacığı izleme modunu açabilirsiniz `true` . Geliştirme ve test aşamalarını tamamladıktan sonra, daha iyi performans için iş parçacığı izleme modunu kapatın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, iş parçacığı izleme modunu gösterir. Kilitden doğru çıkış yapan satırlar, aşağıdaki sonuçlardan birine neden olan bir kodlama hatasının benzetimini yapmak için açıklama yapılır:  
  
- <xref:System.Threading.SpinLock> `true` (Visual Basic) bir bağımsız değişkeni kullanılarak oluşturulduysa bir özel durum oluşturulur `True` .  
  
- <xref:System.Threading.SpinLock>Bir bağımsız değişkeni kullanılarak oluşturulduysa `false` ( `False` Visual Basic) kilitlenme.  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SpinLock](spinlock.md)

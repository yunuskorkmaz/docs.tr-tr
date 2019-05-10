---
title: "Nasıl yapılır: Spinlock'ta iş parçacığı izleme modunu etkinleştirme"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 111ab87ca419217f425eb5d4bc9b52f5f30f0237
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644839"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Nasıl yapılır: Spinlock'ta iş parçacığı izleme modunu etkinleştirme
<xref:System.Threading.SpinLock?displayProperty=nameWithType> çok kısa bekleme süresini sahip senaryolar için kullanabileceğiniz bir alt düzey karşılıklı dışlama kilidini olur. <xref:System.Threading.SpinLock> a değil. Bir iş parçacığı kilit girdikten sonra yeniden girmeden önce kilit doğru çıkmak gerekir. Genellikle, her türlü girişim, kilit yeniden girmek için kilitlenmeye neden olabilir ve kilitlenmeler, hata ayıklamak oldukça zor olabilir. Geliştirmeye yardımcı olarak <xref:System.Threading.SpinLock?displayProperty=nameWithType> bir özel bir iş parçacığı zaten tutan bir kilit znovu girişiminde bulunduğunda durum neden olan bir iş parçacığı izleme modunu destekler. Bu, daha kolayca bulun, kilit doğru bir şekilde çıkıldı değil noktası sağlar. İş parçacığı izleme modunu kullanarak açabilirsiniz <xref:System.Threading.SpinLock> bir Boole değeri alan oluşturucu giriş parametresi ve bir bağımsız değişkeninde geçirme `true`. Geliştirme ve test aşamaları tamamladıktan sonra daha iyi performans için iş parçacığı izleme modunu kapatın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iş parçacığı izleme modunu gösterir. Doğru kilit çıkmak satırları aşağıdaki sonuçlardan birini neden olan bir kodlama hatası benzetimini yapmak için dışı bırakılır:  
  
- Bir özel durum <xref:System.Threading.SpinLock> bağımsız değişkeninin kullanılarak oluşturulmuş `true` (`True` Visual Basic'te).  
  
- Kilitlenme <xref:System.Threading.SpinLock> bağımsız değişkeninin kullanılarak oluşturulmuş `false` (`False` Visual Basic'te).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SpinLock](../../../docs/standard/threading/spinlock.md)

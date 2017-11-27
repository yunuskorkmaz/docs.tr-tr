---
title: "Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme
<xref:System.Threading.SpinLock?displayProperty=nameWithType>çok kısa bekleme süresini sahip senaryolar için kullanabileceğiniz bir alt düzey karşılıklı dışlama kilidi var. <xref:System.Threading.SpinLock>içe değil. Bir iş parçacığı kilidi girdikten sonra yeniden girmeden önce kilidi doğru çıkmak gerekir. Genellikle, her türlü girişim kilidi yeniden girmek için kilitlenme neden olur ve kilitlenmeleri hata ayıklamak oldukça zor olabilir. Geliştirme, bir Yardım olarak <xref:System.Threading.SpinLock?displayProperty=nameWithType> bir iş parçacığı zaten tutan bir kilit yeniden girmek çalıştığında durum için bir özel duruma neden olan bir iş parçacığı izleme modunu destekler. Bu, daha kolay hangi kilidi doğru bir şekilde çıkıldı değil noktasını bulun sağlar. İş parçacığı izleme modunu kullanarak bırakabilir <xref:System.Threading.SpinLock> bir Boole değeri alan oluşturucu giriş parametresi ve bağımsız değişkeninin bilgilerinde `true`. İş parçacığı izleme modunu daha iyi performans için geliştirme ve sınama aşaması tamamlandıktan sonra kapatın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iş parçacığı izleme modunu gösterir. Doğru kilit çıkış satırları aşağıdaki sonuçları biri neden olan bir kodlama hatası benzetimini yapmak için dışı bırakılır:  
  
-   Bir özel durum <xref:System.Threading.SpinLock> bağımsız değişkeninin kullanılarak oluşturulmuş `true` (`True` Visual Basic'te).  
  
-   Varsa kilitlenme <xref:System.Threading.SpinLock> bağımsız değişkeninin kullanılarak oluşturulmuş `false` (`False` Visual Basic'te).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SpinLock](../../../docs/standard/threading/spinlock.md)

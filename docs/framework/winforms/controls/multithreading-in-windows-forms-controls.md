---
title: Denetimlerde çoklu iş parçacığı
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: 79832e12a10f02c909d2a28270594bcb4ea68656
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742134"
---
# <a name="multithreading-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Çoklu Kullanım
Birçok uygulamada, başka bir iş parçacığı üzerinde zaman alan işlemler gerçekleştirerek Kullanıcı arabiriminizi (UI) daha hızlı hale getirebilirsiniz. <xref:System.Threading> ad alanı, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi ve `BackgroundWorker` bileşeni de dahil olmak üzere Windows Forms denetimlerinizi çoklu iş parçacıklı bir dizi araç mevcuttur.  
  
> [!NOTE]
> `BackgroundWorker` bileşeni, <xref:System.Threading> ad alanına ve <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemine işlevsellik koyar. Bununla birlikte, bunlar ' ı seçerseniz hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [BackgroundWorker Component Overview](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Windows Forms Denetimlerine İş Parçacığı Güvenli Aramalar Yapma](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Windows Forms denetimlerine iş parçacığı güvenli çağrıların nasıl yapılacağını gösterir.  
  
 [Nasıl Yapılır: Dosya Aramak için Arka Plan İş Parçacığı Kullanma](how-to-use-a-background-thread-to-search-for-files.md)  
 <xref:System.Threading> ad alanını ve <xref:System.Windows.Forms.Control.BeginInvoke%2A> yöntemini zaman uyumsuz olarak aramak için nasıl kullanacağınızı gösterir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ComponentModel.BackgroundWorker>  
 Zaman uyumsuz işlemler için çalışan iş parçacığını kapsülleyen bir bileşeni belgeler.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Bir sesin zaman uyumsuz olarak nasıl yükleneceğini belgeler.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Bir görüntünün zaman uyumsuz olarak nasıl yükleneceğini belgeler.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](how-to-run-an-operation-in-the-background.md)  
 <xref:System.ComponentModel.BackgroundWorker> bileşeniyle zaman alan bir işlemin nasıl gerçekleştirileceğini gösterir.  
  
 [BackgroundWorker Bileşenine Genel Bakış](backgroundworker-component-overview.md)  
 <xref:System.ComponentModel.BackgroundWorker> bileşeninin zaman uyumsuz işlemler için nasıl kullanılacağını betimleyen konular sağlar.

---
title: Windows Forms Denetimlerinde Çoklu Kullanım
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cc7f358a62c8057abb77e1f5a28544bb6c858d98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012730"
---
# <a name="multithreading-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Çoklu Kullanım
Birçok uygulamada, uygulamanızın kullanıcı arabirimini (UI) daha hızlı yanıt veren başka bir iş parçacığı üzerinde harcanan zamanı ortadan kaldırır işlemleri gerçekleştirerek yapabilirsiniz. Araçlar kullanılabilir çoklu iş parçacığı kullanımı dahil olmak üzere, Windows Forms denetimleri <xref:System.Threading> ad alanı, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi ve `BackgroundWorker` bileşeni.  
  
> [!NOTE]
>  `BackgroundWorker` Bileşeni değiştirir ve işlevsellik ekler <xref:System.Threading> ad alanı ve <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi; seçerseniz ancak bu geriye dönük uyumluluk ve gelecekte kullanım için korunur. Daha fazla bilgi için [BackgroundWorker bileşenine genel bakış](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Windows Forms denetimlerine iş parçacığı güvenli aramalar yapın](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Windows Forms denetimlerine iş parçacığı güvenli aramalar yapma gösterilmektedir.  
  
 [Nasıl yapılır: Dosya aramak için bir arka plan iş parçacığı kullanma](how-to-use-a-background-thread-to-search-for-files.md)  
 Nasıl kullanılacağını gösterir <xref:System.Threading> ad alanı ve <xref:System.Windows.Forms.Control.BeginInvoke%2A> dosyaları zaman uyumsuz olarak aramak için yöntemi.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ComponentModel.BackgroundWorker>  
 Zaman uyumsuz işlemleri için iş parçacığı kapsülleyen bir bileşen belgeler.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Zaman uyumsuz ses yükleme konusunda belgelenmiştir.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Bir görüntüyü zaman uyumsuz olarak yükleme konusunda belgelenmiştir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl yapılır: Arka planda işlem çalıştırma](how-to-run-an-operation-in-the-background.md)  
 Uzun süren bir işlem ile yapma işlemi açıklanır <xref:System.ComponentModel.BackgroundWorker> bileşeni.  
  
 [BackgroundWorker Bileşenine Genel Bakış](backgroundworker-component-overview.md)  
 Nasıl kullanılacağını açıklayan konuları sağlar <xref:System.ComponentModel.BackgroundWorker> zaman uyumsuz işlemler için bileşen.

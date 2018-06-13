---
title: Windows Forms Denetimlerinde Çoklu Kullanım
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: 68822c62a1a195ce3128d51c765cfeba2056955d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536363"
---
# <a name="multithreading-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Çoklu Kullanım
Birçok uygulamada, kullanıcı arabirimi (UI) daha iyi yanıt başka bir iş parçacığında zaman işlemleri gerçekleştirerek yapabilirsiniz. Çok sayıda araç kullanılabilir çoklu iş parçacığı kullanımı dahil olmak üzere, Windows Forms denetimleri <xref:System.Threading> ad alanı, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi ve `BackgroundWorker` bileşeni.  
  
> [!NOTE]
>  `BackgroundWorker` Bileşeni değiştirir ve işlevlerini ekler <xref:System.Threading> ad alanı ve <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi; seçerseniz ancak bunlar geriye dönük uyumluluk ve gelecekte kullanım için korunur. Daha fazla bilgi için bkz: [BackgroundWorker bileşenine genel bakış](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Windows Forms Denetimlerine İş Parçacığı Güvenli Aramalar Yapma](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Windows Forms denetimlerine iş parçacığı güvenli aramalar yapma gösterir.  
  
 [Nasıl Yapılır: Dosya Aramak için Arka Plan İş Parçacığı Kullanma](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 Nasıl kullanılacağını gösterir <xref:System.Threading> ad alanı ve <xref:System.Windows.Forms.Control.BeginInvoke%2A> dosyaları zaman uyumsuz olarak aramak için yöntem.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ComponentModel.BackgroundWorker>  
 Zaman uyumsuz işlemleri için iş parçacığı yalıtan bir bileşen belgeler.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Zaman uyumsuz ses yükleme belgeler.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Bir resmi zaman uyumsuz olarak yüklemek nasıl belgelenir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 İle uzun süren bir işlem gerçekleştirmek nasıl gösterir <xref:System.ComponentModel.BackgroundWorker> bileşeni.  
  
 [BackgroundWorker Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 Nasıl kullanılacağını açıklayan konuları sağlar <xref:System.ComponentModel.BackgroundWorker> zaman uyumsuz işlemleri için bileşen.

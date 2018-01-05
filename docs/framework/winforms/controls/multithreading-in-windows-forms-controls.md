---
title: "Windows Forms Denetimlerinde Çoklu Kullanım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2b9c0a7b19df62867a4148b60e24b7d3ba9bcce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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

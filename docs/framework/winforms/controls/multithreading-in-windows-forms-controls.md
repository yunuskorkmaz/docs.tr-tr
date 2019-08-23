---
title: Windows Forms Denetimlerinde Çoklu Kullanım
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952680"
---
# <a name="multithreading-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Çoklu Kullanım
Birçok uygulamada, başka bir iş parçacığı üzerinde zaman alan işlemler gerçekleştirerek Kullanıcı arabiriminizi (UI) daha hızlı hale getirebilirsiniz. <xref:System.Threading> Ad alanı `BackgroundWorker` , yöntem ve bileşen dahil Windows Forms denetimlerinizi çoklu iş parçacığı için kullanılabilir bir dizi araç vardır. <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>  
  
> [!NOTE]
> Bileşeni, <xref:System.Threading> ad alanına ve <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemine işlevsellik ekler ve bu ve yöntemi sağlar; ancak, bunlar, hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. `BackgroundWorker` Daha fazla bilgi için bkz. [BackgroundWorker Component Overview](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Windows Forms denetimlerine Iş parçacığına güvenli çağrılar yapma](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Windows Forms denetimlerine iş parçacığı güvenli çağrıların nasıl yapılacağını gösterir.  
  
 [Nasıl yapılır: Dosya aramak için arka plan Iş parçacığı kullanma](how-to-use-a-background-thread-to-search-for-files.md)  
 Zaman uyumsuz olarak dosya aramak <xref:System.Threading> için ad alanının <xref:System.Windows.Forms.Control.BeginInvoke%2A> ve yönteminin nasıl kullanılacağını gösterir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ComponentModel.BackgroundWorker>  
 Zaman uyumsuz işlemler için çalışan iş parçacığını kapsülleyen bir bileşeni belgeler.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Bir sesin zaman uyumsuz olarak nasıl yükleneceğini belgeler.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Bir görüntünün zaman uyumsuz olarak nasıl yükleneceğini belgeler.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl yapılır: Arka planda Işlem çalıştırma](how-to-run-an-operation-in-the-background.md)  
 <xref:System.ComponentModel.BackgroundWorker> Bileşeniyle zaman alan bir işlemin nasıl gerçekleştirileceğini gösterir.  
  
 [BackgroundWorker Bileşenine Genel Bakış](backgroundworker-component-overview.md)  
 <xref:System.ComponentModel.BackgroundWorker> Bileşeninin zaman uyumsuz işlemler için nasıl kullanılacağını betimleyen konuları sağlar.

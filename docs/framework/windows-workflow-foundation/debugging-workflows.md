---
title: "İş akışları hata ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44814be3a21e9c0ca9ba2b09a5309661a939bbdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-workflows"></a>İş akışları hata ayıklama
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]geliştirme ortamı'ndan çalışan iş akışları hata ayıklama için çeşitli seçenekler sunar. İş Akışı Tasarımcısı'nda, XAML ve kod hata ayıklaması yapılabilir.  
  
## <a name="debugging-in-the-workflow-designer"></a>İş Akışı Tasarımcısı'nda hata ayıklama  
 Kesme noktaları üzerinde ayarlanabilir iş akışı Tasarımcısı'nda etkinlikler etkinliğin vurgulama ve tuşuna basarak **F9** veya etkinliğin bağlam menüsünü kullanarak. İş akışı sonra iş akışı ana hata ayıklama modunda çalıştırdığınızda sonları yürütülmesi. Aşağıdaki ekran görüntüsünde, iş akışı yürütme sırasında bir kesme noktası duraklatıldı. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][İş akışı Tasarımcısı ile hata ayıklama](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>XAML'de hata ayıklama  
 Bir iş akışı Tasarımcısı'nda bir kesme noktasında duraklatıldı durumunda iş akışı da XAML'de hata ayıklaması yapılabilir. XAML'de yürütme noktası görüntülemek için seçin **XAML görünümü** iş akışı yürütme duraklatıldığında, iş akışı Tasarımcısı'nda. Hata ayıklama geri Designer'a Çözüm Gezgini'nden Tasarımcı iş akışında yeniden açarak değiştirilebilir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Nasıl yapılır: hata ayıklama XAML iş akışı Tasarımcısı ile](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).  
  
## <a name="debugging-in-code"></a>Kodda hata ayıklama  
 Kod kesme noktaları kullanılabilir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] aynı şekilde bunlar kesinlik temelli diğer uygulamalarda kullanılabilir. Bir kod kesme noktası oluşturmak için kodu bölmenin sol kenar boşluğu'ı tıklatın veya basın **F9** İmleç konumuna bir kesme noktası yerleştirilecek.  
  
## <a name="attaching-to-a-workflow-process"></a>Bir iş akışı işlemine iliştirme  
 İş akışı ayrıca hata ayıklama için bir işlem eklemek için Visual Studio'nun altyapısını kullanarak destekler. Bu, Internet Information Services (IIS) 7.0 gibi farklı bir konak ortamında çalışan bir iş akışındaki hata ayıklamak iş akışı yazarı sağlar.  
  
## <a name="remote-debugging"></a>Uzaktan Hata Ayıklama  
 [!INCLUDE[wf](../../../includes/wf-md.md)]Uzaktan hata ayıklama, işlevleri diğer için uzaktan hata ayıklama ile aynı [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] bileşenleri. Uzaktan hata ayıklama kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: uzaktan hata ayıklama etkinleştirme](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  İş akışı uygulaması x86 hedefliyorsa mimarisi ve 64 bit işletim sistemi çalıştıran bir bilgisayarda uzaktan hata ayıklama sürece çalışmaz sonra barındırılan [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] uzak bilgisayara veya hedef iş akışı uygulaması değiştirilirse yüklü için **tüm CPU**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Hizmet hata ayıklama akışı genişletme  
 İş akışı hata ayıklayıcı hizmeti artık genel ve izleme, benzetimi ve yeniden barındırılan Tasarımcısı'nda hata ayıklama gibi özel uygulamalar oluşturmak için kullanılabilir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<xref:System.Activities.Presentation.Debug.DebuggerService> konu.

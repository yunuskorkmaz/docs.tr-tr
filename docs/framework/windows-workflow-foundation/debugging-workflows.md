---
title: İş akışları hata ayıklama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8fa22db7fe613279fcf8487abaf57691250b7d80
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="debugging-workflows"></a>İş akışları hata ayıklama
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] geliştirme ortamı'ndan çalışan iş akışları hata ayıklama için çeşitli seçenekler sunar. İş Akışı Tasarımcısı'nda, XAML ve kod hata ayıklaması yapılabilir.  
  
## <a name="debugging-in-the-workflow-designer"></a>İş Akışı Tasarımcısı'nda hata ayıklama  
 Kesme noktaları üzerinde ayarlanabilir iş akışı Tasarımcısı'nda etkinlikler etkinliğin vurgulama ve tuşuna basarak **F9** veya etkinliğin bağlam menüsünü kullanarak. İş akışı sonra iş akışı ana hata ayıklama modunda çalıştırdığınızda sonları yürütülmesi. Aşağıdaki ekran görüntüsünde, iş akışı yürütme sırasında bir kesme noktası duraklatıldı. Daha fazla bilgi için bkz: [hata ayıklama iş akışı Tasarımcısı ile](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>XAML'de hata ayıklama  
 Bir iş akışı Tasarımcısı'nda bir kesme noktasında duraklatıldı durumunda iş akışı da XAML'de hata ayıklaması yapılabilir. XAML'de yürütme noktası görüntülemek için seçin **XAML görünümü** iş akışı yürütme duraklatıldığında, iş akışı Tasarımcısı'nda. Hata ayıklama geri Designer'a Çözüm Gezgini'nden Tasarımcı iş akışında yeniden açarak değiştirilebilir. Daha fazla bilgi için bkz: [nasıl yapılır: hata ayıklama XAML iş akışı Tasarımcısı ile](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).  
  
## <a name="debugging-in-code"></a>Kodda hata ayıklama  
 Kod kesme noktaları kullanılabilir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] aynı şekilde bunlar kesinlik temelli diğer uygulamalarda kullanılabilir. Bir kod kesme noktası oluşturmak için kodu bölmenin sol kenar boşluğu'ı tıklatın veya basın **F9** İmleç konumuna bir kesme noktası yerleştirilecek.  
  
## <a name="attaching-to-a-workflow-process"></a>Bir iş akışı işlemine iliştirme  
 İş akışı ayrıca hata ayıklama için bir işlem eklemek için Visual Studio'nun altyapısını kullanarak destekler. Bu, Internet Information Services (IIS) 7.0 gibi farklı bir konak ortamında çalışan bir iş akışındaki hata ayıklamak iş akışı yazarı sağlar.  
  
## <a name="remote-debugging"></a>Uzaktan Hata Ayıklama  
 Windows Workflow Foundation (WF) uzaktan hata ayıklama için Visual Studio bileşenlerle uzaktan hata ayıklama ile aynı işlevleri. Uzaktan hata ayıklama kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: uzaktan hata ayıklama etkinleştirme](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  İş akışı uygulaması x86 hedefliyorsa mimarisi ve 64 bit işletim sistemi çalıştıran bir bilgisayarda uzaktan hata ayıklama Visual Studio uzak bilgisayarda yüklü veya iş akışı uygulaması için hedef olarak değiştirildiğinde sürece çalışmaz sonra barındırılan **Tüm CPU**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Hizmet hata ayıklama akışı genişletme  
 İş akışı hata ayıklayıcı hizmeti artık genel ve izleme, benzetimi ve yeniden barındırılan Tasarımcısı'nda hata ayıklama gibi özel uygulamalar oluşturmak için kullanılabilir. Daha fazla bilgi için bkz: <xref:System.Activities.Presentation.Debug.DebuggerService> konu.

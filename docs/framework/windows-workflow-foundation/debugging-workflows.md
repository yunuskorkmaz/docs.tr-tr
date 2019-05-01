---
title: İş Akışlarında Hata Ayıklama
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 17cee1f1b509e777edd3f08c55d473d768b19b55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945879"
---
# <a name="debugging-workflows"></a>İş Akışlarında Hata Ayıklama
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] geliştirme ortamından çalışan iş akışlarında hata ayıklama için çeşitli seçenekler sunar. İş Akışı Tasarımcısı'nda, XAML ve kod ayıklanabilir.  
  
## <a name="debugging-in-the-workflow-designer"></a>İş Akışı Tasarımcısı'nda hata ayıklama  
 Kesme noktaları ayarlanabilir etkinlikleri iş akışı tasarımcısında etkinlik vurgulama ve basarak **F9** veya etkinliğin bağlam menüsünü kullanarak. İş akışı sonra iş akışı konak hata ayıklama modunda çalıştırdığınızda sonları yürütme. Aşağıdaki ekran görüntüsünde, iş akışı yürütme kesme noktasında duraklatıldı. Daha fazla bilgi için [iş akışı Tasarımcısı hata ayıklama iş akışlarıyla](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>XAML içinde hata ayıklama  
 Bir iş akışı Tasarımcısı'nda bir kesme noktasında duraklatıldı durumunda iş akışı XAML içinde de ayıklanabilir. Yürütme noktası XAML içinde görüntülemek için seçin **XAML görünümü** iş akışı yürütme duraklatıldığında iş akışı Tasarımcısı'nda. Hata ayıklama tasarımcıya geri dönün iş akışı içinde Çözüm Gezgini'nden Tasarımcı yeniden açarak değiştirilebilir. Daha fazla bilgi için [nasıl yapılır: İş Akışı Tasarımcısı ile XAML hatalarını ayıklama](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).  
  
## <a name="debugging-in-code"></a>Kodda hata ayıklama  
 Kodu kesme noktaları kullanılabilir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] aynı şekilde, kesinlik temelli diğer uygulamalarda kullanılabilir. Bir kod kesme noktası oluşturmak için kod bölmesinin sol kenar boşluğu tıklayın veya basın **F9** İmleç konumuna bir kesme noktası yerleştirmek için.  
  
## <a name="attaching-to-a-workflow-process"></a>Bir iş akışı işlemine iliştirme  
 Ayrıca iş akışı hata ayıklama, Visual Studio'nun altyapı bir işleme kullanmayı destekler. Bu, Internet Information Services (IIS) 7.0 gibi farklı bir konak ortamında çalışan bir iş akışı hata ayıklamak iş akışı Yazar sağlar.  
  
## <a name="remote-debugging"></a>Uzaktan Hata Ayıklama  
 Windows Workflow Foundation (WF) uzaktan hata ayıklama, uzaktan hata ayıklama için diğer Visual Studio bileşenleri ile aynı işlevleri. Uzaktan hata ayıklama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Uzaktan hata ayıklamayı etkinleştirme](https://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  İş akışı uygulaması x86 hedefliyorsa mimarisi ve uzaktan hata ayıklama Visual Studio uzak bilgisayarda yüklü veya iş akışı uygulama için hedef olarak değiştirilir sürece çalışmaz sonra bir 64 bit işletim sistemi çalıştıran bir bilgisayarda barındırılır **Herhangi bir CPU**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Hizmet hata ayıklama iş akışını genişletme  
 İş akışı hata ayıklayıcı hizmeti artık genel ve izleme, simülasyon ve yeniden barındırılan tasarımcıda hata ayıklama gibi özel uygulamalar oluşturmak için kullanılabilir. Daha fazla bilgi için <xref:System.Activities.Presentation.Debug.DebuggerService> konu.

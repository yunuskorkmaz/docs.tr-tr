---
description: 'Daha fazla bilgi: 1. görev: yeni bir Windows Presentation Foundation uygulaması oluşturma'
title: 'Görev 1: Yeni Bir Windows Presentation Foundation Uygulaması Oluşturma'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 7bbb49e3d663d1878b2b3e150a24f775eeca0135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755245"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Görev 1: Yeni Bir Windows Presentation Foundation Uygulaması Oluşturma

Bu görevde, WPF uygulaması Visual Studio şablonunu kullanarak boş bir Windows Presentation Foundation (WPF) uygulaması oluşturacaksınız ve ilgili [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı derlemelerine başvurular eklersiniz.  
  
## <a name="to-create-the-wpf-application-project"></a>WPF uygulaması projesi oluşturmak için

1. Visual Studio 'Yu açın ve **Dosya** menüsünde **Yeni** üzerine gelin ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, kutunun sol tarafındaki **yüklü şablonlar** bölmesinden **Visual C#** veya **Visual Basic** seçin. Seçtiğiniz dil görünmezse, **diğer diller** bölümüne bakın.

3. **Yüklü şablonlar** bölmesinde **Windows** ' u seçin.

4. Üst bölmede, açılan liste kutusunda **.NET Framework 4 ' ün** seçildiğinden emin olun ve ardından **WPF uygulaması**' nı seçin.

5. Projenin adını pencerenin alt kısmındaki **HostingApplication** olarak ayarlayın.

6. Çözüm adını **yeniden hostingolarak** ayarlayın.

7. Uygulama projesini oluşturmak için **Tamam** ' ı tıklatın. Visual Studio, uygulamanız için temel bir WPF Kullanıcı arabirimi oluşturur ve uygun XAML ve arka plan kod dosyalarını içerir.

8. **WorkflowModel** derlemelerine başvurular ekleyin. Bunu yapmak için, **Çözüm Gezgini**, **HostingApplication** projesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.

9. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesine tıklayın, CTRL tuşunu basılı tutarak aşağıdaki derlemeleri seçin ve ardından **Tamam**' a tıklayın:

    - System. Activities
    - System. Activities. Presentation
    - System. Activities. Core. Presentation

10. Bkz. görev 2: iş akışı Tasarımcısı tasarım tuvali 'nin nasıl barındıralınacağını öğrenmek için [iş akışı Tasarımcısı barındırın](task-2-host-the-workflow-designer.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Yeniden Barındırma](rehosting-the-workflow-designer.md)
- [Görev 2: İş Akışı Tasarımcısını Barındırma](task-2-host-the-workflow-designer.md)

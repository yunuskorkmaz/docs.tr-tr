---
title: 'Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031888"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma

Bu görevde, WPF uygulaması Visual Studio şablonunu kullanarak boş bir Windows Presentation Foundation (WPF) uygulaması oluşturacaksınız ve uygun [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı derlemelerine başvurular eklersiniz.  
  
## <a name="to-create-the-wpf-application-project"></a>WPF uygulaması projesi oluşturmak için

1. Visual Studio 'Yu açın ve **Dosya** menüsünde **Yeni**üzerine gelin ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, kutunun sol tarafındaki **yüklü şablonlar** bölmesinden  **C# görsel** veya **Visual Basic** ' yi seçin. Seçtiğiniz dil görünmezse, **diğer diller**bölümüne bakın.

3. **Yüklü şablonlar** bölmesinde **Windows** ' u seçin.

4. Üst bölmede, açılan liste kutusunda **.NET Framework 4 ' ün** seçildiğinden emin olun ve ardından **WPF uygulaması**' nı seçin.

5. Projenin adını pencerenin alt kısmındaki **HostingApplication** olarak ayarlayın.

6. Çözüm adını **yeniden hostingolarak**ayarlayın.

7. Uygulama projesini oluşturmak için **Tamam** ' ı tıklatın. Visual Studio, uygulamanız için temel bir WPF Kullanıcı arabirimi oluşturur ve uygun XAML ve arka plan kod dosyalarını içerir.

8. **WorkflowModel** derlemelerine başvurular ekleyin. Bunu yapmak için, **Çözüm Gezgini**, **HostingApplication** projesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.

9. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesine tıklayın, CTRL tuşunu basılı tutarak aşağıdaki derlemeleri seçin ve ardından **Tamam**' a tıklayın:

    - System. Activities
    - System. Activities. Presentation
    - System. Activities. Core. Presentation

10. Bkz. görev 2: iş akışı Tasarımcısı tasarım tuvali 'nin nasıl barındıralınacağını öğrenmek için [iş akışı Tasarımcısı barındırın](task-2-host-the-workflow-designer.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısı yeniden barındırma](rehosting-the-workflow-designer.md)
- [Görev 2: İş Akışı Tasarımcısı barındırın](task-2-host-the-workflow-designer.md)

---
title: "Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bfebf11d66ded668d7c0892d11adde76e0a42c01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma
Bu görevde, boş bir oluşturacak [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] WPF uygulaması Visual Studio şablonunu kullanarak uygulama ve uygun başvurular ekleyin [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı derlemeler.  
  
### <a name="to-create-the-wpf-application-project"></a>WPF uygulaması projesi oluşturmak için  
  
1.  Açık [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] ve **dosya** menüsündeki **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda, şunlardan birini seçin **Visual C#** veya **Visual Basic** gelen **yüklü şablonlar** sol tarafındaki bölmesi bir kutu. Tercih ettiğiniz dili görünmüyorsa arayın **diğer diller**.  
  
3.  Seçin **Windows** içinde **yüklü şablonlar** bölmesi.  
  
4.  Üst bölmede onaylayın (varsayılan değer) **.NET Framework 4** aşağı açılan liste kutusunda seçili ve ardından olmamıştı **WPF uygulaması**.  
  
5.  Projeye adını ayarlamak **HostingApplication** pencerenin altındaki.  
  
6.  Çözüm adı ayarlamak **RehostingTheDesigner**.  
  
7.  Tıklatın **Tamam** uygulama projesi oluşturmak için. [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]Uygulamanız için temel bir WPF UI oluşturur ve uygun XAML ve arka plan kodu dosyalarını içerir.  
  
8.  Başvurular ekleyin **WorkflowModel** derlemeler. Bunu yapmak için **Çözüm Gezgini**, sağ **HostingApplication** proje ve seçin **Başvuru Ekle**.  
  
9. İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET** sekmesinde, CTRL tuşunu basılı tutun, aşağıdaki derlemeleri seçin ve ardından **Tamam**:  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. **Tamam**'ı tıklatın.  
  
11. Bkz: [görev 2: İş Akışı Tasarımcısı konak](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) iş akışı Tasarımcısı tasarım tuvale barındırmak hakkında bilgi edinmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Tasarımcısı yeniden barındırma](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Görev 2: ana bilgisayar iş akışı Tasarımcısı](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)

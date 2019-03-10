---
title: '1. Görev: Yeni bir Windows Presentation Foundation uygulaması oluşturma'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 533b4a1030ab5f47eb96ca62dc2805eae7933b9b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711904"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>1. Görev: Yeni bir Windows Presentation Foundation uygulaması oluşturma
Bu görevde, WPF uygulaması Visual Studio şablonu kullanarak boş bir Windows Presentation Foundation (WPF) uygulaması oluşturun ve uygun başvuruları eklemek [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı bütünleştirilmiş kodları.  
  
### <a name="to-create-the-wpf-application-project"></a>WPF uygulaması projesi oluşturmak için  
  
1.  Visual Studio'yu açın ve **dosya** menüsünde **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda, ya da seçin **Visual C#**  veya **Visual Basic** gelen **yüklü şablonlar** sol bölmesi kutunun yanında. Tercih ettiğiniz dili görünmüyorsa altına bakın **diğer diller**.  
  
3.  Seçin **Windows** içinde **yüklü şablonlar** bölmesi.  
  
4.  Üst bölmede onaylayın (varsayılan değer) **.NET Framework 4** aşağı açılan liste kutusunda seçili ve ardından **WPF uygulaması**.  
  
5.  Proje adını ayarlayın **HostingApplication** pencerenin alt kısmındaki.  
  
6.  Çözüm adı kümesine **RehostingTheDesigner**.  
  
7.  Tıklayın **Tamam** uygulaması projesi oluşturmak için. Visual Studio, uygulamanız için temel bir WPF kullanıcı Arabirimi oluşturur ve uygun XAML ve arka plan kod dosyalarını içerir.  
  
8.  Başvuruları Ekle **WorkflowModel** derlemeler. Bunu yapmak için **Çözüm Gezgini**, sağ **HostingApplication** seçin ve proje **Başvuru Ekle**.  
  
9. İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET** sekmesinde, CTRL tuşunu basılı tutun, aşağıdaki derlemeler seçin ve ardından **Tamam**:  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. **Tamam**'ı tıklatın.  
  
11. Bkz: [görev 2: İş akışı tasarımcısını barındırma](task-2-host-the-workflow-designer.md) nasıl iş akışı Tasarımcısı tasarım tuvali barındıracağınızı öğrenin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İş Akışı Tasarımcısını Yeniden Barındırma](rehosting-the-workflow-designer.md)
- [2. Görev: İş akışı tasarımcısını barındırma](task-2-host-the-workflow-designer.md)

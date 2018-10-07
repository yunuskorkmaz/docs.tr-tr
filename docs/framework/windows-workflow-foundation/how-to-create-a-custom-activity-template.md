---
title: 'Nasıl yapılır: Özel Etkinlik şablonu oluşturma'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 87acf0d084154c9c3e5cbc97da4af9821709f0a5
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847620"
---
# <a name="how-to-create-a-custom-activity-template"></a>Nasıl yapılır: Özel Etkinlik şablonu oluşturma

Etkinlikler, böylece kullanıcılar her etkinliği ayrı ayrı oluşturun ve bunların özelliklerini ve diğer ayarları yapılandırmak zorunda değilsiniz özel bileşik etkinlikler dahil olmak üzere yapılandırılmasını özelleştirmek için kullanılan özel etkinlik şablonları el ile. Bu özel şablonları kullanılabilir hale getirilebilir **araç kutusu** üzerinde [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] veya içinden kullanıcılar sürükleyerek bunları önceden yapılandırılmış bir tasarım yüzeyine sürükleyin, yeniden barındırılan bir tasarımcı. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] Böyle şablon iyi örneklerini ile birlikte gelir: [SendAndReceiveReply Şablon tasarımcısı](/visualstudio/workflow-designer/sendandreceivereply-template-designer) ve [ReceiveAndSendReply Şablon tasarımcısı](/visualstudio/workflow-designer/receiveandsendreply-template-designer) içinde [Mesajlaşmaetkinliktasarımcıları](/visualstudio/workflow-designer/messaging-activity-designers) kategorisi.

 Bu konudaki ilk yordamı için bir özel etkinlik şablonu oluşturmayı açıklar bir **gecikme** etkinliği ve ikinci yordam açıklayan kısa bir süre içinde kullanılabilir hale getirmek bir [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] özel şablonu çalıştığını doğrulayın.

 Özel Etkinlik şablonları uygulanmalı <xref:System.Activities.Presentation.IActivityTemplateFactory>. Tek bir arabirime sahip <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> yöntemi ile oluşturabilir ve şablonda kullanılan etkinlik örnekleri yapılandırabilirsiniz.

## <a name="to-create-a-template-for-the-delay-activity"></a>Delay etkinlik için bir şablon oluşturmak için

1.  Visual Studio 2010'u başlatın.

2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.

     **Yeni proje** iletişim kutusu açılır.

3.  İçinde **proje türleri** bölmesinde **iş akışı** da **Visual C#** projeleri veya **Visual Basic** gruplandırmaları bağlı olarak, dil tercihi.

4.  İçinde **şablonları** bölmesinde **etkinlik Kitaplığı**.

5.  İçinde **adı** kutusuna `DelayActivityTemplate`.

6.  Varsayılan değerleri kabul **konumu** ve **çözüm adı** metin kutuları ve ardından **Tamam**.

7.  DelayActivityTemplate projenin başvurular dizini sağ **Çözüm Gezgini** ve **Başvuru Ekle** açmak için **Başvuru Ekle** iletişim kutusu.

8.  Git **.NET** sekmenize **PresentationFramework** gelen **bileşen adı** tıklayın ve sol sütunu **Tamam** başvuru eklemek için PresentationFramework.dll dosyasına.

9. Başvurular System.Activities.Presentation.dll ve WindowsBase.dll dosyaları eklemek için bu yordamı yineleyin.

10. DelayActivityTemplate projeye sağ **Çözüm Gezgini** ve **Ekle** ardından **yeni öğe** açmak için **Add New Item**iletişim kutusu.

11. Seçin **sınıfı** şablon MyDelayTemplate adlandırın ve ardından **Tamam**.

12. MyDelayTemplate.cs dosyasını açın ve aşağıdaki deyimleri ekleyin.

    ```
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. Uygulama <xref:System.Activities.Presentation.IActivityTemplateFactory> ile `MyDelayActivity` aşağıdaki kodla sınıfı. Bu, gecikme süresi 10 saniye için yapılandırır.

    ```
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. Seçin **Çözümü Derle** gelen **derleme** DelayActivityTemplate.dll dosyası oluşturmak için menü.

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Şablonu bir iş akışı Tasarımcısı'nda kullanılabilir yapmak için

1.  DelayActivityTemplate çözüme sağ **Çözüm Gezgini** ve **Ekle** ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.

2.  Seçin **iş akışı konsol uygulaması** şablon adlandırın `CustomActivityTemplateApp`ve ardından **Tamam**.

3.  CustomActivityTemplateApp projenin başvurular dizini sağ **Çözüm Gezgini** ve **Başvuru Ekle** açmak için **Başvuru Ekle** iletişim bir kutu.

4.  Git **projeleri** sekmenize **DelayActivityTemplate** gelen **proje adı** tıklayın ve sol sütunu **Tamam** eklemek için bir ilk yordamda oluşturduğunuz DelayActivityTemplate.dll dosyasına başvurun.

5.  CustomActivityTemplateApp projeye sağ **Çözüm Gezgini** ve **derleme** uygulama derlemek için.

6.  CustomActivityTemplateApp projeye sağ **Çözüm Gezgini** ve **başlangıç projesi olarak ayarla**.

7.  Seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** herhangi anahtar istendiğinde cmd.exe penceresinden devam etmek için menü ve tuşuna basın.

8.  Workflow1.xaml dosyasını açın ve açık **araç kutusu**.

9. Bulun **MyDelayActivity** şablonunda **DelayActivityTemplate** kategorisi. Tasarım yüzeyine sürükleyin. Doğrulayın **özellikleri** penceresi, `Duration` özelliği 10 saniye olarak ayarlandı.

## <a name="example"></a>Örnek
 Aşağıdaki kod MyDelayActivity.cs dosya içermelidir.

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [İş Akışı Tasarım Deneyimini Özelleştirme](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
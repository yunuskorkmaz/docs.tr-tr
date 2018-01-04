---
title: "Nasıl yapılır: Özel Etkinlik şablonu oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 772ad2a7ea56001bf3ecba089e62d6bc0f59e5ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-activity-template"></a>Nasıl yapılır: Özel Etkinlik şablonu oluşturma
Özel Etkinlik şablonları etkinlikleri, böylece kullanıcılar her etkinlik tek tek oluşturabilirsiniz ve bunların özelliklerini ve diğer ayarları yapılandırmak zorunda değilsiniz özel bileşik etkinlikler dahil olmak üzere yapılandırma özelleştirmek için kullanılan el ile. Bu özel şablonları içinde kullanılabilir hale getirilebilir **araç** üzerinde [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] veya hangi kullanıcıların sürükleyebilirsiniz bunları önceden yapılandırılmış tasarım yüzeyine bir rehosted Tasarımcısından. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]Bu tür şablonlar iyi örnekleri ile birlikte gelir: [SendAndReceiveReply şablonu Tasarımcısı](/visualstudio/workflow-designer/sendandreceivereply-template-designer) ve [ReceiveAndSendReply şablonu Tasarımcısı](/visualstudio/workflow-designer/receiveandsendreply-template-designer) içinde [Mesajlaşma etkinlik tasarımcıları](/visualstudio/workflow-designer/messaging-activity-designers) kategorisi.  
  
 Bu konudaki ilk yordamı için bir özel etkinlik şablonu oluşturmayı açıklar bir **gecikme** etkinliği ve ikinci yordam kısa bir süre içinde kullanılabilir duruma nasıl yapılandırılacağını açıklayan bir [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] özel şablonu çalıştığını doğrulayın.  
  
 Özel Etkinlik şablonları uygulanmalı <xref:System.Activities.Presentation.IActivityTemplateFactory>. Tek bir arabirime sahip <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> ile oluşturma ve şablonda kullanılan etkinlik örnekleri yapılandırma yöntemi.  
  
### <a name="to-create-a-template-for-the-delay-activity"></a>Gecikme etkinliği için bir şablon oluşturmak için  
  
1.  Başlat [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **proje türleri** bölmesinde, **iş akışı** da **Visual C#** projeleri veya **Visual Basic** gruplandırmaları bağlı olarak, dil tercihi.  
  
4.  İçinde **şablonları** bölmesinde, **etkinlik Kitaplığı**.  
  
5.  İçinde **adı** kutusuna `DelayActivityTemplate`.  
  
6.  Varsayılan değerleri kabul **konumu** ve **çözüm adı** metin kutuları ve ardından **Tamam**.  
  
7.  DelayActivityTemplate projede başvuruları dizininin sağ **Çözüm Gezgini** ve **Başvuru Ekle** açmak için **Başvuru Ekle** iletişim kutusu.  
  
8.  Git **.NET** sekmesinde ve seçin **PresentationFramework** gelen **bileşen adı** tıklatın ve sol sütunda **Tamam** bir başvuru eklemek için PresentationFramework.dll dosyasına.  
  
9. Başvuruları System.Activities.Presentation.dll ve WindowsBase.dll dosyaları eklemek için bu yordamı yineleyin.  
  
10. DelayActivityTemplate projeye sağ **Çözüm Gezgini** ve **Ekle** ve ardından **yeni öğe** açmak için **Yeni Öğe Ekle**iletişim kutusu.  
  
11. Seçin **sınıfı** şablon MyDelayTemplate adlandırın ve ardından **Tamam**.  
  
12. MyDelayTemplate.cs dosyasını açın ve aşağıdaki deyimleri ekleyin.  
  
    ```  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
    ```  
  
13. Uygulama <xref:System.Activities.Presentation.IActivityTemplateFactory> ile `MyDelayActivity` aşağıdaki kodla sınıfı. Bu gecikme süresi 10 saniye için yapılandırır.  
  
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
  
14. Seçin **yapı çözümü** gelen **yapı** menü DelayActivityTemplate.dll dosyası oluşturun.  
  
### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Şablonun bir iş akışı Tasarımcısı'nda kullanılabilmesini sağlamak için  
  
1.  DelayActivityTemplate çözüme sağ **Çözüm Gezgini** ve **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.  
  
2.  Seçin **iş akışı konsol uygulaması** şablon adlandırın `CustomActivityTemplateApp`ve ardından **Tamam**.  
  
3.  CustomActivityTemplateApp projede başvuruları dizininin sağ **Çözüm Gezgini** ve **Başvuru Ekle** açmak için **Başvuru Ekle** iletişim bir kutu.  
  
4.  Git **projeleri** sekmesinde ve seçin **DelayActivityTemplate** gelen **proje adı** tıklatın ve sol sütunda **Tamam** eklemek için bir ilk yordamda oluşturduğunuz DelayActivityTemplate.dll dosyasına başvurun.  
  
5.  CustomActivityTemplateApp projeye sağ **Çözüm Gezgini** ve **yapı** uygulama derlemek için.  
  
6.  ' Nde CustomActivityTemplateApp projeye sağ **Çözüm Gezgini** ve **başlangıç projesi olarak ayarla**.  
  
7.  Seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** herhangi bir anahtar istendiğinde cmd.exe penceresinden devam etmek için menü ve tuşuna basın.  
  
8.  Workflow1.xaml dosyasını açın ve açık **araç**.  
  
9. Bulun **MyDelayActivity** şablonunda **DelayActivityTemplate** kategorisi. Tasarım yüzeyine sürükleyin. Doğrulayın **özellikleri** penceresi, `Duration` özelliği 10 saniye olarak ayarlandı.  
  
## <a name="example"></a>Örnek  
 MyDelayActivity.cs dosyası aşağıdaki kodu içermelidir.  
  
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
 <xref:System.Activities.Presentation.IActivityTemplateFactory>  
 [İş Akışı Tasarım Deneyimini Özelleştirme](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)

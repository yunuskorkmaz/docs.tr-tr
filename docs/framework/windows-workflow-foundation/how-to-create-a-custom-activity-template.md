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
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="7f9a7-102">Nasıl yapılır: Özel Etkinlik şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="7f9a7-102">How to: Create a Custom Activity Template</span></span>
<span data-ttu-id="7f9a7-103">Özel Etkinlik şablonları etkinlikleri, böylece kullanıcılar her etkinlik tek tek oluşturabilirsiniz ve bunların özelliklerini ve diğer ayarları yapılandırmak zorunda değilsiniz özel bileşik etkinlikler dahil olmak üzere yapılandırma özelleştirmek için kullanılan el ile.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="7f9a7-104">Bu özel şablonları içinde kullanılabilir hale getirilebilir **araç** üzerinde [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] veya hangi kullanıcıların sürükleyebilirsiniz bunları önceden yapılandırılmış tasarım yüzeyine bir rehosted Tasarımcısından.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]<span data-ttu-id="7f9a7-105">Bu tür şablonlar iyi örnekleri ile birlikte gelir: [SendAndReceiveReply şablonu Tasarımcısı](/visualstudio/workflow-designer/sendandreceivereply-template-designer) ve [ReceiveAndSendReply şablonu Tasarımcısı](/visualstudio/workflow-designer/receiveandsendreply-template-designer) içinde [Mesajlaşma etkinlik tasarımcıları](/visualstudio/workflow-designer/messaging-activity-designers) kategorisi.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-105"> ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>  
  
 <span data-ttu-id="7f9a7-106">Bu konudaki ilk yordamı için bir özel etkinlik şablonu oluşturmayı açıklar bir **gecikme** etkinliği ve ikinci yordam kısa bir süre içinde kullanılabilir duruma nasıl yapılandırılacağını açıklayan bir [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] özel şablonu çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>  
  
 <span data-ttu-id="7f9a7-107">Özel Etkinlik şablonları uygulanmalı <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="7f9a7-108">Tek bir arabirime sahip <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> ile oluşturma ve şablonda kullanılan etkinlik örnekleri yapılandırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>  
  
### <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="7f9a7-109">Gecikme etkinliği için bir şablon oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7f9a7-109">To create a template for the Delay activity</span></span>  
  
1.  <span data-ttu-id="7f9a7-110">Başlat [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f9a7-110">Start [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="7f9a7-111">Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>  
  
     <span data-ttu-id="7f9a7-112">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-112">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7f9a7-113">İçinde **proje türleri** bölmesinde, **iş akışı** da **Visual C#** projeleri veya **Visual Basic** gruplandırmaları bağlı olarak, dil tercihi.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>  
  
4.  <span data-ttu-id="7f9a7-114">İçinde **şablonları** bölmesinde, **etkinlik Kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-114">In the **Templates** pane, select **Activity Library**.</span></span>  
  
5.  <span data-ttu-id="7f9a7-115">İçinde **adı** kutusuna `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>  
  
6.  <span data-ttu-id="7f9a7-116">Varsayılan değerleri kabul **konumu** ve **çözüm adı** metin kutuları ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="7f9a7-117">DelayActivityTemplate projede başvuruları dizininin sağ **Çözüm Gezgini** ve **Başvuru Ekle** açmak için **Başvuru Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
8.  <span data-ttu-id="7f9a7-118">Git **.NET** sekmesinde ve seçin **PresentationFramework** gelen **bileşen adı** tıklatın ve sol sütunda **Tamam** bir başvuru eklemek için PresentationFramework.dll dosyasına.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>  
  
9. <span data-ttu-id="7f9a7-119">Başvuruları System.Activities.Presentation.dll ve WindowsBase.dll dosyaları eklemek için bu yordamı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>  
  
10. <span data-ttu-id="7f9a7-120">DelayActivityTemplate projeye sağ **Çözüm Gezgini** ve **Ekle** ve ardından **yeni öğe** açmak için **Yeni Öğe Ekle**iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>  
  
11. <span data-ttu-id="7f9a7-121">Seçin **sınıfı** şablon MyDelayTemplate adlandırın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="7f9a7-122">MyDelayTemplate.cs dosyasını açın ve aşağıdaki deyimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>  
  
    ```  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
    ```  
  
13. <span data-ttu-id="7f9a7-123">Uygulama <xref:System.Activities.Presentation.IActivityTemplateFactory> ile `MyDelayActivity` aşağıdaki kodla sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="7f9a7-124">Bu gecikme süresi 10 saniye için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-124">This configures the delay to have a duration of 10 seconds.</span></span>  
  
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
  
14. <span data-ttu-id="7f9a7-125">Seçin **yapı çözümü** gelen **yapı** menü DelayActivityTemplate.dll dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>  
  
### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="7f9a7-126">Şablonun bir iş akışı Tasarımcısı'nda kullanılabilmesini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="7f9a7-126">To make the template available in a Workflow Designer</span></span>  
  
1.  <span data-ttu-id="7f9a7-127">DelayActivityTemplate çözüme sağ **Çözüm Gezgini** ve **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="7f9a7-128">Seçin **iş akışı konsol uygulaması** şablon adlandırın `CustomActivityTemplateApp`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="7f9a7-129">CustomActivityTemplateApp projede başvuruları dizininin sağ **Çözüm Gezgini** ve **Başvuru Ekle** açmak için **Başvuru Ekle** iletişim bir kutu.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
4.  <span data-ttu-id="7f9a7-130">Git **projeleri** sekmesinde ve seçin **DelayActivityTemplate** gelen **proje adı** tıklatın ve sol sütunda **Tamam** eklemek için bir ilk yordamda oluşturduğunuz DelayActivityTemplate.dll dosyasına başvurun.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>  
  
5.  <span data-ttu-id="7f9a7-131">CustomActivityTemplateApp projeye sağ **Çözüm Gezgini** ve **yapı** uygulama derlemek için.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>  
  
6.  <span data-ttu-id="7f9a7-132">' Nde CustomActivityTemplateApp projeye sağ **Çözüm Gezgini** ve **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>  
  
7.  <span data-ttu-id="7f9a7-133">Seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** herhangi bir anahtar istendiğinde cmd.exe penceresinden devam etmek için menü ve tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>  
  
8.  <span data-ttu-id="7f9a7-134">Workflow1.xaml dosyasını açın ve açık **araç**.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="7f9a7-135">Bulun **MyDelayActivity** şablonunda **DelayActivityTemplate** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="7f9a7-136">Tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-136">Drag it onto the design surface.</span></span> <span data-ttu-id="7f9a7-137">Doğrulayın **özellikleri** penceresi, `Duration` özelliği 10 saniye olarak ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f9a7-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f9a7-138">Example</span></span>  
 <span data-ttu-id="7f9a7-139">MyDelayActivity.cs dosyası aşağıdaki kodu içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-139">The MyDelayActivity.cs file should contain the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f9a7-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7f9a7-140">See Also</span></span>  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>  
 [<span data-ttu-id="7f9a7-141">İş Akışı Tasarım Deneyimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7f9a7-141">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)

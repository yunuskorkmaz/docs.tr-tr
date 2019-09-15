---
title: 'Nasıl yapılır: Özel Etkinlik Şablonu Oluşturma'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 4ec84658dbe3039a4d7d714f8da183e6a5eb6ca4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989707"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="5adbf-102">Nasıl yapılır: Özel Etkinlik Şablonu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5adbf-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="5adbf-103">Özel Birleşik etkinlikler dahil olmak üzere etkinliklerin yapılandırmalarını özelleştirmek için özel etkinlik şablonları kullanılır. böylece, kullanıcılar her bir etkinliği ayrı ayrı oluşturmak ve özelliklerini ve diğer ayarlarını el ile yapılandırmak zorunda kalmayacak.</span><span class="sxs-lookup"><span data-stu-id="5adbf-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="5adbf-104">Bu özel şablonlar, [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] veya yeniden barındırılan bir tasarımcıda bulunan **araç kutusunda** ya da kullanıcıların bunları önceden yapılandırılmış tasarım yüzeyine sürükleyebileceği şekilde kullanılabilir hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5adbf-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]<span data-ttu-id="5adbf-105">Bu tür şablonların iyi örnekleri ile birlikte gelir: [Ileti etkinliği tasarımcıları](/visualstudio/workflow-designer/messaging-activity-designers) kategorisindeki [SendAndReceiveReply şablon Tasarımcısı](/visualstudio/workflow-designer/sendandreceivereply-template-designer) ve [ReceiveAndSendReply şablon Tasarımcısı](/visualstudio/workflow-designer/receiveandsendreply-template-designer) .</span><span class="sxs-lookup"><span data-stu-id="5adbf-105">ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="5adbf-106">Bu konudaki ilk yordam, bir **gecikme** etkinliği için özel etkinlik şablonu oluşturmayı açıklar ve ikinci yordam, özel şablonun çalıştığını doğrulamak için bir [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] ' de nasıl kullanılabilir hale getirmek istediğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="5adbf-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>

 <span data-ttu-id="5adbf-107">Özel etkinlik şablonlarının uygulaması <xref:System.Activities.Presentation.IActivityTemplateFactory>gerekir.</span><span class="sxs-lookup"><span data-stu-id="5adbf-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="5adbf-108">Arabirimin, şablonda kullanılan etkinlik <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> örneklerini oluşturabileceğiniz ve yapılandırabileceği tek bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="5adbf-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="5adbf-109">Gecikme etkinliğine yönelik bir şablon oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5adbf-109">To create a template for the Delay activity</span></span>

1. <span data-ttu-id="5adbf-110">Visual Studio 2010 ' i başlatın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-110">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="5adbf-111">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5adbf-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="5adbf-112">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="5adbf-112">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="5adbf-113">**Proje türleri** bölmesinde, dil tercihlerinize göre **görsel C#**  projelerden veya **Visual Basic** gruplarından **iş akışı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="5adbf-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4. <span data-ttu-id="5adbf-114">**Şablonlar** bölmesinde **etkinlik kitaplığı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="5adbf-114">In the **Templates** pane, select **Activity Library**.</span></span>

5. <span data-ttu-id="5adbf-115">**Ad** kutusuna girin `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="5adbf-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6. <span data-ttu-id="5adbf-116">**Konum** ve **çözüm adı** metin kutularındaki varsayılan değerleri kabul edin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7. <span data-ttu-id="5adbf-117">**Çözüm Gezgini** ' de DelayActivityTemplate projesinin başvurular dizinine sağ tıklayın **ve başvuru Ekle iletişim kutusunu** açmak için **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5adbf-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8. <span data-ttu-id="5adbf-118">**.Net** sekmesine gidin ve soldaki **bileşen adı** sütunundan **PresentationFramework** ' ü seçin ve PresentationFramework. dll dosyasına bir başvuru eklemek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="5adbf-119">System. Activities. Presentation. dll ve WindowsBase. dll dosyalarına başvurular eklemek için bu yordamı tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="5adbf-120">**Çözüm Gezgini** ' de DelayActivityTemplate projesine sağ tıklayın ve **Ekle** ' yi ve **Yeni öğe** ' yi seçerek **Yeni öğe Ekle** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="5adbf-121">**Sınıf** şablonunu seçin, MyDelayTemplate olarak adlandırın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="5adbf-122">MyDelayTemplate.cs dosyasını açın ve aşağıdaki deyimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5adbf-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="5adbf-123">Aşağıdaki kod ile `MyDelayActivity` sınıfını ileuygulayın.<xref:System.Activities.Presentation.IActivityTemplateFactory></span><span class="sxs-lookup"><span data-stu-id="5adbf-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="5adbf-124">Bu, gecikme süresini 10 saniyeye sahip olacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5adbf-124">This configures the delay to have a duration of 10 seconds.</span></span>

    ```csharp
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

14. <span data-ttu-id="5adbf-125">DelayActivityTemplate. dll dosyasını oluşturmak için **derleme** menüsünden **çözüm oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="5adbf-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="5adbf-126">Şablonu bir İş Akışı Tasarımcısı kullanılabilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="5adbf-126">To make the template available in a Workflow Designer</span></span>

1. <span data-ttu-id="5adbf-127">**Çözüm Gezgini** ' de DelayActivityTemplate çözümüne sağ tıklayın ve **Ekle** ' yi ve ardından **Yeni proje** ' yi seçerek **Yeni Proje Ekle** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="5adbf-128">**İş akışı konsol uygulaması** şablonunu seçin, adlandırın `CustomActivityTemplateApp`ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3. <span data-ttu-id="5adbf-129">**Çözüm Gezgini** ' de CustomActivityTemplateApp projesinin başvurular dizinine sağ tıklayın **ve başvuru Ekle iletişim kutusunu** açmak için **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5adbf-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4. <span data-ttu-id="5adbf-130">**Projeler** sekmesine gidin ve soldaki **Proje adı** sütunundan **DelayActivityTemplate** öğesini seçin ve ilk yordamda oluşturduğunuz DelayActivityTemplate. dll dosyasına bir başvuru eklemek için **Tamam** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5. <span data-ttu-id="5adbf-131">**Çözüm Gezgini** ' de CustomActivityTemplateApp projesine sağ tıklayın ve uygulamayı derlemek için **Oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="5adbf-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6. <span data-ttu-id="5adbf-132">**Çözüm Gezgini** ' de CustomActivityTemplateApp projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="5adbf-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7. <span data-ttu-id="5adbf-133">**Hata ayıklama** menüsünde **hata ayıklama olmadan Başlat** ' ı seçin ve cmd. exe penceresinden sorulduğunda devam etmek için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8. <span data-ttu-id="5adbf-134">Workflow1. xaml dosyasını açın ve **araç kutusunu**açın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="5adbf-135">**DelayActivityTemplate** kategorisinde **MyDelayActivity** şablonunu bulun.</span><span class="sxs-lookup"><span data-stu-id="5adbf-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="5adbf-136">Tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="5adbf-136">Drag it onto the design surface.</span></span> <span data-ttu-id="5adbf-137">**Özellikler** penceresinde, `Duration` özelliğin 10 saniyeye ayarlandığını onaylayın.</span><span class="sxs-lookup"><span data-stu-id="5adbf-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="5adbf-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="5adbf-138">Example</span></span>
 <span data-ttu-id="5adbf-139">MyDelayActivity.cs dosyası aşağıdaki kodu içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5adbf-139">The MyDelayActivity.cs file should contain the following code.</span></span>

```csharp
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

## <a name="see-also"></a><span data-ttu-id="5adbf-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5adbf-140">See also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="5adbf-141">İş Akışı Tasarım Deneyimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5adbf-141">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)

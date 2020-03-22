---
title: 'Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: c3c81e331eb3d8ee450ba0cac38e57976846ee63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352068"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="49e1f-102">Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49e1f-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="49e1f-103">Uygulamanızda meydana `My.Application.Log` `My.Log` gelen olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49e1f-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="49e1f-104">Bu örnek, izleme `My.Application.Log.WriteEntry` bilgilerini bir günlük dosyasına günlüğe kaydetmek için yöntemin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="49e1f-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="49e1f-105">Dosya günlüğü dinleyicisini eklemek ve yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="49e1f-105">To add and configure the file log listener</span></span>

1. <span data-ttu-id="49e1f-106">**Solution Explorer'da** app.config'e sağ tıklayın ve **Aç'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="49e1f-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="49e1f-107">\-veya -</span><span class="sxs-lookup"><span data-stu-id="49e1f-107">\- or -</span></span>

     <span data-ttu-id="49e1f-108">App.config dosyası yoksa:</span><span class="sxs-lookup"><span data-stu-id="49e1f-108">If there is no app.config file:</span></span>

    1. <span data-ttu-id="49e1f-109">**Proje** menüsünde **Yeni Öğe Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="49e1f-109">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="49e1f-110">Yeni **Öğe Ekle** iletişim kutusundan, **Uygulama Yapılandırma Dosyası'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="49e1f-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="49e1f-111">**Ekle**’ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="49e1f-111">Click **Add**.</span></span>

2. <span data-ttu-id="49e1f-112">Uygulama `<listeners>` yapılandırma dosyasındaki bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="49e1f-112">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="49e1f-113">\<Dinleyiciler> bölümünde \<kaynak> bölümünde, \<sistem.diagnostics> bölümü \<altında iç içe olan "DefaultSource" ad özniteliği ile> bölümü bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="49e1f-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="49e1f-114">Bu öğeyi `<listeners>` bu bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="49e1f-114">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="49e1f-115">Üst `<sharedListeners>` düzey `<configuration>` bölümün `<system.diagnostics>` altında iç içe olan bölümdeki bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="49e1f-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="49e1f-116">Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="49e1f-116">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="49e1f-117">Özniteliğin değerini `customlocation` günlük dizinine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="49e1f-117">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="49e1f-118">Dinleyici özelliğinin değerini ayarlamak için, ad küçük harfindeki tüm harflerle birlikte özellik ile aynı ada sahip bir öznitelik kullanın.</span><span class="sxs-lookup"><span data-stu-id="49e1f-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="49e1f-119">Örneğin, ve `location` `customlocation` öznitelikleri <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> özellikleri değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="49e1f-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="49e1f-120">Dosya günlüğüne olay bilgilerini yazmak için</span><span class="sxs-lookup"><span data-stu-id="49e1f-120">To write event information to the file log</span></span>

<span data-ttu-id="49e1f-121">Dosya `My.Application.Log.WriteEntry` günlüğüne bilgi yazmak için veya `My.Application.Log.WriteException` yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="49e1f-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="49e1f-122">Daha fazla bilgi için [bkz: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [Nasıl Yazılır: Özel Durumları Günlüğe Kaydedin.](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)</span><span class="sxs-lookup"><span data-stu-id="49e1f-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="49e1f-123">Bir derleme için dosya günlüğü dinleyicisini yapılandırıldıktan sonra, `My.Application.Log` bu derlemeden yazan tüm iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="49e1f-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="49e1f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49e1f-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="49e1f-125">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="49e1f-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="49e1f-126">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="49e1f-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)

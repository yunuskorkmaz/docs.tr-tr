---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: olay bilgilerini metin dosyasına yazma (Visual Basic)'
title: 'Nasıl yapılır: Olay Bilgilerini Metin Dosyasına Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: eb6fab9976c010080c0cffa37edd4f790dc73956
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775142"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="a5f2f-103">Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5f2f-103">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="a5f2f-104">`My.Application.Log` `My.Log` Uygulamanızda gerçekleşen olaylar hakkındaki bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-104">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="a5f2f-105">Bu örnek, `My.Application.Log.WriteEntry` izleme bilgilerini bir günlük dosyasına kaydetmek için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-105">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="a5f2f-106">Dosya günlüğü dinleyicisini eklemek ve yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="a5f2f-106">To add and configure the file log listener</span></span>

1. <span data-ttu-id="a5f2f-107">**Çözüm Gezgini** app.config sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-107">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="a5f2f-108">\- veya</span><span class="sxs-lookup"><span data-stu-id="a5f2f-108">\- or -</span></span>

     <span data-ttu-id="a5f2f-109">app.config dosya yoksa:</span><span class="sxs-lookup"><span data-stu-id="a5f2f-109">If there is no app.config file:</span></span>

    1. <span data-ttu-id="a5f2f-110">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-110">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="a5f2f-111">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-111">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="a5f2f-112">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-112">Click **Add**.</span></span>

2. <span data-ttu-id="a5f2f-113">`<listeners>`Uygulama yapılandırma dosyasında bölümünü bulun.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-113">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="a5f2f-114">Bölümünün, \<listeners> \<source> \<system.diagnostics> üst düzey bölüm altında iç içe yerleştirilmiş olan bölümünde iç içe yerleştirilmiş olan "DefaultSource" adlı ad özniteliğiyle birlikte bölümünü bulabilirsiniz \<configuration> .</span><span class="sxs-lookup"><span data-stu-id="a5f2f-114">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="a5f2f-115">Bu öğeyi bu bölüme ekleyin `<listeners>` :</span><span class="sxs-lookup"><span data-stu-id="a5f2f-115">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="a5f2f-116">Bölümünün `<sharedListeners>` `<system.diagnostics>` üst düzey bölüm altında iç içe olan bölümünü bulun `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="a5f2f-116">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="a5f2f-117">Bu öğeyi bu bölüme ekleyin `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="a5f2f-117">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="a5f2f-118">`customlocation`Özniteliğin değerini günlük dizinine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-118">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a5f2f-119">Bir dinleyici özelliğinin değerini ayarlamak için, özelliğindeki aynı ada sahip bir özniteliği kullanın, ad küçük harfli tüm harfler.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-119">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="a5f2f-120">Örneğin, `location` ve öznitelikleri, `customlocation` <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve özelliklerinin değerlerini ayarlar <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> .</span><span class="sxs-lookup"><span data-stu-id="a5f2f-120">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="a5f2f-121">Olay bilgilerini dosya günlüğüne yazmak için</span><span class="sxs-lookup"><span data-stu-id="a5f2f-121">To write event information to the file log</span></span>

<span data-ttu-id="a5f2f-122">`My.Application.Log.WriteEntry` `My.Application.Log.WriteException` Dosya günlüğüne bilgi yazmak için veya yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-122">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="a5f2f-123">Daha fazla bilgi için bkz. [nasıl yapılır: yazma günlüğü iletileri](how-to-write-log-messages.md) ve [nasıl yapılır: günlüğe kaydetme özel durumları](how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="a5f2f-123">For more information, see [How to: Write Log Messages](how-to-write-log-messages.md) and [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

<span data-ttu-id="a5f2f-124">Bir derlemenin dosya günlüğü dinleyicisini yapılandırdıktan sonra, `My.Application.Log` Bu derlemeden yazan tüm iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-124">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5f2f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="a5f2f-126">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="a5f2f-126">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="a5f2f-127">Nasıl yapılır: Özel Durumları Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="a5f2f-127">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)

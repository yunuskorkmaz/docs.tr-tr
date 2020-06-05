---
title: 'Nasıl yapılır: Olay Bilgilerini Metin Dosyasına Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 6e83f8450ca7be8a2dcd5ff43eab3dd2ec0d2f1b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410068"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="48b95-102">Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48b95-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="48b95-103">`My.Application.Log` `My.Log` Uygulamanızda gerçekleşen olaylar hakkındaki bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48b95-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="48b95-104">Bu örnek, `My.Application.Log.WriteEntry` izleme bilgilerini bir günlük dosyasına kaydetmek için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="48b95-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="48b95-105">Dosya günlüğü dinleyicisini eklemek ve yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="48b95-105">To add and configure the file log listener</span></span>

1. <span data-ttu-id="48b95-106">**Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="48b95-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="48b95-107">\-veya</span><span class="sxs-lookup"><span data-stu-id="48b95-107">\- or -</span></span>

     <span data-ttu-id="48b95-108">App. config dosyası yoksa:</span><span class="sxs-lookup"><span data-stu-id="48b95-108">If there is no app.config file:</span></span>

    1. <span data-ttu-id="48b95-109">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="48b95-109">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="48b95-110">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="48b95-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="48b95-111">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="48b95-111">Click **Add**.</span></span>

2. <span data-ttu-id="48b95-112">`<listeners>`Uygulama yapılandırma dosyasında bölümünü bulun.</span><span class="sxs-lookup"><span data-stu-id="48b95-112">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="48b95-113">Bölümünün, \<listeners> \<source> \<system.diagnostics> üst düzey bölüm altında iç içe yerleştirilmiş olan bölümünde iç içe yerleştirilmiş olan "DefaultSource" adlı ad özniteliğiyle birlikte bölümünü bulabilirsiniz \<configuration> .</span><span class="sxs-lookup"><span data-stu-id="48b95-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="48b95-114">Bu öğeyi bu bölüme ekleyin `<listeners>` :</span><span class="sxs-lookup"><span data-stu-id="48b95-114">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="48b95-115">Bölümünün `<sharedListeners>` `<system.diagnostics>` üst düzey bölüm altında iç içe olan bölümünü bulun `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="48b95-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="48b95-116">Bu öğeyi bu bölüme ekleyin `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="48b95-116">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="48b95-117">`customlocation`Özniteliğin değerini günlük dizinine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48b95-117">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="48b95-118">Bir dinleyici özelliğinin değerini ayarlamak için, özelliğindeki aynı ada sahip bir özniteliği kullanın, ad küçük harfli tüm harfler.</span><span class="sxs-lookup"><span data-stu-id="48b95-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="48b95-119">Örneğin, `location` ve öznitelikleri, `customlocation` <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve özelliklerinin değerlerini ayarlar <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> .</span><span class="sxs-lookup"><span data-stu-id="48b95-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="48b95-120">Olay bilgilerini dosya günlüğüne yazmak için</span><span class="sxs-lookup"><span data-stu-id="48b95-120">To write event information to the file log</span></span>

<span data-ttu-id="48b95-121">`My.Application.Log.WriteEntry` `My.Application.Log.WriteException` Dosya günlüğüne bilgi yazmak için veya yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="48b95-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="48b95-122">Daha fazla bilgi için bkz. [nasıl yapılır: yazma günlüğü iletileri](how-to-write-log-messages.md) ve [nasıl yapılır: günlüğe kaydetme özel durumları](how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="48b95-122">For more information, see [How to: Write Log Messages](how-to-write-log-messages.md) and [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

<span data-ttu-id="48b95-123">Bir derlemenin dosya günlüğü dinleyicisini yapılandırdıktan sonra, `My.Application.Log` Bu derlemeden yazan tüm iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="48b95-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="48b95-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48b95-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="48b95-125">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="48b95-125">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="48b95-126">Nasıl yapılır: Özel Durumları Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="48b95-126">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)

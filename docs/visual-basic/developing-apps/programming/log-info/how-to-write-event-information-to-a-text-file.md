---
title: 'Nasıl yapılır: Olay bilgilerini metin dosyasına yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 4a34b57eb0a22dcf206456775cdd5817431292e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956830"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="912e7-102">Nasıl yapılır: Olay bilgilerini metin dosyasına yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="912e7-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>
<span data-ttu-id="912e7-103">Uygulamanızda gerçekleşen olaylar hakkındaki `My.Application.Log` bilgileri `My.Log` günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="912e7-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="912e7-104">Bu örnek, `My.Application.Log.WriteEntry` izleme bilgilerini bir günlük dosyasına kaydetmek için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="912e7-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>  
  
### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="912e7-105">Dosya günlüğü dinleyicisini eklemek ve yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="912e7-105">To add and configure the file log listener</span></span>  
  
1. <span data-ttu-id="912e7-106">**Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="912e7-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="912e7-107">\- veya -</span><span class="sxs-lookup"><span data-stu-id="912e7-107">\- or -</span></span>  
  
     <span data-ttu-id="912e7-108">App. config dosyası yoksa:</span><span class="sxs-lookup"><span data-stu-id="912e7-108">If there is no app.config file:</span></span>  
  
    1. <span data-ttu-id="912e7-109">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="912e7-109">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="912e7-110">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="912e7-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="912e7-111">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="912e7-111">Click **Add**.</span></span>  
  
2. <span data-ttu-id="912e7-112">Uygulama yapılandırma dosyasında bölümünü bulun. `<listeners>`</span><span class="sxs-lookup"><span data-stu-id="912e7-112">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="912e7-113">Üst düzey \< \< \<altında içiçeyerleştirilmişolanSystem.Diagnostics>bölümündeiçiçeyerleştirilmişolan"DefaultSource"adözniteliğiyle,kaynak>bölümündebulunanListeners>bölümünübulabilirsiniz.\<yapılandırma > bölümü.</span><span class="sxs-lookup"><span data-stu-id="912e7-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>  
  
3. <span data-ttu-id="912e7-114">Bu öğeyi `<listeners>` bu bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="912e7-114">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. <span data-ttu-id="912e7-115">Bölümünün üst `<system.diagnostics>` düzey`<configuration>` bölüm altında iç içe olan bölümünü bulun. `<sharedListeners>`</span><span class="sxs-lookup"><span data-stu-id="912e7-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>  
  
5. <span data-ttu-id="912e7-116">Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="912e7-116">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     <span data-ttu-id="912e7-117">`customlocation` Özniteliğin değerini günlük dizinine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="912e7-117">Change the value of the `customlocation` attribute to the log directory.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="912e7-118">Bir dinleyici özelliğinin değerini ayarlamak için, özelliğindeki aynı ada sahip bir özniteliği kullanın, ad küçük harfli tüm harfler.</span><span class="sxs-lookup"><span data-stu-id="912e7-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="912e7-119">Örneğin, `location` ve `customlocation` öznitelikleri, <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> özelliklerinin değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="912e7-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>  
  
### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="912e7-120">Olay bilgilerini dosya günlüğüne yazmak için</span><span class="sxs-lookup"><span data-stu-id="912e7-120">To write event information to the file log</span></span>  
  
- <span data-ttu-id="912e7-121">Dosya günlüğüne bilgi `My.Application.Log.WriteException` yazmak için veyayönteminikullanın.`My.Application.Log.WriteEntry`</span><span class="sxs-lookup"><span data-stu-id="912e7-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="912e7-122">Daha fazla bilgi için [nasıl yapılır: Yazma günlüğü iletileri](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: Günlük özel](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)durumları.</span><span class="sxs-lookup"><span data-stu-id="912e7-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="912e7-123">Bir derlemenin dosya günlüğü dinleyicisini yapılandırdıktan sonra, bu derlemeden `My.Application.Log` yazan tüm iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="912e7-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912e7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="912e7-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="912e7-125">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="912e7-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="912e7-126">Nasıl yapılır: Günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="912e7-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)

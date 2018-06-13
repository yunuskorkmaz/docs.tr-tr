---
title: 'Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 3adb594ee42b7b1fad77a54af04bb9f37f30c19a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589064"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="07a28-102">Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07a28-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>
<span data-ttu-id="07a28-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="07a28-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="07a28-104">Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` yöntemi izleme bilgilerini bir günlük dosyasına kaydedin.</span><span class="sxs-lookup"><span data-stu-id="07a28-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>  
  
### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="07a28-105">Ekleme ve dosya günlüğünü dinleyicisi yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="07a28-105">To add and configure the file log listener</span></span>  
  
1.  <span data-ttu-id="07a28-106">App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.</span><span class="sxs-lookup"><span data-stu-id="07a28-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="07a28-107">\- veya -</span><span class="sxs-lookup"><span data-stu-id="07a28-107">\- or -</span></span>  
  
     <span data-ttu-id="07a28-108">Herhangi bir app.config dosyası ise:</span><span class="sxs-lookup"><span data-stu-id="07a28-108">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="07a28-109">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="07a28-109">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="07a28-110">Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="07a28-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="07a28-111">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="07a28-111">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="07a28-112">Bulun `<listeners>` uygulama yapılandırma dosyasında bölüm.</span><span class="sxs-lookup"><span data-stu-id="07a28-112">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="07a28-113">Size \<dinleyicileri > bölümüne \<kaynak > bölümü altında yer alan "DefaultSource" ad özniteliği olan \<system.diagnostics > altında en üst düzey içiçebölüm\<yapılandırma > bölümü.</span><span class="sxs-lookup"><span data-stu-id="07a28-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>  
  
3.  <span data-ttu-id="07a28-114">Bu öğe için eklemek `<listeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="07a28-114">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4.  <span data-ttu-id="07a28-115">Bulun `<sharedListeners>` bölümüne `<system.diagnostics>` altında en üst düzey iç içe geçmiş bölüm `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="07a28-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="07a28-116">Bu öğe için eklemek `<sharedListeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="07a28-116">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     <span data-ttu-id="07a28-117">Değerini değiştirme `customlocation` özniteliği günlük dizini.</span><span class="sxs-lookup"><span data-stu-id="07a28-117">Change the value of the `customlocation` attribute to the log directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07a28-118">Dinleyici özelliğinin değeri ayarlamak için tüm adı küçük harflerle sahip özellik aynı ada sahip bir öznitelik kullanın.</span><span class="sxs-lookup"><span data-stu-id="07a28-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="07a28-119">Örneğin, `location` ve `customlocation` özniteliklerini ayarla değerlerini <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="07a28-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>  
  
### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="07a28-120">Olay bilgilerini dosya günlüğüne yazmak için</span><span class="sxs-lookup"><span data-stu-id="07a28-120">To write event information to the file log</span></span>  
  
-   <span data-ttu-id="07a28-121">Kullanım `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` yöntemi dosya günlük bilgilerini yazar.</span><span class="sxs-lookup"><span data-stu-id="07a28-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="07a28-122">Daha fazla bilgi için bkz: [nasıl yapılır: günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="07a28-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="07a28-123">Bir derlemenin dosya günlük dinleyicisi yapılandırdıktan sonra tüm aldığı iletileri `My.Application.Log` bütünleştirilmiş koddan yazar.</span><span class="sxs-lookup"><span data-stu-id="07a28-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a28-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07a28-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="07a28-125">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="07a28-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="07a28-126">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="07a28-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)

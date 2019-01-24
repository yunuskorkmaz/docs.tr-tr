---
title: 'Nasıl yapılır: Olay bilgilerini metin dosyasına (Visual Basic) yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 198e78b9b94111a4c07266287b943cbbccb2e978
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646181"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="f499e-102">Nasıl yapılır: Olay bilgilerini metin dosyasına (Visual Basic) yazma</span><span class="sxs-lookup"><span data-stu-id="f499e-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>
<span data-ttu-id="f499e-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` gerçekleşen olaylar hakkında bilgileri, uygulamanızda oturum nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f499e-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="f499e-104">Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` bir günlük dosyasına izleme bilgileri günlüğe kaydetmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f499e-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>  
  
### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="f499e-105">Ekleme ve dosya günlüğünü dinleyici yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f499e-105">To add and configure the file log listener</span></span>  
  
1.  <span data-ttu-id="f499e-106">App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.</span><span class="sxs-lookup"><span data-stu-id="f499e-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="f499e-107">\- veya -</span><span class="sxs-lookup"><span data-stu-id="f499e-107">\- or -</span></span>  
  
     <span data-ttu-id="f499e-108">App.config dosyası yoksa:</span><span class="sxs-lookup"><span data-stu-id="f499e-108">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="f499e-109">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="f499e-109">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="f499e-110">Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="f499e-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="f499e-111">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f499e-111">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="f499e-112">Bulun `<listeners>` uygulama yapılandırma dosyasında bölümü.</span><span class="sxs-lookup"><span data-stu-id="f499e-112">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="f499e-113">Size \<dinleyicileri > konusundaki \<kaynak > bölümü altında iç içe "DefaultSource" ad özniteliği ile \<system.diagnostics > üst düzey altındaiçiçebölümünde\<yapılandırma > bölümü.</span><span class="sxs-lookup"><span data-stu-id="f499e-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>  
  
3.  <span data-ttu-id="f499e-114">Bu öğe ekleyen `<listeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="f499e-114">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4.  <span data-ttu-id="f499e-115">Bulun `<sharedListeners>` konusundaki `<system.diagnostics>` bölümünde, üst düzey altında iç içe geçmiş `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="f499e-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="f499e-116">Bu öğe ekleyen `<sharedListeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="f499e-116">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     <span data-ttu-id="f499e-117">Değiştirin `customlocation` günlük dizini için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f499e-117">Change the value of the `customlocation` attribute to the log directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f499e-118">Dinleyici özelliğin değerini ayarlamak için tüm adı küçük harfle ile özelliğiyle aynı ada sahip bir öznitelik kullanın.</span><span class="sxs-lookup"><span data-stu-id="f499e-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="f499e-119">Örneğin, `location` ve `customlocation` özniteliklerini ayarlayın değerlerini <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> ve <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="f499e-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>  
  
### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="f499e-120">Olay bilgilerini dosya günlüğüne yazmak için</span><span class="sxs-lookup"><span data-stu-id="f499e-120">To write event information to the file log</span></span>  
  
-   <span data-ttu-id="f499e-121">Kullanım `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` bilgi dosyası günlüğüne yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f499e-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="f499e-122">Daha fazla bilgi için [nasıl yapılır: Günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="f499e-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="f499e-123">Bir derleme için dosya günlük dinleyici yapılandırdıktan sonra tüm aldığı iletileri `My.Application.Log` Bu bütünleştirilmiş koddan yazar.</span><span class="sxs-lookup"><span data-stu-id="f499e-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f499e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f499e-124">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="f499e-125">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="f499e-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="f499e-126">Nasıl yapılır: Günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="f499e-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)

---
title: My.Application.Log (Visual Basic) bilgileri yazdığı yeri değiştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: ed7f88b20e4d519e67c8ef7b9f74909a38ea9c14
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829323"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="dce6f-102">İzlenecek yol: My.Application.Log (Visual Basic) bilgileri yazdığı yeri değiştirme</span><span class="sxs-lookup"><span data-stu-id="dce6f-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="dce6f-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` gerçekleşen olaylar hakkında bilgileri, uygulamanızda oturum nesneleri.</span><span class="sxs-lookup"><span data-stu-id="dce6f-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="dce6f-104">Bu izlenecek yol varsayılan ayarları geçersiz kılar ve neden gösterilmektedir `Log` diğer günlük dinleyicileri için yazılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="dce6f-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dce6f-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="dce6f-105">Prerequisites</span></span>  
 <span data-ttu-id="dce6f-106">`Log` Nesne için birkaç günlük dinleyicileri bilgileri yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dce6f-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="dce6f-107">Yapılandırmaları değiştirmeden önce geçerli yapılandırmasını günlük dinleyicileri belirlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="dce6f-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="dce6f-108">Daha fazla bilgi için [izlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="dce6f-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="dce6f-109">Gözden geçirmek isteyebilirsiniz [nasıl yapılır: Olay bilgilerini metin dosyasına yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) veya [nasıl yapılır: Uygulama olay günlüğüne yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="dce6f-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>  
  
### <a name="to-add-listeners"></a><span data-ttu-id="dce6f-110">Dinleyiciler eklemek için</span><span class="sxs-lookup"><span data-stu-id="dce6f-110">To add listeners</span></span>  
  
1.  <span data-ttu-id="dce6f-111">App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.</span><span class="sxs-lookup"><span data-stu-id="dce6f-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="dce6f-112">\- veya -</span><span class="sxs-lookup"><span data-stu-id="dce6f-112">\- or -</span></span>  
  
     <span data-ttu-id="dce6f-113">App.config dosyası yoksa:</span><span class="sxs-lookup"><span data-stu-id="dce6f-113">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="dce6f-114">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="dce6f-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="dce6f-115">Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="dce6f-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="dce6f-116">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="dce6f-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="dce6f-117">Bulun `<listeners>` bölümündeki `<source>` ile bölümünde `name` "DefaultSource" özniteliğini `<sources>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="dce6f-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="dce6f-118">`<sources>` Bölümü olduğundan `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="dce6f-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="dce6f-119">Bu öğeleri eklemek için `<listeners>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="dce6f-119">Add these elements to that `<listeners>` section.</span></span>  
  
    ```xml  
    <!-- Uncomment to connect the application file log. -->  
    <!-- <add name="FileLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="EventLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="Delimited" /> -->  
    <!-- Uncomment to connect the XML log. -->  
    <!-- <add name="XmlWriter" /> -->  
    <!-- Uncomment to connect the console log. -->  
    <!-- <add name="Console" /> -->  
    ```  
  
4.  <span data-ttu-id="dce6f-120">Almak istediğiniz günlük dinleyicileri açıklamadan çıkarın `Log` iletileri.</span><span class="sxs-lookup"><span data-stu-id="dce6f-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>  
  
5.  <span data-ttu-id="dce6f-121">Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="dce6f-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="dce6f-122">Bu öğeleri eklemek için `<sharedListeners>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="dce6f-122">Add these elements to that `<sharedListeners>` section.</span></span>  
  
    ```xml  
    <add name="FileLog"  
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
               Microsoft.VisualBasic, Version=8.0.0.0,   
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
         initializeData="FileLogWriter" />  
    <add name="EventLog"  
         type="System.Diagnostics.EventLogTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="sample application"/>  
    <add name="Delimited"   
         type="System.Diagnostics.DelimitedListTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleDelimitedFile.txt"  
         traceOutputOptions="DateTime" />  
    <add name="XmlWriter"  
         type="System.Diagnostics.XmlWriterTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleLogFile.xml" />  
    <add name="Console"  
         type="System.Diagnostics.ConsoleTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="true" />  
    ```  
  
7.  <span data-ttu-id="dce6f-123">App.config dosyasının içeriği aşağıdaki XML'e benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="dce6f-123">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Uncomment to connect the application file log. -->  
              <!-- <add name="FileLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="EventLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="Delimited" /> -->  
              <!-- Uncomment to connect the XML log. -->  
              <!-- <add name="XmlWriter" /> -->  
              <!-- Uncomment to connect the console log. -->  
              <!-- <add name="Console" /> -->  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
               initializeData="FileLogWriter" />  
          <add name="EventLog"  
               type="System.Diagnostics.EventLogTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="sample application"/>  
          <add name="Delimited"   
               type="System.Diagnostics.DelimitedListTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleDelimitedFile.txt"  
               traceOutputOptions="DateTime" />  
          <add name="XmlWriter"  
               type="System.Diagnostics.XmlWriterTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleLogFile.xml" />  
          <add name="Console"  
               type="System.Diagnostics.ConsoleTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="true" />  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="dce6f-124">Dinleyici yeniden yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="dce6f-124">To reconfigure a listener</span></span>  
  
1.  <span data-ttu-id="dce6f-125">Dinleyicinin bulun `<add>` öğesinden `<sharedListeners>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="dce6f-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>  
  
2.  <span data-ttu-id="dce6f-126">`type` Özniteliği dinleyici türü adını verir.</span><span class="sxs-lookup"><span data-stu-id="dce6f-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="dce6f-127">Bu tür devralmalıdır <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dce6f-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="dce6f-128">Kesin adlandırılmış tür adı doğru tür kullanıldığından emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dce6f-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="dce6f-129">Daha fazla bilgi için "kesin adlandırılmış tür başvurmak için" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dce6f-129">For more information, see the "To reference a strongly named type" section below.</span></span>  
  
     <span data-ttu-id="dce6f-130">Kullanabileceğiniz bazı türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dce6f-130">Some types that you can use are:</span></span>  
  
    -   <span data-ttu-id="dce6f-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyici, bir dosyayı günlüğe yazar.</span><span class="sxs-lookup"><span data-stu-id="dce6f-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>  
  
    -   <span data-ttu-id="dce6f-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> bilgileri tarafından belirtilen bilgisayarın olay günlüğüne yazan dinleyici `initializeData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="dce6f-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="dce6f-133"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> Ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> belirtilen dosyaya yazma dinleyici `initializeData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="dce6f-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="dce6f-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> dinleyici, komut satırı konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="dce6f-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>  
  
     <span data-ttu-id="dce6f-135">Burada günlük dinleyicileri diğer tür bilgilerini yazma hakkında daha fazla bilgi için bu türün belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="dce6f-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
3.  <span data-ttu-id="dce6f-136">Uygulama günlüğü dinleyici nesne oluşturduğunda, arabimini `initializeData` öznitelik oluşturucu parametresi olarak.</span><span class="sxs-lookup"><span data-stu-id="dce6f-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="dce6f-137">Anlamını `initializeData` öznitelik üzerinde İzleme dinleyicisi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dce6f-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>  
  
4.  <span data-ttu-id="dce6f-138">Günlük dinleyici oluşturduktan sonra uygulama dinleyicinin özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dce6f-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="dce6f-139">Bu özellikler diğer öznitelikleri tarafından tanımlanan `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="dce6f-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="dce6f-140">Belirli bir dinleyici özellikleri hakkında daha fazla bilgi için bu dinleyicinin türü için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="dce6f-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>  
  
### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="dce6f-141">Kesin adlandırılmış tür referansı</span><span class="sxs-lookup"><span data-stu-id="dce6f-141">To reference a strongly named type</span></span>  
  
1.  <span data-ttu-id="dce6f-142">Doğru tür günlük dinleyicinize için kullanıldığından emin olmak için tam nitelikli tür adı ve türü kesin adlandırılmış bütünleştirilmiş kod adı kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="dce6f-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="dce6f-143">Kesin adlandırılmış tür söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="dce6f-143">The syntax of a strongly named type is as follows:</span></span>  
  
     <span data-ttu-id="dce6f-144">\<*tür adı*>, \< *derleme adı*>, \< *sürüm numarası*>, \< *kültür*>, \< *tanımlayıcı ad*></span><span class="sxs-lookup"><span data-stu-id="dce6f-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>  
  
2.  <span data-ttu-id="dce6f-145">Bu kod örneği için tam type—"System.Diagnostics.FileLogTraceListener kesin adlandırılmış tür adını belirlemek bu durumda gösterilmektedir".</span><span class="sxs-lookup"><span data-stu-id="dce6f-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]  
  
     <span data-ttu-id="dce6f-146">Bu çıktı ve benzersiz olarak "dinleyiciler eklemek için" yordamı yukarıdaki olduğu gibi kesin adlandırılmış bir tür başvuru için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dce6f-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a><span data-ttu-id="dce6f-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dce6f-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="dce6f-148">Nasıl yapılır: Olay bilgilerini metin dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="dce6f-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="dce6f-149">Nasıl yapılır: Uygulama olay günlüğüne yazma</span><span class="sxs-lookup"><span data-stu-id="dce6f-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)

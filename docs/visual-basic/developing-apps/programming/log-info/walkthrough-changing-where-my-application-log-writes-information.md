---
title: "My.Application.Log (Visual Basic) bilgileri yazdığı yeri değiştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c4cd2e675bf1be4f065ee116795a95dae64d13d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="e2a5e-102">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2a5e-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="e2a5e-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="e2a5e-104">Bu kılavuz varsayılan ayarları geçersiz kılar ve neden gösterilmektedir `Log` diğer günlük dinleyicileri yazılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e2a5e-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e2a5e-105">Prerequisites</span></span>  
 <span data-ttu-id="e2a5e-106">`Log` Nesne için birden fazla günlük dinleyicileri bilgileri yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="e2a5e-107">Yapılandırmaları değiştirmeden önce günlük dinleyicileri geçerli yapılandırmasını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="e2a5e-108">Daha fazla bilgi için bkz: [izlenecek yol: belirleme nerede My.Application.Log Yazar bilgisini](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="e2a5e-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="e2a5e-109">Gözden geçirmek isteyebileceğiniz [nasıl yapılır: olay bilgilerini metin dosyasına yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) veya [nasıl yapılır: uygulama olay günlüğüne yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="e2a5e-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>  
  
### <a name="to-add-listeners"></a><span data-ttu-id="e2a5e-110">Dinleyicileri eklemek için</span><span class="sxs-lookup"><span data-stu-id="e2a5e-110">To add listeners</span></span>  
  
1.  <span data-ttu-id="e2a5e-111">App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="e2a5e-112">\-veya -</span><span class="sxs-lookup"><span data-stu-id="e2a5e-112">\- or -</span></span>  
  
     <span data-ttu-id="e2a5e-113">Herhangi bir app.config dosyası ise:</span><span class="sxs-lookup"><span data-stu-id="e2a5e-113">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="e2a5e-114">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="e2a5e-115">Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="e2a5e-116">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="e2a5e-117">Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource" özniteliğini `<sources>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="e2a5e-118">`<sources>` Bölümdür içinde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="e2a5e-119">Bu öğeler olarak Ekle `<listeners>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-119">Add these elements to that `<listeners>` section.</span></span>  
  
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
  
4.  <span data-ttu-id="e2a5e-120">Almak istediğiniz günlük dinleyicileri açıklamadan çıkarın `Log` iletileri.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>  
  
5.  <span data-ttu-id="e2a5e-121">Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="e2a5e-122">Bu öğeler olarak Ekle `<sharedListeners>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-122">Add these elements to that `<sharedListeners>` section.</span></span>  
  
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
  
7.  <span data-ttu-id="e2a5e-123">App.config dosyasının içeriğini aşağıdaki XML'e benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e2a5e-123">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="e2a5e-124">Dinleyici yeniden yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="e2a5e-124">To reconfigure a listener</span></span>  
  
1.  <span data-ttu-id="e2a5e-125">Dinleyici 's bulun `<add>` öğesinden `<sharedListeners>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>  
  
2.  <span data-ttu-id="e2a5e-126">`type` Özniteliği dinleyicisi türünün adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="e2a5e-127">Bu tür öğesinden devralmalıdır <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="e2a5e-128">Doğru türde kullanıldığından emin olmak için kesin adlandırılmış tür adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="e2a5e-129">Daha fazla bilgi için aşağıdaki "kesin adlandırılmış bir türü başvurmak için" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-129">For more information, see the "To reference a strongly named type" section below.</span></span>  
  
     <span data-ttu-id="e2a5e-130">Kullanabileceğiniz bazı türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e2a5e-130">Some types that you can use are:</span></span>  
  
    -   <span data-ttu-id="e2a5e-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> bir dosyayı günlüğe yazar dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>  
  
    -   <span data-ttu-id="e2a5e-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> bilgileri tarafından belirtilen bilgisayar olay günlüğüne yazar dinleyici `initializeData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="e2a5e-133"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> Ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> belirtilen dosyaya yazma dinleyicileri `initializeData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="e2a5e-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> komut satırı konsola dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>  
  
     <span data-ttu-id="e2a5e-135">Burada günlük dinleyicileri diğer tür bilgilerini yazma hakkında daha fazla bilgi için bu tür belgelerine başvurun.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
3.  <span data-ttu-id="e2a5e-136">Uygulama günlüğü dinleyici nesne oluşturduğunda, geçirir `initializeData` Oluşturucu parametresi olarak özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="e2a5e-137">Anlamını `initializeData` özniteliği üzerinde İzleme dinleyicisi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>  
  
4.  <span data-ttu-id="e2a5e-138">Günlük dinleyicisi oluşturduktan sonra uygulama dinleyiciyi'nın özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="e2a5e-139">Bu özellikleri diğer öznitelikleri tarafından tanımlanan `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="e2a5e-140">Belli bir Dinleyicide özellikleri hakkında daha fazla bilgi için dinleyici'nın türü için belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>  
  
### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="e2a5e-141">Türü kesin adlandırılmış bir tür referansı</span><span class="sxs-lookup"><span data-stu-id="e2a5e-141">To reference a strongly named type</span></span>  
  
1.  <span data-ttu-id="e2a5e-142">Doğru türde günlük dinleyici için kullanıldığından emin olmak için tam olarak nitelenmiş tür adını ve kesin adlandırılmış derleme adı kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="e2a5e-143">Türü kesin adlandırılmış bir türün söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e2a5e-143">The syntax of a strongly named type is as follows:</span></span>  
  
     <span data-ttu-id="e2a5e-144">\<*tür adı*>, \< *derleme adı*>, \< *sürüm numarası*>, \< *kültür*>, \< *kesin adı*></span><span class="sxs-lookup"><span data-stu-id="e2a5e-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>  
  
2.  <span data-ttu-id="e2a5e-145">Bu kod örneği için tam type—"System.Diagnostics.FileLogTraceListener kesin adlandırılmış tür adını belirlemek bu durumda gösterilmiştir".</span><span class="sxs-lookup"><span data-stu-id="e2a5e-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     <span data-ttu-id="e2a5e-146">Bu çıktı ve benzersiz olduğu gibi "dinleyicileri eklemek için" Yukarıdaki yordamı kesin adlandırılmış bir türe başvuruda için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a><span data-ttu-id="e2a5e-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-147">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>  
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>  
 [<span data-ttu-id="e2a5e-148">Nasıl yapılır: olay bilgilerini metin dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="e2a5e-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)  
 [<span data-ttu-id="e2a5e-149">Nasıl yapılır: uygulama olay günlüğüne yazma</span><span class="sxs-lookup"><span data-stu-id="e2a5e-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)

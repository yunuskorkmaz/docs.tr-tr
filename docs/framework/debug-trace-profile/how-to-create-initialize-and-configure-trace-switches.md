---
title: 'Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87170035df47e7605d25531df4b0759bf121ad80
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325715"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="e3976-102">Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="e3976-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="e3976-103">İzleme anahtarları etkinleştirmek, devre dışı bırakın ve İzleme çıkışı filtrelemek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3976-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="e3976-104">Oluşturma ve bir izleme anahtarı başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="e3976-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="e3976-105">İzleme anahtarları kullanmak için önce bunları oluşturur ve bunları kodunuzda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="e3976-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="e3976-106">Anahtar nesneleri içinden oluşturabileceğiniz iki önceden tanımlanmış sınıfı vardır: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> sınıfı ve <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e3976-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="e3976-107">Kullanacağınız <xref:System.Diagnostics.BooleanSwitch> yalnızca olup olmadığı bir izleme iletisi görünür hakkında; sizin varsa, kullanacağınız <xref:System.Diagnostics.TraceSwitch> izleme düzeyleri arasında ayrım istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="e3976-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="e3976-108">Kullanıyorsanız bir <xref:System.Diagnostics.TraceSwitch>, kendi hata ayıklama iletilerini tanımlamak ve bunları farklı izleme düzeyleriyle ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="e3976-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="e3976-109">Her iki tür anahtar, izleme veya hata ayıklama ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3976-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="e3976-110">Varsayılan olarak, bir <xref:System.Diagnostics.BooleanSwitch> devre dışı bırakıldı ve <xref:System.Diagnostics.TraceSwitch> düzeyine ayarlanmış <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e3976-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e3976-111">İzleme anahtarları oluşturulur ve bunları kullanabilecek kodunuzu herhangi bir bölümü yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e3976-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="e3976-112">Kodda izleme düzeylerini ve diğer yapılandırma seçeneklerini ayarlayabilirsiniz ancak anahtarlarınızda durumunu yönetmek için yapılandırma dosyasını kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="e3976-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="e3976-113">Daha fazla esneklik sağlar, anahtarların yapılandırmasını yönetme yapılandırma sistemi olmasıdır — açma ve kapatma çeşitli anahtarları ve uygulamanızı yeniden derlemeden düzeylerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e3976-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="e3976-114">Oluşturma ve bir izleme anahtarı'nı başlatmak için</span><span class="sxs-lookup"><span data-stu-id="e3976-114">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="e3976-115">Bir anahtar ya da türü olarak tanımlamanız <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> veya türü <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> ve anahtar açıklaması ve adını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e3976-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="e3976-116">Uygulamanızın izleme anahtarını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e3976-116">Configure your trace switch.</span></span> <span data-ttu-id="e3976-117">Daha fazla bilgi için [izleme anahtarları yapılandırma](#configure).</span><span class="sxs-lookup"><span data-stu-id="e3976-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="e3976-118">Aşağıdaki kod, her türden iki anahtarlarını oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e3976-118">The following code creates two switches, one of each type:</span></span>  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =   
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =   
       new System.Diagnostics.TraceSwitch("General",   
       "Entire application");  
    ```  
  
<a name="configure"></a>   
## <a name="configuring-trace-switches"></a><span data-ttu-id="e3976-119">İzleme anahtarları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e3976-119">Configuring trace switches</span></span>  
 <span data-ttu-id="e3976-120">Uygulamanız dağıtıldıktan sonra hala etkinleştirebilir veya uygulamanızda izleme anahtarları yapılandırarak izleme çıkışını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="e3976-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="e3976-121">Bir anahtarı yapılandırmadan, başlatıldıktan sonra bir dış kaynaktan değerini değiştirme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e3976-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="e3976-122">Yapılandırma dosyası kullanarak anahtar nesne değerleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3976-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="e3976-123">Açıp kapatmak için bir izleme anahtarı yapılandırabilir veya miktarını belirleyen kendi düzeyini ayarlamak ve iletilerin yazmanız boyunca dinleyicilere geçirir.</span><span class="sxs-lookup"><span data-stu-id="e3976-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="e3976-124">Anahtarlarınızda .config dosyasını kullanarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e3976-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="e3976-125">Bir Web uygulaması için bu yöntem, projeyle ilişkili Web.config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e3976-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="e3976-126">Bir Windows uygulamasında, bu dosya (uygulama adı) olarak adlandırılır. exe.config olarak. Dağıtılan bir uygulamada, bu dosya, yürütülebilir dosya ile aynı klasörde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3976-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="e3976-127">Uygulamanızı ilk kez bir anahtar örneği oluşturan kodu yürütüldüğünde, adlandırılmış anahtarı hakkında bilgi izleme düzeyi için yapılandırma dosyasını denetler.</span><span class="sxs-lookup"><span data-stu-id="e3976-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="e3976-128">Yapılandırma dosyası belirli bir anahtar için yalnızca bir kez izleme sistemi inceler; uygulamanızın oluşturduğu anahtar ilk kez.</span><span class="sxs-lookup"><span data-stu-id="e3976-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="e3976-129">Dağıtılan bir uygulamada, uygulamanız çalışmadığı zaman, anahtar nesneleri yapılandırarak, izleme kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3976-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="e3976-130">Genellikle bu anahtar nesneleri üzerinde ve devre dışı veya izleme düzeylerini değiştirip ardından uygulamanızı yeniden başlatmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="e3976-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="e3976-131">Bir anahtar örneğini oluşturduğunuzda, ayrıca, iki bağımsız değişkeni belirterek başlatın: bir *displayName* bağımsız değişken ve *açıklama* bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="e3976-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="e3976-132">*DisplayName* bağımsız değişken Oluşturucu kümelerinin <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> özelliği <xref:System.Diagnostics.Switch> sınıfı örneği.</span><span class="sxs-lookup"><span data-stu-id="e3976-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="e3976-133">*DisplayName* anahtarını .config dosyasında yapılandırmak için kullanılan addır ve *açıklama* bağımsız değişkeni, anahtar ve hangi denetimleri iletileri kısa bir açıklamasını döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="e3976-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="e3976-134">Yapılandırmak için bir anahtar adını belirten ek olarak, bir anahtarın değerini de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3976-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="e3976-135">Bu değer bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="e3976-135">This value is an Integer.</span></span> <span data-ttu-id="e3976-136">İçin <xref:System.Diagnostics.BooleanSwitch>, 0 değerine karşılık gelen **kapalı**, ve sıfır dışında bir değere karşılık gelen **üzerinde**.</span><span class="sxs-lookup"><span data-stu-id="e3976-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="e3976-137">İçin <xref:System.Diagnostics.TraceSwitch>0,1,2,3 ve 4 karşılık gelen **kapalı**, **hata**, **uyarı**, **bilgisi**, ve **ayrıntılı**sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="e3976-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="e3976-138">Herhangi 4 olarak işlenir büyük sayı **ayrıntılı**ve her sayı daha az sıfır değerlendirilir daha **kapalı**.</span><span class="sxs-lookup"><span data-stu-id="e3976-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3976-139">.NET Framework sürüm 2. 0'da, metin anahtar değeri belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3976-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="e3976-140">Örneğin, `true` için bir <xref:System.Diagnostics.BooleanSwitch> veya bir sabit listesi değeri gibi temsil eden metin `Error` için bir <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="e3976-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="e3976-141">Satır `<add name="myTraceSwitch" value="Error" />` eşdeğerdir `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="e3976-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="e3976-142">Son kullanıcıların uygulama izleme anahtarları yapılandırabilmesi için sırada uygulamanızda anahtarlarla ilgili ayrıntılı belgelere sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="e3976-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="e3976-143">Hangi anahtarları ne denetlemek ve nasıl açıp kapatmak ayrıntılı.</span><span class="sxs-lookup"><span data-stu-id="e3976-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="e3976-144">Son kullanıcınızın, uygun Yardım açıklamaları olan bir .config dosyası ile de sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3976-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="e3976-145">İzleme anahtarları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e3976-145">To configure trace switches</span></span>  
  
1. <span data-ttu-id="e3976-146">İzleme anahtarları kullanmak için önce bunları oluşturmak ve bunları kodunuzda bölümünde açıklandığı gibi yerleştirmek [oluşturma ve bir izleme anahtarı başlatma](#create).</span><span class="sxs-lookup"><span data-stu-id="e3976-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="e3976-147">Projenize bir yapılandırma dosyası (app.config veya Web.config), ardından gelen içermiyorsa **proje** menüsünde **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e3976-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    -   <span data-ttu-id="e3976-148">**Visual Basic:** İçinde **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="e3976-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="e3976-149">Uygulama yapılandırma dosyası oluşturulur ve açılır.</span><span class="sxs-lookup"><span data-stu-id="e3976-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="e3976-150">Bu, kök öğesi bir XML belgesi</span><span class="sxs-lookup"><span data-stu-id="e3976-150">This is an XML document whose root element is</span></span> `<configuration>.`  
  
    -   <span data-ttu-id="e3976-151">**Görsel C#:** İçinde **Yeni Öğe Ekle** iletişim kutusunda **XML dosyası**.</span><span class="sxs-lookup"><span data-stu-id="e3976-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="e3976-152">Bu dosya adı **app.config**. XML Düzenleyicisi'nde XML bildiriminden sonra aşağıdaki XML ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3976-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="e3976-153">App.config dosyasını proje derlendiğinde, proje çıktı klasörüne kopyalanır ve yeniden adlandırılır *applicationname*. exe.config olarak.</span><span class="sxs-lookup"><span data-stu-id="e3976-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="e3976-154">Sonra `<configuration>` önce etiket `</configuration>` etiketi, anahtarlarınızda yapılandırmak için uygun XML ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3976-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="e3976-155">Aşağıdaki örnekler gösteren bir **BooleanSwitch** ile bir **DisplayName** özelliği `DataMessageSwitch` ve **TraceSwitch** ile bir **DisplayName**  özelliği `TraceLevelSwitch`.</span><span class="sxs-lookup"><span data-stu-id="e3976-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="e3976-156">Bu yapılandırmada her iki anahtarları kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3976-156">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="e3976-157">Etkinleştirmek gerekiyorsa bir **BooleanSwitch**, gibi `DataMessagesSwitch` değiştirmek önceki örnekte gösterilen **değer** 0 dışındaki herhangi bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e3976-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="e3976-158">Etkinleştirmek gerekiyorsa bir **TraceSwitch**, gibi `TraceLevelSwitch` değiştirmek önceki örnekte gösterilen **değer** uygun düzeyi ayarı (1-4).</span><span class="sxs-lookup"><span data-stu-id="e3976-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="e3976-159">Son kullanıcı anahtarları uygun şekilde yapılandırmak için değiştirmek için hangi değerlerin açık bir anlama sahiptir açıklamaları .config dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3976-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="e3976-160">Aşağıdaki örnek, Yorumlar dahil olmak üzere son kodu nasıl görünebileceği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e3976-160">The following example shows how the final code, including comments, might look:</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e3976-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3976-161">See also</span></span>

- [<span data-ttu-id="e3976-162">İzleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="e3976-162">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="e3976-163">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="e3976-163">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="e3976-164">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="e3976-164">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="e3976-165">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e3976-165">Trace and Debug Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)

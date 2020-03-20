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
ms.openlocfilehash: 8bf3b974ff0ef9f719274ab684b3dce85295c917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181833"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="81c57-102">Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="81c57-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="81c57-103">İzleme anahtarları, izleme çıktısını etkinleştirmenizi, devre dışı bırakmanızı ve filtrelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="81c57-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="81c57-104">İzleme anahtarı oluşturma ve başlatma</span><span class="sxs-lookup"><span data-stu-id="81c57-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="81c57-105">İzleme anahtarlarını kullanmak için önce bunları oluşturmanız ve kodunuza yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="81c57-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="81c57-106">Anahtar nesneleri oluşturabileceğiniz önceden tanımlanmış iki sınıf vardır: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> sınıf <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> ve sınıf.</span><span class="sxs-lookup"><span data-stu-id="81c57-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="81c57-107">Yalnızca bir <xref:System.Diagnostics.BooleanSwitch> izleme iletisi görünüp görünmediğini önemsiyorsanız kullanırsınız; izleme düzeyleri <xref:System.Diagnostics.TraceSwitch> arasında ayrım yapmak istiyorsanız kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="81c57-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="81c57-108">Bir <xref:System.Diagnostics.TraceSwitch>, kendi hata ayıklama iletileri tanımlamak ve farklı izleme düzeyleri ile ilişkilendirmek kullanıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="81c57-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="81c57-109">Her iki anahtar türünü de izleme veya hata ayıklama ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81c57-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="81c57-110">Varsayılan olarak, <xref:System.Diagnostics.BooleanSwitch> a devre <xref:System.Diagnostics.TraceSwitch> dışı bırakılır <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>ve a düzeyine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="81c57-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="81c57-111">İzleme anahtarları oluşturulabilir ve kodunuzun bunları kullanabilecek herhangi bir bölümüne yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="81c57-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="81c57-112">İzleme düzeylerini ve koddaki diğer yapılandırma seçeneklerini ayarlayabilirsiniz, ancak anahtarlarınızın durumunu yönetmek için yapılandırma dosyasını kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="81c57-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="81c57-113">Bunun nedeni, yapılandırma sistemindeki anahtarlarınızın yapılandırmasını yönetmenin size daha fazla esneklik sunabileceğidir — uygulamanızı yeniden derlemeden çeşitli anahtarları açıp kapatabilir ve düzeyleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81c57-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="81c57-114">İzleme anahtarı oluşturmak ve başlatma</span><span class="sxs-lookup"><span data-stu-id="81c57-114">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="81c57-115">Bir anahtarı tür <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> veya <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> tür olarak tanımlayın ve anahtarın adını ve açıklamasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="81c57-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="81c57-116">İzleme anahtarınızı yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="81c57-116">Configure your trace switch.</span></span> <span data-ttu-id="81c57-117">Daha fazla bilgi için [bkz.](#configure)</span><span class="sxs-lookup"><span data-stu-id="81c57-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="81c57-118">Aşağıdaki kod, her türden biri olmak üzere iki anahtar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="81c57-118">The following code creates two switches, one of each type:</span></span>  
  
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
## <a name="configuring-trace-switches"></a><span data-ttu-id="81c57-119">İzleme anahtarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="81c57-119">Configuring trace switches</span></span>  
 <span data-ttu-id="81c57-120">Uygulamanız dağıtıldıktan sonra, uygulamanızdaki izleme anahtarlarını yapılandırarak izleme çıktısını etkinleştirebilir veya devre dışı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81c57-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="81c57-121">Bir anahtarı yapılandırmak, değerini baş harfe alındıktan sonra harici bir kaynaktan değiştirmek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="81c57-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="81c57-122">Yapılandırma dosyasını kullanarak anahtar nesnelerinin değerlerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81c57-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="81c57-123">İzleme anahtarını açıp kapatmak veya düzeyini ayarlamak için, dinleyicilere geçtiği iletimiktarını ve türünü belirlemek için yapılandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="81c57-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="81c57-124">Anahtarlarınız .config dosyası kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="81c57-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="81c57-125">Bir Web uygulaması için bu, projeyle ilişkili Web.config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="81c57-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="81c57-126">Bir Windows uygulamasında, bu dosya (uygulama adı).exe.config olarak adlandırılır. Dağıtılan bir uygulamada, bu dosya yürütülebilir klasörde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="81c57-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="81c57-127">Uygulamanız ilk kez bir anahtar örneği oluşturan kodu çalıştırdığında, yapılandırma dosyasını adlandırılmış anahtar hakkında izleme düzeyi bilgileri için denetler.</span><span class="sxs-lookup"><span data-stu-id="81c57-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="81c57-128">İzleme sistemi yapılandırma dosyasını belirli bir anahtar için yalnızca bir kez inceler — uygulamanız anahtarı ilk kez oluşturduğunda.</span><span class="sxs-lookup"><span data-stu-id="81c57-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="81c57-129">Dağıtılan bir uygulamada, uygulamanız çalışmadığında anahtar nesnelerini yeniden yapılandırarak izleme kodunu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="81c57-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="81c57-130">Genellikle bu, anahtar nesnelerini açıp kapatmayı veya izleme düzeylerini değiştirerek ve ardından uygulamanızı yeniden başlatmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="81c57-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="81c57-131">Bir anahtar örneği oluşturduğunuzda, iki bağımsız değişken belirterek de bu anahtarın başlatılmasını da *gösterirsiniz: displayName* bağımsız değişkeni ve *açıklama* bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="81c57-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="81c57-132">*DisplayName* bağımsız değişkeni, sınıf <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> örneğinin <xref:System.Diagnostics.Switch> özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="81c57-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="81c57-133">*displayName,.config* dosyasındaki anahtarı yapılandırmak için kullanılan addır ve *açıklama* bağımsız değişkeni anahtarın ve hangi iletileri denetlemesi hakkında kısa bir açıklama döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="81c57-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="81c57-134">Yapılandırmak için bir anahtarın adını belirtmenin yanı sıra, anahtar için bir değer de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="81c57-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="81c57-135">Bu değer bir Tamsayı'dır.</span><span class="sxs-lookup"><span data-stu-id="81c57-135">This value is an Integer.</span></span> <span data-ttu-id="81c57-136">Çünkü, <xref:System.Diagnostics.BooleanSwitch>0 değeri **Kapalı'ya**karşılık gelir ve sıfır olmayan herhangi bir değer **On'a**karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="81c57-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="81c57-137">Için <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, ve 4 karşılık **Off**, **Hata**, **Uyarı**, **Bilgi**, ve **Verbose**, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="81c57-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="81c57-138">4'ten büyük herhangi bir sayı **Verbose**olarak kabul edilir ve sıfırdan küçük herhangi bir sayı **Kapalı**olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="81c57-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81c57-139">.NET Framework sürüm 2.0'da, bir anahtarın değerini belirtmek için metni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81c57-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="81c57-140">Örneğin, `true` bir <xref:System.Diagnostics.BooleanSwitch> numaralandırma değerini temsil eden bir metin `Error` veya <xref:System.Diagnostics.TraceSwitch>metin için .</span><span class="sxs-lookup"><span data-stu-id="81c57-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="81c57-141">Satır `<add name="myTraceSwitch" value="Error" />` ' a `<add name="myTraceSwitch" value="1" />`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="81c57-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="81c57-142">Son kullanıcıların bir uygulamanın izleme anahtarlarını yapılandırabilmesi için, uygulamanızdaki anahtarlar hakkında ayrıntılı belgeler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="81c57-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="81c57-143">Hangi anahtarların neyi ve nasıl açıp kapatabileceğinizi ayrıntılı olarak anlatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="81c57-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="81c57-144">Ayrıca, son kullanıcınıza yorumlarda uygun Yardım içeren bir .config dosyası da sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="81c57-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="81c57-145">İzleme anahtarlarını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="81c57-145">To configure trace switches</span></span>  
  
1. <span data-ttu-id="81c57-146">İzleme anahtarlarını kullanmak için, önce bunları oluşturmanız ve izleme [anahtarı oluşturma ve başlatma](#create)bölümünde açıklandığı gibi kodunuza yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="81c57-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="81c57-147">Projenizde bir yapılandırma dosyası (app.config veya Web.config) yoksa, **Proje** menüsünden **Yeni Öğe Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="81c57-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="81c57-148">**Görsel Temel:** Yeni **Öğe Ekle** iletişim kutusunda, **Uygulama Yapılandırma Dosyası'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="81c57-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="81c57-149">Uygulama yapılandırma dosyası oluşturulur ve açılır.</span><span class="sxs-lookup"><span data-stu-id="81c57-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="81c57-150">Bu, kök öğesi olan bir XML belgesidir`<configuration>.`</span><span class="sxs-lookup"><span data-stu-id="81c57-150">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="81c57-151">**Görsel C#:** Yeni **Öğe Ekle** iletişim kutusunda **XML Dosyası'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="81c57-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="81c57-152">Bu **dosyaapp.config**adı . XML düzenleyicisinde, XML bildiriminden sonra aşağıdaki XML'yi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="81c57-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="81c57-153">Projeniz derlendiğinde, app.config dosyası proje çıktı klasörüne kopyalanır ve *uygulama adı*.exe.config olarak yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="81c57-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="81c57-154">Etiketten `<configuration>` sonra ancak `</configuration>` etiketten önce, anahtarlarınızı yapılandırmak için uygun XML'i ekleyin.</span><span class="sxs-lookup"><span data-stu-id="81c57-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="81c57-155">Aşağıdaki örnekler, **DisplayName** özelliğine `DataMessageSwitch` sahip bir **BooleanSwitch** ve **DisplayName** `TraceLevelSwitch`özelliğine sahip bir **TraceSwitch'i** göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="81c57-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="81c57-156">Bu yapılandırmada, her iki anahtar da kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="81c57-156">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="81c57-157">Önceki örnekte gösterildiği gibi `DataMessagesSwitch` bir **BooleanSwitch'i**açmanız gerekiyorsa, **Değeri** 0'dan başka bir tamsayı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="81c57-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="81c57-158">Önceki örnekte gösterildiği gibi `TraceLevelSwitch` bir **TraceSwitch'i**açmanız gerekiyorsa, **Değeri** uygun düzey ayarına (1- 4) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="81c57-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="81c57-159">Son kullanıcının anahtarları uygun şekilde yapılandırmak için hangi değerleri değiştireceğini net bir şekilde anlaması için .config dosyasına yorum ekleyin.</span><span class="sxs-lookup"><span data-stu-id="81c57-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="81c57-160">Aşağıdaki örnek, yorumlar da dahil olmak üzere son kodun nasıl görünebileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="81c57-160">The following example shows how the final code, including comments, might look:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81c57-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81c57-161">See also</span></span>

- [<span data-ttu-id="81c57-162">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="81c57-162">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="81c57-163">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="81c57-163">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="81c57-164">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="81c57-164">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="81c57-165">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="81c57-165">Trace and Debug Settings Schema</span></span>](../configure-apps/file-schema/trace-debug/index.md)

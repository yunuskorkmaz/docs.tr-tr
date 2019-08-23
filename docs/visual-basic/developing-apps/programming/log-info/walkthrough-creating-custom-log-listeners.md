---
title: Özel günlük dinleyicileri oluşturma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 90135074a4d34ea73743faffb2531305fcb326fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965269"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="e27ff-102">İzlenecek yol: Özel günlük dinleyicileri oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e27ff-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="e27ff-103">Bu izlenecek yol, özel bir günlük dinleyicisinin nasıl oluşturulacağını ve `My.Application.Log` nesnenin çıkışını dinlemek için nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e27ff-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="e27ff-104">Başlarken</span><span class="sxs-lookup"><span data-stu-id="e27ff-104">Getting Started</span></span>  
 <span data-ttu-id="e27ff-105">Günlük dinleyicileri <xref:System.Diagnostics.TraceListener> sınıfından devralması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e27ff-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="e27ff-106">Dinleyiciyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e27ff-106">To create the listener</span></span>  
  
- <span data-ttu-id="e27ff-107">Uygulamanızda öğesinden `SimpleListener` <xref:System.Diagnostics.TraceListener>devralan adlı bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e27ff-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     <span data-ttu-id="e27ff-108">Temel sınıf <xref:System.Diagnostics.TraceListener.WriteLine%2A> için gereken `MsgBox` ve yöntemleri, girişini göstermek için çağırır. <xref:System.Diagnostics.TraceListener.Write%2A></span><span class="sxs-lookup"><span data-stu-id="e27ff-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="e27ff-109"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği <xref:System.Diagnostics.TraceListener.Write%2A> ve yöntemlerine<xref:System.Diagnostics.TraceListener.WriteLine%2A> , özniteliklerinin temel sınıf yöntemleriyle eşleşecek şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e27ff-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="e27ff-110"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği kodu çalıştıran konağın, kodun konak koruma eşitlemesini gösterir olduğunu belirlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e27ff-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e27ff-111"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği yalnızca ortak dil çalışma zamanını barındıran yönetilmeyen uygulamalarda etkilidir ve SQL Server gibi konak korumasını uygular.</span><span class="sxs-lookup"><span data-stu-id="e27ff-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="e27ff-112">Günlük dinleyicinizi `My.Application.Log` kullandığından emin olmak için, günlük dinleyicinizi içeren derlemeyi kesin bir şekilde adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e27ff-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="e27ff-113">Sonraki yordam, kesin adlandırılmış bir log-Listener derlemesi oluşturmak için bazı basit adımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e27ff-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="e27ff-114">Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="e27ff-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="e27ff-115">Log dinleyicisi derlemesini kesin olarak adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="e27ff-115">To strongly name the log-listener assembly</span></span>  
  
1. <span data-ttu-id="e27ff-116">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e27ff-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e27ff-117">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e27ff-117">On the **Project** menu, choose **Properties**.</span></span>   
  
2. <span data-ttu-id="e27ff-118">**İmzalama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e27ff-118">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="e27ff-119">**Derlemeyi imzala** kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="e27ff-119">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="e27ff-120">**Tanımlayıcı ad anahtar dosyası seçin** açılır listesinden  **\<yeni >** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e27ff-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="e27ff-121">**Tanımlayıcı ad anahtarı oluştur** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="e27ff-121">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5. <span data-ttu-id="e27ff-122">Anahtar dosya **adı** kutusuna anahtar dosyası için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="e27ff-122">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6. <span data-ttu-id="e27ff-123">Parolayı **gir** ve **Parolayı Onayla** kutularına bir parola girin.</span><span class="sxs-lookup"><span data-stu-id="e27ff-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7. <span data-ttu-id="e27ff-124">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e27ff-124">Click **OK**.</span></span>  
  
8. <span data-ttu-id="e27ff-125">Uygulamayı yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="e27ff-125">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="e27ff-126">Dinleyiciyi ekleme</span><span class="sxs-lookup"><span data-stu-id="e27ff-126">Adding the Listener</span></span>  
 <span data-ttu-id="e27ff-127">Artık derlemenin tanımlayıcı bir adı olduğuna göre, günlük dinleyicinizi `My.Application.Log` kullanması için dinleyicinin tanımlayıcı adını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e27ff-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="e27ff-128">Kesin adlandırılmış türün biçimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="e27ff-128">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="e27ff-129">\<tür adı >, \<derleme adı >, \<sürüm numarası >, \<Kültür >, \<tanımlayıcı ad ></span><span class="sxs-lookup"><span data-stu-id="e27ff-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="e27ff-130">Dinleyicinin tanımlayıcı adını belirleme</span><span class="sxs-lookup"><span data-stu-id="e27ff-130">To determine the strong name of the listener</span></span>  
  
- <span data-ttu-id="e27ff-131">Aşağıdaki kod, için `SimpleListener`kesin adlandırılmış tür adının nasıl belirleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e27ff-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     <span data-ttu-id="e27ff-132">Türün tanımlayıcı adı projenize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e27ff-132">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="e27ff-133">Tanımlayıcı adıyla, dinleyiciyi `My.Application.Log` log-Listener koleksiyonuna ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e27ff-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="e27ff-134">Dinleyiciyi My. Application. log dosyasına eklemek için</span><span class="sxs-lookup"><span data-stu-id="e27ff-134">To add the listener to My.Application.Log</span></span>  
  
1. <span data-ttu-id="e27ff-135">**Çözüm Gezgini** App. config dosyasına sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="e27ff-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="e27ff-136">-veya-</span><span class="sxs-lookup"><span data-stu-id="e27ff-136">-or-</span></span>  
  
     <span data-ttu-id="e27ff-137">Bir App. config dosyası varsa:</span><span class="sxs-lookup"><span data-stu-id="e27ff-137">If there is an app.config file:</span></span>  
  
    1. <span data-ttu-id="e27ff-138">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e27ff-138">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="e27ff-139">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="e27ff-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="e27ff-140">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e27ff-140">Click **Add**.</span></span>  
  
2. <span data-ttu-id="e27ff-141">Bölümünde yer `name` alan "DefaultSource"özniteliğinesahipbölümündebölümünübulun`<sources>`. `<listeners>` `<source>`</span><span class="sxs-lookup"><span data-stu-id="e27ff-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="e27ff-142">Bölümü, bölümünde, üst düzey `<system.diagnostics>` `<configuration>` bölümünde bulunur. `<sources>`</span><span class="sxs-lookup"><span data-stu-id="e27ff-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3. <span data-ttu-id="e27ff-143">Bu öğeyi `<listeners>` bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e27ff-143">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4. <span data-ttu-id="e27ff-144">Bölümünde, üst düzey `<system.diagnostics>` `<configuration>` bölümünde bölümünde bulunan bölümünübulun.`<sharedListeners>`</span><span class="sxs-lookup"><span data-stu-id="e27ff-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5. <span data-ttu-id="e27ff-145">Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e27ff-145">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="e27ff-146">Değerini dinleyicinin tanımlayıcı adı `SimpleLogStrongName` olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e27ff-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27ff-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e27ff-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="e27ff-148">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="e27ff-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="e27ff-149">Nasıl yapılır: Günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="e27ff-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="e27ff-150">Nasıl yapılır: Yazma günlüğü Iletileri</span><span class="sxs-lookup"><span data-stu-id="e27ff-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="e27ff-151">İzlenecek yol: My. Application. log dosyası yazma bilgilerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="e27ff-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

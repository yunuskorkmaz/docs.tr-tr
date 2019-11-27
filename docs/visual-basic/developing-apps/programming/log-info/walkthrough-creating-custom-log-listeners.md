---
title: Özel Günlük Dinleyicileri Oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353619"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="aa2f9-102">İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa2f9-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="aa2f9-103">Bu izlenecek yol, özel bir günlük dinleyicisi oluşturmayı ve `My.Application.Log` nesnesinin çıkışını dinlemek için yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="aa2f9-104">Başlarken</span><span class="sxs-lookup"><span data-stu-id="aa2f9-104">Getting Started</span></span>

<span data-ttu-id="aa2f9-105">Günlük dinleyicileri <xref:System.Diagnostics.TraceListener> sınıftan devralması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="aa2f9-106">Dinleyiciyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="aa2f9-106">To create the listener</span></span>

- <span data-ttu-id="aa2f9-107">Uygulamanızda, <xref:System.Diagnostics.TraceListener>devralan `SimpleListener` adlı bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="aa2f9-108">Temel sınıf için gereken <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemleri, girişlerini göstermek için `MsgBox` çağırır.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="aa2f9-109"><xref:System.Security.Permissions.HostProtectionAttribute> özniteliği, özniteliklerinin temel sınıf yöntemleriyle eşleşmesi için <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemlerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="aa2f9-110"><xref:System.Security.Permissions.HostProtectionAttribute> özniteliği, kodu çalıştıran konağın, kodun konak koruma eşitlemesini gösterir olduğunu belirlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aa2f9-111"><xref:System.Security.Permissions.HostProtectionAttribute> özniteliği yalnızca ortak dil çalışma zamanını barındıran ve SQL Server gibi konak korumasını uygulayan yönetilmeyen uygulamalarda etkilidir.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="aa2f9-112">`My.Application.Log` günlük dinleyicinizi kullandığından emin olmak için, günlük dinleyicinizi içeren derlemeyi kesin bir şekilde adlandırın.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="aa2f9-113">Sonraki yordam, kesin adlandırılmış bir log-Listener derlemesi oluşturmak için bazı basit adımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="aa2f9-114">Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="aa2f9-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="aa2f9-115">Log dinleyicisi derlemesini kesin olarak adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="aa2f9-115">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="aa2f9-116">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="aa2f9-117">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-117">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="aa2f9-118">**İmzalama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-118">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="aa2f9-119">**Derlemeyi imzala** kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-119">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="aa2f9-120">**Tanımlayıcı ad anahtar dosyası seçin** açılır listesinden **Yeni\<>** seçin.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="aa2f9-121">**Tanımlayıcı ad anahtarı oluştur** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-121">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="aa2f9-122">Anahtar dosya **adı** kutusuna anahtar dosyası için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-122">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="aa2f9-123">Parolayı **gir** ve **Parolayı Onayla** kutularına bir parola girin.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="aa2f9-124">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-124">Click **OK**.</span></span>

8. <span data-ttu-id="aa2f9-125">Uygulamayı yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-125">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="aa2f9-126">Dinleyiciyi ekleme</span><span class="sxs-lookup"><span data-stu-id="aa2f9-126">Adding the Listener</span></span>

<span data-ttu-id="aa2f9-127">Artık derlemenin tanımlayıcı bir adı olduğuna göre, `My.Application.Log` günlük dinleyicinizi kullanması için dinleyicinin tanımlayıcı adını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="aa2f9-128">Kesin adlandırılmış türün biçimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-128">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="aa2f9-129">\<tür adı >, \<derleme adı >, \<sürüm numarası >, \<Kültür >, \<tanımlayıcı ad ></span><span class="sxs-lookup"><span data-stu-id="aa2f9-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="aa2f9-130">Dinleyicinin tanımlayıcı adını belirleme</span><span class="sxs-lookup"><span data-stu-id="aa2f9-130">To determine the strong name of the listener</span></span>

- <span data-ttu-id="aa2f9-131">Aşağıdaki kod, `SimpleListener`için kesin adlandırılmış tür adının nasıl belirleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="aa2f9-132">Türün tanımlayıcı adı projenize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-132">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="aa2f9-133">Tanımlayıcı adıyla, dinleyiciyi `My.Application.Log` log-Listener koleksiyonuna ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="aa2f9-134">Dinleyiciyi My. Application. log dosyasına eklemek için</span><span class="sxs-lookup"><span data-stu-id="aa2f9-134">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="aa2f9-135">**Çözüm Gezgini** App. config dosyasına sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="aa2f9-136">veya</span><span class="sxs-lookup"><span data-stu-id="aa2f9-136">-or-</span></span>

     <span data-ttu-id="aa2f9-137">Bir App. config dosyası varsa:</span><span class="sxs-lookup"><span data-stu-id="aa2f9-137">If there is an app.config file:</span></span>

    1. <span data-ttu-id="aa2f9-138">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-138">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="aa2f9-139">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="aa2f9-140">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-140">Click **Add**.</span></span>

2. <span data-ttu-id="aa2f9-141">`<sources>` bölümünde yer alan "DefaultSource" `name` özniteliğiyle birlikte `<source>` bölümünde `<listeners>` bölümünü bulun.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="aa2f9-142">`<sources>` bölümü, üst düzey `<configuration>` bölümünde `<system.diagnostics>` bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="aa2f9-143">Bu öğeyi `<listeners>` bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="aa2f9-143">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="aa2f9-144">Üst düzey `<configuration>` bölümündeki `<system.diagnostics>` bölümünde `<sharedListeners>` bölümünü bulun.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="aa2f9-145">Bu öğeyi bu `<sharedListeners>` bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="aa2f9-145">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="aa2f9-146">`SimpleLogStrongName` değerini, dinleyicinin tanımlayıcı adı olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa2f9-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa2f9-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="aa2f9-148">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="aa2f9-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="aa2f9-149">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="aa2f9-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="aa2f9-150">Nasıl Yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="aa2f9-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="aa2f9-151">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="aa2f9-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

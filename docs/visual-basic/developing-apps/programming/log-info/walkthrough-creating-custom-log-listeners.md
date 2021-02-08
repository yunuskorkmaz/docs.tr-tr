---
description: 'Daha fazla bilgi edinin: Izlenecek yol: özel günlük dinleyicileri oluşturma (Visual Basic)'
title: Özel Günlük Dinleyicileri Oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: bc5e1743eeaec427adf909ca95aa1979ce61a993
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792303"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="1e446-103">İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e446-103">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="1e446-104">Bu izlenecek yol, özel bir günlük dinleyicisinin nasıl oluşturulacağını ve nesnenin çıkışını dinlemek için nasıl yapılandırılacağını gösterir `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="1e446-104">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="1e446-105">Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="1e446-105">Getting Started</span></span>

<span data-ttu-id="1e446-106">Günlük dinleyicileri sınıfından devralması gerekir <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="1e446-106">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="1e446-107">Dinleyiciyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1e446-107">To create the listener</span></span>

- <span data-ttu-id="1e446-108">Uygulamanızda öğesinden devralan adlı bir sınıf oluşturun `SimpleListener` <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="1e446-108">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="1e446-109"><xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> Temel sınıf için gereken ve yöntemleri, `MsgBox` girişini göstermek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="1e446-109">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="1e446-110"><xref:System.Security.Permissions.HostProtectionAttribute>Özniteliği <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemlerine, özniteliklerinin temel sınıf yöntemleriyle eşleşecek şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1e446-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="1e446-111"><xref:System.Security.Permissions.HostProtectionAttribute>Özniteliği kodu çalıştıran konağın, kodun konak koruma eşitlemesini gösterir olduğunu belirlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e446-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1e446-112"><xref:System.Security.Permissions.HostProtectionAttribute>Özniteliği yalnızca ortak dil çalışma zamanını barındıran yönetilmeyen uygulamalarda etkilidir ve SQL Server gibi konak korumasını uygular.</span><span class="sxs-lookup"><span data-stu-id="1e446-112">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="1e446-113">`My.Application.Log`Günlük dinleyicinizi kullandığından emin olmak için, günlük dinleyicinizi içeren derlemeyi kesin bir şekilde adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1e446-113">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="1e446-114">Sonraki yordam, kesin adlandırılmış bir log-Listener derlemesi oluşturmak için bazı basit adımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e446-114">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="1e446-115">Daha fazla bilgi için bkz. [Strong-Named derlemeleri oluşturma ve kullanma](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="1e446-115">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="1e446-116">Log dinleyicisi derlemesini kesin olarak adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="1e446-116">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="1e446-117">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e446-117">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1e446-118">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1e446-118">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="1e446-119">**İmzalama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1e446-119">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="1e446-120">**Derlemeyi imzala** kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="1e446-120">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="1e446-121">**\<New>** **Tanımlayıcı ad anahtar dosyası seçin** aşağı açılan listesinden seçim yapın.</span><span class="sxs-lookup"><span data-stu-id="1e446-121">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="1e446-122">**Tanımlayıcı ad anahtarı oluştur** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="1e446-122">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="1e446-123">Anahtar dosya **adı** kutusuna anahtar dosyası için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="1e446-123">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="1e446-124">Parolayı **gir** ve **Parolayı Onayla** kutularına bir parola girin.</span><span class="sxs-lookup"><span data-stu-id="1e446-124">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="1e446-125">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1e446-125">Click **OK**.</span></span>

8. <span data-ttu-id="1e446-126">Uygulamayı yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="1e446-126">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="1e446-127">Dinleyiciyi ekleme</span><span class="sxs-lookup"><span data-stu-id="1e446-127">Adding the Listener</span></span>

<span data-ttu-id="1e446-128">Artık derlemenin tanımlayıcı bir adı olduğuna göre, günlük dinleyicinizi kullanması için dinleyicinin tanımlayıcı adını belirlemeniz gerekir `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="1e446-128">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="1e446-129">Kesin adlandırılmış türün biçimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="1e446-129">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="1e446-130">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span><span class="sxs-lookup"><span data-stu-id="1e446-130">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="1e446-131">Dinleyicinin tanımlayıcı adını belirleme</span><span class="sxs-lookup"><span data-stu-id="1e446-131">To determine the strong name of the listener</span></span>

- <span data-ttu-id="1e446-132">Aşağıdaki kod, için kesin adlandırılmış tür adının nasıl belirleneceğini göstermektedir `SimpleListener` .</span><span class="sxs-lookup"><span data-stu-id="1e446-132">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="1e446-133">Türün tanımlayıcı adı projenize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e446-133">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="1e446-134">Tanımlayıcı adıyla, dinleyiciyi `My.Application.Log` log-Listener koleksiyonuna ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e446-134">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="1e446-135">Dinleyiciyi My. Application. log dosyasına eklemek için</span><span class="sxs-lookup"><span data-stu-id="1e446-135">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="1e446-136">**Çözüm Gezgini** app.config sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1e446-136">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="1e446-137">-veya-</span><span class="sxs-lookup"><span data-stu-id="1e446-137">-or-</span></span>

     <span data-ttu-id="1e446-138">Bir app.config dosyası varsa:</span><span class="sxs-lookup"><span data-stu-id="1e446-138">If there is an app.config file:</span></span>

    1. <span data-ttu-id="1e446-139">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1e446-139">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="1e446-140">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="1e446-140">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="1e446-141">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1e446-141">Click **Add**.</span></span>

2. <span data-ttu-id="1e446-142">Bölümünde `<listeners>` `<source>` `name` yer alan "DefaultSource" özniteliğine sahip bölümünde bölümünü bulun `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="1e446-142">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="1e446-143">Bölümü, bölümünde `<sources>` `<system.diagnostics>` , üst düzey `<configuration>` bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1e446-143">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="1e446-144">Bu öğeyi `<listeners>` bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e446-144">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="1e446-145">Bölümünde, `<sharedListeners>` üst düzey bölümünde bölümünde bulunan bölümünü bulun `<system.diagnostics>` `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="1e446-145">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="1e446-146">Bu öğeyi bu bölüme ekleyin `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="1e446-146">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="1e446-147">Değerini `SimpleLogStrongName` dinleyicinin tanımlayıcı adı olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1e446-147">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e446-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e446-148">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="1e446-149">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="1e446-149">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="1e446-150">Nasıl yapılır: Özel Durumları Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="1e446-150">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="1e446-151">Nasıl yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="1e446-151">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="1e446-152">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1e446-152">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)

---
title: Özel Günlük Dinleyicileri Oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 5a140607a4fe7e1e13de54e8d56cab53e52aaa2a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398272"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="f2714-102">İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2714-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="f2714-103">Bu izlenecek yol, özel bir günlük dinleyicisinin nasıl oluşturulacağını ve nesnenin çıkışını dinlemek için nasıl yapılandırılacağını gösterir `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="f2714-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="f2714-104">Başlarken</span><span class="sxs-lookup"><span data-stu-id="f2714-104">Getting Started</span></span>

<span data-ttu-id="f2714-105">Günlük dinleyicileri sınıfından devralması gerekir <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f2714-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="f2714-106">Dinleyiciyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f2714-106">To create the listener</span></span>

- <span data-ttu-id="f2714-107">Uygulamanızda öğesinden devralan adlı bir sınıf oluşturun `SimpleListener` <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f2714-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="f2714-108"><xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> Temel sınıf için gereken ve yöntemleri, `MsgBox` girişini göstermek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="f2714-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="f2714-109"><xref:System.Security.Permissions.HostProtectionAttribute>Özniteliği <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemlerine, özniteliklerinin temel sınıf yöntemleriyle eşleşecek şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f2714-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="f2714-110"><xref:System.Security.Permissions.HostProtectionAttribute>Özniteliği kodu çalıştıran konağın, kodun konak koruma eşitlemesini gösterir olduğunu belirlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2714-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f2714-111"><xref:System.Security.Permissions.HostProtectionAttribute>Özniteliği yalnızca ortak dil çalışma zamanını barındıran yönetilmeyen uygulamalarda etkilidir ve SQL Server gibi konak korumasını uygular.</span><span class="sxs-lookup"><span data-stu-id="f2714-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="f2714-112">`My.Application.Log`Günlük dinleyicinizi kullandığından emin olmak için, günlük dinleyicinizi içeren derlemeyi kesin bir şekilde adlandırın.</span><span class="sxs-lookup"><span data-stu-id="f2714-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="f2714-113">Sonraki yordam, kesin adlandırılmış bir log-Listener derlemesi oluşturmak için bazı basit adımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2714-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="f2714-114">Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="f2714-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="f2714-115">Log dinleyicisi derlemesini kesin olarak adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="f2714-115">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="f2714-116">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2714-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f2714-117">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2714-117">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="f2714-118">**İmzalama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f2714-118">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="f2714-119">**Derlemeyi imzala** kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="f2714-119">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="f2714-120">**\<New>** **Tanımlayıcı ad anahtar dosyası seçin** aşağı açılan listesinden seçim yapın.</span><span class="sxs-lookup"><span data-stu-id="f2714-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="f2714-121">**Tanımlayıcı ad anahtarı oluştur** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="f2714-121">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="f2714-122">Anahtar dosya **adı** kutusuna anahtar dosyası için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="f2714-122">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="f2714-123">Parolayı **gir** ve **Parolayı Onayla** kutularına bir parola girin.</span><span class="sxs-lookup"><span data-stu-id="f2714-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="f2714-124">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f2714-124">Click **OK**.</span></span>

8. <span data-ttu-id="f2714-125">Uygulamayı yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="f2714-125">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="f2714-126">Dinleyiciyi ekleme</span><span class="sxs-lookup"><span data-stu-id="f2714-126">Adding the Listener</span></span>

<span data-ttu-id="f2714-127">Artık derlemenin tanımlayıcı bir adı olduğuna göre, günlük dinleyicinizi kullanması için dinleyicinin tanımlayıcı adını belirlemeniz gerekir `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="f2714-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="f2714-128">Kesin adlandırılmış türün biçimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="f2714-128">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="f2714-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span><span class="sxs-lookup"><span data-stu-id="f2714-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="f2714-130">Dinleyicinin tanımlayıcı adını belirleme</span><span class="sxs-lookup"><span data-stu-id="f2714-130">To determine the strong name of the listener</span></span>

- <span data-ttu-id="f2714-131">Aşağıdaki kod, için kesin adlandırılmış tür adının nasıl belirleneceğini göstermektedir `SimpleListener` .</span><span class="sxs-lookup"><span data-stu-id="f2714-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="f2714-132">Türün tanımlayıcı adı projenize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2714-132">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="f2714-133">Tanımlayıcı adıyla, dinleyiciyi `My.Application.Log` log-Listener koleksiyonuna ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2714-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="f2714-134">Dinleyiciyi My. Application. log dosyasına eklemek için</span><span class="sxs-lookup"><span data-stu-id="f2714-134">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="f2714-135">**Çözüm Gezgini** App. config dosyasına sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f2714-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="f2714-136">-veya-</span><span class="sxs-lookup"><span data-stu-id="f2714-136">-or-</span></span>

     <span data-ttu-id="f2714-137">Bir App. config dosyası varsa:</span><span class="sxs-lookup"><span data-stu-id="f2714-137">If there is an app.config file:</span></span>

    1. <span data-ttu-id="f2714-138">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f2714-138">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="f2714-139">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="f2714-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="f2714-140">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f2714-140">Click **Add**.</span></span>

2. <span data-ttu-id="f2714-141">Bölümünde `<listeners>` `<source>` `name` yer alan "DefaultSource" özniteliğine sahip bölümünde bölümünü bulun `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="f2714-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="f2714-142">Bölümü, bölümünde `<sources>` `<system.diagnostics>` , üst düzey `<configuration>` bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f2714-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="f2714-143">Bu öğeyi `<listeners>` bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2714-143">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="f2714-144">Bölümünde, `<sharedListeners>` üst düzey bölümünde bölümünde bulunan bölümünü bulun `<system.diagnostics>` `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="f2714-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="f2714-145">Bu öğeyi bu bölüme ekleyin `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="f2714-145">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="f2714-146">Değerini `SimpleLogStrongName` dinleyicinin tanımlayıcı adı olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2714-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2714-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2714-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="f2714-148">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="f2714-148">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="f2714-149">Nasıl yapılır: Özel Durumları Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="f2714-149">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="f2714-150">Nasıl yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="f2714-150">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="f2714-151">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f2714-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)

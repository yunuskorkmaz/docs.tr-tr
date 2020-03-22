---
title: Özel Günlük Dinleyicileri Oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353619"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="85449-102">İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85449-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="85449-103">Bu izlik, özel bir günlük dinleyicisinin nasıl oluşturulup nesnenin `My.Application.Log` çıktısını dinleyecek şekilde yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="85449-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="85449-104">Başlarken</span><span class="sxs-lookup"><span data-stu-id="85449-104">Getting Started</span></span>

<span data-ttu-id="85449-105">Günlük dinleyicileri <xref:System.Diagnostics.TraceListener> sınıftan devralmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85449-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="85449-106">Dinleyiciyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="85449-106">To create the listener</span></span>

- <span data-ttu-id="85449-107">Uygulamanızda, 'den `SimpleListener` <xref:System.Diagnostics.TraceListener>devralınan adlı bir sınıf oluşturun</span><span class="sxs-lookup"><span data-stu-id="85449-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="85449-108">Taban <xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> sınıfın gerektirdiği ve yöntemler, `MsgBox` girişlerini görüntülemek için çağrıda bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="85449-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="85449-109">Öznitelik, <xref:System.Security.Permissions.HostProtectionAttribute> özniteliklerinin <xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> taban sınıf yöntemleriyle eşleşecek şekilde ve metotlara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="85449-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="85449-110">Öznitelik, <xref:System.Security.Permissions.HostProtectionAttribute> kodu çalıştıran ana bilgisayara kodun ana bilgisayar koruması eşitlemesi ortaya çıkardığını belirleme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="85449-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="85449-111">Öznitelik, <xref:System.Security.Permissions.HostProtectionAttribute> yalnızca ortak dil çalışma süresini barındıran ve SQL Server gibi ana bilgisayar koruması uygulayan yönetilmeyen uygulamalarda etkilidir.</span><span class="sxs-lookup"><span data-stu-id="85449-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="85449-112">Günlük dinleyicinizi kullandığından `My.Application.Log` emin olmak için, günlük dinleyicinizi içeren derlemeye güçlü bir şekilde isim vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="85449-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="85449-113">Sonraki yordam, güçlü bir şekilde adlandırılmış bir log-dinleyici derlemesi oluşturmak için bazı basit adımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="85449-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="85449-114">Daha fazla bilgi için [bkz.](../../../../standard/assembly/create-use-strong-named.md)</span><span class="sxs-lookup"><span data-stu-id="85449-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="85449-115">Günlük dinleyici derlemesini güçlü bir şekilde adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="85449-115">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="85449-116">**Çözüm Gezgini'nde**bir proje seçili var.</span><span class="sxs-lookup"><span data-stu-id="85449-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="85449-117">**Proje** menüsünde **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="85449-117">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="85449-118">**İmzala** sekmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="85449-118">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="85449-119">Montaj kutusunu **Imzala'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="85449-119">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="85449-120">**Güçlü bir ad anahtarı** açılır listesi seçin Yeni \*\* \<>'yi\*\* seçin.</span><span class="sxs-lookup"><span data-stu-id="85449-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="85449-121">**Güçlü Ad Anahtarı Oluştur** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="85449-121">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="85449-122">**Anahtar dosyası adı** kutusundaki anahtar dosyası için bir ad sağlayın.</span><span class="sxs-lookup"><span data-stu-id="85449-122">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="85449-123">**Parolayı Girin** ve Parola kutularını **onaylayın'** a bir parola girin.</span><span class="sxs-lookup"><span data-stu-id="85449-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="85449-124">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="85449-124">Click **OK**.</span></span>

8. <span data-ttu-id="85449-125">Uygulamayı yeniden yeniden oluştur.</span><span class="sxs-lookup"><span data-stu-id="85449-125">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="85449-126">Dinleyici ekleme</span><span class="sxs-lookup"><span data-stu-id="85449-126">Adding the Listener</span></span>

<span data-ttu-id="85449-127">Derlemenin güçlü bir adı olduğuna göre, günlük dinleyicinizi `My.Application.Log` kullanabilmesi için dinleyicinin güçlü adını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="85449-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="85449-128">Güçlü bir şekilde adlandırılmış bir türün biçimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="85449-128">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="85449-129">\<tür adı \<>, montaj \<adı>, sürüm numarası>, \<kültür>, \<güçlü isim></span><span class="sxs-lookup"><span data-stu-id="85449-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="85449-130">Dinleyicinin güçlü adını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="85449-130">To determine the strong name of the listener</span></span>

- <span data-ttu-id="85449-131">Aşağıdaki kod, `SimpleListener`'' için güçlü adlandırılmış tür adının nasıl belirlenip belirlenilmeye cereyecek</span><span class="sxs-lookup"><span data-stu-id="85449-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="85449-132">Türünün güçlü adı projenize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="85449-132">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="85449-133">Güçlü bir adla, dinleyiciyi günlük `My.Application.Log` dinleyici koleksiyonuna ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85449-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="85449-134">Dinleyiciyi My.Application.Log'a eklemek için</span><span class="sxs-lookup"><span data-stu-id="85449-134">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="85449-135">**Çözüm Gezgini'nde** app.config'e sağ tıklayın ve **Aç'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="85449-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="85449-136">-veya-</span><span class="sxs-lookup"><span data-stu-id="85449-136">-or-</span></span>

     <span data-ttu-id="85449-137">Bir app.config dosyası varsa:</span><span class="sxs-lookup"><span data-stu-id="85449-137">If there is an app.config file:</span></span>

    1. <span data-ttu-id="85449-138">**Proje** menüsünde **Yeni Öğe Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="85449-138">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="85449-139">Yeni **Öğe Ekle** iletişim kutusundan, **Uygulama Yapılandırma Dosyası'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="85449-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="85449-140">**Ekle**’ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="85449-140">Click **Add**.</span></span>

2. <span data-ttu-id="85449-141">Bölümde bulunan "DefaultSource" `<source>` `name` özniteliğinin bulunduğu bölümdeki bölümü bulun. `<listeners>` `<sources>`</span><span class="sxs-lookup"><span data-stu-id="85449-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="85449-142">Bölüm, `<sources>` üst düzey `<system.diagnostics>` `<configuration>` bölümde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="85449-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="85449-143">Bu öğeyi `<listeners>` bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="85449-143">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="85449-144">`<sharedListeners>` Bölümü, `<system.diagnostics>` bölümü, üst düzey `<configuration>` bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="85449-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="85449-145">Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="85449-145">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="85449-146">Dinleyicinin güçlü `SimpleLogStrongName` adı olma değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="85449-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="85449-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85449-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="85449-148">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="85449-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="85449-149">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="85449-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="85449-150">Nasıl Yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="85449-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="85449-151">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="85449-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

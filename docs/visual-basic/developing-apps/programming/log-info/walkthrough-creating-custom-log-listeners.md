---
title: Özel günlük dinleyicileri (Visual Basic) oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 07c13d22235f1198188d26122c137db1d91e64e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342470"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="1a925-102">İzlenecek yol: Özel günlük dinleyicileri (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a925-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="1a925-103">Bu kılavuzda, özel günlük dinleyiciyi oluşturun ve çıkışına dinleyecek şekilde yapılandırma gösterilmiştir `My.Application.Log` nesne.</span><span class="sxs-lookup"><span data-stu-id="1a925-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="1a925-104">Başlarken</span><span class="sxs-lookup"><span data-stu-id="1a925-104">Getting Started</span></span>  
 <span data-ttu-id="1a925-105">Günlük dinleyicileri devralmalıdır <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a925-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="1a925-106">Dinleyici oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1a925-106">To create the listener</span></span>  
  
-   <span data-ttu-id="1a925-107">Uygulamanızda adlı bir sınıf oluşturun `SimpleListener` öğesinden devralan <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="1a925-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     <span data-ttu-id="1a925-108"><xref:System.Diagnostics.TraceListener.Write%2A> Ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> taban sınıfı tarafından gerekli yöntemleri çağırmak `MsgBox` kendi girişlerini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="1a925-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="1a925-109"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği uygulandığı <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemleri taban sınıf yöntemlerini özniteliklerinin eşleşen böylece.</span><span class="sxs-lookup"><span data-stu-id="1a925-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="1a925-110"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği kod konak koruma eşitleme sunan belirlemek için kod çalıştıran konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a925-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1a925-111"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliktir yönetilmeyen uygulamalar yalnızca ortak dil çalışma zamanı konak ve konak koruması, SQL Server gibi uygulama üzerinde etkili.</span><span class="sxs-lookup"><span data-stu-id="1a925-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="1a925-112">Emin olmak için `My.Application.Log` günlük dinleyicinize kullanan kesin günlük dinleyicinize içeren derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="1a925-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="1a925-113">Sonraki yordamda, günlük dinleyici kesin adlandırılmış bütünleştirilmiş kod oluşturmak için gerekli olan basit adımlarda sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a925-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="1a925-114">Daha fazla bilgi için [bkz](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="1a925-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="1a925-115">Dinleyici günlük derleme kesin adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="1a925-115">To strongly name the log-listener assembly</span></span>  
  
1. <span data-ttu-id="1a925-116">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="1a925-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1a925-117">Üzerinde **proje** menüsünde seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="1a925-117">On the **Project** menu, choose **Properties**.</span></span>   
  
2. <span data-ttu-id="1a925-118">Tıklayın **imzalama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="1a925-118">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="1a925-119">Seçin **derlemeyi imzalamayı** kutusu.</span><span class="sxs-lookup"><span data-stu-id="1a925-119">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="1a925-120">Seçin  **\<yeni >** gelen **bir tanımlayıcı ad anahtar dosyası seç** aşağı açılan listesi.</span><span class="sxs-lookup"><span data-stu-id="1a925-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="1a925-121">**Katı ad anahtarı oluştur** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="1a925-121">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5. <span data-ttu-id="1a925-122">Anahtar dosyasında için bir ad sağlayın **anahtar dosya adı** kutusu.</span><span class="sxs-lookup"><span data-stu-id="1a925-122">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6. <span data-ttu-id="1a925-123">Bir parolayı girin **parola gir** ve **parolayı onayla** kutuları.</span><span class="sxs-lookup"><span data-stu-id="1a925-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7. <span data-ttu-id="1a925-124">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1a925-124">Click **OK**.</span></span>  
  
8. <span data-ttu-id="1a925-125">Uygulamayı yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1a925-125">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="1a925-126">Dinleyici ekleme</span><span class="sxs-lookup"><span data-stu-id="1a925-126">Adding the Listener</span></span>  
 <span data-ttu-id="1a925-127">Derlemeyi tanımlayıcı bir ada sahip, güçlü dinleyicisinin adını belirlemek gereken şekilde `My.Application.Log` günlük dinleyicinize kullanır.</span><span class="sxs-lookup"><span data-stu-id="1a925-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="1a925-128">Kesin adlandırılmış tür biçimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="1a925-128">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="1a925-129">\<tür adı >, \<derleme adı >, \<sürüm numarası >, \<kültür >, \<tanımlayıcı ad ></span><span class="sxs-lookup"><span data-stu-id="1a925-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="1a925-130">Dinleyici güçlü adını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1a925-130">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="1a925-131">Aşağıdaki kod, kesin adlandırılmış tür adını belirlemek gösterilmektedir `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="1a925-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     <span data-ttu-id="1a925-132">Tür tanımlayıcı adı projenize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1a925-132">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="1a925-133">Tanımlayıcı ad ile dinleyiciye ekleyebilirsiniz `My.Application.Log` dinleyici günlük koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1a925-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="1a925-134">My.Application.Log için dinleyici eklemek için</span><span class="sxs-lookup"><span data-stu-id="1a925-134">To add the listener to My.Application.Log</span></span>  
  
1. <span data-ttu-id="1a925-135">App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.</span><span class="sxs-lookup"><span data-stu-id="1a925-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="1a925-136">-veya-</span><span class="sxs-lookup"><span data-stu-id="1a925-136">-or-</span></span>  
  
     <span data-ttu-id="1a925-137">Bir app.config dosyası varsa:</span><span class="sxs-lookup"><span data-stu-id="1a925-137">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="1a925-138">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1a925-138">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="1a925-139">Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="1a925-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="1a925-140">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1a925-140">Click **Add**.</span></span>  
  
2. <span data-ttu-id="1a925-141">Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource bulunan", öznitelik `<sources>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="1a925-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="1a925-142">`<sources>` Bölümünde bulunan `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="1a925-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3. <span data-ttu-id="1a925-143">Bu öğeye eklemek `<listeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="1a925-143">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4. <span data-ttu-id="1a925-144">Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="1a925-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5. <span data-ttu-id="1a925-145">Bu öğe ekleyen `<sharedListeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="1a925-145">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="1a925-146">Değiştirin `SimpleLogStrongName` dinleyici tanımlayıcı adı olarak.</span><span class="sxs-lookup"><span data-stu-id="1a925-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a925-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a925-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="1a925-148">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="1a925-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="1a925-149">Nasıl yapılır: Günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="1a925-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="1a925-150">Nasıl yapılır: Günlük iletileri yazma</span><span class="sxs-lookup"><span data-stu-id="1a925-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="1a925-151">İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı yeri değiştirme</span><span class="sxs-lookup"><span data-stu-id="1a925-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

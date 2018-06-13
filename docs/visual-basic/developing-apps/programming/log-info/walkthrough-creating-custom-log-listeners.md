---
title: Özel günlük dinleyicileri (Visual Basic) oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 6139a1fef2b2c37bc2c8a6167febd060d8d01fb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591657"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="4649d-102">İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4649d-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="4649d-103">Bu kılavuz, özel günlük bir dinleyici oluşturun ve bunu çıkışına dinlemek için yapılandırmak üzere gösterilmiştir `My.Application.Log` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4649d-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="4649d-104">Başlarken</span><span class="sxs-lookup"><span data-stu-id="4649d-104">Getting Started</span></span>  
 <span data-ttu-id="4649d-105">Günlük dinleyicileri öğesinden devralmalıdır <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4649d-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="4649d-106">Dinleyici oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4649d-106">To create the listener</span></span>  
  
-   <span data-ttu-id="4649d-107">Uygulamanızda adlı bir sınıf oluşturun `SimpleListener` devraldığı <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="4649d-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]  
  
     <span data-ttu-id="4649d-108"><xref:System.Diagnostics.TraceListener.Write%2A> Ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> temel sınıfı tarafından gerekli yöntemlerini çağıran `MsgBox` kendi girişi görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="4649d-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="4649d-109"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği uygulanan <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemleri taban sınıf yöntemlerini öznitelikleriyle eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="4649d-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="4649d-110"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği kodu konak koruma eşitleme sunan belirlemek için kod çalıştıran ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4649d-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4649d-111"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliktir ortak dil çalışma zamanı barındırma ve SQL Server gibi ana bilgisayar koruması uygulamak yalnızca yönetilmeyen uygulamalar üzerinde etkili.</span><span class="sxs-lookup"><span data-stu-id="4649d-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="4649d-112">Emin olmak için `My.Application.Log` , günlük dinleyicisi kullanır, günlük dinleyicisi içeren derlemenin kesinlikle adlandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4649d-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="4649d-113">Sonraki yordam kesin adlandırılmış günlük dinleyicisi derleme oluşturmak için bazı basit adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="4649d-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="4649d-114">Daha fazla bilgi için bkz: [bkz](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="4649d-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="4649d-115">Güçlü ad günlük dinleyicisi derlemeye</span><span class="sxs-lookup"><span data-stu-id="4649d-115">To strongly name the log-listener assembly</span></span>  
  
1.  <span data-ttu-id="4649d-116">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="4649d-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4649d-117">Üzerinde **proje** menüsünde seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="4649d-117">On the **Project** menu, choose **Properties**.</span></span>   
  
2.  <span data-ttu-id="4649d-118">Tıklatın **imzalama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="4649d-118">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="4649d-119">Seçin **derlemeyi imzalamak** kutusu.</span><span class="sxs-lookup"><span data-stu-id="4649d-119">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="4649d-120">Seçin  **\<yeni >** gelen **güçlü ad anahtar dosyası seçin** aşağı açılan liste.</span><span class="sxs-lookup"><span data-stu-id="4649d-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="4649d-121">**Güçlü ad anahtarı oluştur** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="4649d-121">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="4649d-122">Anahtar dosyası için bir ad **anahtar dosya adını** kutusu.</span><span class="sxs-lookup"><span data-stu-id="4649d-122">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6.  <span data-ttu-id="4649d-123">Bir parolayı girin **parola gir** ve **parolayı onayla** kutuları.</span><span class="sxs-lookup"><span data-stu-id="4649d-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7.  <span data-ttu-id="4649d-124">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4649d-124">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="4649d-125">Uygulama yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4649d-125">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="4649d-126">Dinleyici ekleme</span><span class="sxs-lookup"><span data-stu-id="4649d-126">Adding the Listener</span></span>  
 <span data-ttu-id="4649d-127">Derleme güçlü olan bir ada sahip, güçlü dinleyicisinin adını belirlemeniz gerekir böylece `My.Application.Log` günlük dinleyicisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="4649d-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="4649d-128">Türü kesin adlandırılmış bir türün biçimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="4649d-128">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="4649d-129">\<tür adı >, \<derleme adı >, \<sürüm numarası >, \<kültür >, \<güçlü adı ></span><span class="sxs-lookup"><span data-stu-id="4649d-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="4649d-130">Dinleyici güçlü adını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="4649d-130">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="4649d-131">Aşağıdaki kod, kesin adlandırılmış tür adını belirlemek gösterilmiştir `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="4649d-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]  
  
     <span data-ttu-id="4649d-132">Türü kesin adı projenizde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4649d-132">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="4649d-133">Güçlü adıyla bir dinleyici ekleyebilirsiniz `My.Application.Log` günlük dinleyicisi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4649d-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="4649d-134">Dinleyici için My.Application.Log eklemek için</span><span class="sxs-lookup"><span data-stu-id="4649d-134">To add the listener to My.Application.Log</span></span>  
  
1.  <span data-ttu-id="4649d-135">App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.</span><span class="sxs-lookup"><span data-stu-id="4649d-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="4649d-136">-veya-</span><span class="sxs-lookup"><span data-stu-id="4649d-136">-or-</span></span>  
  
     <span data-ttu-id="4649d-137">Bir app.config dosyası ise:</span><span class="sxs-lookup"><span data-stu-id="4649d-137">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="4649d-138">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="4649d-138">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="4649d-139">Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="4649d-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="4649d-140">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4649d-140">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="4649d-141">Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource bulunan", öznitelik `<sources>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="4649d-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="4649d-142">`<sources>` Bölüm bulunduğu `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="4649d-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="4649d-143">Bu öğeye ekleyin `<listeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="4649d-143">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  <span data-ttu-id="4649d-144">Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="4649d-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="4649d-145">Bu öğe için eklemek `<sharedListeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="4649d-145">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="4649d-146">Değerini değiştirme `SimpleLogStrongName` dinleyicisi güçlü adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4649d-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4649d-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4649d-147">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="4649d-148">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="4649d-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="4649d-149">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="4649d-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="4649d-150">Nasıl Yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="4649d-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="4649d-151">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="4649d-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

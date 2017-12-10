---
title: "Özel günlük dinleyicileri (Visual Basic) oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1bda4a3465af4ed95de720117ea2e03f9a86b84
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="77733-102">İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77733-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="77733-103">Bu kılavuz, özel günlük bir dinleyici oluşturun ve bunu çıkışına dinlemek için yapılandırmak üzere gösterilmiştir `My.Application.Log` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77733-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="77733-104">Başlarken</span><span class="sxs-lookup"><span data-stu-id="77733-104">Getting Started</span></span>  
 <span data-ttu-id="77733-105">Günlük dinleyicileri öğesinden devralmalıdır <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="77733-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="77733-106">Dinleyici oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="77733-106">To create the listener</span></span>  
  
-   <span data-ttu-id="77733-107">Uygulamanızda adlı bir sınıf oluşturun `SimpleListener` devraldığı <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="77733-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]  
  
     <span data-ttu-id="77733-108"><xref:System.Diagnostics.TraceListener.Write%2A> Ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> temel sınıfı tarafından gerekli yöntemlerini çağıran `MsgBox` kendi girişi görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="77733-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="77733-109"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği uygulanan <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemleri taban sınıf yöntemlerini öznitelikleriyle eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="77733-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="77733-110"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği kodu konak koruma eşitleme sunan belirlemek için kod çalıştıran ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="77733-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="77733-111"><xref:System.Security.Permissions.HostProtectionAttribute> Özniteliktir ortak dil çalışma zamanı barındırma ve SQL Server gibi ana bilgisayar koruması uygulamak yalnızca yönetilmeyen uygulamalar üzerinde etkili.</span><span class="sxs-lookup"><span data-stu-id="77733-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="77733-112">Emin olmak için `My.Application.Log` , günlük dinleyicisi kullanır, günlük dinleyicisi içeren derlemenin kesinlikle adlandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="77733-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="77733-113">Sonraki yordam kesin adlandırılmış günlük dinleyicisi derleme oluşturmak için bazı basit adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="77733-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="77733-114">Daha fazla bilgi için bkz: [bkz](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="77733-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="77733-115">Güçlü ad günlük dinleyicisi derlemeye</span><span class="sxs-lookup"><span data-stu-id="77733-115">To strongly name the log-listener assembly</span></span>  
  
1.  <span data-ttu-id="77733-116">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="77733-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="77733-117">Üzerinde **proje** menüsünde seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="77733-117">On the **Project** menu, choose **Properties**.</span></span> <span data-ttu-id="77733-118">Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="77733-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="77733-119">Tıklatın **imzalama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="77733-119">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="77733-120">Seçin **derlemeyi imzalamak** kutusu.</span><span class="sxs-lookup"><span data-stu-id="77733-120">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="77733-121">Seçin  **\<yeni >** gelen **güçlü ad anahtar dosyası seçin** aşağı açılan liste.</span><span class="sxs-lookup"><span data-stu-id="77733-121">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="77733-122">**Güçlü ad anahtarı oluştur** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="77733-122">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="77733-123">Anahtar dosyası için bir ad **anahtar dosya adını** kutusu.</span><span class="sxs-lookup"><span data-stu-id="77733-123">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6.  <span data-ttu-id="77733-124">Bir parolayı girin **parola gir** ve **parolayı onayla** kutuları.</span><span class="sxs-lookup"><span data-stu-id="77733-124">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7.  <span data-ttu-id="77733-125">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="77733-125">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="77733-126">Uygulama yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="77733-126">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="77733-127">Dinleyici ekleme</span><span class="sxs-lookup"><span data-stu-id="77733-127">Adding the Listener</span></span>  
 <span data-ttu-id="77733-128">Derleme güçlü olan bir ada sahip, güçlü dinleyicisinin adını belirlemeniz gerekir böylece `My.Application.Log` günlük dinleyicisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="77733-128">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="77733-129">Türü kesin adlandırılmış bir türün biçimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="77733-129">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="77733-130">\<tür adı >, \<derleme adı >, \<sürüm numarası >, \<kültür >, \<güçlü adı ></span><span class="sxs-lookup"><span data-stu-id="77733-130">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="77733-131">Dinleyici güçlü adını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="77733-131">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="77733-132">Aşağıdaki kod, kesin adlandırılmış tür adını belirlemek gösterilmiştir `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="77733-132">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]  
  
     <span data-ttu-id="77733-133">Türü kesin adı projenizde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="77733-133">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="77733-134">Güçlü adıyla bir dinleyici ekleyebilirsiniz `My.Application.Log` günlük dinleyicisi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="77733-134">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="77733-135">Dinleyici için My.Application.Log eklemek için</span><span class="sxs-lookup"><span data-stu-id="77733-135">To add the listener to My.Application.Log</span></span>  
  
1.  <span data-ttu-id="77733-136">App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.</span><span class="sxs-lookup"><span data-stu-id="77733-136">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="77733-137">veya</span><span class="sxs-lookup"><span data-stu-id="77733-137">-or-</span></span>  
  
     <span data-ttu-id="77733-138">Bir app.config dosyası ise:</span><span class="sxs-lookup"><span data-stu-id="77733-138">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="77733-139">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="77733-139">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="77733-140">Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="77733-140">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="77733-141">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="77733-141">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="77733-142">Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource bulunan", öznitelik `<sources>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="77733-142">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="77733-143">`<sources>` Bölüm bulunduğu `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="77733-143">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="77733-144">Bu öğeye ekleyin `<listeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="77733-144">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  <span data-ttu-id="77733-145">Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="77733-145">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="77733-146">Bu öğe için eklemek `<sharedListeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="77733-146">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="77733-147">Değerini değiştirme `SimpleLogStrongName` dinleyicisi güçlü adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77733-147">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77733-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77733-148">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="77733-149">Uygulama günlükleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="77733-149">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="77733-150">Nasıl yapılır: günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="77733-150">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="77733-151">Nasıl yapılır: günlük iletileri yazma</span><span class="sxs-lookup"><span data-stu-id="77733-151">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="77733-152">İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı değiştirme</span><span class="sxs-lookup"><span data-stu-id="77733-152">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

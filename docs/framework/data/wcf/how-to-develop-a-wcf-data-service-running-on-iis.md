---
title: "Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 467c572d456bf2beca9f69359d362867aefbe5a1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="de5d6-102">Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme</span><span class="sxs-lookup"><span data-stu-id="de5d6-102">How to: Develop a WCF Data Service Running on IIS</span></span>
<span data-ttu-id="de5d6-103">Bu konuda nasıl kullanılacağını gösterir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Internet Information Services (IIS) çalıştıran bir ASP.NET Web uygulaması tarafından barındırılan Northwind örnek veritabanı dayalı bir veri hizmeti oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="de5d6-103">This topic shows how to use [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="de5d6-104">ASP.NET geliştirme sunucusu üzerinde çalışan bir ASP.NET Web uygulaması olarak aynı Northwind veri hizmeti oluşturma örneği için bkz: [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="de5d6-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de5d6-105">Northwind veri hizmeti oluşturmak için Northwind örnek veritabanı yerel bilgisayarda yüklü gerekir.</span><span class="sxs-lookup"><span data-stu-id="de5d6-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="de5d6-106">Bu örnek veritabanı karşıdan yüklemek için indirme sayfasına bakın [örnek veritabanları için SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="de5d6-106">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
 <span data-ttu-id="de5d6-107">Bu konu Entity Framework sağlayıcı kullanarak bir veri hizmeti oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="de5d6-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="de5d6-108">Diğer Veri Hizmetleri sağlayıcılar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de5d6-108">Other data services providers are available.</span></span> <span data-ttu-id="de5d6-109">Daha fazla bilgi için bkz: [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="de5d6-109">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="de5d6-110">Hizmeti oluşturduktan sonra veri hizmeti kaynaklarına erişimi açıkça sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de5d6-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="de5d6-111">Daha fazla bilgi için bkz: [nasıl yapılır: veri hizmeti erişimi etkinleştir](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="de5d6-111">For more information, see [How to: Enable Access to the Data Service](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="de5d6-112">IIS üzerinde çalışır ASP.NET Web uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="de5d6-112">To create the ASP.NET Web application that runs on IIS</span></span>  
  
1.  <span data-ttu-id="de5d6-113">Visual Studio'da üzerinde **dosya** menüsünde, select **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-113">In Visual Studio, on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="de5d6-114">İçinde **yeni proje** iletişim kutusunda, Visual Basic veya Visual C# programlama dili olarak seçin.</span><span class="sxs-lookup"><span data-stu-id="de5d6-114">In the **New Project** dialog box, select either Visual Basic or Visual C# as the programming language.</span></span>  
  
3.  <span data-ttu-id="de5d6-115">İçinde **şablonları** bölmesinde, **ASP.NET Web uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-115">In the **Templates** pane, select **ASP.NET Web Application**.</span></span> <span data-ttu-id="de5d6-116">Not: Visual Studio Web Developer kullanırsanız, yeni bir Web uygulaması yerine yeni bir Web sitesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de5d6-116">Note: If you use Visual Studio Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
4.  <span data-ttu-id="de5d6-117">Tür `NorthwindService` projesinin adı olarak.</span><span class="sxs-lookup"><span data-stu-id="de5d6-117">Type `NorthwindService` as the name of the project.</span></span>  
  
5.  <span data-ttu-id="de5d6-118">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="de5d6-118">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="de5d6-119">Üzerinde **proje** menüsünde, select **NorthwindService özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-119">On the **Project** menu, select **NorthwindService Properties**.</span></span>  
  
7.  <span data-ttu-id="de5d6-120">Seçin **Web** sekmesini tıklatın ve ardından **kullanım yerel IIS Web sunucusunda**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-120">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>  
  
8.  <span data-ttu-id="de5d6-121">Tıklatın **sanal dizin oluştur** ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-121">Click **Create Virtual Directory** and then click **OK**.</span></span>  
  
9. <span data-ttu-id="de5d6-122">Yönetici ayrıcalıklarıyla komut isteminden (işletim sistemi için) bağlı olarak aşağıdaki komutlardan birini yürütün:</span><span class="sxs-lookup"><span data-stu-id="de5d6-122">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="de5d6-123">32 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="de5d6-123">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   <span data-ttu-id="de5d6-124">64 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="de5d6-124">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     <span data-ttu-id="de5d6-125">Bu bilgisayarda Windows Communication Foundation (WCF) kayıtlı olduğundan emin olur.</span><span class="sxs-lookup"><span data-stu-id="de5d6-125">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>  
  
10. <span data-ttu-id="de5d6-126">Yönetici ayrıcalıklarıyla komut isteminden (işletim sistemi için) bağlı olarak aşağıdaki komutlardan birini yürütün:</span><span class="sxs-lookup"><span data-stu-id="de5d6-126">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="de5d6-127">32 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="de5d6-127">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   <span data-ttu-id="de5d6-128">64 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="de5d6-128">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     <span data-ttu-id="de5d6-129">Bu bilgisayarda WCF yüklendikten sonra IIS düzgün çalıştığından emin hale getirir.</span><span class="sxs-lookup"><span data-stu-id="de5d6-129">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="de5d6-130">Ayrıca IIS yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="de5d6-130">You might have to also restart IIS.</span></span>  
  
11. <span data-ttu-id="de5d6-131">ASP.NET uygulaması IIS7 üzerinde çalıştığında, aşağıdaki adımları gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="de5d6-131">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="de5d6-132">IIS Yöneticisi'ni açın ve altındaki PhotoService uygulamaya gidin **varsayılan Web sitesi**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-132">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="de5d6-133">İçinde **özellikler görünümü**, çift **kimlik doğrulama**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-133">In **Features View**, double-click **Authentication**.</span></span>  
  
    3.  <span data-ttu-id="de5d6-134">Üzerinde **kimlik doğrulaması** sayfasında, **anonim kimlik doğrulaması**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-134">On the **Authentication** page, select **Anonymous Authentication**.</span></span>  
  
    4.  <span data-ttu-id="de5d6-135">İçinde **Eylemler** bölmesinde tıklatın **Düzenle** altında hangi anonim kullanıcıların siteye bağlanacak güvenlik sorumlusu ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="de5d6-135">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>  
  
    5.  <span data-ttu-id="de5d6-136">İçinde **anonim kimlik doğrulama bilgilerini Düzenle** iletişim kutusunda **uygulama havuzu kimliği**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-136">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="de5d6-137">Ağ hizmeti hesabı kullandığınızda, anonim kullanıcılara bu hesaba ilişkin tüm iç ağ erişimini vermiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="de5d6-137">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>  
  
12. <span data-ttu-id="de5d6-138">Visual Studio'da SQL Server Management Studio, sqlcmd.exe yardımcı programını veya Transact-SQL Düzenleyicisi'ni kullanarak, bağlı Northwind veritabanı olan SQL Server örneğini karşı aşağıdaki Transact-SQL komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="de5d6-138">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     <span data-ttu-id="de5d6-139">Bu IIS çalıştırmak için kullanılan Windows hesabının SQL Server örneğinde bir oturum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de5d6-139">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="de5d6-140">Bu SQL Server örneğine bağlanmak IIS sağlar.</span><span class="sxs-lookup"><span data-stu-id="de5d6-140">This enables IIS to connect to the SQL Server instance.</span></span>  
  
13. <span data-ttu-id="de5d6-141">Northwind veritabanı bağlı aşağıdaki Transact-SQL komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="de5d6-141">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     <span data-ttu-id="de5d6-142">Bu verileri okumak ve Northwind veritabanına veri yazmak IIS sağlayan yeni oturum açma, hakkı verir.</span><span class="sxs-lookup"><span data-stu-id="de5d6-142">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="de5d6-143">Veri modeli tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="de5d6-143">To define the data model</span></span>  
  
1.  <span data-ttu-id="de5d6-144">İçinde **Çözüm Gezgini**, ASP.NET proje adına sağ tıklayın ve ardından **Yeni Öğe Ekle.**</span><span class="sxs-lookup"><span data-stu-id="de5d6-144">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="de5d6-145">İçinde **Yeni Öğe Ekle** iletişim kutusunda **ADO.NET varlık veri modeli**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-145">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="de5d6-146">Veri modeli ad için `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="de5d6-146">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="de5d6-147">Varlık veri modeli Sihirbazı'nda seçin **veritabanından Oluştur**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-147">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="de5d6-148">Aşağıdaki adımlardan birini yaparak veri modeli veritabanına bağlanmak ve ardından **sonraki**:</span><span class="sxs-lookup"><span data-stu-id="de5d6-148">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="de5d6-149">Önceden yapılandırılmış bir veritabanı bağlantısı yoksa tıklatın **yeni bağlantı** ve yeni bir bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="de5d6-149">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="de5d6-150">Daha fazla bilgi için bkz: [nasıl yapılır: SQL Server veritabanları için bağlantıları oluşturma](http://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="de5d6-150">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="de5d6-151">Bu [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] örnek, iliştirilmiş Northwind örnek veritabanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de5d6-151">This [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="de5d6-152">\-veya -</span><span class="sxs-lookup"><span data-stu-id="de5d6-152">\- or -</span></span>  
  
    -   <span data-ttu-id="de5d6-153">Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantısı varsa, bu bağlantıyı bağlantılar listesinden seçin.</span><span class="sxs-lookup"><span data-stu-id="de5d6-153">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="de5d6-154">Sihirbazın son sayfasında, veritabanındaki tüm tablolar için onay kutularını seçin ve görünümleri ve saklı yordamlar için onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="de5d6-154">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="de5d6-155">Tıklatın **son** sihirbazı kapatın.</span><span class="sxs-lookup"><span data-stu-id="de5d6-155">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de5d6-156">Bu üretilen veri modeli varlık türlerine yabancı anahtar özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="de5d6-156">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="de5d6-157">Visual Studio 2008 kullanılarak oluşturulan veri modelleri bu yabancı anahtar özelliklerini içermez.</span><span class="sxs-lookup"><span data-stu-id="de5d6-157">Data models created using Visual Studio 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="de5d6-158">Bu nedenle, Northwind veri hizmetinin bu sürümü erişmeye çalışmadan önce Visual Studio 2008 kullanılarak oluşturulmuş Northwind veri hizmete erişmek için oluşturulmuş tüm istemci uygulamaları istemci veri hizmeti sınıflarını güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="de5d6-158">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using Visual Studio 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="de5d6-159">Veri hizmetini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="de5d6-159">To create the data service</span></span>  
  
1.  <span data-ttu-id="de5d6-160">İçinde **Çözüm Gezgini**, ASP.NET proje adına sağ tıklayın ve ardından **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-160">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="de5d6-161">İçinde **Yeni Öğe Ekle** iletişim kutusunda **ADO.NET veri hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="de5d6-161">In the **Add New Item** dialog box, select **ADO.NET Data Service**.</span></span>  
  
3.  <span data-ttu-id="de5d6-162">Hizmet ad için `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="de5d6-162">For the name of the service, type `Northwind`.</span></span>  
  
     <span data-ttu-id="de5d6-163">Visual Studio yeni hizmet için XML biçimlendirme ve kodun dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de5d6-163">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="de5d6-164">Varsayılan olarak Kod Düzenleyicisi penceresini açar.</span><span class="sxs-lookup"><span data-stu-id="de5d6-164">By default, the code-editor window opens.</span></span> <span data-ttu-id="de5d6-165">İçinde **Çözüm Gezgini**, hizmet adı, Northwind, uzantıya sahip olacaktır. svc.cs veya. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="de5d6-165">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="de5d6-166">Veri Hizmeti kodunu açıklamayı değiştirin `/* TODO: put your data source class name here */` , varlık kapsayıcısının veri modelinin türü olan veri hizmeti tanımlayan sınıf tanımında bu durumda olduğu `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="de5d6-166">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="de5d6-167">Sınıf tanımı bu görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="de5d6-167">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a><span data-ttu-id="de5d6-168">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de5d6-168">See Also</span></span>  
 [<span data-ttu-id="de5d6-169">Bir hizmet olarak verilerinizi gösterme</span><span class="sxs-lookup"><span data-stu-id="de5d6-169">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)

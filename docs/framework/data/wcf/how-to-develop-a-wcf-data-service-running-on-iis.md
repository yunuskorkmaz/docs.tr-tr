---
title: 'Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: af81e65dfd4661d62d7aa4a3e6075be312765cb7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777827"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="cb2f6-102">Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme</span><span class="sxs-lookup"><span data-stu-id="cb2f6-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="cb2f6-103">Bu konuda, WCF Veri Hizmetleri Internet Information Services (IIS) üzerinde çalışan bir ASP.NET Web uygulaması tarafından barındırılıyor Northwind örnek veritabanını temel alan bir veri hizmeti oluşturmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-103">This topic shows how to use WCF Data Services to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="cb2f6-104">ASP.NET geliştirme sunucusu üzerinde çalışan ASP.NET Web uygulaması olarak aynı Northwind verileri hizmeti oluşturmak nasıl bir örnek için bkz [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="cb2f6-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="cb2f6-105">Northwind verileri hizmeti oluşturmak için Northwind örnek veritabanıyla yerel bilgisayarda yüklü gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="cb2f6-106">Bu örnek veritabanı karşıdan yüklemek için indirme sayfasında bakın [örnek veritabanları için SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="cb2f6-106">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

 <span data-ttu-id="cb2f6-107">Bu konuda Entity Framework kullanarak bir veri hizmeti oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="cb2f6-108">Diğer Veri Hizmetleri sağlayıcıları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-108">Other data services providers are available.</span></span> <span data-ttu-id="cb2f6-109">Daha fazla bilgi için [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="cb2f6-109">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>

 <span data-ttu-id="cb2f6-110">Hizmeti oluşturduktan sonra veri hizmeti kaynaklarına erişimi açıkça sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="cb2f6-111">Daha fazla bilgi için [nasıl yapılır: veri hizmetine erişimi etkinleştirme](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="cb2f6-111">For more information, see [How to: Enable Access to the Data Service](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="cb2f6-112">IIS üzerinde çalışan ASP.NET web uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="cb2f6-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="cb2f6-113">Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="cb2f6-114">İçinde **yeni proje** iletişim kutusunda **yüklü** > [**Visual C#** veya **Visual Basic**] > **Web** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="cb2f6-115">Seçin **ASP.NET Web uygulaması** şablonu.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-115">Select the **ASP.NET Web Application** template.</span></span>

1. <span data-ttu-id="cb2f6-116">Girin `NorthwindService` olarak projenin adı.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="cb2f6-117">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-117">Click **OK**.</span></span>

6. <span data-ttu-id="cb2f6-118">Üzerinde **proje** menüsünde **NorthwindService özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="cb2f6-119">Seçin **Web** sekmesine tıklayın ve ardından **kullanım yerel IIS Web sunucusunda**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="cb2f6-120">Tıklayın **sanal dizin oluştur** ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="cb2f6-121">Yönetici ayrıcalıklarıyla komut isteminden (işletim sistemi) bağlı olarak aşağıdaki komutlardan birini yürütün:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    -   <span data-ttu-id="cb2f6-122">32 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    -   <span data-ttu-id="cb2f6-123">64 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="cb2f6-124">Bu bilgisayarda Windows Communication Foundation (WCF) kayıtlı olduğundan emin olur.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="cb2f6-125">Yönetici ayrıcalıklarıyla komut isteminden (işletim sistemi) bağlı olarak aşağıdaki komutlardan birini yürütün:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    -   <span data-ttu-id="cb2f6-126">32 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    -   <span data-ttu-id="cb2f6-127">64 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="cb2f6-128">Bu WCF bilgisayara yüklendikten sonra IIS doğru şekilde çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="cb2f6-129">Ayrıca IIS yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="cb2f6-130">IIS7'de ASP.NET uygulama çalıştığında, aşağıdaki adımları da gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="cb2f6-131">IIS Yöneticisi'ni açın ve altındaki PhotoService uygulamaya gidin **varsayılan Web sitesi**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="cb2f6-132">İçinde **özellikler görünümü**, çift **kimlik doğrulaması**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="cb2f6-133">Üzerinde **kimlik doğrulaması** sayfasında **anonim kimlik doğrulaması**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="cb2f6-134">İçinde **eylemleri** bölmesinde tıklayın **Düzenle** altında hangi anonim kullanıcıların siteye bağlanacak güvenlik sorumlusu ayarlamak üzere.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="cb2f6-135">İçinde **anonim kimlik doğrulama bilgilerini Düzenle** iletişim kutusunda **uygulama havuzu kimliği**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="cb2f6-136">Ağ hizmeti hesabı kullandığınızda, anonim kullanıcılara bu hesaba ilişkin tüm iç ağ erişimini verin.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="cb2f6-137">Visual Studio'da SQL Server Management Studio, sqlcmd.exe yardımcı programı veya Transact-SQL Düzenleyicisi'ni kullanarak Northwind veritabanına ekli olan SQL Server örneği üzerinde aşağıdaki Transact-SQL komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="cb2f6-138">Bu, IIS çalıştırmak için kullanılan Windows hesabının SQL Server örneğinde bir oturum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="cb2f6-139">Bu SQL Server örneğine bağlanmak IIS sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="cb2f6-140">Northwind veritabanına ekli ile aşağıdaki Transact-SQL komutlarını yürütün:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="cb2f6-141">Bu verileri okumak ve Northwind veritabanına veri yazmak IIS sağlayan yeni oturum açma hakkı verir.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="cb2f6-142">Veri modelini tanımlama</span><span class="sxs-lookup"><span data-stu-id="cb2f6-142">Define the data model</span></span>

1. <span data-ttu-id="cb2f6-143">İçinde **Çözüm Gezgini**ASP.NET proje adına sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="cb2f6-144">İçinde **Yeni Öğe Ekle** iletişim kutusunda **ADO.NET varlık veri modeli**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="cb2f6-145">Veri modeli için adını, `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="cb2f6-146">Varlık veri modeli Sihirbazı'nda seçin **veritabanından Oluştur**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="cb2f6-147">Aşağıdakilerden birini yaparak veri modeli veritabanına bağlanmak ve ardından **sonraki**:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    -   <span data-ttu-id="cb2f6-148">Önceden yapılandırılmış bir veritabanı bağlantısı yoksa tıklayın **yeni bağlantı** ve yeni bir bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="cb2f6-149">Daha fazla bilgi için [nasıl yapılır: SQL Server veritabanları oluşturma bağlantıları](https://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="cb2f6-149">For more information, see [How to: Create Connections to SQL Server Databases](https://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="cb2f6-150">Bu SQL Server örneği, Northwind örnek veritabanına ekli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="cb2f6-151">\- veya -</span><span class="sxs-lookup"><span data-stu-id="cb2f6-151">\- or -</span></span>

    -   <span data-ttu-id="cb2f6-152">Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantısı varsa, bu bağlantı bağlantılar listesinden seçin.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="cb2f6-153">Sihirbazın son sayfasında, veritabanında tüm tabloların onay kutularını işaretleyin ve görünümler ve saklı yordamlar için onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="cb2f6-154">Tıklayın **son** sihirbazı kapatın.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="cb2f6-155">Veri hizmetini oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb2f6-155">Create the data service</span></span>

1. <span data-ttu-id="cb2f6-156">İçinde **Çözüm Gezgini**ASP.NET projenizin adına sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="cb2f6-157">İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Visual Studio 2015'te WCF veri hizmeti öğe şablonu](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="cb2f6-159">**WCF veri hizmeti** şablonu kullanılabilir Visual Studio 2015, ancak Visual Studio 2017 içinde değil.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="cb2f6-160">Hizmet adını girin `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="cb2f6-161">Visual Studio, yeni hizmet için XML işaretleme ve kod dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="cb2f6-162">Varsayılan olarak, kod düzenleyicisi penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="cb2f6-163">İçinde **Çözüm Gezgini**, hizmet adı, Northwind ve uzantısını içerir. svc.cs veya. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="cb2f6-164">Veri Hizmeti için kod içinde açıklamayı değiştirin `/* TODO: put your data source class name here */` veri modelinin varlık kapsayıcı türü olan veri hizmeti tanımlayan sınıf tanımında, bu durumda olduğu `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="cb2f6-165">Sınıf tanımını aşağıdaki görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="cb2f6-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="cb2f6-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-166">See also</span></span>

- [<span data-ttu-id="cb2f6-167">Verilerinizi Hizmet Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="cb2f6-167">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)

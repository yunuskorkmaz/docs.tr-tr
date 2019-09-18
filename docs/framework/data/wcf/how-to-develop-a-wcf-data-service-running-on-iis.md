---
title: 'Nasıl yapılır: IIS üzerinde çalışan bir WCF Veri Hizmeti Geliştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 89be7aa8339a4edf6d6ab9c0c243e4320d2fdfa8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052969"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="6d1bf-102">Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme</span><span class="sxs-lookup"><span data-stu-id="6d1bf-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="6d1bf-103">Bu konu, Internet Information Services (IIS) üzerinde çalışan bir ASP.NET Web uygulaması tarafından barındırılan Northwind örnek veritabanına dayalı bir veri hizmeti oluşturmak için WCF Veri Hizmetleri nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-103">This topic shows how to use WCF Data Services to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="6d1bf-104">ASP.NET geliştirme sunucusunda çalışan bir ASP.NET Web uygulaması olarak aynı Northwind Data Service 'in nasıl oluşturulacağı hakkında bir örnek için [WCF veri hizmetleri hızlı başlangıç](quickstart-wcf-data-services.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6d1bf-105">Northwind veri hizmetini oluşturmak için, yerel bilgisayara Northwind örnek veritabanını yüklemiş olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="6d1bf-106">Bu örnek veritabanını indirmek için indirme sayfasına, [SQL Server Için örnek veritabanlarına](https://go.microsoft.com/fwlink/?linkid=24758)bakın.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-106">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

<span data-ttu-id="6d1bf-107">Bu konuda, Entity Framework sağlayıcısı kullanılarak bir veri hizmetinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="6d1bf-108">Diğer veri hizmetleri sağlayıcıları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-108">Other data services providers are available.</span></span> <span data-ttu-id="6d1bf-109">Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6d1bf-109">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="6d1bf-110">Hizmeti oluşturduktan sonra, veri hizmeti kaynaklarına açıkça erişim sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="6d1bf-111">Daha fazla bilgi için [nasıl yapılır: Veri hizmetine](how-to-enable-access-to-the-data-service-wcf-data-services.md)erişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-111">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="6d1bf-112">IIS üzerinde çalışan ASP.NET Web uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d1bf-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="6d1bf-113">Visual Studio 'da, **Dosya** menüsünde **Yeni** > **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="6d1bf-114">**Yeni proje** iletişim kutusunda, **yüklü** > [ **C# Visual** veya **Visual Basic**] > **Web** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="6d1bf-115">**ASP.NET Web uygulaması** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-115">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="6d1bf-116">Projenin `NorthwindService` adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="6d1bf-117">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-117">Click **OK**.</span></span>

6. <span data-ttu-id="6d1bf-118">**Proje** menüsünde, **NorthwindService özellikleri**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="6d1bf-119">**Web** sekmesini seçin ve ardından **yerel IIS Web sunucusu kullan**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="6d1bf-120">**Sanal dizin oluştur** ' a ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="6d1bf-121">Komut isteminden yönetici ayrıcalıklarıyla, aşağıdaki komutlardan birini yürütün (işletim sistemine bağlı olarak):</span><span class="sxs-lookup"><span data-stu-id="6d1bf-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="6d1bf-122">32 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="6d1bf-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="6d1bf-123">64 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="6d1bf-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="6d1bf-124">Bu, Windows Communication Foundation (WCF) bilgisayarda kayıtlı olduğundan emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="6d1bf-125">Komut isteminden yönetici ayrıcalıklarıyla, aşağıdaki komutlardan birini yürütün (işletim sistemine bağlı olarak):</span><span class="sxs-lookup"><span data-stu-id="6d1bf-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="6d1bf-126">32 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="6d1bf-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="6d1bf-127">64 bit sistemler:</span><span class="sxs-lookup"><span data-stu-id="6d1bf-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="6d1bf-128">Bu, bilgisayarda WCF yüklendikten sonra IIS 'nin düzgün şekilde çalıştığından emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="6d1bf-129">Ayrıca IIS 'yi de yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="6d1bf-130">ASP.NET uygulaması ııS7 üzerinde çalıştığında, aşağıdaki adımları da gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="6d1bf-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="6d1bf-131">IIS Yöneticisi 'Ni açın ve **varsayılan Web sitesi**altında photoservice uygulamasına gidin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="6d1bf-132">**Özellikler Görünümü**' nde, **kimlik doğrulaması**' na çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="6d1bf-133">**Kimlik doğrulama** sayfasında, **anonim kimlik doğrulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="6d1bf-134">**Eylemler** bölmesinde, anonim kullanıcıların siteye bağlanacağı güvenlik sorumlusunu ayarlamak için **Düzenle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="6d1bf-135">**Anonim kimlik doğrulaması kimlik bilgilerini düzenle** Iletişim kutusunda **uygulama havuzu kimliği**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="6d1bf-136">Ağ hizmeti hesabı 'nı kullandığınızda, anonim kullanıcılara bu hesapla ilişkili tüm iç ağ erişimini vermiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="6d1bf-137">Visual Studio 'daki SQL Server Management Studio, sqlcmd. exe yardımcı programını veya Transact-SQL düzenleyicisini kullanarak, Northwind veritabanının eklendiği SQL Server örneğine karşı aşağıdaki Transact-SQL komutunu yürütün:</span><span class="sxs-lookup"><span data-stu-id="6d1bf-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="6d1bf-138">Bu, IIS çalıştırmak için kullanılan Windows hesabının SQL Server örneğinde bir oturum açma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="6d1bf-139">Bu, IIS 'nin SQL Server örneğine bağlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="6d1bf-140">Northwind veritabanı ekli olarak, aşağıdaki Transact-SQL komutlarını yürütün:</span><span class="sxs-lookup"><span data-stu-id="6d1bf-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="6d1bf-141">Bu, yeni oturum açma haklarına izin verir ve bu da IIS 'nin Northwind veritabanına verileri okumasını ve verileri yazmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="6d1bf-142">Veri modelini tanımlama</span><span class="sxs-lookup"><span data-stu-id="6d1bf-142">Define the data model</span></span>

1. <span data-ttu-id="6d1bf-143">**Çözüm Gezgini**, ASP.net projesinin adına sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="6d1bf-144">**Yeni öğe Ekle** iletişim kutusunda **ADO.net varlık veri modeli**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="6d1bf-145">Veri modeli adı için, yazın `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="6d1bf-146">Varlık Veri Modeli sihirbazında, **veritabanından oluştur**' u seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="6d1bf-147">Aşağıdaki adımlardan birini gerçekleştirerek veri modelini veritabanına bağlayın ve ardından **İleri**' ye tıklayın:</span><span class="sxs-lookup"><span data-stu-id="6d1bf-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="6d1bf-148">Zaten yapılandırılmış bir veritabanı bağlantınız yoksa **Yeni bağlantı** ' ya tıklayın ve yeni bir bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="6d1bf-149">Daha fazla bilgi için [nasıl yapılır: SQL Server veritabanlarına](https://go.microsoft.com/fwlink/?LinkId=123631)bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-149">For more information, see [How to: Create Connections to SQL Server Databases](https://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="6d1bf-150">Bu SQL Server örneğine Northwind örnek veritabanının eklenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="6d1bf-151">\- veya -</span><span class="sxs-lookup"><span data-stu-id="6d1bf-151">\- or -</span></span>

    - <span data-ttu-id="6d1bf-152">Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantınız varsa, bağlantı listesinden bu bağlantıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="6d1bf-153">Sihirbazın son sayfasında, veritabanındaki tüm tablolar için onay kutularını seçin ve görünümler ve saklı yordamlar onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="6d1bf-154">Sihirbazı kapatmak için **son** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="6d1bf-155">Veri hizmetini oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d1bf-155">Create the data service</span></span>

1. <span data-ttu-id="6d1bf-156">**Çözüm Gezgini**, ASP.net projenizin adına sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="6d1bf-157">**Yeni öğe Ekle** iletişim kutusunda, **WCF veri hizmeti**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Visual Studio 2015 ' de WCF veri hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="6d1bf-159">**WCF veri hizmeti** şablonu visual Studio 2015 'de kullanılabilir, ancak visual Studio 2017 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="6d1bf-160">Hizmetin adı için girin `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="6d1bf-161">Visual Studio, yeni hizmet için XML işaretlemesini ve kod dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="6d1bf-162">Varsayılan olarak, kod Düzenleyicisi penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="6d1bf-163">**Çözüm Gezgini**, hizmetin adı, Northwind ve uzantısı. svc.cs veya. svc. vb ' dir.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="6d1bf-164">Veri Hizmeti kodunda, veri hizmetini tanımlayan sınıfın tanımındaki, bu `/* TODO: put your data source class name here */` örnekte olduğu `NorthwindEntities`gibi veri modelinin varlık kapsayıcısı olan türde olan açıklamayı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="6d1bf-165">Sınıf tanımı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="6d1bf-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="6d1bf-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d1bf-166">See also</span></span>

- [<span data-ttu-id="6d1bf-167">Verilerinizi Hizmet Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="6d1bf-167">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)

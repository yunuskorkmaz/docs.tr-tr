---
description: "Daha fazla bilgi edinin: nasıl yapılır: IIS 'de çalışan bir WCF veri hizmeti geliştirme"
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
ms.openlocfilehash: b4d7b322a00e3c9c43005a416c608e1b98f1ce51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765484"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="9fcdf-103">Nasıl yapılır: IIS 'de çalışan bir WCF veri hizmeti geliştirme</span><span class="sxs-lookup"><span data-stu-id="9fcdf-103">How to: Develop a WCF data service running on IIS</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="9fcdf-104">Bu makalede, Internet Information Services (IIS) üzerinde çalışan bir ASP.NET Web uygulaması tarafından barındırılan Northwind örnek veritabanına dayalı bir veri hizmeti oluşturmak için WCF Veri Hizmetleri nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-104">This article shows how to use WCF Data Services to create a data service that's based on the Northwind sample database that's hosted by an ASP.NET Web app running on Internet Information Services (IIS).</span></span> <span data-ttu-id="9fcdf-105">ASP.NET geliştirme sunucusunda çalışan bir ASP.NET Web uygulaması olarak aynı Northwind Data Service 'in nasıl oluşturulacağı hakkında bir örnek için [WCF veri hizmetleri hızlı başlangıç](quickstart-wcf-data-services.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-105">For an example of how to create the same Northwind data service as an ASP.NET Web app that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9fcdf-106">Northwind veri hizmetini oluşturmak için önce yerel bilgisayara Northwind örnek veritabanını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-106">To create the Northwind data service, first install the Northwind sample database on the local computer.</span></span> <span data-ttu-id="9fcdf-107">Veritabanını yüklemek için [Northwind ve pubs örnek veritabanlarından](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)Transact-SQL betiğini çalıştırın Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-107">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

<span data-ttu-id="9fcdf-108">Bu makalede, Entity Framework sağlayıcısı kullanılarak bir veri hizmetinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-108">This article shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="9fcdf-109">Diğer veri hizmetleri sağlayıcıları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-109">Other data services providers are available.</span></span> <span data-ttu-id="9fcdf-110">Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9fcdf-110">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="9fcdf-111">Hizmeti oluşturduktan sonra, veri hizmeti kaynaklarına açıkça erişim sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-111">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="9fcdf-112">Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmetine erişimi etkinleştirme](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9fcdf-112">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="9fcdf-113">IIS üzerinde çalışan ASP.NET Web uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9fcdf-113">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="9fcdf-114">Visual Studio 'da, **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-114">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="9fcdf-115">**Yeni proje** iletişim kutusunda, **yüklü** > [**Visual C#** veya **Visual Basic**] > **Web** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-115">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="9fcdf-116">**ASP.NET Web uygulaması** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-116">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="9fcdf-117">`NorthwindService`Projenin adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-117">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="9fcdf-118">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-118">Click **OK**.</span></span>

6. <span data-ttu-id="9fcdf-119">**Proje** menüsünde, **NorthwindService özellikleri**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-119">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="9fcdf-120">**Web** sekmesini seçin ve ardından **yerel IIS Web sunucusu kullan**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-120">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="9fcdf-121">**Sanal dizin oluştur** ' a ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-121">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="9fcdf-122">Komut isteminden yönetici ayrıcalıklarıyla, aşağıdaki komutlardan birini yürütün (işletim sistemine bağlı olarak):</span><span class="sxs-lookup"><span data-stu-id="9fcdf-122">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="9fcdf-123">32 bit sistemler: </span><span class="sxs-lookup"><span data-stu-id="9fcdf-123">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="9fcdf-124">64 bit sistemler: </span><span class="sxs-lookup"><span data-stu-id="9fcdf-124">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="9fcdf-125">Bu, Windows Communication Foundation (WCF) bilgisayarda kayıtlı olduğundan emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-125">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="9fcdf-126">Komut isteminden yönetici ayrıcalıklarıyla, aşağıdaki komutlardan birini yürütün (işletim sistemine bağlı olarak):</span><span class="sxs-lookup"><span data-stu-id="9fcdf-126">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="9fcdf-127">32 bit sistemler: </span><span class="sxs-lookup"><span data-stu-id="9fcdf-127">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="9fcdf-128">64 bit sistemler: </span><span class="sxs-lookup"><span data-stu-id="9fcdf-128">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="9fcdf-129">Bu, bilgisayarda WCF yüklendikten sonra IIS 'nin düzgün şekilde çalıştığından emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-129">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="9fcdf-130">Ayrıca IIS 'yi de yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-130">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="9fcdf-131">ASP.NET uygulaması ııS7 üzerinde çalıştığında, aşağıdaki adımları da gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="9fcdf-131">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="9fcdf-132">IIS Yöneticisi 'Ni açın ve **varsayılan Web sitesi** altında photoservice uygulamasına gidin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-132">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="9fcdf-133">**Özellikler Görünümü**' nde, **kimlik doğrulaması**' na çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-133">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="9fcdf-134">**Kimlik doğrulama** sayfasında, **anonim kimlik doğrulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-134">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="9fcdf-135">**Eylemler** bölmesinde, anonim kullanıcıların siteye bağlanacağı güvenlik sorumlusunu ayarlamak için **Düzenle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-135">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="9fcdf-136">**Anonim kimlik doğrulaması kimlik bilgilerini düzenle** Iletişim kutusunda **uygulama havuzu kimliği**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-136">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="9fcdf-137">Ağ hizmeti hesabı 'nı kullandığınızda, anonim kullanıcılara bu hesapla ilişkili tüm iç ağ erişimini vermiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-137">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="9fcdf-138">SQL Server Management Studio, sqlcmd.exe yardımcı programını veya Visual Studio 'daki Transact-SQL düzenleyicisini kullanarak, Northwind veritabanının eklendiği SQL Server örneğine karşı aşağıdaki Transact-SQL komutunu yürütün:</span><span class="sxs-lookup"><span data-stu-id="9fcdf-138">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="9fcdf-139">Bu, IIS çalıştırmak için kullanılan Windows hesabının SQL Server örneğinde bir oturum açma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-139">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="9fcdf-140">Bu, IIS 'nin SQL Server örneğine bağlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-140">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="9fcdf-141">Northwind veritabanı ekli olarak, aşağıdaki Transact-SQL komutlarını yürütün:</span><span class="sxs-lookup"><span data-stu-id="9fcdf-141">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="9fcdf-142">Bu, yeni oturum açma haklarına izin verir ve bu da IIS 'nin Northwind veritabanına verileri okumasını ve verileri yazmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-142">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="9fcdf-143">Veri modelini tanımlama</span><span class="sxs-lookup"><span data-stu-id="9fcdf-143">Define the data model</span></span>

1. <span data-ttu-id="9fcdf-144">**Çözüm Gezgini**, ASP.net projesinin adına sağ tıklayın ve ardından   >  **Yeni öğe** Ekle ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-144">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="9fcdf-145">**Yeni öğe Ekle** iletişim kutusunda **ADO.net varlık veri modeli**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-145">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="9fcdf-146">Veri modeli adı için, yazın `Northwind.edmx` .</span><span class="sxs-lookup"><span data-stu-id="9fcdf-146">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="9fcdf-147">Varlık Veri Modeli sihirbazında, **veritabanından oluştur**' u seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-147">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="9fcdf-148">Aşağıdaki adımlardan birini gerçekleştirerek veri modelini veritabanına bağlayın ve ardından **İleri**' ye tıklayın:</span><span class="sxs-lookup"><span data-stu-id="9fcdf-148">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="9fcdf-149">Zaten yapılandırılmış bir veritabanı bağlantınız yoksa **Yeni bağlantı** ' ya tıklayın ve yeni bir bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-149">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="9fcdf-150">Daha fazla bilgi için bkz. [nasıl yapılır: SQL Server veritabanlarına bağlantı oluşturma](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="9fcdf-150">For more information, see [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="9fcdf-151">Bu SQL Server örneğine Northwind örnek veritabanının eklenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-151">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="9fcdf-152">\- veya</span><span class="sxs-lookup"><span data-stu-id="9fcdf-152">\- or -</span></span>

    - <span data-ttu-id="9fcdf-153">Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantınız varsa, bağlantı listesinden bu bağlantıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-153">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="9fcdf-154">Sihirbazın son sayfasında, veritabanındaki tüm tablolar için onay kutularını seçin ve görünümler ve saklı yordamlar onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-154">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="9fcdf-155">Sihirbazı kapatmak için **son** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-155">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="9fcdf-156">Veri hizmetini oluşturma</span><span class="sxs-lookup"><span data-stu-id="9fcdf-156">Create the data service</span></span>

1. <span data-ttu-id="9fcdf-157">**Çözüm Gezgini**, ASP.net projenizin adına sağ tıklayın ve ardından   >  **Yeni öğe** Ekle ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-157">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="9fcdf-158">**Yeni öğe Ekle** iletişim kutusunda, **WCF veri hizmeti**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-158">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Visual Studio 2015 ' de WCF veri hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="9fcdf-160">**WCF veri hizmeti** şablonu visual Studio 2015 'de kullanılabilir, ancak visual Studio 2017 veya üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-160">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="9fcdf-161">Hizmetin adı için girin `Northwind` .</span><span class="sxs-lookup"><span data-stu-id="9fcdf-161">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="9fcdf-162">Visual Studio, yeni hizmet için XML işaretlemesini ve kod dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-162">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="9fcdf-163">Varsayılan olarak, kod Düzenleyicisi penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-163">By default, the code-editor window opens.</span></span> <span data-ttu-id="9fcdf-164">**Çözüm Gezgini**, hizmetin adı, Northwind ve uzantısı. svc.cs veya. svc. vb ' dir.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-164">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="9fcdf-165">Veri Hizmeti kodunda, veri `/* TODO: put your data source class name here */` hizmetini tanımlayan sınıfın tanımındaki, bu örnekte olduğu gibi veri modelinin varlık kapsayıcısı olan türde olan açıklamayı değiştirin `NorthwindEntities` .</span><span class="sxs-lookup"><span data-stu-id="9fcdf-165">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="9fcdf-166">Sınıf tanımı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="9fcdf-166">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="9fcdf-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fcdf-167">See also</span></span>

- [<span data-ttu-id="9fcdf-168">Verilerinizi Hizmet Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="9fcdf-168">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)

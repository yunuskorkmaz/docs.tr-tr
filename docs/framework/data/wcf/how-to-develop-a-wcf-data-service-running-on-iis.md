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
ms.openlocfilehash: 8a1a0c2c55267940463e2c9ab82bb52345269260
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121608"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="41a5e-102">Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme</span><span class="sxs-lookup"><span data-stu-id="41a5e-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="41a5e-103">Bu makalede, Internet Information Services (IIS) üzerinde çalışan ASP.NET bir Web uygulaması tarafından barındırılan Northwind örnek veritabanını temel alan bir veri hizmeti oluşturmak için WCF Veri Hizmetleri'nin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41a5e-103">This article shows how to use WCF Data Services to create a data service that's based on the Northwind sample database that's hosted by an ASP.NET Web app running on Internet Information Services (IIS).</span></span> <span data-ttu-id="41a5e-104">ASP.NET Geliştirme Sunucusu'nda çalışan ASP.NET bir Web uygulamasıyla aynı Northwind veri hizmetini nasıl oluşturabileceğinize ilişkin bir örnek için [WCF Veri Hizmetleri'ne hızlı bir şekilde başlayın.](quickstart-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="41a5e-104">For an example of how to create the same Northwind data service as an ASP.NET Web app that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="41a5e-105">Northwind veri hizmetini oluşturmak için önce Northwind örnek veritabanını yerel bilgisayara yükleyin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-105">To create the Northwind data service, first install the Northwind sample database on the local computer.</span></span> <span data-ttu-id="41a5e-106">Veritabanını yüklemek [için, Northwind'den](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)Transact-SQL komut dosyasını çalıştırın ve Microsoft SQL Server için pub örnek veritabanlarını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="41a5e-106">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

<span data-ttu-id="41a5e-107">Bu makalede, Varlık Çerçevesi sağlayıcısını kullanarak bir veri hizmetinin nasıl oluşturulacak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41a5e-107">This article shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="41a5e-108">Diğer veri hizmetleri sağlayıcıları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="41a5e-108">Other data services providers are available.</span></span> <span data-ttu-id="41a5e-109">Daha fazla bilgi için [Bkz. Veri Hizmetleri Sağlayıcıları.](data-services-providers-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="41a5e-109">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="41a5e-110">Hizmeti oluşturduktan sonra, veri hizmeti kaynaklarına açıkça erişim sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="41a5e-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="41a5e-111">Daha fazla bilgi için [bkz: Veri Hizmetine Erişimi Etkinleştirin.](how-to-enable-access-to-the-data-service-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="41a5e-111">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="41a5e-112">IIS'de çalışan ASP.NET web uygulamasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="41a5e-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="41a5e-113">Visual Studio'da Dosya **menüsünde** **Yeni** > **Proje'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="41a5e-114">Yeni **Proje** iletişim kutusunda, Web **>** **Yüklü** > [**Visual C#** veya **Visual Basic**] seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="41a5e-115">ASP.NET **Web Uygulaması** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-115">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="41a5e-116">Projenin `NorthwindService` adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="41a5e-117">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="41a5e-117">Click **OK**.</span></span>

6. <span data-ttu-id="41a5e-118">**Project** menüsünde **NorthwindService Özellikleri'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="41a5e-119">**Web** sekmesini seçin ve ardından **Yerel IIS Web Sunucusu'nu kullan'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="41a5e-120">**Sanal Dizin Oluştur'u** tıklatın ve ardından **Tamam'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="41a5e-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="41a5e-121">Yönetici ayrıcalıkları içeren komut isteminden aşağıdaki komutlardan birini uygulayın (işletim sistemine bağlı olarak):</span><span class="sxs-lookup"><span data-stu-id="41a5e-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="41a5e-122">32 bit sistemler: </span><span class="sxs-lookup"><span data-stu-id="41a5e-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="41a5e-123">64 bit sistemler: </span><span class="sxs-lookup"><span data-stu-id="41a5e-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="41a5e-124">Bu, Windows Communication Foundation'ın (WCF) bilgisayarda kayıtlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="41a5e-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="41a5e-125">Yönetici ayrıcalıkları içeren komut isteminden aşağıdaki komutlardan birini uygulayın (işletim sistemine bağlı olarak):</span><span class="sxs-lookup"><span data-stu-id="41a5e-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="41a5e-126">32 bit sistemler: </span><span class="sxs-lookup"><span data-stu-id="41a5e-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="41a5e-127">64 bit sistemler: </span><span class="sxs-lookup"><span data-stu-id="41a5e-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="41a5e-128">Bu, WCF bilgisayara yüklendikten sonra IIS'nin doğru çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="41a5e-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="41a5e-129">IIS'yi yeniden başlatmanız da gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="41a5e-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="41a5e-130">ASP.NET uygulaması IIS7'de çalıştığında, aşağıdaki adımları da gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="41a5e-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="41a5e-131">IIS Manager'ı açın ve **Varsayılan Web Sitesi**altında PhotoService uygulamasına gidin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="41a5e-132">**Özellikler Görünümü'nde**, **kimlik doğrulamayı**çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="41a5e-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="41a5e-133">Kimlik **Doğrulama** sayfasında **Anonim Kimlik Doğrulama'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="41a5e-134">**Eylemler** bölmesinde, anonim kullanıcıların siteye bağlanacağı güvenlik ilkesini ayarlamak için **Edet'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="41a5e-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="41a5e-135">Anonim **Kimlik Doğrulama Kimlik Bilgilerini Edit** iletişim kutusunda, **Uygulama havuzu kimliği'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="41a5e-136">Ağ Hizmeti hesabını kullandığınızda, anonim kullanıcılara bu hesapla ilişkili tüm dahili ağ erişimi verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41a5e-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="41a5e-137">SQL Server Management Studio,sqlcmd.exe yardımcı programını veya Visual Studio'daki Transact-SQL Düzenleyicisi'ni kullanarak, Northwind veritabanını ekleyen SQL Server örneğine karşı aşağıdaki Transact-SQL komutunu uygulayın:</span><span class="sxs-lookup"><span data-stu-id="41a5e-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="41a5e-138">Bu, IIS'yi çalıştırmak için kullanılan Windows hesabı için SQL Server örneğinde bir oturum açar.</span><span class="sxs-lookup"><span data-stu-id="41a5e-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="41a5e-139">Bu, IIS'nin SQL Server örneğine bağlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="41a5e-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="41a5e-140">Northwind veritabanı bağlı ile aşağıdaki Transact-SQL komutlarını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="41a5e-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="41a5e-141">Bu, IIS'nin Northwind veritabanından gelen verileri okumasına ve verileri yazmasına olanak tanıyan yeni oturum açma hakları verir.</span><span class="sxs-lookup"><span data-stu-id="41a5e-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="41a5e-142">Veri modelini tanımlama</span><span class="sxs-lookup"><span data-stu-id="41a5e-142">Define the data model</span></span>

1. <span data-ttu-id="41a5e-143">**Çözüm Gezgini'nde,** ASP.NET projesinin adını sağ tıklatın ve sonra**Yeni Öğe** **Ekle'yi** > tıklatın.</span><span class="sxs-lookup"><span data-stu-id="41a5e-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="41a5e-144">Yeni **Öğe Ekle** iletişim kutusunda, **Varlık Veri Modeli ADO.NET**seçin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="41a5e-145">Veri modelinin adı `Northwind.edmx`için.</span><span class="sxs-lookup"><span data-stu-id="41a5e-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="41a5e-146">Varlık Veri Modeli Sihirbazı'nda **Veritabanından**Oluştur'u'nu seçin ve sonra **İleri'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="41a5e-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="41a5e-147">Aşağıdaki adımlardan birini yaparak veri modelini veritabanına bağlayın ve **sonra İleri'yi**tıklatın:</span><span class="sxs-lookup"><span data-stu-id="41a5e-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="41a5e-148">Zaten yapılandırılmış bir veritabanı bağlantınız yoksa, **Yeni Bağlantı'yı** tıklatın ve yeni bir bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="41a5e-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="41a5e-149">Daha fazla bilgi için [bkz: SQL Server Veritabanlarına Bağlantı Oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="41a5e-149">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="41a5e-150">Bu SQL Server örneğinde Northwind örnek veritabanı eklenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41a5e-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="41a5e-151">\-veya -</span><span class="sxs-lookup"><span data-stu-id="41a5e-151">\- or -</span></span>

    - <span data-ttu-id="41a5e-152">Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantınız varsa, bu bağlantıyı bağlantı listesinden seçin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="41a5e-153">Sihirbazın son sayfasında, veritabanındaki tüm tabloların onay kutularını seçin ve görünümler ve depolanan yordamlar için onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="41a5e-154">Sihirbazı kapatmak için **Bitir'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="41a5e-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="41a5e-155">Veri hizmetini oluşturma</span><span class="sxs-lookup"><span data-stu-id="41a5e-155">Create the data service</span></span>

1. <span data-ttu-id="41a5e-156">**Çözüm Gezgini'nde,** ASP.NET projenizin adını sağ tıklatın ve sonra**Yeni Öğe** **Ekle'yi** > tıklatın.</span><span class="sxs-lookup"><span data-stu-id="41a5e-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="41a5e-157">Yeni **Öğe Ekle** iletişim kutusunda **WCF Veri Hizmeti'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Visual Studio 2015'te WCF Veri Hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="41a5e-159">**WCF Veri Hizmeti** şablonu Visual Studio 2015'te kullanılabilir, ancak Visual Studio 2017 veya sonraki ülkelerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="41a5e-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="41a5e-160">Hizmetin adı için, `Northwind`girin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="41a5e-161">Visual Studio, yeni hizmet için XML biçimlendirmesi ve kod dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41a5e-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="41a5e-162">Varsayılan olarak, kod düzenleyicipenceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="41a5e-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="41a5e-163">**Solution Explorer'da**hizmetin adı, Northwind ve uzantısı .svc.cs veya .svc.vb vardır.</span><span class="sxs-lookup"><span data-stu-id="41a5e-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="41a5e-164">Veri hizmeti kodunda, veri hizmetini `/* TODO: put your data source class name here */` tanımlayan sınıfın tanımındaki yorumu, bu durumda `NorthwindEntities`veri modelinin varlık kapsayıcısı olan türle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="41a5e-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="41a5e-165">Sınıf tanımı aşağıdaki lere bakmalıdır:</span><span class="sxs-lookup"><span data-stu-id="41a5e-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="41a5e-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41a5e-166">See also</span></span>

- [<span data-ttu-id="41a5e-167">Verilerinizi Hizmet Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="41a5e-167">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)

---
title: 'Nasıl yapılır: Bağlantı Dizesi Tanımlama'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150577"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="911fb-102">Nasıl yapılır: Bağlantı Dizesi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="911fb-102">How to: Define the Connection String</span></span>

<span data-ttu-id="911fb-103">Bu konu, kavramsal bir modele bağlanırken kullanılan bağlantı dizesinin nasıl tanımlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="911fb-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="911fb-104">Bu konu [AdventureWorks Satış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) kavramsal modeline dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="911fb-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="911fb-105">AdventureWorks Satış Modeli, Entity Framework belgelerinde görevle ilgili konular boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="911fb-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="911fb-106">Bu konu, Varlık Çerçevesi'ni zaten yapılandırdığınızı ve AdventureWorks Satış Modelini tanımladığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="911fb-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="911fb-107">Daha fazla bilgi için [bkz: Modeli el ile tanımla ve Dosyaları Eşleme.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="911fb-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="911fb-108">Bu konudaki yordamlar, Nasıl [Yapılır: Varlık Çerçeve Projesi'ni el ile yapılandırın.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="911fb-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="911fb-109">Visual Studio projesinde Varlık Veri Modeli Sihirbazı'nı kullanırsanız, otomatik olarak bir .edmx dosyası oluşturur ve projeyi Varlık Çerçevesi'ni kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="911fb-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="911fb-110">Daha fazla bilgi için [bkz: Varlık Veri Modeli Sihirbazı'nı kullanın.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="911fb-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="911fb-111">Varlık Çerçevesi bağlantı dizesini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="911fb-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="911fb-112">Projenin uygulama yapılandırma dosyasını (app.config) açın ve aşağıdaki bağlantı dizesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="911fb-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="911fb-113">Projenizde bir uygulama yapılandırma dosyası yoksa, **Proje** menüsünden **Yeni Öğe Ekle'yi** seçerek, **Genel** kategoriyi seçerek, Uygulama **Yapılandırma Dosyası'nı**seçerek ve sonra **Ekle'yi**tıklatarak bir tane ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="911fb-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="911fb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="911fb-114">See also</span></span>

- <span data-ttu-id="911fb-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="911fb-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="911fb-116">[Nasıl Yapılsın: Yeni .edmx Dosyası Oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="911fb-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="911fb-117">[ADO.NET Varlık Veri Modeli Araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="911fb-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

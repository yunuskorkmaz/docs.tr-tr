---
title: 'Nasıl yapılır: Bağlantı Dizesi Tanımlama'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 8386f93d0e80aa824b1e91a130812b9b3a2b3619
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306379"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="2a5c2-102">Nasıl yapılır: Bağlantı Dizesi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="2a5c2-102">How to: Define the Connection String</span></span>

<span data-ttu-id="2a5c2-103">Bu konuda, kavramsal bir modele bağlanırken kullanılan bağlantı dizesi tanımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2a5c2-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="2a5c2-104">Bu konuda dayanır [AdventureWorks satış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) kavramsal model.</span><span class="sxs-lookup"><span data-stu-id="2a5c2-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="2a5c2-105">AdventureWorks satışları modeli içinde görevle ilgili konuları genelinde kullanılan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belgeleri.</span><span class="sxs-lookup"><span data-stu-id="2a5c2-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="2a5c2-106">Bu konuda, zaten yapılandırmış olduğunuz varsayılır, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve AdventureWorks satış Model tanımlı.</span><span class="sxs-lookup"><span data-stu-id="2a5c2-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2a5c2-107">Daha fazla bilgi için [nasıl yapılır: El ile bir modeli tanımlamak ve dosyaları eşleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2a5c2-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="2a5c2-108">Bu konudaki yordamlar da yer [nasıl yapılır: El ile bir Entity Framework projesinin yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2a5c2-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="2a5c2-109">Varlık veri modeli Sihirbazı bir Visual Studio projede kullanıyorsanız, otomatik olarak bir .edmx dosyası oluşturur ve projeyi kullanacak şekilde yapılandırır [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2a5c2-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="2a5c2-110">Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a5c2-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="2a5c2-111">Entity Framework bağlantı dizenizi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="2a5c2-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="2a5c2-112">Projenin uygulama yapılandırma dosyasına (app.config) açın ve aşağıdaki bağlantı dizesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2a5c2-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="2a5c2-113">Projeniz bir uygulama yapılandırma dosyası yoksa belirleyerek bir tane ekleyebilirsiniz **Yeni Öğe Ekle** gelen **proje** menüsünde seçerek **genel** kategorisi seçme **uygulama yapılandırma dosyası**ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="2a5c2-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a5c2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a5c2-114">See also</span></span>

- <span data-ttu-id="2a5c2-115">[Hızlı başlangıç](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a5c2-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="2a5c2-116">[Nasıl yapılır: Yeni bir .edmx dosyası oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a5c2-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="2a5c2-117">[ADO.NET varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a5c2-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

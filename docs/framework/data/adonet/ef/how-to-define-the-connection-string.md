---
title: 'Nasıl yapılır: Bağlantı Dizesi Tanımlama'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 7fb722acbb13b3502d004978581701cc70118ff8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606116"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="58f53-102">Nasıl yapılır: Bağlantı Dizesi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="58f53-102">How to: Define the Connection String</span></span>

<span data-ttu-id="58f53-103">Bu konuda, kavramsal bir modele bağlanırken kullanılan bağlantı dizesi tanımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58f53-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="58f53-104">Bu konuda dayanır [AdventureWorks satış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) kavramsal model.</span><span class="sxs-lookup"><span data-stu-id="58f53-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="58f53-105">AdventureWorks satışları modeli içinde görevle ilgili konuları genelinde kullanılan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belgeleri.</span><span class="sxs-lookup"><span data-stu-id="58f53-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="58f53-106">Bu konuda, zaten yapılandırmış olduğunuz varsayılır, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve AdventureWorks satış Model tanımlı.</span><span class="sxs-lookup"><span data-stu-id="58f53-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="58f53-107">Daha fazla bilgi için [nasıl yapılır: El ile bir modeli tanımlamak ve dosyaları eşleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="58f53-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="58f53-108">Bu konudaki yordamlar da yer [nasıl yapılır: El ile bir Entity Framework projesinin yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="58f53-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="58f53-109">Kullanırsanız [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Sihirbazı bir Visual Studio projesi içinde otomatik olarak bir .edmx dosyası oluşturur ve projeyi kullanacak şekilde yapılandırır [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58f53-109">If you use the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="58f53-110">Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="58f53-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="58f53-111">Entity Framework bağlantı dizenizi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="58f53-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="58f53-112">Projenin uygulama yapılandırma dosyasına (app.config) açın ve aşağıdaki bağlantı dizesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="58f53-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="58f53-113">Projeniz bir uygulama yapılandırma dosyası yoksa belirleyerek bir tane ekleyebilirsiniz **Yeni Öğe Ekle** gelen **proje** menüsünde seçerek **genel** kategorisi seçme **uygulama yapılandırma dosyası**ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="58f53-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="58f53-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58f53-114">See also</span></span>

- <span data-ttu-id="58f53-115">[Hızlı başlangıç](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="58f53-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="58f53-116">[Nasıl yapılır: Yeni bir .edmx dosyası oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="58f53-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="58f53-117">[ADO.NET varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="58f53-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

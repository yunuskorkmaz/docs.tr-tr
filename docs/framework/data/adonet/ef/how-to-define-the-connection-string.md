---
title: 'Nasıl yapılır: Bağlantı Dizesi Tanımlama'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9b029644e0d4e4c7467fbe1e1144579e6edb3478
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536216"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="1c422-102">Nasıl yapılır: Bağlantı Dizesi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="1c422-102">How to: Define the Connection String</span></span>

<span data-ttu-id="1c422-103">Bu konu başlığı altında, kavramsal bir modele bağlanırken kullanılan bağlantı dizesinin nasıl tanımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c422-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="1c422-104">Bu konu, [AdventureWorks Sales](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) kavramsal modeline dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="1c422-104">This topic is based on the [AdventureWorks Sales](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="1c422-105">AdventureWorks Sales modeli, Entity Framework belgelerindeki görevle ilgili konular boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c422-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="1c422-106">Bu konu, Entity Framework yapılandırdığınız ve AdventureWorks Sales modelini tanımladığınız varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c422-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1c422-107">Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını el Ile tanımlama](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1c422-107">For more information, see [How to: Manually Define the Model and Mapping Files](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="1c422-108">Bu konudaki yordamlar, [nasıl yapılır: el ile Entity Framework projesi yapılandırma](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))bölümüne de eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c422-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="1c422-109">Visual Studio projesinde Varlık Veri Modeli Sihirbazı 'nı kullanırsanız, otomatik olarak bir. edmx dosyası oluşturur ve projeyi Entity Framework kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1c422-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="1c422-110">Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1c422-110">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="1c422-111">Entity Framework bağlantı dizesini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="1c422-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="1c422-112">Projenin uygulama yapılandırma dosyasını (app.config) açın ve aşağıdaki bağlantı dizesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1c422-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="1c422-113">Projenizde bir uygulama yapılandırma dosyası yoksa, **Proje** menüsünde **Yeni öğe Ekle** ' yi seçerek, **genel** kategorisini seçerek, **uygulama yapılandırma dosyası**' nı seçip **Ekle**' ye tıklayarak bir tane ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c422-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c422-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c422-114">See also</span></span>

- <span data-ttu-id="1c422-115">[Hızlı Başlangıç](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c422-115">[Quickstart](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="1c422-116">[Nasıl yapılır: yeni bir. edmx dosyası oluşturma](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c422-116">[How to: Create a New .edmx File](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="1c422-117">[ADO.NET Varlık Veri Modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c422-117">[ADO.NET Entity Data Model  Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

---
title: Veri tanımlama dili ile çalışma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 9ca3732de5e4cfa07fe08dec78edc9de23a1a036
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904371"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="9c862-102">Veri tanımlama dili ile çalışma</span><span class="sxs-lookup"><span data-stu-id="9c862-102">Working with Data Definition Language</span></span>
<span data-ttu-id="9c862-103">İle başlayarak [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürüm 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] veri tanımlama dili (DDL) destekler.</span><span class="sxs-lookup"><span data-stu-id="9c862-103">Starting with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] version 4, the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supports data definition language (DDL).</span></span> <span data-ttu-id="9c862-104">Bu, oluşturmak veya bağlantı dizesi ve depolama (SSDL) model meta verilerini temel alan bir veritabanı örneğini silmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c862-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="9c862-105">Aşağıdaki yöntemlerden <xref:System.Data.Objects.ObjectContext> aşağıdakileri gerçekleştirmek için bağlantı dizesini ve SSDL içeriği kullanın: oluşturun veya veritabanını silin, veritabanı var ve oluşturulan DDL betiğini görüntüle olup olmadığını denetleyin:</span><span class="sxs-lookup"><span data-stu-id="9c862-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  <span data-ttu-id="9c862-106">DDL komutları yürütmeden yeterli izinlere varsayar.</span><span class="sxs-lookup"><span data-stu-id="9c862-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="9c862-107">Daha önce listelenen yöntemlerden istediğinizi çoğunu alttaki ADO.NET veri sağlayıcı için temsilci.</span><span class="sxs-lookup"><span data-stu-id="9c862-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="9c862-108">Veritabanı nesneleri oluşturmak için kullanılan adlandırma kuralı sorgulamak için kullanılan kuralları ile tutarlı olmasını sağlamak üzere sağlayıcısının sorumluluğundadır ve güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="9c862-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="9c862-109">Aşağıdaki örnek mevcut modelini temel alan bir veritabanı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c862-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="9c862-110">Ayrıca nesne bağlamı için yeni bir varlık nesnesi ekler ve sonra veritabanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9c862-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="9c862-111">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9c862-111">Procedures</span></span>  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="9c862-112">Mevcut modelini temel alan bir veritabanı tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="9c862-112">To define a database based on the existing model</span></span>  
  
1.  <span data-ttu-id="9c862-113">Bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9c862-113">Create a console application.</span></span>  
  
2.  <span data-ttu-id="9c862-114">Mevcut bir model uygulamanıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9c862-114">Add an existing model to your application.</span></span>  
  
    1.  <span data-ttu-id="9c862-115">Adlı boş bir model ekleme `SchoolModel`.</span><span class="sxs-lookup"><span data-stu-id="9c862-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="9c862-116">Boş bir model oluşturmak için bkz [nasıl yapılır: Yeni bir .edmx dosyası oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) konu.</span><span class="sxs-lookup"><span data-stu-id="9c862-116">To create an empty model, see the [How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="9c862-117">SchoolModel.edmx dosyası projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="9c862-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1.  <span data-ttu-id="9c862-118">Kavramsal, depolama kopyalayın ve eşleme içeriği Okul modeli [Okul modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) konu.</span><span class="sxs-lookup"><span data-stu-id="9c862-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2.  <span data-ttu-id="9c862-119">SchoolModel.edmx dosyasını açın ve içeriği yapıştırın `edmx:Runtime` etiketler.</span><span class="sxs-lookup"><span data-stu-id="9c862-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3.  <span data-ttu-id="9c862-120">Aşağıdaki kodu ana işlevinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9c862-120">Add the following code to your main function.</span></span> <span data-ttu-id="9c862-121">Kod, veritabanı sunucunuza DDL betik veritabanı oluşturur, yeni bir varlık için bir bağlam eklenmiştir ve değişiklikleri veritabanına kaydeder görünümleri bağlantı dizesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="9c862-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]

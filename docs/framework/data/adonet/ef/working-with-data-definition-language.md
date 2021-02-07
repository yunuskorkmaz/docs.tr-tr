---
description: 'Hakkında daha fazla bilgi edinin: veri tanımlama diliyle çalışma'
title: Veri Tanımlama Dili ile Çalışma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 2f924087d12b519e6086289a91dedce3a88199f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673030"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="f584d-103">Veri Tanımlama Dili ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="f584d-103">Working with Data Definition Language</span></span>

<span data-ttu-id="f584d-104">.NET Framework sürüm 4 ' te başlayarak, Entity Framework veri tanımlama dili 'ni (DDL) destekler.</span><span class="sxs-lookup"><span data-stu-id="f584d-104">Starting with the .NET Framework version 4, the Entity Framework supports data definition language (DDL).</span></span> <span data-ttu-id="f584d-105">Bu, bağlantı dizesini ve depolama (SSDL) modelinin meta verilerini temel alarak bir veritabanı örneği oluşturmanıza veya silmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f584d-105">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="f584d-106">Aşağıdaki yöntemler, <xref:System.Data.Objects.ObjectContext> aşağıdakileri gerçekleştirmek için bağlantı dizesini ve SSDL içeriğini kullanır: veritabanını oluşturun veya silin, veritabanının mevcut olup olmadığını denetleyin ve oluşturulan DDL betiğini görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="f584d-106">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> <span data-ttu-id="f584d-107">DDL komutlarının yürütülmesi yeterli izinleri varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="f584d-107">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="f584d-108">Daha önce, temel alınan ADO.NET veri sağlayıcısı üzerinde çalışmanın büyük bir kısmını temsil eden yöntemler.</span><span class="sxs-lookup"><span data-stu-id="f584d-108">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="f584d-109">Veritabanı nesneleri oluşturmak için kullanılan adlandırma kuralının, sorgulama ve güncelleştirme için kullanılan kurallara uygun olduğundan emin olmak sağlayıcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="f584d-109">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="f584d-110">Aşağıdaki örnek, var olan modele göre veritabanının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f584d-110">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="f584d-111">Ayrıca, nesne bağlamına yeni bir varlık nesnesi ekler ve sonra veritabanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f584d-111">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="f584d-112">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f584d-112">Procedures</span></span>  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="f584d-113">Mevcut modele göre bir veritabanı tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="f584d-113">To define a database based on the existing model</span></span>  
  
1. <span data-ttu-id="f584d-114">Konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f584d-114">Create a console application.</span></span>  
  
2. <span data-ttu-id="f584d-115">Uygulamanıza var olan bir modeli ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f584d-115">Add an existing model to your application.</span></span>  
  
    1. <span data-ttu-id="f584d-116">Adlı boş bir model ekleyin `SchoolModel` .</span><span class="sxs-lookup"><span data-stu-id="f584d-116">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="f584d-117">Boş bir model oluşturmak için bkz. [nasıl yapılır: yeni bir. edmx dosyası oluşturma](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) konusu.</span><span class="sxs-lookup"><span data-stu-id="f584d-117">To create an empty model, see the [How to: Create a New .edmx File](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="f584d-118">SchoolModel. edmx dosyası projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="f584d-118">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1. <span data-ttu-id="f584d-119">Okul modeline ait kavramsal, depolama ve eşleme içeriğini [okul modeli](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) konusundan kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f584d-119">Copy the conceptual, storage, and mapping content for the School model from the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2. <span data-ttu-id="f584d-120">SchoolModel. edmx dosyasını açın ve içeriği Etiketler içine yapıştırın `edmx:Runtime` .</span><span class="sxs-lookup"><span data-stu-id="f584d-120">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3. <span data-ttu-id="f584d-121">Ana işlevinizde aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f584d-121">Add the following code to your main function.</span></span> <span data-ttu-id="f584d-122">Kod, bağlantı dizesini veritabanı sunucunuza başlatır, DDL betiğini görüntüler, veritabanını oluşturur, içeriğe yeni bir varlık ekler ve değişiklikleri veritabanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f584d-122">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]

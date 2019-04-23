---
title: 'Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: ab5e2867ce85fcc82e1114696c129aae878bbee6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072395"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="b5c34-102">Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5c34-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="b5c34-103">LINQ to SQL nesne modeli, bir ilişkisel veritabanına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="b5c34-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="b5c34-104">İlişkisel veritabanının yapısını tanımlamak için öznitelik tabanlı eşleme veya bir dış eşleme dosyası kullanarak eşleme etkindir.</span><span class="sxs-lookup"><span data-stu-id="b5c34-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="b5c34-105">Her iki senaryoda veritabanı kullanarak yeni bir örneğini oluşturabilirsiniz ilişkisel veritabanı hakkında yeterli bilgi yok <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b5c34-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="b5c34-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Yöntemi, nesne modelinde kodlanmış bilgilerin kapsamını veritabanına yalnızca bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5c34-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="b5c34-107">Dosyaları ve öznitelikler, nesne modelinden var olan bir veritabanının yapısı hakkında her şeyi kodlamamayı.</span><span class="sxs-lookup"><span data-stu-id="b5c34-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="b5c34-108">Eşleme bilgileri değil kullanıcı tarafından tanımlanan İşlevler, saklı yordamlar, Tetikleyiciler içeriğini temsil veya denetim kısıtlamaları.</span><span class="sxs-lookup"><span data-stu-id="b5c34-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="b5c34-109">Bu davranış, çeşitli veritabanları için yeterli olur.</span><span class="sxs-lookup"><span data-stu-id="b5c34-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="b5c34-110">Kullanabileceğiniz <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> senaryoları, özellikle de Microsoft SQL Server 2008 gibi bir bilinen veri sağlayıcısı kullanılabilir olduğunda herhangi bir sayıda yöntem.</span><span class="sxs-lookup"><span data-stu-id="b5c34-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="b5c34-111">Tipik senaryolar aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="b5c34-111">Typical scenarios include the following:</span></span>  
  
-   <span data-ttu-id="b5c34-112">Otomatik olarak kendisini bir müşteri sisteminde yükleyen bir uygulama oluşturuyorsanız.</span><span class="sxs-lookup"><span data-stu-id="b5c34-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
-   <span data-ttu-id="b5c34-113">Yerel bir veritabanı çevrimdışı durumunu kaydetmek için gereken bir istemci uygulaması oluşturuyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="b5c34-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="b5c34-114">Ayrıca <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> .mdf dosyası veya bağlantı dizenizi bağlı olarak bir katalog adı'nı kullanarak SQL Server ile yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b5c34-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b5c34-115">kullandığı bağlantı dizesi oluşturulacak veritabanının tanımlamak için ve hangi sunucuda veritabanı oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="b5c34-115">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5c34-116">Mümkün olduğunda, böylece bağlantı dizesinde parola gerekli değildir veritabanına bağlanmak için Windows tümleşik güvenliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5c34-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5c34-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5c34-117">Example</span></span>  
 <span data-ttu-id="b5c34-118">Aşağıdaki kod MyDVDs.mdf adlı yeni bir veritabanı oluşturmak nasıl bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5c34-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="b5c34-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5c34-119">Example</span></span>  
 <span data-ttu-id="b5c34-120">Aşağıdakileri yaparak bir veritabanı oluşturmak için nesne modeli kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b5c34-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="b5c34-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5c34-121">Example</span></span>  
 <span data-ttu-id="b5c34-122">Otomatik olarak uygulama oluşturma kendisi bir müşteri sistemine yükler veritabanı zaten var ve yeni bir tane oluşturmadan önce bırak görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b5c34-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="b5c34-123"><xref:System.Data.Linq.DataContext> Sağlar sınıfını <xref:System.Data.Linq.DataContext.DatabaseExists%2A> ve <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> bu işlemde size yardımcı olacak yöntemler.</span><span class="sxs-lookup"><span data-stu-id="b5c34-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="b5c34-124">Aşağıdaki örnek bu yaklaşımı uygulamak için bu yöntemleri kullanılabilir yollarından biri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b5c34-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b5c34-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5c34-125">See also</span></span>

- [<span data-ttu-id="b5c34-126">Öznitelik Tabanlı Eşleme</span><span class="sxs-lookup"><span data-stu-id="b5c34-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="b5c34-127">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="b5c34-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [<span data-ttu-id="b5c34-128">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="b5c34-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [<span data-ttu-id="b5c34-129">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="b5c34-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="b5c34-130">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="b5c34-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)

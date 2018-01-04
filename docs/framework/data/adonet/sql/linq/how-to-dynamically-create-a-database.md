---
title: "Nasıl yapılır: dinamik olarak bir veritabanı oluşturun"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 27986236c6b693b2c89157229cd79f0de64266e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="df70d-102">Nasıl yapılır: dinamik olarak bir veritabanı oluşturun</span><span class="sxs-lookup"><span data-stu-id="df70d-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="df70d-103">LINQ-SQL, nesne modeli ilişkisel bir veritabanına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="df70d-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="df70d-104">Eşleme ilişkisel veritabanı yapısını tanımlamak için öznitelik tabanlı eşleme veya bir dış eşleme dosyası kullanarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="df70d-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="df70d-105">Her iki senaryoda kullanarak veritabanını yeni bir örneğini oluşturabilirsiniz ilişkisel veritabanı hakkında yeterli bilgi yok <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df70d-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="df70d-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Yöntemi, nesne modelinde kodlanmış bilgilerin kapsamını veritabanına yalnızca bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df70d-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="df70d-107">Dosya ve nesne modeli öznitelikleri eşleme varolan bir veritabanını yapısı hakkında her şeyi kodlayın değil.</span><span class="sxs-lookup"><span data-stu-id="df70d-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="df70d-108">Eşleme bilgileri değil kullanıcı tanımlı işlevler, saklı yordamlar, Tetikleyiciler içeriğini temsil veya denetim kısıtlamaları.</span><span class="sxs-lookup"><span data-stu-id="df70d-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="df70d-109">Bu davranış, çeşitli veritabanları için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="df70d-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="df70d-110">Kullanabileceğiniz <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> senaryolarında özellikle Microsoft SQL Server 2008 gibi bilinen veri sağlayıcısı kullanılabilir olduğunda, herhangi bir sayıda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df70d-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="df70d-111">Tipik senaryolar aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="df70d-111">Typical scenarios include the following:</span></span>  
  
-   <span data-ttu-id="df70d-112">Otomatik olarak kendisini bir müşteri sistemde yükleyen bir uygulama oluşturmakta olduğunuz.</span><span class="sxs-lookup"><span data-stu-id="df70d-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
-   <span data-ttu-id="df70d-113">Yerel bir veritabanı çevrimdışı durumunu kaydetmek için gereken bir istemci uygulaması oluşturuyorsanız.</span><span class="sxs-lookup"><span data-stu-id="df70d-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="df70d-114">Aynı zamanda <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> .mdf dosyasını veya bağlantı dizenizi bağlı olarak bir katalog adı kullanarak SQL Server ile yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df70d-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="df70d-115">kullandığı bağlantı dizesi oluşturulacak veritabanının tanımlamanızı ve hangi sunucuda veritabanı oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="df70d-115"> uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df70d-116">Mümkün olduğunda, böylece parolaları bağlantı dizesinde gerekli değildir veritabanına bağlanmak için Windows tümleşik güvenliğini kullan.</span><span class="sxs-lookup"><span data-stu-id="df70d-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df70d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="df70d-117">Example</span></span>  
 <span data-ttu-id="df70d-118">Aşağıdaki kod MyDVDs.mdf adlı yeni bir veritabanı oluşturmak nasıl bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="df70d-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="df70d-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="df70d-119">Example</span></span>  
 <span data-ttu-id="df70d-120">Aşağıdakileri yaparak bir veritabanı oluşturmak için nesne modeli kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df70d-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="df70d-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="df70d-121">Example</span></span>  
 <span data-ttu-id="df70d-122">Otomatik olarak uygulama oluşturma kendisini bir müşteri sistemde yüklendiğinde, veritabanı zaten var ve yenisini oluşturmadan önce bırakma bakın.</span><span class="sxs-lookup"><span data-stu-id="df70d-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="df70d-123"><xref:System.Data.Linq.DataContext> SAX <xref:System.Data.Linq.DataContext.DatabaseExists%2A> ve <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> bu işlemde size yardımcı olacak yöntemler.</span><span class="sxs-lookup"><span data-stu-id="df70d-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="df70d-124">Aşağıdaki örnek, bu yöntemleri bu yaklaşımı uygulamak için kullanılan bir yolu gösterir:</span><span class="sxs-lookup"><span data-stu-id="df70d-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="df70d-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df70d-125">See Also</span></span>  
 [<span data-ttu-id="df70d-126">Öznitelik Tabanlı Eşleme</span><span class="sxs-lookup"><span data-stu-id="df70d-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="df70d-127">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="df70d-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="df70d-128">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="df70d-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="df70d-129">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="df70d-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="df70d-130">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="df70d-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)

---
title: 'Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 4cadf20cdadb39483f26a29619cae058eac47e50
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793648"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="b0718-102">Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b0718-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="b0718-103">LINQ to SQL, bir nesne modeli ilişkisel veritabanıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="b0718-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="b0718-104">Eşleme, ilişkisel veritabanının yapısını betimleyen öznitelik tabanlı eşleme veya bir dış eşleme dosyası kullanılarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b0718-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="b0718-105">Her iki senaryoda da, <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemini kullanarak veritabanının yeni bir örneğini oluşturabileceğiniz ilişkisel veritabanı hakkında yeterli bilgi vardır.</span><span class="sxs-lookup"><span data-stu-id="b0718-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="b0718-106">Yöntemi <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> , veritabanının bir çoğaltmasını yalnızca nesne modelinde kodlanan bilgilerin kapsamına oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b0718-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="b0718-107">Nesne modelinizdeki dosya ve öznitelikleri eşleme, var olan bir veritabanının yapısıyla ilgili her şeyi kodlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="b0718-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="b0718-108">Eşleme bilgileri Kullanıcı tanımlı işlevlerin, saklı yordamların, tetikleyicilerin veya denetim kısıtlamalarının içeriğini temsil etmez.</span><span class="sxs-lookup"><span data-stu-id="b0718-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="b0718-109">Bu davranış çeşitli veritabanları için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="b0718-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="b0718-110"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Yöntemi, özellikle de Microsoft SQL Server 2008 gibi bilinen bir veri sağlayıcısı varsa dilediğiniz sayıda senaryoda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0718-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="b0718-111">Tipik senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b0718-111">Typical scenarios include the following:</span></span>  
  
- <span data-ttu-id="b0718-112">Kendisini bir müşteri sistemine otomatik olarak yükleyen bir uygulama derleniyor.</span><span class="sxs-lookup"><span data-stu-id="b0718-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
- <span data-ttu-id="b0718-113">Çevrimdışı durumunu kaydetmek için yerel bir veritabanına ihtiyacı olan bir istemci uygulaması derleniyor.</span><span class="sxs-lookup"><span data-stu-id="b0718-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="b0718-114">Ayrıca, bağlantı dizeniz <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> temelinde bir. mdf dosyası veya bir katalog adı kullanarak SQL Server yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0718-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b0718-115">oluşturulacak veritabanını ve veritabanının oluşturulacağı sunucuyu tanımlamak için bağlantı dizesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0718-115">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0718-116">Mümkün olduğunda, bağlantı dizesinde parolaların gerekli olmaması için veritabanına bağlanmak üzere Windows tümleşik güvenliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b0718-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0718-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0718-117">Example</span></span>  
 <span data-ttu-id="b0718-118">Aşağıdaki kod, MyDVD 'Ler. mdf adlı yeni bir veritabanının nasıl oluşturulacağı hakkında bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0718-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="b0718-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0718-119">Example</span></span>  
 <span data-ttu-id="b0718-120">Aşağıdaki işlemleri yaparak bir veritabanı oluşturmak için nesne modelini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b0718-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="b0718-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0718-121">Example</span></span>  
 <span data-ttu-id="b0718-122">Kendisini bir müşteri sistemine otomatik olarak yükleyen bir uygulama oluştururken, veritabanının zaten var olup olmadığını ve yeni bir tane oluşturmadan önce onu bırakıp bırakmaya bakın.</span><span class="sxs-lookup"><span data-stu-id="b0718-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="b0718-123">Sınıfı, <xref:System.Data.Linq.DataContext.DatabaseExists%2A> bu işlemle ilgili <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> size yardımcı olmak için ve yöntemlerini sağlar. <xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="b0718-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="b0718-124">Aşağıdaki örnek bu yaklaşımı uygulamak için bu yöntemlerin kullanılabileceği bir yolu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="b0718-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b0718-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0718-125">See also</span></span>

- [<span data-ttu-id="b0718-126">Öznitelik Tabanlı Eşleme</span><span class="sxs-lookup"><span data-stu-id="b0718-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="b0718-127">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="b0718-127">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="b0718-128">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="b0718-128">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="b0718-129">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="b0718-129">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="b0718-130">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="b0718-130">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)

---
title: "Programlama Kılavuzu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03d4febc7e61425d0057c48949b18281ca3dec4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="programming-guide"></a><span data-ttu-id="31929-102">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="31929-102">Programming Guide</span></span>
<span data-ttu-id="31929-103">Bu bölüm oluşturma ve kullanma hakkında bilgi içerir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="31929-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="31929-104">Kullanıyorsanız [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], aynı zamanda [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] bu gerçekleştirdiğiniz görevlerin çoğunu gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="31929-104">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="31929-105">Microsoft Docs belirli sorunları için arama da yapabilirsiniz ve katılabilirsiniz [LINQ Forumu](http://go.microsoft.com/fwlink/?LinkId=76488), uzmanlarıyla ayrıntılı daha karmaşık konular burada ele.</span><span class="sxs-lookup"><span data-stu-id="31929-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="31929-106">Son olarak, [LINQ-SQL: ilişkisel veri .NET Language-Integrated sorgusu](http://go.microsoft.com/fwlink/?LinkId=93205) incelemeyi ayrıntıları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] teknolojisi ile tam [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ve C# kod örnekleri.</span><span class="sxs-lookup"><span data-stu-id="31929-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31929-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="31929-107">In This Section</span></span>  
 [<span data-ttu-id="31929-108">Nesne modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="31929-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="31929-109">Nesne modeli oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="31929-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="31929-110">Veritabanı ile iletişim</span><span class="sxs-lookup"><span data-stu-id="31929-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="31929-111">Nasıl kullanılacağını açıklar bir <xref:System.Data.Linq.DataContext> nesne bir veritabanı kanalı olarak.</span><span class="sxs-lookup"><span data-stu-id="31929-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="31929-112">Veritabanı sorgulama</span><span class="sxs-lookup"><span data-stu-id="31929-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="31929-113">Sorguları yürütmek açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ve birçok örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31929-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="31929-114">Sağlama ve veri değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="31929-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="31929-115">Açıklar nasıl veritabanındaki verileri değiştirme.</span><span class="sxs-lookup"><span data-stu-id="31929-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="31929-116">Hata ayıklama desteği</span><span class="sxs-lookup"><span data-stu-id="31929-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="31929-117">Hata ayıklama için kullanılabilecek destek açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeleri.</span><span class="sxs-lookup"><span data-stu-id="31929-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="31929-118">Arka plan bilgileri</span><span class="sxs-lookup"><span data-stu-id="31929-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="31929-119">Eşzamanlılık çakışması çözümleme, yeni veritabanları oluşturma gibi ve daha fazlasını daha gelişmiş kullanıcılar için ek öğeler içerir.</span><span class="sxs-lookup"><span data-stu-id="31929-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="31929-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="31929-120">Related Sections</span></span>  
 [<span data-ttu-id="31929-121">LINQ-SQL</span><span class="sxs-lookup"><span data-stu-id="31929-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="31929-122">Açıklayan konulara bağlantılar sağlanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] teknolojisi ve özellikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="31929-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="31929-123">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="31929-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="31929-124">Saklı yordamlar kullanmak nasıl çalışılacağını konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="31929-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="31929-125">Lınq'ye giriş</span><span class="sxs-lookup"><span data-stu-id="31929-125">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 <span data-ttu-id="31929-126">Hakkında bilgi edinmek başlamanıza yardımcı olacak kaynaklar sunulmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31929-126">Provides resources to help you begin to learn about [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

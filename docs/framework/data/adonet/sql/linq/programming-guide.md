---
title: Programlama Kılavuzu
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 542567cf07e86b642a23a879fa6e5476253005b8
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848944"
---
# <a name="programming-guide"></a><span data-ttu-id="39649-102">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="39649-102">Programming Guide</span></span>
<span data-ttu-id="39649-103">Bu bölümde nesne modelinizin nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturulup kullanılacağı hakkında bilgiler yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="39649-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="39649-104">Visual Studio kullanıyorsanız, bu aynı görevlerin çoğunu gerçekleştirmek için Nesne İlişkisel Tasarımcısı'nı da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39649-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="39649-105">Ayrıca belirli sorunlar için Microsoft Dokümanları'nda arama yapabilir ve daha karmaşık konuları uzmanlarla ayrıntılı olarak tartışabileceğiniz [LINQ Forumu'na](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)katılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39649-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="39649-106">Son olarak, [LINQ'dan SQL'e: .NET Dil-İlişkisel Veri için Tümleşik Sorgu](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) teknik [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bilgileri, Visual Basic ve C# kod örnekleri ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="39649-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39649-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="39649-107">In This Section</span></span>  
 [<span data-ttu-id="39649-108">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="39649-108">Creating the Object Model</span></span>](creating-the-object-model.md)  
 <span data-ttu-id="39649-109">Nesne modelinin nasıl üretilebildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="39649-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="39649-110">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="39649-110">Communicating with the Database</span></span>](communicating-with-the-database.md)  
 <span data-ttu-id="39649-111">Veritabanına kanal <xref:System.Data.Linq.DataContext> olarak bir nesnenin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="39649-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="39649-112">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="39649-112">Querying the Database</span></span>](querying-the-database.md)  
 <span data-ttu-id="39649-113">Sorguların [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nasıl yürütüleceklerini açıklar ve birçok örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="39649-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="39649-114">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="39649-114">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)  
 <span data-ttu-id="39649-115">Veritabanındaki verileri nasıl değiştirdiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="39649-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="39649-116">Hata Ayıklama Desteği</span><span class="sxs-lookup"><span data-stu-id="39649-116">Debugging Support</span></span>](debugging-support.md)  
 <span data-ttu-id="39649-117">Hata ayıklama [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeleri için kullanılabilir desteği açıklar.</span><span class="sxs-lookup"><span data-stu-id="39649-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="39649-118">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="39649-118">Background Information</span></span>](background-information.md)  
 <span data-ttu-id="39649-119">Daha gelişmiş kullanıcılar için eşzamanlılık çakışma çözümü, yeni veritabanları oluşturma ve daha fazlası gibi ek öğeler içerir.</span><span class="sxs-lookup"><span data-stu-id="39649-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="39649-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="39649-120">Related Sections</span></span>  
 [<span data-ttu-id="39649-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="39649-121">LINQ to SQL</span></span>](index.md)  
 <span data-ttu-id="39649-122">Teknolojiyi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] açıklayan ve özellikleri gösteren konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="39649-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="39649-123">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="39649-123">Stored Procedures</span></span>](stored-procedures.md)  
 <span data-ttu-id="39649-124">Depolanan yordamların nasıl kullanılacağını gösteren konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="39649-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="39649-125">LINQ'a Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="39649-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="39649-126">C# kullanarak LINQ'dan SQL'e bilgi edinmenize yardımcı olacak kaynaklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="39649-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="39649-127">LINQ'a Giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39649-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="39649-128">Visual Basic'i kullanarak LINQ'dan SQL'e kadar bilgi edinmenize yardımcı olacak kaynaklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="39649-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>

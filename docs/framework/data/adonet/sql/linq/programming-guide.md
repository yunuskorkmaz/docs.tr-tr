---
title: Programlama Kılavuzu
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 50c4370e23faf8400eb23f1e8c0cc74cd4dce80e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203572"
---
# <a name="programming-guide"></a><span data-ttu-id="ffc9f-102">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ffc9f-102">Programming Guide</span></span>

<span data-ttu-id="ffc9f-103">Bu bölüm, nesne modelinizi oluşturma ve kullanma hakkında bilgi içerir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ffc9f-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="ffc9f-104">Visual Studio kullanıyorsanız, aynı görevlerin birçoğunu gerçekleştirmek için Nesne İlişkisel Tasarımcısı de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="ffc9f-105">Ayrıca, belirli sorunlar için Microsoft Docs arayabilir ve uzmanlarla ayrıntılı olarak daha karmaşık konular tartışabilirsiniz [LINQ forumuna](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)katılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="ffc9f-106">Son olarak, [LINQ to SQL: Ilişkisel veri teknik incelemesi için .NET dil tümleşik sorgusu](/previous-versions/dotnet/articles/bb425822(v=msdn.10)) [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , Visual Basic ve C# kod örnekleriyle birlikte tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ffc9f-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ffc9f-107">In This Section</span></span>  

 [<span data-ttu-id="ffc9f-108">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ffc9f-108">Creating the Object Model</span></span>](creating-the-object-model.md)  
 <span data-ttu-id="ffc9f-109">Bir nesne modelinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="ffc9f-110">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="ffc9f-110">Communicating with the Database</span></span>](communicating-with-the-database.md)  
 <span data-ttu-id="ffc9f-111">Bir <xref:System.Data.Linq.DataContext> nesnenin veritabanına bir iletken olarak nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="ffc9f-112">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="ffc9f-112">Querying the Database</span></span>](querying-the-database.md)  
 <span data-ttu-id="ffc9f-113">' De sorguların nasıl yürütüleceğini açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve birçok örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="ffc9f-114">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="ffc9f-114">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)  
 <span data-ttu-id="ffc9f-115">Veritabanındaki verileri değiştirme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="ffc9f-116">Hata Ayıklama Desteği</span><span class="sxs-lookup"><span data-stu-id="ffc9f-116">Debugging Support</span></span>](debugging-support.md)  
 <span data-ttu-id="ffc9f-117">Projelerde hata ayıklama için kullanılabilen desteği açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ffc9f-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="ffc9f-118">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="ffc9f-118">Background Information</span></span>](background-information.md)  
 <span data-ttu-id="ffc9f-119">, Daha gelişmiş kullanıcılar için eşzamanlılık çakışma çözümü, yeni veritabanları oluşturma ve daha fazlası gibi ek öğeler içerir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ffc9f-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ffc9f-120">Related Sections</span></span>  

 [<span data-ttu-id="ffc9f-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ffc9f-121">LINQ to SQL</span></span>](index.md)  
 <span data-ttu-id="ffc9f-122">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Teknolojiyi açıklayan ve özellikleri gösteren konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="ffc9f-123">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="ffc9f-123">Stored Procedures</span></span>](stored-procedures.md)  
 <span data-ttu-id="ffc9f-124">Saklı yordamların nasıl kullanılacağını gösteren konuların bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="ffc9f-125">LINQ 'e giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="ffc9f-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="ffc9f-126">C# kullanarak LINQ to SQL hakkında bilgi edinmenize başlamanıza yardımcı olacak kaynaklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="ffc9f-127">LINQ 'e giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffc9f-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="ffc9f-128">Visual Basic kullanarak LINQ to SQL hakkında bilgi edinmenize başlamanıza yardımcı olacak kaynaklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>

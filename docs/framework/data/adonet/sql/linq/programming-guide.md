---
description: 'Hakkında daha fazla bilgi edinin: Programlama Kılavuzu'
title: Programlama Kılavuzu
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 37f3974864e9bfc11bff762617bab27e25a44007
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695248"
---
# <a name="programming-guide"></a><span data-ttu-id="e2c79-103">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e2c79-103">Programming Guide</span></span>

<span data-ttu-id="e2c79-104">Bu bölüm, nesne modelinizi oluşturma ve kullanma hakkında bilgi içerir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2c79-104">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="e2c79-105">Visual Studio kullanıyorsanız, aynı görevlerin birçoğunu gerçekleştirmek için Nesne İlişkisel Tasarımcısı de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2c79-105">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="e2c79-106">Ayrıca, belirli sorunlar için Microsoft Docs arayabilir ve uzmanlarla ayrıntılı olarak daha karmaşık konular tartışabilirsiniz [LINQ forumuna](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)katılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2c79-106">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="e2c79-107">Son olarak, [Ilişkisel veri teknik incelemesi için LINQ to SQL: .net Language-Integrated sorgusu](/previous-versions/dotnet/articles/bb425822(v=msdn.10)) [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , Visual Basic ve C# kod örnekleri ile birlikte tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e2c79-107">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2c79-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e2c79-108">In This Section</span></span>  

 [<span data-ttu-id="e2c79-109">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e2c79-109">Creating the Object Model</span></span>](creating-the-object-model.md)  
 <span data-ttu-id="e2c79-110">Bir nesne modelinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2c79-110">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="e2c79-111">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="e2c79-111">Communicating with the Database</span></span>](communicating-with-the-database.md)  
 <span data-ttu-id="e2c79-112">Bir <xref:System.Data.Linq.DataContext> nesnenin veritabanına bir iletken olarak nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2c79-112">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="e2c79-113">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="e2c79-113">Querying the Database</span></span>](querying-the-database.md)  
 <span data-ttu-id="e2c79-114">' De sorguların nasıl yürütüleceğini açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve birçok örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2c79-114">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="e2c79-115">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="e2c79-115">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)  
 <span data-ttu-id="e2c79-116">Veritabanındaki verileri değiştirme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2c79-116">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="e2c79-117">Hata Ayıklama Desteği</span><span class="sxs-lookup"><span data-stu-id="e2c79-117">Debugging Support</span></span>](debugging-support.md)  
 <span data-ttu-id="e2c79-118">Projelerde hata ayıklama için kullanılabilen desteği açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2c79-118">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="e2c79-119">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="e2c79-119">Background Information</span></span>](background-information.md)  
 <span data-ttu-id="e2c79-120">, Daha gelişmiş kullanıcılar için eşzamanlılık çakışma çözümü, yeni veritabanları oluşturma ve daha fazlası gibi ek öğeler içerir.</span><span class="sxs-lookup"><span data-stu-id="e2c79-120">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e2c79-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e2c79-121">Related Sections</span></span>  

 [<span data-ttu-id="e2c79-122">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e2c79-122">LINQ to SQL</span></span>](index.md)  
 <span data-ttu-id="e2c79-123">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Teknolojiyi açıklayan ve özellikleri gösteren konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2c79-123">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="e2c79-124">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="e2c79-124">Stored Procedures</span></span>](stored-procedures.md)  
 <span data-ttu-id="e2c79-125">Saklı yordamların nasıl kullanılacağını gösteren konuların bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e2c79-125">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="e2c79-126">LINQ 'e giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="e2c79-126">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="e2c79-127">C# kullanarak LINQ to SQL hakkında bilgi edinmenize başlamanıza yardımcı olacak kaynaklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2c79-127">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="e2c79-128">LINQ 'e giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c79-128">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="e2c79-129">Visual Basic kullanarak LINQ to SQL hakkında bilgi edinmenize başlamanıza yardımcı olacak kaynaklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2c79-129">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>

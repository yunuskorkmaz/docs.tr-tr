---
title: Programlama Kılavuzu
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 102d2ecba162e19258b707c1c902c29b0a7f2f02
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490041"
---
# <a name="programming-guide"></a><span data-ttu-id="a7372-102">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a7372-102">Programming Guide</span></span>
<span data-ttu-id="a7372-103">Bu bölüm oluşturma ve kullanma hakkında bilgi içerir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="a7372-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="a7372-104">Visual Studio kullanıyorsanız, ayrıca kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] bu görevlerin çoğunu gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="a7372-104">If you are using Visual Studio, you can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="a7372-105">Microsoft Docs belirli sorunlar için de arama yapabilir ve katılmak [LINQ Forumu](https://go.microsoft.com/fwlink/?LinkId=76488), uzmanlarıyla ayrıntılı daha karmaşık konuları burada tartışabilir miyiz.</span><span class="sxs-lookup"><span data-stu-id="a7372-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="a7372-106">Son olarak, [LINQ to SQL: ilişkisel veri .NET Language-Integrated sorgusu](https://go.microsoft.com/fwlink/?LinkId=93205) incelemeyi ayrıntıları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] teknolojisi, Visual Basic ve C# kod örnekleri ile tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a7372-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7372-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a7372-107">In This Section</span></span>  
 [<span data-ttu-id="a7372-108">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7372-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="a7372-109">Bir nesne modeli oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a7372-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="a7372-110">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="a7372-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="a7372-111">Nasıl kullanılacağını açıklayan bir <xref:System.Data.Linq.DataContext> veritabanı bir kanalı olarak nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a7372-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="a7372-112">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="a7372-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="a7372-113">Sorguları yürütmek açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ve birçok örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7372-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="a7372-114">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="a7372-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="a7372-115">Açıklayan nasıl veritabanındaki verileri değiştirme.</span><span class="sxs-lookup"><span data-stu-id="a7372-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="a7372-116">Hata Ayıklama Desteği</span><span class="sxs-lookup"><span data-stu-id="a7372-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="a7372-117">Hata ayıklama için kullanılabilir desteğini açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeleri.</span><span class="sxs-lookup"><span data-stu-id="a7372-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="a7372-118">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="a7372-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="a7372-119">Ek öğeler, yeni veritabanları oluşturmak eşzamanlılık çakışma çözümü gibi ve daha gelişmiş kullanıcılar için daha fazlasını içerir.</span><span class="sxs-lookup"><span data-stu-id="a7372-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a7372-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a7372-120">Related Sections</span></span>  
 [<span data-ttu-id="a7372-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a7372-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="a7372-122">Açıklayan konulara bağlantılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] teknoloji ve özellikleri göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a7372-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="a7372-123">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a7372-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="a7372-124">Saklı yordamlar kullanma işlemini gösteren konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="a7372-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="a7372-125">Lınq'ye giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="a7372-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="a7372-126">SQL kullanarak LINQ hakkında bilgi edinmek başlayan yardımcı olacak kaynaklar sunulmaktadır C#.</span><span class="sxs-lookup"><span data-stu-id="a7372-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="a7372-127">Lınq'ye giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7372-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="a7372-128">LINQ-SQL Visual Basic kullanma hakkında bilgi edinmek başlayan yardımcı olacak kaynaklar sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7372-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>

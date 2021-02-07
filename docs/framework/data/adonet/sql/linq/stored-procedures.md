---
description: 'Daha fazla bilgi edinin: saklı yordamlar'
title: Saklı Yordamlar
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 16157dc5a8d2da880deb2d43b649b872d19c73a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681441"
---
# <a name="stored-procedures"></a><span data-ttu-id="22409-103">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="22409-103">Stored Procedures</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="22409-104">Veritabanındaki saklı yordamları göstermek için nesne modelinizdeki yöntemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="22409-104">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="22409-105">Özniteliği ve gereken yerlerde özniteliğini uygulayarak saklı yordamlar olarak yöntemleri belirlersiniz <xref:System.Data.Linq.Mapping.FunctionAttribute> <xref:System.Data.Linq.Mapping.ParameterAttribute> .</span><span class="sxs-lookup"><span data-stu-id="22409-105">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="22409-106">Daha fazla bilgi için bkz. [LINQ to SQL nesne modeli](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="22409-106">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="22409-107">Visual Studio kullanan geliştiriciler, saklı yordamları eşlemek için genellikle Nesne İlişkisel Tasarımcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="22409-107">Developers using Visual Studio would typically use the Object Relational Designer to map stored procedures.</span></span> <span data-ttu-id="22409-108">Bu bölümdeki konularda, kodu kendiniz yazarsanız uygulamanızda bu yöntemlerin nasıl ayarlanacağı ve çağrılacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="22409-108">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22409-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="22409-109">In This Section</span></span>  

 [<span data-ttu-id="22409-110">Nasıl yapılır: Satır Kümeleri Döndürme</span><span class="sxs-lookup"><span data-stu-id="22409-110">How to: Return Rowsets</span></span>](how-to-return-rowsets.md)  
 <span data-ttu-id="22409-111">Veri satırlarının nasıl döndürülmesini açıklar ve bir giriş parametresinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="22409-111">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="22409-112">Nasıl yapılır: Parametre Alan Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="22409-112">How to: Use Stored Procedures that Take Parameters</span></span>](how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="22409-113">Giriş ve çıkış parametrelerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="22409-113">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="22409-114">Nasıl yapılır: Birden Çok Sonuç Şekli İçin Eşlenmiş Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="22409-114">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="22409-115">Aynı saklı yordamda birden çok şeklin döndürülme için nasıl sağlayabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="22409-115">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="22409-116">Nasıl yapılır: Sıralı Sonuç Şekilleri İçin Eşlenmiş Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="22409-116">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="22409-117">Dönüş dizisinin bilindiğinde birden çok şekil için nasıl sağlayabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="22409-117">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="22409-118">Saklı Yordamları Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="22409-118">Customizing Operations By Using Stored Procedures</span></span>](customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="22409-119">INSERT, Update ve DELETE işlemlerini uygulamak için saklı yordamların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="22409-119">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="22409-120">Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="22409-120">Customizing Operations by Using Stored Procedures Exclusively</span></span>](customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="22409-121">INSERT, Update ve DELETE işlemlerini uygulamak için Nothing ancak saklı yordamların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="22409-121">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="22409-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="22409-122">Related Sections</span></span>  

 [<span data-ttu-id="22409-123">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="22409-123">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="22409-124">Nesne modelinizi oluşturma ve kullanma hakkında bilgi sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="22409-124">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="22409-125">İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22409-125">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="22409-126">Visual Basic içinde saklı yordamların nasıl kullanılacağını gösteren yordamları içerir.</span><span class="sxs-lookup"><span data-stu-id="22409-126">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="22409-127">İzlenecek yol: Yalnızca Saklı Yordamları Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="22409-127">Walkthrough: Using Only Stored Procedures (C#)</span></span>](walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="22409-128">C# dilinde saklı yordamların nasıl kullanılacağını gösteren yordamları içerir.</span><span class="sxs-lookup"><span data-stu-id="22409-128">Includes procedures that illustrate how to use stored procedures in C#.</span></span>

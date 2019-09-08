---
title: Saklı Yordamlar
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 80ea105eef33ebb2a0e52d91a631258400ea3dff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792484"
---
# <a name="stored-procedures"></a><span data-ttu-id="28197-102">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="28197-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="28197-103">Veritabanındaki saklı yordamları göstermek için nesne modelinizdeki yöntemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="28197-103">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="28197-104"><xref:System.Data.Linq.Mapping.FunctionAttribute> Özniteliği ve gereken <xref:System.Data.Linq.Mapping.ParameterAttribute> yerlerde özniteliğini uygulayarak saklı yordamlar olarak yöntemleri belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="28197-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="28197-105">Daha fazla bilgi için bkz. [LINQ to SQL nesne modeli](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="28197-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="28197-106">Visual Studio kullanan geliştiriciler, saklı yordamları eşlemek için genellikle Nesne İlişkisel Tasarımcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="28197-106">Developers using Visual Studio would typically use the Object Relational Designer to map stored procedures.</span></span> <span data-ttu-id="28197-107">Bu bölümdeki konularda, kodu kendiniz yazarsanız uygulamanızda bu yöntemlerin nasıl ayarlanacağı ve çağrılacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="28197-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28197-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="28197-108">In This Section</span></span>  
 [<span data-ttu-id="28197-109">Nasıl yapılır: Satır kümelerini döndür</span><span class="sxs-lookup"><span data-stu-id="28197-109">How to: Return Rowsets</span></span>](how-to-return-rowsets.md)  
 <span data-ttu-id="28197-110">Veri satırlarının nasıl döndürülmesini açıklar ve bir giriş parametresinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28197-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="28197-111">Nasıl yapılır: Parametreleri alan saklı yordamları kullanma</span><span class="sxs-lookup"><span data-stu-id="28197-111">How to: Use Stored Procedures that Take Parameters</span></span>](how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="28197-112">Giriş ve çıkış parametrelerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="28197-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="28197-113">Nasıl yapılır: Birden çok sonuç şekli için eşlenmiş saklı yordamları kullan</span><span class="sxs-lookup"><span data-stu-id="28197-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="28197-114">Aynı saklı yordamda birden çok şeklin döndürülme için nasıl sağlayabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="28197-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="28197-115">Nasıl yapılır: Sıralı sonuç şekilleri için eşlenmiş saklı yordamları kullan</span><span class="sxs-lookup"><span data-stu-id="28197-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="28197-116">Dönüş dizisinin bilindiğinde birden çok şekil için nasıl sağlayabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="28197-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="28197-117">Saklı Yordamları Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="28197-117">Customizing Operations By Using Stored Procedures</span></span>](customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="28197-118">INSERT, Update ve DELETE işlemlerini uygulamak için saklı yordamların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="28197-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="28197-119">Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="28197-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="28197-120">INSERT, Update ve DELETE işlemlerini uygulamak için Nothing ancak saklı yordamların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="28197-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="28197-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="28197-121">Related Sections</span></span>  
 [<span data-ttu-id="28197-122">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="28197-122">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="28197-123">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Nesne modelinizi oluşturma ve kullanma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="28197-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="28197-124">İzlenecek yol: Yalnızca saklı yordamları kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28197-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="28197-125">Visual Basic içinde saklı yordamların nasıl kullanılacağını gösteren yordamları içerir.</span><span class="sxs-lookup"><span data-stu-id="28197-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="28197-126">İzlenecek yol: Yalnızca saklı yordamları kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="28197-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="28197-127">Uygulamasında C#saklı yordamların nasıl kullanılacağını gösteren yordamları içerir.</span><span class="sxs-lookup"><span data-stu-id="28197-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>

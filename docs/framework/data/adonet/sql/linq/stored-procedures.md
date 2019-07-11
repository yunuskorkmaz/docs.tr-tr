---
title: Saklı Yordamlar
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: b06dc19aa8b767da6a1c6b00bd5b465465db6060
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742841"
---
# <a name="stored-procedures"></a><span data-ttu-id="6598c-102">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="6598c-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6598c-103">yöntemi, nesne modelinde veritabanında saklı yordamlar temsil etmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="6598c-103">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="6598c-104">Uygulayarak olarak saklı yordamlar belirlediğiniz yöntemleri <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği ve gerekli olduğu durumlarda <xref:System.Data.Linq.Mapping.ParameterAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6598c-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="6598c-105">Daha fazla bilgi için [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="6598c-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="6598c-106">Visual Studio kullanan geliştiricilerin genellikle saklı yordamlar eşlemek için Nesne İlişkisel Tasarımcısı'nı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6598c-106">Developers using Visual Studio would typically use the Object Relational Designer to map stored procedures.</span></span> <span data-ttu-id="6598c-107">Bu bölümdeki konular, form ve kendinize kod yazma, uygulamanız bu yöntemleri çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6598c-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6598c-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6598c-108">In This Section</span></span>  
 [<span data-ttu-id="6598c-109">Nasıl yapılır: Dönüş satır kümeleri</span><span class="sxs-lookup"><span data-stu-id="6598c-109">How to: Return Rowsets</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 <span data-ttu-id="6598c-110">Veri satırı döndürmeyi açıklar ve giriş parametresi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6598c-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="6598c-111">Nasıl yapılır: Parametre alan saklı yordamlar kullanma</span><span class="sxs-lookup"><span data-stu-id="6598c-111">How to: Use Stored Procedures that Take Parameters</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="6598c-112">Giriş ve çıkış parametrelerini kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6598c-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="6598c-113">Nasıl yapılır: Birden çok sonuç şekli için eşlenmiş saklı yordamlar kullanma</span><span class="sxs-lookup"><span data-stu-id="6598c-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="6598c-114">Aynı saklı yordamında birden çok şekil verir sağlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="6598c-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="6598c-115">Nasıl yapılır: Sıralı sonuç şekilleri için eşlenmiş saklı yordamlar kullanma</span><span class="sxs-lookup"><span data-stu-id="6598c-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="6598c-116">Dönüş dizisi olduğu bilinen birden çok şekil için sağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6598c-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="6598c-117">Saklı Yordamları Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6598c-117">Customizing Operations By Using Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="6598c-118">Uygulama ekleme, güncelleştirme ve silme işlemleri için saklı yordamlar kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6598c-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="6598c-119">Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6598c-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="6598c-120">Uygulama ekleme, güncelleştirme ve silme işlemleri için saklı yordamlar ancak hiçbir şey kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6598c-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6598c-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6598c-121">Related Sections</span></span>  
 [<span data-ttu-id="6598c-122">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6598c-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="6598c-123">Oluşturma ve kullanma hakkında bilgi sağlar, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="6598c-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="6598c-124">İzlenecek yol: Yalnızca saklı yordamları (Visual Basic) kullanma</span><span class="sxs-lookup"><span data-stu-id="6598c-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="6598c-125">Visual Basic'te saklı yordamları kullanmak nasıl çalışılacağını yordamları içerir.</span><span class="sxs-lookup"><span data-stu-id="6598c-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="6598c-126">İzlenecek yol: Kullanarak yalnızca saklı yordamları (C#)</span><span class="sxs-lookup"><span data-stu-id="6598c-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="6598c-127">Saklı yordamları kullanmak nasıl çalışılacağını yordamlarını içermektedir C#.</span><span class="sxs-lookup"><span data-stu-id="6598c-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>

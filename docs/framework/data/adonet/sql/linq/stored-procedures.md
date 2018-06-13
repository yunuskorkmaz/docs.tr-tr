---
title: Saklı yordamlar
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 9201965192f300de62679c1e5be75cf98a24e700
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360602"
---
# <a name="stored-procedures"></a><span data-ttu-id="0845e-102">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="0845e-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0845e-103"> yöntemleri nesne modelinde veritabanında depolanan yordamları göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0845e-103"> uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="0845e-104">Uygulayarak olarak saklı yordamlar belirttiğiniz yöntemleri <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği ve gerektiğinde, <xref:System.Data.Linq.Mapping.ParameterAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0845e-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="0845e-105">Daha fazla bilgi için bkz: [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="0845e-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="0845e-106">Visual Studio kullanarak geliştiriciler genellikle kullandığınız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] saklı yordamlar eşlemek için.</span><span class="sxs-lookup"><span data-stu-id="0845e-106">Developers using Visual Studio would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map stored procedures.</span></span> <span data-ttu-id="0845e-107">Bu bölümdeki konular, form ve kodu kendiniz yazarsanız, uygulamanızda bu yöntemleri çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0845e-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0845e-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0845e-108">In This Section</span></span>  
 [<span data-ttu-id="0845e-109">Nasıl yapılır: Satır Kümeleri Döndürme</span><span class="sxs-lookup"><span data-stu-id="0845e-109">How to: Return Rowsets</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 <span data-ttu-id="0845e-110">Veri satırı döndürmeyi açıklar ve bir giriş parametresinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0845e-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="0845e-111">Nasıl yapılır: Parametre Alan Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="0845e-111">How to: Use Stored Procedures that Take Parameters</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="0845e-112">Giriş ve çıkış parametreleri kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0845e-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="0845e-113">Nasıl yapılır: Birden Çok Sonuç Şekli İçin Eşlenmiş Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="0845e-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="0845e-114">Aynı saklı yordamında birden çok şekil verir sağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0845e-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="0845e-115">Nasıl yapılır: Sıralı Sonuç Şekilleri İçin Eşlenmiş Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="0845e-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="0845e-116">Birden çok şekiller için geri dönüş sırası olduğu bilinen sağlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="0845e-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="0845e-117">Saklı Yordamları Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0845e-117">Customizing Operations By Using Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="0845e-118">Uygulama ekleme, güncelleştirme ve silme işlemleri için saklı yordamlar kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0845e-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="0845e-119">Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0845e-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="0845e-120">Uygulama ekleme, güncelleştirme ve silme işlemleri için saklı yordamlar ancak hiçbir şey kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0845e-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0845e-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0845e-121">Related Sections</span></span>  
 [<span data-ttu-id="0845e-122">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0845e-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="0845e-123">Oluşturma ve kullanma hakkında bilgi sağlar, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="0845e-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="0845e-124">İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0845e-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="0845e-125">Visual Basic'te saklı yordamları kullanma göstermeye yordamları içerir.</span><span class="sxs-lookup"><span data-stu-id="0845e-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="0845e-126">İzlenecek yol: Yalnızca Saklı Yordamları Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="0845e-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="0845e-127">Saklı yordamlar C# ile kullanmak nasıl çalışılacağını yordamları içerir.</span><span class="sxs-lookup"><span data-stu-id="0845e-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>

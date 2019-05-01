---
title: <type> türündeki ifade sorgulanabilir değil
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 121c0a95a3a6bb695d9c73347c733cba215a0de4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801627"
---
# <a name="expression-of-type-type-is-not-queryable"></a><span data-ttu-id="f70d7-102">Türündeki ifade \<türü > sorgulanabilir değil</span><span class="sxs-lookup"><span data-stu-id="f70d7-102">Expression of type \<type> is not queryable</span></span>
<span data-ttu-id="f70d7-103">Türündeki ifade \<türü > sorgulanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="f70d7-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="f70d7-104">Bir derleme başvurusunun ve/veya ad alanı alma LINQ sağlayıcısı için eksik olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f70d7-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="f70d7-105">Sorgulanabilir türleri <xref:System.Linq>, <xref:System.Data.Linq>, ve <xref:System.Xml.Linq> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="f70d7-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="f70d7-106">Bir veya daha fazla LINQ sorguları gerçekleştirmek için bu ad alanları içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f70d7-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="f70d7-107"><xref:System.Linq> Ad alanı sağlar, koleksiyonlar ve diziler gibi sorgu nesnelere LINQ kullanarak.</span><span class="sxs-lookup"><span data-stu-id="f70d7-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="f70d7-108"><xref:System.Data.Linq> Ad alanı, ADO.NET veri kümeleri ve SQL Server veritabanlarını LINQ kullanarak sorgulama olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f70d7-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="f70d7-109"><xref:System.Xml.Linq> Ad alanı sayesinde sorgu XML'i LINQ kullanarak ve Visual Basic'te XML özellikleri kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="f70d7-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="f70d7-110">**Hata Kimliği:** BC36593</span><span class="sxs-lookup"><span data-stu-id="f70d7-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f70d7-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f70d7-111">To correct this error</span></span>  
  
1. <span data-ttu-id="f70d7-112">Ekleme bir `Import` bildirimi <xref:System.Linq>, <xref:System.Data.Linq>, veya <xref:System.Xml.Linq> kod dosyanıza ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f70d7-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="f70d7-113">Kullanarak projeniz için ad alanları aktarabilirsiniz **başvuruları** sayfası Proje Tasarımcısı (**Projem**).</span><span class="sxs-lookup"><span data-stu-id="f70d7-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2. <span data-ttu-id="f70d7-114">Sorgulanabilir tür kaynak sorgunuzun olduğu gibi belirlediğiniz türü emin olun.</span><span class="sxs-lookup"><span data-stu-id="f70d7-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="f70d7-115">Diğer bir deyişle, uygulayan bir tür <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="f70d7-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f70d7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f70d7-116">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="f70d7-117">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="f70d7-117">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f70d7-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="f70d7-118">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="f70d7-119">XML</span><span class="sxs-lookup"><span data-stu-id="f70d7-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="f70d7-120">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="f70d7-120">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="f70d7-121">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="f70d7-121">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="f70d7-122">Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f70d7-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)

---
title: İfade türü &lt;türü&gt; sorgulanabilir değil
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 9d333abda5e303f8fab6d1f707df7ac77d8e03ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589015"
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="1ccb6-102">İfade türü &lt;türü&gt; sorgulanabilir değil</span><span class="sxs-lookup"><span data-stu-id="1ccb6-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="1ccb6-103">İfade türü \<türü > sorgulanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="1ccb6-104">Size bir derleme başvurusu ve/veya ad alanı içe aktarma için LINQ sağlayıcısı eksik değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="1ccb6-105">Sorgulanabilir türleri tanımlanmış <xref:System.Linq>, <xref:System.Data.Linq>, ve <xref:System.Xml.Linq> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="1ccb6-106">Bir veya daha fazla LINQ sorgularını gerçekleştirmek için bu ad alanları içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="1ccb6-107"><xref:System.Linq> Ad alanı sağlar, koleksiyonlar ve dizi gibi sorgu nesnelere LINQ kullanarak.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="1ccb6-108"><xref:System.Data.Linq> Ad alanı LINQ kullanarak sorgu ADO.NET veri kümeleri ve SQL Server veritabanlarını olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="1ccb6-109"><xref:System.Xml.Linq> Ad alanı sağlar, sorgu XML'i LINQ kullanarak ve Visual Basic'te XML özellikleri kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="1ccb6-110">**Hata Kimliği:** BC36593</span><span class="sxs-lookup"><span data-stu-id="1ccb6-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1ccb6-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1ccb6-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="1ccb6-112">Ekleme bir `Import` bildirimi <xref:System.Linq>, <xref:System.Data.Linq>, veya <xref:System.Xml.Linq> kodu dosyanıza ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="1ccb6-113">Kullanarak projeniz için ad alanları aktarabilirsiniz **başvuruları** sayfası Proje Tasarımcısı'nın (**My proje**).</span><span class="sxs-lookup"><span data-stu-id="1ccb6-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="1ccb6-114">Sorgunuzun kaynak sorgulanabilir bir türü olarak tanımlanmış türü emin olun.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="1ccb6-115">Diğer bir deyişle, uygulayan bir tür <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ccb6-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ccb6-116">See Also</span></span>  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [<span data-ttu-id="1ccb6-117">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="1ccb6-117">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="1ccb6-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="1ccb6-118">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="1ccb6-119">XML</span><span class="sxs-lookup"><span data-stu-id="1ccb6-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="1ccb6-120">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="1ccb6-120">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="1ccb6-121">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="1ccb6-121">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="1ccb6-122">Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ccb6-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)

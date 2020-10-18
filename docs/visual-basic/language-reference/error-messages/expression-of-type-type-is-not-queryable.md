---
title: <type> türündeki ifade sorgulanabilir değil
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: d605243c213166f20592fdc440a3362f957ebbf2
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163070"
---
# <a name="bc36593-expression-of-type-type-is-not-queryable"></a><span data-ttu-id="aec71-102">BC36593: tür Ifadesi \<type> sorgulanabilir değil</span><span class="sxs-lookup"><span data-stu-id="aec71-102">BC36593: Expression of type \<type> is not queryable</span></span>

<span data-ttu-id="aec71-103">Türündeki ifade \<type> sorgulanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="aec71-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="aec71-104">LINQ sağlayıcısı için bir derleme başvurusu ve/veya ad alanı içeri aktarma olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="aec71-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>

 <span data-ttu-id="aec71-105">Sorgulanabilir türler <xref:System.Linq> ,, <xref:System.Data.Linq> ve <xref:System.Xml.Linq> ad alanlarında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="aec71-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="aec71-106">LINQ sorguları gerçekleştirmek için bu ad alanlarından bir veya daha fazlasını içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aec71-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>

 <span data-ttu-id="aec71-107"><xref:System.Linq>Ad alanı, LINQ kullanarak koleksiyonlar ve diziler gibi nesneleri sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="aec71-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>

 <span data-ttu-id="aec71-108"><xref:System.Data.Linq>Ad alanı, LINQ kullanarak ADO.NET veri kümelerini ve SQL Server veritabanlarını sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="aec71-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>

 <span data-ttu-id="aec71-109"><xref:System.Xml.Linq>Ad alanı, LINQ kullanarak XML sorgusu yapmanızı ve VISUAL BASIC xml özelliklerini kullanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="aec71-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>

 <span data-ttu-id="aec71-110">**Hata kimliği:** BC36593</span><span class="sxs-lookup"><span data-stu-id="aec71-110">**Error ID:** BC36593</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="aec71-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="aec71-111">To correct this error</span></span>

1. <span data-ttu-id="aec71-112">`Import` <xref:System.Linq> <xref:System.Data.Linq> Kod dosyanıza, veya ad alanı için bir ifade ekleyin <xref:System.Xml.Linq> .</span><span class="sxs-lookup"><span data-stu-id="aec71-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="aec71-113">Ayrıca, proje Tasarımcısı 'nın (**projem**) **Başvurular** sayfasını kullanarak projenizin ad alanlarını içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aec71-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>

2. <span data-ttu-id="aec71-114">Sorgunuzun kaynağı olarak tanımladığınız türün sorgulanabilir bir tür olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="aec71-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="aec71-115">Diğer bir deyişle, veya uygulayan bir <xref:System.Collections.Generic.IEnumerable%601> tür <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="aec71-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>

## <a name="see-also"></a><span data-ttu-id="aec71-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aec71-116">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="aec71-117">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="aec71-117">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="aec71-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="aec71-118">LINQ</span></span>](../../programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="aec71-119">XML</span><span class="sxs-lookup"><span data-stu-id="aec71-119">XML</span></span>](../../programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="aec71-120">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="aec71-120">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="aec71-121">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="aec71-121">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="aec71-122">Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aec71-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)

---
description: 'Hakkında daha fazla bilgi edinin: BC36593: tür Ifadesi <type> sorgulanabilir değil'
title: <type> türündeki ifade sorgulanabilir değil
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: b2fc6c81ee34c1f8e251ac65ba582fde1c6a7b9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796359"
---
# <a name="bc36593-expression-of-type-type-is-not-queryable"></a><span data-ttu-id="db324-103">BC36593: tür Ifadesi \<type> sorgulanabilir değil</span><span class="sxs-lookup"><span data-stu-id="db324-103">BC36593: Expression of type \<type> is not queryable</span></span>

<span data-ttu-id="db324-104">Türündeki ifade \<type> sorgulanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="db324-104">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="db324-105">LINQ sağlayıcısı için bir derleme başvurusu ve/veya ad alanı içeri aktarma olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="db324-105">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>

 <span data-ttu-id="db324-106">Sorgulanabilir türler <xref:System.Linq> ,, <xref:System.Data.Linq> ve <xref:System.Xml.Linq> ad alanlarında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="db324-106">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="db324-107">LINQ sorguları gerçekleştirmek için bu ad alanlarından bir veya daha fazlasını içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="db324-107">You must import one or more of these namespaces to perform LINQ queries.</span></span>

 <span data-ttu-id="db324-108"><xref:System.Linq>Ad alanı, LINQ kullanarak koleksiyonlar ve diziler gibi nesneleri sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="db324-108">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>

 <span data-ttu-id="db324-109"><xref:System.Data.Linq>Ad alanı, LINQ kullanarak ADO.NET veri kümelerini ve SQL Server veritabanlarını sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="db324-109">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>

 <span data-ttu-id="db324-110"><xref:System.Xml.Linq>Ad alanı, LINQ kullanarak XML sorgusu yapmanızı ve VISUAL BASIC xml özelliklerini kullanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="db324-110">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>

 <span data-ttu-id="db324-111">**Hata kimliği:** BC36593</span><span class="sxs-lookup"><span data-stu-id="db324-111">**Error ID:** BC36593</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="db324-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="db324-112">To correct this error</span></span>

1. <span data-ttu-id="db324-113">`Import` <xref:System.Linq> <xref:System.Data.Linq> Kod dosyanıza, veya ad alanı için bir ifade ekleyin <xref:System.Xml.Linq> .</span><span class="sxs-lookup"><span data-stu-id="db324-113">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="db324-114">Ayrıca, proje Tasarımcısı 'nın (**projem**) **Başvurular** sayfasını kullanarak projenizin ad alanlarını içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db324-114">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>

2. <span data-ttu-id="db324-115">Sorgunuzun kaynağı olarak tanımladığınız türün sorgulanabilir bir tür olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="db324-115">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="db324-116">Diğer bir deyişle, veya uygulayan bir <xref:System.Collections.Generic.IEnumerable%601> tür <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="db324-116">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>

## <a name="see-also"></a><span data-ttu-id="db324-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db324-117">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="db324-118">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="db324-118">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="db324-119">LINQ</span><span class="sxs-lookup"><span data-stu-id="db324-119">LINQ</span></span>](../../programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="db324-120">XML</span><span class="sxs-lookup"><span data-stu-id="db324-120">XML</span></span>](../../programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="db324-121">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="db324-121">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="db324-122">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="db324-122">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="db324-123">Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db324-123">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)

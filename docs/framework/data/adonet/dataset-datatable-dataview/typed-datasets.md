---
title: "Yazılan veri kümeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3d5edc4f469b59ff787e500ad447fe0076c332c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="typed-datasets"></a><span data-ttu-id="232d6-102">Yazılan veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="232d6-102">Typed DataSets</span></span>
<span data-ttu-id="232d6-103">Zayıf yazılmış değişkenlerinin değerlerini geç bağlama erişimi birlikte <xref:System.Data.DataSet> kesin türü belirtilmiş bir benzetimini verilerine erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="232d6-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="232d6-104">Tabloları ve parçası olan sütunları **DataSet** kolay adlar kullanılarak erişilebilir ve değişkenleri'kesin türü belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="232d6-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="232d6-105">Yazılmış bir **DataSet** türeyen bir sınıf bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="232d6-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="232d6-106">Bu nedenle, tüm yöntemleri, olayları ve özelliklerini devralır bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="232d6-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="232d6-107">Ayrıca, yazılı **DataSet** kesin türü belirtilmiş yöntemleri, olayları ve özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="232d6-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="232d6-108">Başka bir deyişle, koleksiyon tabanlı yöntemleri kullanmak yerine ada göre tablolar ve sütunlar erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="232d6-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="232d6-109">Yazılmış bir kod geliştirilmiş okunabilirliğini yanı sıra **DataSet** Visual Studio .NET kod yazarken satırları otomatik olarak tamamlamak Düzenleyicisi'ni de sağlar.</span><span class="sxs-lookup"><span data-stu-id="232d6-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="232d6-110">Ayrıca, kesin türü belirtilmiş **DataSet** derleme zamanında doğru türü olarak değerlerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="232d6-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="232d6-111">Kesin türü belirtilmiş ile **DataSet**, tür uyuşmazlığı hatalarının kodu derlenmiş yerine, çalışma zamanında yakalandı.</span><span class="sxs-lookup"><span data-stu-id="232d6-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="232d6-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="232d6-112">In This Section</span></span>  
 [<span data-ttu-id="232d6-113">Kesin türü belirtilmiş veri kümeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="232d6-113">Generating Strongly Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 <span data-ttu-id="232d6-114">Oluşturma ve kesin türü belirtilmiş kullanma açıklar **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="232d6-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="232d6-115">Yazılan veri kümeleri yorumlama</span><span class="sxs-lookup"><span data-stu-id="232d6-115">Annotating Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 <span data-ttu-id="232d6-116">Kesin türü belirtilmiş oluşturmak için kullanılan XML Şeması Tanım Dili (XSD) şeması açıklama ekleme açıklar **DataSet**, vermek için **DataSet** temel şeması değiştirmeden öğeleri kolay adlar.</span><span class="sxs-lookup"><span data-stu-id="232d6-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="232d6-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="232d6-117">See Also</span></span>  
 [<span data-ttu-id="232d6-118">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="232d6-118">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="232d6-119">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="232d6-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

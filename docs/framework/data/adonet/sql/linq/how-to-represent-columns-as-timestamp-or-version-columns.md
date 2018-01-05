---
title: "Nasıl yapılır: zaman damgası veya sürümü sütunları sütunları temsil eder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 465be5cc0125d0ac45c0a00d7f1f238f3de8a390
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="bedc7-102">Nasıl yapılır: zaman damgası veya sürümü sütunları sütunları temsil eder</span><span class="sxs-lookup"><span data-stu-id="bedc7-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="bedc7-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> veritabanı zaman damgaları ya da sürüm numaralarıyla tutan bir veritabanı sütununa temsil eden farklı bir alan veya özellik atamak özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bedc7-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="bedc7-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="bedc7-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="bedc7-105">Bir alan veya özellik bir zaman damgası veya sürüm sütunu temsil eden olarak atamak için</span><span class="sxs-lookup"><span data-stu-id="bedc7-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="bedc7-106">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bedc7-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="bedc7-107">Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özellik değerine `true`.</span><span class="sxs-lookup"><span data-stu-id="bedc7-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bedc7-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bedc7-108">See Also</span></span>  
 [<span data-ttu-id="bedc7-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="bedc7-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="bedc7-110">Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme</span><span class="sxs-lookup"><span data-stu-id="bedc7-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [<span data-ttu-id="bedc7-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="bedc7-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)

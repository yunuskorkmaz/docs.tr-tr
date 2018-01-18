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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2f97b87b2070ea39dbd16d03a967d80dcfc8f500
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="b81b2-102">Nasıl yapılır: zaman damgası veya sürümü sütunları sütunları temsil eder</span><span class="sxs-lookup"><span data-stu-id="b81b2-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="b81b2-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> veritabanı zaman damgaları ya da sürüm numaralarıyla tutan bir veritabanı sütununa temsil eden farklı bir alan veya özellik atamak özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b81b2-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="b81b2-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="b81b2-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="b81b2-105">Bir alan veya özellik bir zaman damgası veya sürüm sütunu temsil eden olarak atamak için</span><span class="sxs-lookup"><span data-stu-id="b81b2-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="b81b2-106">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b81b2-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="b81b2-107">Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özellik değerine `true`.</span><span class="sxs-lookup"><span data-stu-id="b81b2-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b81b2-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b81b2-108">See Also</span></span>  
 [<span data-ttu-id="b81b2-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="b81b2-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="b81b2-110">Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme</span><span class="sxs-lookup"><span data-stu-id="b81b2-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [<span data-ttu-id="b81b2-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b81b2-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)

---
title: "Nasıl yapılır: hesaplanan sütunlar temsil eder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eef3d12d3b0baa849d8eee1a01a87e3c6eee1c7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="a3abd-102">Nasıl yapılır: hesaplanan sütunlar temsil eder</span><span class="sxs-lookup"><span data-stu-id="a3abd-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="a3abd-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> özelliği bir <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği içeriği hesaplamanın sonucu olan bir sütunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a3abd-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="a3abd-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3abd-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a3abd-105">Hesaplanan sütunlar birincil anahtarlar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a3abd-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="a3abd-106">Hesaplanmış bir sütun göstermek için</span><span class="sxs-lookup"><span data-stu-id="a3abd-106">To represent a computed column</span></span>  
  
1.  <span data-ttu-id="a3abd-107">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a3abd-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="a3abd-108">Bir formüle dize gösterimini atamak <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a3abd-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3abd-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3abd-109">See Also</span></span>  
 [<span data-ttu-id="a3abd-110">LINQ to SQL nesne modeli</span><span class="sxs-lookup"><span data-stu-id="a3abd-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="a3abd-111">Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a3abd-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)

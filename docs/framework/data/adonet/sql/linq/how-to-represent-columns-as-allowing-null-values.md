---
title: 'Nasıl yapılır: Sütunları Null Değerlere İzin Verecek Şekilde Temsil Etme'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: ec88429ed9c1f91917476cc807bd6b53f0bcc3a3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166371"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="aa6b3-102">Nasıl yapılır: Sütunları Null Değerlere İzin Verecek Şekilde Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="aa6b3-102">How to: Represent Columns as Allowing Null Values</span></span>

<span data-ttu-id="aa6b3-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> İlişkili veritabanı sütununun null değerleri tutabilmek için özniteliğinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa6b3-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="aa6b3-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> ..</span><span class="sxs-lookup"><span data-stu-id="aa6b3-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="aa6b3-105">Bir sütunu null değerlere izin verecek şekilde belirlemek için</span><span class="sxs-lookup"><span data-stu-id="aa6b3-105">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="aa6b3-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aa6b3-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="aa6b3-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>Özellik değerini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="aa6b3-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa6b3-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa6b3-108">See also</span></span>

- [<span data-ttu-id="aa6b3-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="aa6b3-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="aa6b3-110">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="aa6b3-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)

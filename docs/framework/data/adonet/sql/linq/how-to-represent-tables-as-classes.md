---
title: 'Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 1169def4e0180b1d14103d4a968ff3ed56f63d0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781761"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="98d44-102">Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="98d44-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="98d44-103">Bir sınıfı bir veritabanı tablosuyla ilişkili bir varlık sınıfı olarak belirlemek için özniteliğinikullanın.<xref:System.Data.Linq.Mapping.TableAttribute> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98d44-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="98d44-104">Bir sınıfı bir veritabanı tablosuyla eşlemek için</span><span class="sxs-lookup"><span data-stu-id="98d44-104">To map a class to a database table</span></span>  
  
- <span data-ttu-id="98d44-105"><xref:System.Data.Linq.Mapping.TableAttribute> Özniteliği sınıf bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="98d44-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98d44-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="98d44-106">Example</span></span>  
 <span data-ttu-id="98d44-107">Aşağıdaki kod, `Customer` sınıfını `Customers` veritabanı tablosuyla ilişkili bir varlık sınıfı olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98d44-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="98d44-108">Ad çıkarsancan <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> özelliğini belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="98d44-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="98d44-109">Bir ad belirtmezseniz, ad, özellik veya alanla aynı ada sahip olacak şekilde adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="98d44-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d44-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98d44-110">See also</span></span>

- [<span data-ttu-id="98d44-111">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="98d44-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="98d44-112">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="98d44-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)

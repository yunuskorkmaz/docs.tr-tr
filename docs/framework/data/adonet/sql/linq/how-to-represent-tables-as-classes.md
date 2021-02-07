---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: tabloları sınıf olarak temsil etme'
title: 'Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 9ec5b7309d7d10eaa6e4da6cd6fe4b1d03df1dd9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723588"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="67688-103">Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="67688-103">How to: Represent Tables as Classes</span></span>

<span data-ttu-id="67688-104">Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> sınıfı bir veritabanı tablosuyla ilişkili bir varlık sınıfı olarak belirlemek için özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="67688-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="67688-105">Bir sınıfı bir veritabanı tablosuyla eşlemek için</span><span class="sxs-lookup"><span data-stu-id="67688-105">To map a class to a database table</span></span>  
  
- <span data-ttu-id="67688-106"><xref:System.Data.Linq.Mapping.TableAttribute>Özniteliği sınıf bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="67688-106">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67688-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="67688-107">Example</span></span>  

 <span data-ttu-id="67688-108">Aşağıdaki kod, `Customer` sınıfını veritabanı tablosuyla ilişkili bir varlık sınıfı olarak oluşturur `Customers` .</span><span class="sxs-lookup"><span data-stu-id="67688-108">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="67688-109"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>Ad çıkarsancan özelliğini belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="67688-109">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="67688-110">Bir ad belirtmezseniz, ad, özellik veya alanla aynı ada sahip olacak şekilde adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="67688-110">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67688-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67688-111">See also</span></span>

- [<span data-ttu-id="67688-112">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="67688-112">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="67688-113">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="67688-113">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)

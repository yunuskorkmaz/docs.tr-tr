---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sıralı sonuç şekilleri için eşlenmiş saklı yordamları kullanma'
title: 'Nasıl yapılır: Sıralı Sonuç Şekilleri İçin Eşlenmiş Saklı Yordamlar Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 3b5791875a7beb5a0c702e787e775cd528ab2517
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738773"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="80d90-103">Nasıl yapılır: Sıralı Sonuç Şekilleri İçin Eşlenmiş Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="80d90-103">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>

<span data-ttu-id="80d90-104">Bu tür bir saklı yordam birden fazla sonuç şekli oluşturabilir, ancak sonuçların döndürüldüğü sırayı bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80d90-104">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="80d90-105">Bu senaryoya, döndürmeyen diziyi bildiğiniz senaryolarla kontrast.</span><span class="sxs-lookup"><span data-stu-id="80d90-105">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="80d90-106">Daha fazla bilgi için bkz. [nasıl yapılır: birden çok sonuç şekli Için eşlenmiş saklı yordamları kullanma](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="80d90-106">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80d90-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="80d90-107">Example</span></span>  

 <span data-ttu-id="80d90-108">Ardışık olarak birden çok sonuç şekli döndüren saklı yordamın T-SQL ' i aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="80d90-108">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```sql
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="80d90-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="80d90-109">Example</span></span>  

 <span data-ttu-id="80d90-110">Bu saklı yordamı yürütmek için aşağıdakine benzer bir kod kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="80d90-110">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="80d90-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80d90-111">See also</span></span>

- [<span data-ttu-id="80d90-112">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="80d90-112">Stored Procedures</span></span>](stored-procedures.md)

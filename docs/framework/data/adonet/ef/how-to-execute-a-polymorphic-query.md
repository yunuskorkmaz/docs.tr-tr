---
description: 'Daha fazla bilgi edinin: nasıl yapılır: çok biçimli bir sorgu yürütme'
title: 'Nasıl yapılır: Çok Biçimli Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 02074fb0ad60e5ba8d62094e25f35db40f8a2dbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650748"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="8467a-103">Nasıl yapılır: Çok Biçimli Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="8467a-103">How to: Execute a Polymorphic Query</span></span>

<span data-ttu-id="8467a-104">Bu konuda [!INCLUDE[esql](../../../../../includes/esql-md.md)] , [OFTYPE](./language-reference/oftype-entity-sql.md) işleci kullanılarak çok biçimli bir sorgunun nasıl yürütüleceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8467a-104">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](./language-reference/oftype-entity-sql.md) operator.</span></span>

### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="8467a-105">Bu örnekteki kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8467a-105">To run the code in this example</span></span>

1. <span data-ttu-id="8467a-106">[Okul modelini](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) projenize ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="8467a-106">Add the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="8467a-107">Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8467a-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

2. <span data-ttu-id="8467a-108">Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="8467a-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. <span data-ttu-id="8467a-109">Kavramsal modeli, [Izlenecek yol: eşleme devralma-tablo başına hiyerarşiye](/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100))göre bir hiyerarşi başına devralma olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8467a-109">Modify the conceptual model to have a table-per-hierarchy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="8467a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8467a-110">Example</span></span>

<span data-ttu-id="8467a-111">Aşağıdaki örnek, yalnızca bir koleksiyonundan bir koleksiyon almak ve göstermek için bir OFTYPE işleci kullanır `OnsiteCourses` `Courses` .</span><span class="sxs-lookup"><span data-stu-id="8467a-111">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a><span data-ttu-id="8467a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8467a-112">See also</span></span>

- [<span data-ttu-id="8467a-113">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8467a-113">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="8467a-114">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="8467a-114">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)

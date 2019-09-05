---
title: 'Nasıl yapılır: Çok Biçimli Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 49e0a6b44af0729959fabf6278cc6d8ecf37a16b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251505"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="f4d08-102">Nasıl yapılır: Çok Biçimli Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="f4d08-102">How to: Execute a Polymorphic Query</span></span>

<span data-ttu-id="f4d08-103">Bu konuda, [OFTYPE](./language-reference/oftype-entity-sql.md) işleci kullanılarak çok biçimli [!INCLUDE[esql](../../../../../includes/esql-md.md)] bir sorgunun nasıl yürütüleceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4d08-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](./language-reference/oftype-entity-sql.md) operator.</span></span>

### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="f4d08-104">Bu örnekteki kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f4d08-104">To run the code in this example</span></span>

1. <span data-ttu-id="f4d08-105">[Okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) projenize ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f4d08-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="f4d08-106">Daha fazla bilgi için [nasıl yapılır: Varlık Veri Modeli Sihirbazı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4d08-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

2. <span data-ttu-id="f4d08-107">Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin (`Imports` Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="f4d08-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. <span data-ttu-id="f4d08-108">Adım adım [İzlenecek adımları izleyerek kavramsal modeli bir hiyerarşi başına tablo devralım olacak şekilde değiştirin: Eşleme devralma-tablo başına hiyerarşi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f4d08-108">Modify the conceptual model to have a table-per-hierarchy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="f4d08-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4d08-109">Example</span></span>

<span data-ttu-id="f4d08-110">Aşağıdaki örnek, yalnızca `OnsiteCourses` bir `Courses`koleksiyonundan bir koleksiyon almak ve göstermek için bir OFTYPE işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4d08-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a><span data-ttu-id="f4d08-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4d08-111">See also</span></span>

- [<span data-ttu-id="f4d08-112">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="f4d08-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="f4d08-113">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="f4d08-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)

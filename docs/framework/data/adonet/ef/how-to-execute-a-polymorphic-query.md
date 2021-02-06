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
# <a name="how-to-execute-a-polymorphic-query"></a>Nasıl yapılır: Çok Biçimli Sorgu Yürütme

Bu konuda [!INCLUDE[esql](../../../../../includes/esql-md.md)] , [OFTYPE](./language-reference/oftype-entity-sql.md) işleci kullanılarak çok biçimli bir sorgunun nasıl yürütüleceği gösterilmektedir.

### <a name="to-run-the-code-in-this-example"></a>Bu örnekteki kodu çalıştırmak için

1. [Okul modelini](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) projenize ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

2. Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. Kavramsal modeli, [Izlenecek yol: eşleme devralma-tablo başına hiyerarşiye](/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100))göre bir hiyerarşi başına devralma olacak şekilde değiştirin.

## <a name="example"></a>Örnek

Aşağıdaki örnek, yalnızca bir koleksiyonundan bir koleksiyon almak ve göstermek için bir OFTYPE işleci kullanır `OnsiteCourses` `Courses` .

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için EntityClient Sağlayıcısı](entityclient-provider-for-the-entity-framework.md)
- [Entity SQL Dili](./language-reference/entity-sql-language.md)

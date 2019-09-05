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
# <a name="how-to-execute-a-polymorphic-query"></a>Nasıl yapılır: Çok Biçimli Sorgu Yürütme

Bu konuda, [OFTYPE](./language-reference/oftype-entity-sql.md) işleci kullanılarak çok biçimli [!INCLUDE[esql](../../../../../includes/esql-md.md)] bir sorgunun nasıl yürütüleceği gösterilmektedir.

### <a name="to-run-the-code-in-this-example"></a>Bu örnekteki kodu çalıştırmak için

1. [Okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) projenize ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın. Daha fazla bilgi için [nasıl yapılır: Varlık Veri Modeli Sihirbazı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))'nı kullanın.

2. Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin (`Imports` Visual Basic):

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. Adım adım [İzlenecek adımları izleyerek kavramsal modeli bir hiyerarşi başına tablo devralım olacak şekilde değiştirin: Eşleme devralma-tablo başına hiyerarşi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).

## <a name="example"></a>Örnek

Aşağıdaki örnek, yalnızca `OnsiteCourses` bir `Courses`koleksiyonundan bir koleksiyon almak ve göstermek için bir OFTYPE işleci kullanır.

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için EntityClient Sağlayıcısı](entityclient-provider-for-the-entity-framework.md)
- [Entity SQL Dili](./language-reference/entity-sql-language.md)

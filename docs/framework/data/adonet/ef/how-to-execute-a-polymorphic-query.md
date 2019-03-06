---
title: 'Nasıl yapılır: Çok biçimli sorgu yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 08ae5722267ef781ed6bee59c7895269f63a75e5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355561"
---
# <a name="how-to-execute-a-polymorphic-query"></a>Nasıl yapılır: Çok biçimli sorgu yürütme

Bu konuda, bir çok biçimli yürütülecek gösterilmektedir [!INCLUDE[esql](../../../../../includes/esql-md.md)] kullanarak sorgu [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) işleci.

### <a name="to-run-the-code-in-this-example"></a>Bu örnekte, kodu çalıştırmak için

1. Ekleme [Okul modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) projenize ve projenizi Entity Framework kullanmak üzere yapılandırın. Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

2. Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. İçindeki adımları izleyerek bir tablo başına hiyerarşi devralma için kavramsal model değiştirme [izlenecek yol: Devralma - tablo başına hiyerarşi eşleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).

## <a name="example"></a>Örnek

Aşağıdaki örnek, almak ve yalnızca koleksiyonunu görüntülemek için bir OFTYPE işleci kullanır. `OnsiteCourses` koleksiyonundan `Courses`.

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için EntityClient Sağlayıcısı](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
- [Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)

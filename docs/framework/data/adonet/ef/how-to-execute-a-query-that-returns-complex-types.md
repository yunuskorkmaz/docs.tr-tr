---
title: 'Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: a428f54c3834ccdf6a0c7a5bfce8307172724524
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322894"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme
Bu konu nasıl çalıştırılacağını gösteren bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] varlığı içeren bir karmaşık türü bir özellik türü nesneleri döndüren sorgu.  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekte, kodu çalıştırmak için  
  
1. Ekleme [AdventureWorks satışları modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Modelinde görüntülemek üzere .edmx dosyasını çift tıklatın [Model tarayıcı penceresi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) varlık Tasarımcısı'nın. Varlık Tasarımcısı yüzeyine seçin `Email` ve `Phone` özelliklerini `Contact` varlık türü, ardından sütuna sağ tıklayıp **yeni karmaşık tür yeniden düzenleme**.  
  
4. Yeni bir karmaşık türü ile seçilen `Email` ve `Phone` özellikler eklenir **Model tarayıcı**. Karmaşık tür bir varsayılan ad verilir: türüne Yeniden Adlandır `EmailPhone` içinde **özellikleri** penceresi. Ayrıca, yeni `ComplexProperty` özelliği eklenir `Contact` varlık türü. Özelliği yeniden adlandır `EmailPhoneComplexType.`  
  
     Oluşturma ve varlık veri modeli Sihirbazı'nı kullanarak karmaşık türler değiştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir karmaşık tür özelliği mevcut özellikleri yeniden düzenleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) ve [nasıl yapılır: Karmaşık türler oluşturup](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir koleksiyonunu döndüren bir sorgu yürütür `Contact` nesneleri ve iki özelliklerini görüntüler `Contact` nesneleri: `ContactID` ve değerlerini `EmailPhoneComplexType` karmaşık tür.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]

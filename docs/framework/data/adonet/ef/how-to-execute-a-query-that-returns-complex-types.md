---
title: 'Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b08b220e969ad1c400413978c85b2f107d64a688
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854645"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme
Bu konu, karmaşık bir türün özelliğini [!INCLUDE[esql](../../../../../includes/esql-md.md)] içeren varlık türü nesneleri döndüren bir sorgunun nasıl yürütüleceğini gösterir.  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekteki kodu çalıştırmak için  
  
1. Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın. Daha fazla bilgi için [nasıl yapılır: Varlık Veri Modeli Sihirbazı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))'nı kullanın.  
  
2. Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin (`Imports` Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Modeli Entity Desisgner [model tarayıcısı penceresinde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) göstermek için. edmx dosyasına çift tıklayın. Entity Desisgner yüzeyinde `Email` `Contact` varlık türünün ve `Phone` özelliklerini seçin, sonra sağ tıklayıp **Yeni karmaşık türde yeniden Düzenle**' yi seçin.  
  
4. `Email` **Model tarayıcıya**seçili ve `Phone` özelliklere sahip yeni bir karmaşık tür eklenmiştir. Karmaşık türe varsayılan ad verilir: `EmailPhone` **Özellikler** penceresinde türü olarak yeniden adlandırın. Ayrıca, `Contact` varlık türüne `ComplexProperty` yeni bir özellik eklenir. Özelliği olarak yeniden adlandırın`EmailPhoneComplexType.`  
  
     Varlık veri modeli Sihirbazı 'nı kullanarak karmaşık türleri oluşturma ve değiştirme hakkında bilgi için bkz [. nasıl yapılır: Varolan özellikleri karmaşık bir tür özelliğinde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) yeniden düzenleyin ve [şunları yapın: Karmaşık türler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))oluşturun ve değiştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir `Contact` nesne koleksiyonu döndüren ve `Contact` nesnelerin `ContactID` iki özelliğini ve `EmailPhoneComplexType` karmaşık türün değerlerini görüntüleyen bir sorgu yürütür.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]

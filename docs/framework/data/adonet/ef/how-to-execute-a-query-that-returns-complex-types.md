---
title: 'Nasıl yapılır: karmaşık türler döndüren bir sorgu yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 013f1980d2ea13927871719aeea293cfce38b4d5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861900"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Nasıl yapılır: karmaşık türler döndüren bir sorgu yürütme
Bu konu nasıl çalıştırılacağını gösteren bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] varlığı içeren bir karmaşık türü bir özellik türü nesneleri döndüren sorgu.  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekte, kodu çalıştırmak için  
  
1.  Ekleme [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Modelinde görüntülemek üzere .edmx dosyasını çift tıklatın [Model tarayıcı penceresi](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) varlık Tasarımcısı'nın. Varlık Tasarımcısı yüzeyine seçin `Email` ve `Phone` özelliklerini `Contact` varlık türü, ardından sütuna sağ tıklayıp **yeni karmaşık tür yeniden düzenleme**.  
  
4.  Yeni bir karmaşık türü ile seçilen `Email` ve `Phone` özellikler eklenir **Model tarayıcı**. Karmaşık tür bir varsayılan ad verilir: türüne Yeniden Adlandır `EmailPhone` içinde **özellikleri** penceresi. Ayrıca, yeni `ComplexProperty` özelliği eklenir `Contact` varlık türü. Özelliği yeniden adlandır `EmailPhoneComplexType.`  
  
     Oluşturma ve varlık veri modeli Sihirbazı'nı kullanarak karmaşık türler değiştirme hakkında daha fazla bilgi için bkz [nasıl yapılır: karmaşık bir tür özelliği mevcut özelliklerine yeniden düzenleyin](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) ve [nasıl yapılır: oluşturma ve karmaşık türlerdeğiştirme](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir koleksiyonunu döndüren bir sorgu yürütür `Contact` nesneleri ve iki özelliklerini görüntüler `Contact` nesneleri: `ContactID` ve değerlerini `EmailPhoneComplexType` karmaşık tür.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]

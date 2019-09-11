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
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="71cf5-102">Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="71cf5-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="71cf5-103">Bu konu, karmaşık bir türün özelliğini [!INCLUDE[esql](../../../../../includes/esql-md.md)] içeren varlık türü nesneleri döndüren bir sorgunun nasıl yürütüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="71cf5-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="71cf5-104">Bu örnekteki kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="71cf5-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="71cf5-105">Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="71cf5-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="71cf5-106">Daha fazla bilgi için [nasıl yapılır: Varlık Veri Modeli Sihirbazı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="71cf5-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="71cf5-107">Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin (`Imports` Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="71cf5-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="71cf5-108">Modeli Entity Desisgner [model tarayıcısı penceresinde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) göstermek için. edmx dosyasına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="71cf5-108">Double click the .edmx file to display the model in the [Model Browser window](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) of the Entity Designer.</span></span> <span data-ttu-id="71cf5-109">Entity Desisgner yüzeyinde `Email` `Contact` varlık türünün ve `Phone` özelliklerini seçin, sonra sağ tıklayıp **Yeni karmaşık türde yeniden Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="71cf5-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4. <span data-ttu-id="71cf5-110">`Email` **Model tarayıcıya**seçili ve `Phone` özelliklere sahip yeni bir karmaşık tür eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="71cf5-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="71cf5-111">Karmaşık türe varsayılan ad verilir: `EmailPhone` **Özellikler** penceresinde türü olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="71cf5-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="71cf5-112">Ayrıca, `Contact` varlık türüne `ComplexProperty` yeni bir özellik eklenir.</span><span class="sxs-lookup"><span data-stu-id="71cf5-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="71cf5-113">Özelliği olarak yeniden adlandırın`EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="71cf5-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="71cf5-114">Varlık veri modeli Sihirbazı 'nı kullanarak karmaşık türleri oluşturma ve değiştirme hakkında bilgi için bkz [. nasıl yapılır: Varolan özellikleri karmaşık bir tür özelliğinde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) yeniden düzenleyin ve [şunları yapın: Karmaşık türler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))oluşturun ve değiştirin.</span><span class="sxs-lookup"><span data-stu-id="71cf5-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) and [How to: Create and Modify Complex Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71cf5-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="71cf5-115">Example</span></span>  
 <span data-ttu-id="71cf5-116">Aşağıdaki örnek bir `Contact` nesne koleksiyonu döndüren ve `Contact` nesnelerin `ContactID` iki özelliğini ve `EmailPhoneComplexType` karmaşık türün değerlerini görüntüleyen bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="71cf5-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]

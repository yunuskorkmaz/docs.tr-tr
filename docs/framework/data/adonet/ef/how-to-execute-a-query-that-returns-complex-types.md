---
title: 'Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: a428f54c3834ccdf6a0c7a5bfce8307172724524
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322894"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="e8b54-102">Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="e8b54-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="e8b54-103">Bu konu nasıl çalıştırılacağını gösteren bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] varlığı içeren bir karmaşık türü bir özellik türü nesneleri döndüren sorgu.</span><span class="sxs-lookup"><span data-stu-id="e8b54-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="e8b54-104">Bu örnekte, kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e8b54-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="e8b54-105">Ekleme [AdventureWorks satışları modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8b54-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="e8b54-106">Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e8b54-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="e8b54-107">Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="e8b54-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="e8b54-108">Modelinde görüntülemek üzere .edmx dosyasını çift tıklatın [Model tarayıcı penceresi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) varlık Tasarımcısı'nın.</span><span class="sxs-lookup"><span data-stu-id="e8b54-108">Double click the .edmx file to display the model in the [Model Browser window](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) of the Entity Designer.</span></span> <span data-ttu-id="e8b54-109">Varlık Tasarımcısı yüzeyine seçin `Email` ve `Phone` özelliklerini `Contact` varlık türü, ardından sütuna sağ tıklayıp **yeni karmaşık tür yeniden düzenleme**.</span><span class="sxs-lookup"><span data-stu-id="e8b54-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4. <span data-ttu-id="e8b54-110">Yeni bir karmaşık türü ile seçilen `Email` ve `Phone` özellikler eklenir **Model tarayıcı**.</span><span class="sxs-lookup"><span data-stu-id="e8b54-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="e8b54-111">Karmaşık tür bir varsayılan ad verilir: türüne Yeniden Adlandır `EmailPhone` içinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="e8b54-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="e8b54-112">Ayrıca, yeni `ComplexProperty` özelliği eklenir `Contact` varlık türü.</span><span class="sxs-lookup"><span data-stu-id="e8b54-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="e8b54-113">Özelliği yeniden adlandır</span><span class="sxs-lookup"><span data-stu-id="e8b54-113">Rename the property to</span></span> `EmailPhoneComplexType.`  
  
     <span data-ttu-id="e8b54-114">Oluşturma ve varlık veri modeli Sihirbazı'nı kullanarak karmaşık türler değiştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir karmaşık tür özelliği mevcut özellikleri yeniden düzenleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) ve [nasıl yapılır: Karmaşık türler oluşturup](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e8b54-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) and [How to: Create and Modify Complex Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8b54-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8b54-115">Example</span></span>  
 <span data-ttu-id="e8b54-116">Aşağıdaki örnek bir koleksiyonunu döndüren bir sorgu yürütür `Contact` nesneleri ve iki özelliklerini görüntüler `Contact` nesneleri: `ContactID` ve değerlerini `EmailPhoneComplexType` karmaşık tür.</span><span class="sxs-lookup"><span data-stu-id="e8b54-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]

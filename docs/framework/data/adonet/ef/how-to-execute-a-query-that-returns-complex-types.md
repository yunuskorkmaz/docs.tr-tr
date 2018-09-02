---
title: 'Nasıl yapılır: karmaşık türler döndüren bir sorgu yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 013f1980d2ea13927871719aeea293cfce38b4d5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385313"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="f2f0a-102">Nasıl yapılır: karmaşık türler döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="f2f0a-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="f2f0a-103">Bu konu nasıl çalıştırılacağını gösteren bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] varlığı içeren bir karmaşık türü bir özellik türü nesneleri döndüren sorgu.</span><span class="sxs-lookup"><span data-stu-id="f2f0a-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="f2f0a-104">Bu örnekte, kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f2f0a-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="f2f0a-105">Ekleme [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2f0a-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="f2f0a-106">Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="f2f0a-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="f2f0a-107">Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="f2f0a-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="f2f0a-108">Modelinde görüntülemek üzere .edmx dosyasını çift tıklatın [Model tarayıcı penceresi](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) varlık Tasarımcısı'nın.</span><span class="sxs-lookup"><span data-stu-id="f2f0a-108">Double click the .edmx file to display the model in the [Model Browser window](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) of the Entity Designer.</span></span> <span data-ttu-id="f2f0a-109">Varlık Tasarımcısı yüzeyine seçin `Email` ve `Phone` özelliklerini `Contact` varlık türü, ardından sütuna sağ tıklayıp **yeni karmaşık tür yeniden düzenleme**.</span><span class="sxs-lookup"><span data-stu-id="f2f0a-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="f2f0a-110">Yeni bir karmaşık türü ile seçilen `Email` ve `Phone` özellikler eklenir **Model tarayıcı**.</span><span class="sxs-lookup"><span data-stu-id="f2f0a-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="f2f0a-111">Karmaşık tür bir varsayılan ad verilir: türüne Yeniden Adlandır `EmailPhone` içinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="f2f0a-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="f2f0a-112">Ayrıca, yeni `ComplexProperty` özelliği eklenir `Contact` varlık türü.</span><span class="sxs-lookup"><span data-stu-id="f2f0a-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="f2f0a-113">Özelliği yeniden adlandır `EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="f2f0a-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="f2f0a-114">Oluşturma ve varlık veri modeli Sihirbazı'nı kullanarak karmaşık türler değiştirme hakkında daha fazla bilgi için bkz [nasıl yapılır: karmaşık bir tür özelliği mevcut özelliklerine yeniden düzenleyin](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) ve [nasıl yapılır: oluşturma ve karmaşık türlerdeğiştirme](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span><span class="sxs-lookup"><span data-stu-id="f2f0a-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) and [How to: Create and Modify Complex Types](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2f0a-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2f0a-115">Example</span></span>  
 <span data-ttu-id="f2f0a-116">Aşağıdaki örnek bir koleksiyonunu döndüren bir sorgu yürütür `Contact` nesneleri ve iki özelliklerini görüntüler `Contact` nesneleri: `ContactID` ve değerlerini `EmailPhoneComplexType` karmaşık tür.</span><span class="sxs-lookup"><span data-stu-id="f2f0a-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]

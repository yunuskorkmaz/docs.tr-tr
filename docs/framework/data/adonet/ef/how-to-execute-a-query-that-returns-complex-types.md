---
title: 'Nasıl yapılır: karmaşık türleri döndüren bir sorgu yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b999033046eb251400f033314ae7eb197a8f110a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760537"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="dc21a-102">Nasıl yapılır: karmaşık türleri döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="dc21a-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="dc21a-103">Bu konuda nasıl yürütüleceği gösterilmektedir bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] bir karmaşık türde bir özellik, içeren türde nesne varlık döndüren sorgu.</span><span class="sxs-lookup"><span data-stu-id="dc21a-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="dc21a-104">Bu örnekte kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="dc21a-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="dc21a-105">Ekleme [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) projenize ve kullanmak için projenizin yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc21a-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="dc21a-106">Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="dc21a-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="dc21a-107">Uygulamanız için kod sayfasında aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="dc21a-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="dc21a-108">Modelinde görüntülemek üzere .edmx dosyasına çift tıklayın [modeli tarayıcı penceresini](http://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="dc21a-108">Double click the .edmx file to display the model in the [Model Browser window](http://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) of the Entity Designer.</span></span> <span data-ttu-id="dc21a-109">Entity Designer yüzeyine seçin `Email` ve `Phone` özelliklerini `Contact` varlık türü, sonra sağ tıklatın ve seçin **yeni karmaşık tür yeniden düzenlemeniz**.</span><span class="sxs-lookup"><span data-stu-id="dc21a-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="dc21a-110">Seçili olan yeni bir karmaşık tür `Email` ve `Phone` özellikler eklenir **modeli tarayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="dc21a-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="dc21a-111">Karmaşık türü bir varsayılan adı verilir: türünü yeniden adlandırmak `EmailPhone` içinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="dc21a-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="dc21a-112">Ayrıca, yeni `ComplexProperty` özellik eklenir `Contact` varlık türü.</span><span class="sxs-lookup"><span data-stu-id="dc21a-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="dc21a-113">Özelliği yeniden adlandırma `EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="dc21a-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="dc21a-114">Oluşturma ve karmaşık türler, varlık veri modeli Sihirbazı'nı kullanarak değiştirme hakkında daha fazla bilgi için bkz [nasıl yapılır: bir karmaşık tür özelliği mevcut özelliklerine yeniden düzenlemeniz](http://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) ve [nasıl yapılır: oluşturmak ve karmaşık türler değiştirme](http://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span><span class="sxs-lookup"><span data-stu-id="dc21a-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](http://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) and [How to: Create and Modify Complex Types](http://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc21a-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc21a-115">Example</span></span>  
 <span data-ttu-id="dc21a-116">Aşağıdaki örnek koleksiyonu döndüren bir sorgu yürütür `Contact` nesneleri ve iki özelliklerini görüntüler `Contact` nesneleri: `ContactID` ve değerlerini `EmailPhoneComplexType` karmaşık tür.</span><span class="sxs-lookup"><span data-stu-id="dc21a-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]

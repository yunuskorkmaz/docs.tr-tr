---
title: 'Nasıl yapılır: EntityCommand kullanarak parametreli bir saklı yordamı yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 68589cf8906e35313e261e373cf87017ffe6f8f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="31efd-102">Nasıl yapılır: EntityCommand kullanarak parametreli bir saklı yordamı yürütme</span><span class="sxs-lookup"><span data-stu-id="31efd-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>
<span data-ttu-id="31efd-103">Bu konuda kullanarak parametreli bir saklı yordamı yürütme gösterilmektedir <xref:System.Data.EntityClient.EntityCommand> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="31efd-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="31efd-104">Bu örnekte kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="31efd-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="31efd-105">Ekleme [Okul modeli](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) projenize ve kullanmak için projenizin yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31efd-105">Add the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="31efd-106">Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="31efd-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="31efd-107">Uygulamanız için kod sayfasında aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="31efd-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="31efd-108">İçeri aktarma `GetStudentGrades` saklı yordamı ve belirtin `CourseGrade` varlıkları bir dönüş türü olarak.</span><span class="sxs-lookup"><span data-stu-id="31efd-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="31efd-109">Saklı yordam alma konusunda daha fazla bilgi için bkz: [nasıl yapılır: bir saklı yordam alma](http://msdn.microsoft.com/library/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).</span><span class="sxs-lookup"><span data-stu-id="31efd-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](http://msdn.microsoft.com/library/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="31efd-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="31efd-110">Example</span></span>  
 <span data-ttu-id="31efd-111">Aşağıdaki kodu yürütür `GetStudentGrades` saklı yordamı nerede `StudentId` gerekli bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="31efd-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="31efd-112">Sonuçları sonra tarafından okunan bir <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="31efd-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="31efd-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31efd-113">See Also</span></span>  
 [<span data-ttu-id="31efd-114">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="31efd-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)

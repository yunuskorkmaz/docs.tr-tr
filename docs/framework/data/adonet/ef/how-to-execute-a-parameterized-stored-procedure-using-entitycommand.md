---
title: 'Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: deb1877397053ceab8c284a537a861ba56ffb729
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326664"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="44841-102">Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme</span><span class="sxs-lookup"><span data-stu-id="44841-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>
<span data-ttu-id="44841-103">Bu konuda, kullanarak bir parametreli saklı yordamı yürütmek gösterilmektedir <xref:System.Data.EntityClient.EntityCommand> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="44841-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="44841-104">Bu örnekte, kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="44841-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="44841-105">Ekleme [Okul modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44841-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="44841-106">Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="44841-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="44841-107">Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="44841-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="44841-108">İçeri aktarma `GetStudentGrades` belirtin ve saklı yordamı `CourseGrade` varlıklar bir dönüş türü olarak.</span><span class="sxs-lookup"><span data-stu-id="44841-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="44841-109">Bir saklı yordam içeri aktarma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir saklı yordam alma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="44841-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44841-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="44841-110">Example</span></span>  
 <span data-ttu-id="44841-111">Aşağıdaki kodu çalıştırır `GetStudentGrades` saklı yordamı burada `StudentId` gerekli bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="44841-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="44841-112">Sonuçları tarafından okunana bir <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="44841-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="44841-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44841-113">See also</span></span>

- [<span data-ttu-id="44841-114">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="44841-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)

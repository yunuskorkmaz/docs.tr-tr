---
title: 'Nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
ms.openlocfilehash: a35a0bf54d7850e4b10e59c259e4ee512bc93aad
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197614"
---
# <a name="how-to-build-an-entityconnection-connection-string"></a><span data-ttu-id="ee896-102">Nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ee896-102">How to: Build an EntityConnection Connection String</span></span>
<span data-ttu-id="ee896-103">Bu konu nasıl oluşturulacağını gösteren bir örnek sağlar bir <xref:System.Data.EntityClient.EntityConnection>.</span><span class="sxs-lookup"><span data-stu-id="ee896-103">This topic provides an example of how to build an <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="ee896-104">Bu örnekte, kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ee896-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="ee896-105">Ekleme [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee896-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="ee896-106">Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="ee896-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="ee896-107">Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="ee896-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="ee896-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee896-108">Example</span></span>  
 <span data-ttu-id="ee896-109">Aşağıdaki örnek başlatır <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> için alttaki sağlayıcı, ardından başlatır <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> nesne ve bu nesnesi oluşturucusuna iletir <xref:System.Data.EntityClient.EntityConnection>.</span><span class="sxs-lookup"><span data-stu-id="ee896-109">The following example initializes the <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> for the underlying provider, then initializes the <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> object and passes this object to the constructor of the <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="ee896-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee896-110">See Also</span></span>  
 [<span data-ttu-id="ee896-111">Nasıl yapılır: bir nesne bağlamına ile EntityConnection kullanın</span><span class="sxs-lookup"><span data-stu-id="ee896-111">How to: Use EntityConnection with an Object Context</span></span>](https://msdn.microsoft.com/library/2140fe7b-b88b-47c8-a749-d7f142eb1080)  
 [<span data-ttu-id="ee896-112">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="ee896-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)

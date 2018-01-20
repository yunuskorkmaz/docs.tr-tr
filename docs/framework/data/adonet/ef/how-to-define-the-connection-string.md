---
title: "Nasıl yapılır: bağlantı dizesi tanımlayın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 355d313fd607ccf85ba55b09b9ece4d9c88e298f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="a8cd6-102">Nasıl yapılır: bağlantı dizesi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="a8cd6-102">How to: Define the Connection String</span></span>
<span data-ttu-id="a8cd6-103">Bu konu, kavramsal bir model bağlanırken kullanılan bağlantı dizesi tanımlayın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a8cd6-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="a8cd6-104">Bu konuda dayanır [AdventureWorks satış](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) kavramsal model.</span><span class="sxs-lookup"><span data-stu-id="a8cd6-104">This topic is based on the [AdventureWorks Sales](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) conceptual model.</span></span> <span data-ttu-id="a8cd6-105">AdventureWorks satış modeli görevle ilgili konulara genelinde kullanılan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belgeleri.</span><span class="sxs-lookup"><span data-stu-id="a8cd6-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="a8cd6-106">Bu konu, zaten yapılandırmış olduğunuz varsayılır, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve AdventureWorks satış modeli tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="a8cd6-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a8cd6-107">Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model el ile tanımlamak](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span><span class="sxs-lookup"><span data-stu-id="a8cd6-107">For more information, see [How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span></span> <span data-ttu-id="a8cd6-108">Bu konudaki yordamlar da yer alan [nasıl yapılır: bir Entity Framework projesi el ile yapılandırmanız](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span><span class="sxs-lookup"><span data-stu-id="a8cd6-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8cd6-109">Kullanırsanız [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Sihirbazı'nda bir [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] proje, otomatik olarak bir .edmx dosyasının oluşturur ve kullanmak için proje yapılandırır [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8cd6-109">If you use the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Wizard in a [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="a8cd6-110">Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı kullanın](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)</span><span class="sxs-lookup"><span data-stu-id="a8cd6-110">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)</span></span>  
  
### <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="a8cd6-111">Entity Framework bağlantı dizesi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="a8cd6-111">To define the Entity Framework connection string</span></span>  
  
-   <span data-ttu-id="a8cd6-112">Projenin uygulama yapılandırma dosyasına (app.config) açın ve bağlantı dizesi olarak şunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a8cd6-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>  
  
  
  
     <span data-ttu-id="a8cd6-113">Projenizi bir uygulama yapılandırma dosyası yoksa belirleyerek bir tane ekleyebilirsiniz **Yeni Öğe Ekle** gelen **proje** menüsünde seçerek **genel** kategorisi seçme **uygulama yapılandırma dosyası**ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a8cd6-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8cd6-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8cd6-114">See Also</span></span>  
 [<span data-ttu-id="a8cd6-115">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="a8cd6-115">Quickstart</span></span>](http://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675)  
 [<span data-ttu-id="a8cd6-116">Nasıl yapılır: yeni bir .edmx dosyasının oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8cd6-116">How to: Create a New .edmx File</span></span>](http://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)  
 [<span data-ttu-id="a8cd6-117">ADO.NET varlık veri modeli araçları</span><span class="sxs-lookup"><span data-stu-id="a8cd6-117">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)

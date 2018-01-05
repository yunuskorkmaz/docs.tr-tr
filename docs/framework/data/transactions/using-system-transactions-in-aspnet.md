---
title: System.Transactions ASP.NET kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caa0f8cc5b98ae50e1c9d2da716dd03eb5cb4565
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="385da-102">System.Transactions ASP.NET kullanma</span><span class="sxs-lookup"><span data-stu-id="385da-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="385da-103">Bu konu, başarılı bir şekilde nasıl kullanabileceğinizi açıklar <xref:System.Transactions> içinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="385da-103">This topic describes how you can successfully use <xref:System.Transactions> inside an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="385da-104">ASP.NET DistributedTransactionPermission etkinleştir</span><span class="sxs-lookup"><span data-stu-id="385da-104">Enable DistributedTransactionPermission in ASP.NET</span></span>  
 <span data-ttu-id="385da-105"><xref:System.Transactions>kısmen güvenilen arayanlara destekler ve ile işaretli **AllowPartiallyTrustedCallers** özniteliği (APTCA).</span><span class="sxs-lookup"><span data-stu-id="385da-105"><xref:System.Transactions> supports partially trusted callers and is marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="385da-106">Güven düzeyleri için <xref:System.Transactions> (örnek, sistem belleği, paylaşılan işlem genelinde kaynakları, sistem genelinde kaynakları ve diğer kaynaklara ilişkin), kaynak türleri göre tanımlanır, <xref:System.Transactions> çıkarır ve gerekip gerekmeyeceğini güven düzeyi Bu kaynaklara erişmek için.</span><span class="sxs-lookup"><span data-stu-id="385da-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources, (for example, system memory, shared process-wide resources, system-wide resources, and other resources), that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="385da-107">Kısmi güven ortamında, bir tam olmayan güven derleme yalnızca işlemleri uygulama etki alanı içinde kullanabilirsiniz (Bu durumda, sistem belleği korunan yalnızca kaynak değil), onu verilmemişse <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="385da-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>  
  
 <span data-ttu-id="385da-108"><xref:System.Transactions.DistributedTransactionPermission>işlem yönetimi Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından yönetilecek ilerletilen her talep.</span><span class="sxs-lookup"><span data-stu-id="385da-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="385da-109">Bu tür bir senaryo işlemi genelinde kaynakları ve MSDTC günlüğünde ayrılmış alandır özellikle bir genel kaynağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="385da-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="385da-110">Bir Web ön uç bir veritabanı veya veritabanı sağladığı hizmetler bir parçası olarak kullanan bir uygulama için bu kullanım örneğidir.</span><span class="sxs-lookup"><span data-stu-id="385da-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="385da-111">güven düzeyleri kendi kümesi vardır ve belirli bir izin kümesi ile bu güven düzeyi ilke dosyalar ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="385da-111"> has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="385da-112">[ASP.NET güven düzeyleri ve ilke dosyaları](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span><span class="sxs-lookup"><span data-stu-id="385da-112"> [ASP.NET Trust Levels and Policy Files](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span></span> <span data-ttu-id="385da-113">İlk yüklediğinizde, Windows SDK, varsayılan hiçbiri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ile ilişkili ilke dosyaları <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="385da-113">When you initially install the Windows SDK, none of the default [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="385da-114">Bu nedenle, işlem içinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] MSDTC tarafından yönetilmek üzere uygulama ilerletilen, yükseltme başarısız olur bir <xref:System.Security.SecurityException> yoğun üzerine <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="385da-114">As such, when your transaction in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="385da-115">İşlem yükseltme etkinleştirmek için bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kısmi güven ortamında vermek <xref:System.Transactions.DistributedTransactionPermission> içeriğiyle olarak aynı varsayılan güven düzeylerinde <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="385da-115">To enable transaction escalation in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="385da-116">Bunu desteklemek için kendi özel güven düzeyi ve ilke dosyası ya da yapılandırabilirsiniz ya da olan varsayılan ilke dosyaları değiştirebileceğiniz **Web_hightrust.config** ve **Web_mediumtrust.config**.</span><span class="sxs-lookup"><span data-stu-id="385da-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>  
  
 <span data-ttu-id="385da-117">İlke dosyaları değiştirmek için add bir **SecurityClass** öğesi için **DistributedTransactionPermission** için **SecurityClasses** öğesinin altında  **PolicyLevel** öğesi ve karşılık gelen ekleyin **IPermission** öğesinin altında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** System.Transactions için.</span><span class="sxs-lookup"><span data-stu-id="385da-117">To modify the policy files, add a **SecurityClass** element for **DistributedTransactionPermission** to the **SecurityClasses** element under the **PolicyLevel** element and add a corresponding **IPermission** element under the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** for System.Transactions.</span></span> <span data-ttu-id="385da-118">Aşağıdaki yapılandırma dosyası bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="385da-118">The following configuration file demonstrates this.</span></span>  
  
```xml  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="385da-119">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] güvenlik ilkesine bakın [securityPolicy öğesi (ASP.NET Ayarlar Şeması)](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba).</span><span class="sxs-lookup"><span data-stu-id="385da-119"> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] security policy, see [securityPolicy Element (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba).</span></span>  
  
## <a name="dynamic-compilation"></a><span data-ttu-id="385da-120">Dinamik derleme</span><span class="sxs-lookup"><span data-stu-id="385da-120">Dynamic Compilation</span></span>  
 <span data-ttu-id="385da-121">İçeri aktarma ve kullanmak istiyorsanız, <xref:System.Transactions> içinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] erişimi dinamik olarak derlenmiş olan uygulamayı bir başvuru yerleştirin <xref:System.Transactions> derleme yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="385da-121">If you want to import and use <xref:System.Transactions> in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="385da-122">Özellikle, başvuru altında eklenmesi gereken **derleme**/**derlemeleri** varsayılan kök bölümünü **Web.config** yapılandırma dosyası veya bir Belirli Web uygulamasının yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="385da-122">Specifically, the reference should be added under the **compilation**/**assemblies** section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="385da-123">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="385da-123">The following example demonstrates this.</span></span>  
  
```xml  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="385da-124">[öğesi (ASP.NET Ayarlar Şeması) için derlemeleri add](http://msdn.microsoft.com/en-us/602197e8-108d-4249-b752-ba2a318f75e4).</span><span class="sxs-lookup"><span data-stu-id="385da-124"> [add Element for assemblies for compilation (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/602197e8-108d-4249-b752-ba2a318f75e4).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385da-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="385da-125">See Also</span></span>  
 [<span data-ttu-id="385da-126">ASP.NET güven düzeyleri ve ilke dosyaları</span><span class="sxs-lookup"><span data-stu-id="385da-126">ASP.NET Trust Levels and Policy Files</span></span>](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [<span data-ttu-id="385da-127">securityPolicy öğesi (ASP.NET Ayarlar Şeması)</span><span class="sxs-lookup"><span data-stu-id="385da-127">securityPolicy Element (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba)  
 [<span data-ttu-id="385da-128">İşlem Yönetimi Yükseltme</span><span class="sxs-lookup"><span data-stu-id="385da-128">Transaction Management Escalation</span></span>](../../../../docs/framework/data/transactions/transaction-management-escalation.md)

---
title: ASP.NET’te System.Transactions kullanma
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: df9a9f1878b2268d1d6bc3d9b05d0ad8d7bcc3f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134602"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="fddeb-102">ASP.NET’te System.Transactions kullanma</span><span class="sxs-lookup"><span data-stu-id="fddeb-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="fddeb-103">Bu konu, başarılı bir şekilde nasıl kullanabileceğinizi açıklar <xref:System.Transactions> içinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="fddeb-103">This topic describes how you can successfully use <xref:System.Transactions> inside an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="fddeb-104">ASP.NET DistributedTransactionPermission etkinleştir</span><span class="sxs-lookup"><span data-stu-id="fddeb-104">Enable DistributedTransactionPermission in ASP.NET</span></span>  
 <span data-ttu-id="fddeb-105"><xref:System.Transactions> kısmen güvenilen arayanlar destekler ve ile işaretlenen **AllowPartiallyTrustedCallers** özniteliği (APTCA).</span><span class="sxs-lookup"><span data-stu-id="fddeb-105"><xref:System.Transactions> supports partially trusted callers and is marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="fddeb-106">Güven düzeyleri için <xref:System.Transactions> (için örnek, sistem belleği, paylaşılan işlem genelinde kaynakları, sistem genelinde kaynakları ve diğer kaynakları), bir kaynak türleri göre tanımlanan, <xref:System.Transactions> kullanıma sunan ve gerekli güven düzeyi Bu kaynakları erişmek için.</span><span class="sxs-lookup"><span data-stu-id="fddeb-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources, (for example, system memory, shared process-wide resources, system-wide resources, and other resources), that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="fddeb-107">Kısmi güven ortamında, bir tam olmayan güven derleme yalnızca işlemler uygulama etki alanı içinde kullanabilirsiniz (Bu durumda, sistem belleği korumalı yalnızca kaynak olan), verilen sürece <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="fddeb-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>  
  
 <span data-ttu-id="fddeb-108"><xref:System.Transactions.DistributedTransactionPermission> Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından yönetilmek üzere işlem yönetim ilerletilmiş her talep.</span><span class="sxs-lookup"><span data-stu-id="fddeb-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="fddeb-109">Bu tür bir senaryo işlemi genelinde kaynakları ve MSDTC günlüğünde ayrılmış alandır özellikle bir genel kaynağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="fddeb-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="fddeb-110">Bir Web ön uç bir veritabanı veya veritabanı sağladığı hizmetler bir parçası olarak kullanan bir uygulama için bu kullanım örneğidir.</span><span class="sxs-lookup"><span data-stu-id="fddeb-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] <span data-ttu-id="fddeb-111">kendi güven düzeyleri kümesi vardır ve belirli bir izin kümesi ilke dosyaları aracılığıyla bu güven düzeyleri ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="fddeb-111">has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="fddeb-112">Daha fazla bilgi için [ASP.NET güven düzeylerini ve ilke dosyaları](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fddeb-112">For more information, see [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="fddeb-113">İlk yüklediğinizde, Windows SDK, varsayılan hiçbiri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ile ilişkili ilke dosyaları <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="fddeb-113">When you initially install the Windows SDK, none of the default [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="fddeb-114">Bu nedenle, zaman, işlemde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama ilerletilmiş MSDTC tarafından yönetilmek üzere, yükseltme başarısız olur bir <xref:System.Security.SecurityException> yoğun üzerine <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="fddeb-114">As such, when your transaction in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="fddeb-115">İşlem yükseltme içinde etkinleştirmek için bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kısmi güven ortam vermek <xref:System.Transactions.DistributedTransactionPermission> aynı varsayılan güven düzeyleri içinde <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="fddeb-115">To enable transaction escalation in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="fddeb-116">Bunu desteklemek için kendi özel güven düzeyini ve ilke dosya ya da yapılandırabilirsiniz veya varsayılan ilkesi dosyaları değiştirebilirsiniz **Web_hightrust.config** ve **Web_mediumtrust.config**.</span><span class="sxs-lookup"><span data-stu-id="fddeb-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>  
  
 <span data-ttu-id="fddeb-117">İlke dosyaları değiştirmek için ekleme bir **SecurityClass** öğesi için **DistributedTransactionPermission** için **SecurityClasses** öğesi altında  **PolicyLevel** öğesi ve karşılık gelen ekleme **IPermission** öğesi altında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** System.Transactions için.</span><span class="sxs-lookup"><span data-stu-id="fddeb-117">To modify the policy files, add a **SecurityClass** element for **DistributedTransactionPermission** to the **SecurityClasses** element under the **PolicyLevel** element and add a corresponding **IPermission** element under the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** for System.Transactions.</span></span> <span data-ttu-id="fddeb-118">Aşağıdaki yapılandırma dosyası bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fddeb-118">The following configuration file demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="fddeb-119">Hakkında daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] güvenlik ilkesi bakın [securityPolicy öğesi (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fddeb-119">For more information about [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] security policy, see [securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>  
  
## <a name="dynamic-compilation"></a><span data-ttu-id="fddeb-120">Dinamik derleme</span><span class="sxs-lookup"><span data-stu-id="fddeb-120">Dynamic Compilation</span></span>  
 <span data-ttu-id="fddeb-121">İçeri aktarma ve kullanmak istiyorsanız, <xref:System.Transactions> içinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] erişimi dinamik olarak derlenmiş olan uygulamayı bir başvuru yerleştirin <xref:System.Transactions> derleme yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="fddeb-121">If you want to import and use <xref:System.Transactions> in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="fddeb-122">Özellikle, başvuru altında eklenmesi gerekip **derleme**/**derlemeleri** varsayılan kök bölümünü **Web.config** yapılandırma dosyası veya Belirli Web uygulamanın yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="fddeb-122">Specifically, the reference should be added under the **compilation**/**assemblies** section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="fddeb-123">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fddeb-123">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="fddeb-124">Daha fazla bilgi için [derlemeler için derleme (ASP.NET Settings Schema) öğesi ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fddeb-124">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fddeb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fddeb-125">See also</span></span>

- <span data-ttu-id="fddeb-126">[ASP.NET güven düzeylerini ve ilke dosyaları](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fddeb-126">[ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="fddeb-127">[securityPolicy öğesi (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fddeb-127">[securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="fddeb-128">İşlem Yönetimi Yükseltme</span><span class="sxs-lookup"><span data-stu-id="fddeb-128">Transaction Management Escalation</span></span>](../../../../docs/framework/data/transactions/transaction-management-escalation.md)

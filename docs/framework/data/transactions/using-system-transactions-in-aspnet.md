---
title: ASP.NET’te System.Transactions kullanma
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 866d7b69fa6c18f6edfb48655b213e140a095a28
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880228"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="bcc63-102">ASP.NET’te System.Transactions kullanma</span><span class="sxs-lookup"><span data-stu-id="bcc63-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="bcc63-103">Bu konuda, başarılı bir şekilde nasıl kullanabileceğinizi açıklar <xref:System.Transactions> içinde bir ASP.NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="bcc63-103">This topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="bcc63-104">ASP.NET DistributedTransactionPermission etkinleştir</span><span class="sxs-lookup"><span data-stu-id="bcc63-104">Enable DistributedTransactionPermission in ASP.NET</span></span>  
 <span data-ttu-id="bcc63-105"><xref:System.Transactions> kısmen güvenilen arayanlar destekler ve ile işaretlenen **AllowPartiallyTrustedCallers** özniteliği (APTCA).</span><span class="sxs-lookup"><span data-stu-id="bcc63-105"><xref:System.Transactions> supports partially trusted callers and is marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="bcc63-106">Güven düzeyleri için <xref:System.Transactions> (için örnek, sistem belleği, paylaşılan işlem genelinde kaynakları, sistem genelinde kaynakları ve diğer kaynakları), bir kaynak türleri göre tanımlanan, <xref:System.Transactions> kullanıma sunan ve gerekli güven düzeyi Bu kaynakları erişmek için.</span><span class="sxs-lookup"><span data-stu-id="bcc63-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources, (for example, system memory, shared process-wide resources, system-wide resources, and other resources), that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="bcc63-107">Kısmi güven ortamında, bir tam olmayan güven derleme yalnızca işlemler uygulama etki alanı içinde kullanabilirsiniz (Bu durumda, sistem belleği korumalı yalnızca kaynak olan), verilen sürece <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="bcc63-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>  
  
 <span data-ttu-id="bcc63-108"><xref:System.Transactions.DistributedTransactionPermission> Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından yönetilmek üzere işlem yönetim ilerletilmiş her talep.</span><span class="sxs-lookup"><span data-stu-id="bcc63-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="bcc63-109">Bu tür bir senaryo işlemi genelinde kaynakları ve MSDTC günlüğünde ayrılmış alandır özellikle bir genel kaynağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="bcc63-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="bcc63-110">Bir Web ön uç bir veritabanı veya veritabanı sağladığı hizmetler bir parçası olarak kullanan bir uygulama için bu kullanım örneğidir.</span><span class="sxs-lookup"><span data-stu-id="bcc63-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>  
  
 <span data-ttu-id="bcc63-111">ASP.NET, kendi güven düzeyleri kümesi vardır ve belirli bir izin kümesi ilke dosyaları aracılığıyla bu güven düzeyleri ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="bcc63-111">ASP.NET has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="bcc63-112">Daha fazla bilgi için [ASP.NET güven düzeylerini ve ilke dosyaları](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bcc63-112">For more information, see [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="bcc63-113">Windows SDK'yı ilk kez yüklediğinizde, varsayılan ASP.NET İlkesi dosyaların hiçbiri ile ilişkili <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="bcc63-113">When you initially install the Windows SDK, none of the default ASP.NET policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="bcc63-114">Bir ASP.NET uygulamasında işlem ilerletilmiş MSDTC tarafından yönetilmek üzere, bu nedenle, yükseltme başarısız olur bir <xref:System.Security.SecurityException> yoğun üzerine <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="bcc63-114">As such, when your transaction in an ASP.NET application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="bcc63-115">İşlem yükseltme ASP.NET kısmi güven ortamında etkinleştirmek için vermelisiniz <xref:System.Transactions.DistributedTransactionPermission> aynı varsayılan güven düzeyleri içinde <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="bcc63-115">To enable transaction escalation in an ASP.NET partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="bcc63-116">Bunu desteklemek için kendi özel güven düzeyini ve ilke dosya ya da yapılandırabilirsiniz veya varsayılan ilkesi dosyaları değiştirebilirsiniz **Web_hightrust.config** ve **Web_mediumtrust.config**.</span><span class="sxs-lookup"><span data-stu-id="bcc63-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>  
  
 <span data-ttu-id="bcc63-117">İlke dosyaları değiştirmek için ekleme bir **SecurityClass** öğesi için **DistributedTransactionPermission** için **SecurityClasses** öğesi altında  **PolicyLevel** öğesi ve karşılık gelen ekleme **IPermission** öğesi altında ASP.NET **NamedPermissionSet** System.Transactions için.</span><span class="sxs-lookup"><span data-stu-id="bcc63-117">To modify the policy files, add a **SecurityClass** element for **DistributedTransactionPermission** to the **SecurityClasses** element under the **PolicyLevel** element and add a corresponding **IPermission** element under the ASP.NET **NamedPermissionSet** for System.Transactions.</span></span> <span data-ttu-id="bcc63-118">Aşağıdaki yapılandırma dosyası bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bcc63-118">The following configuration file demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="bcc63-119">ASP.NET güvenlik ilkesi hakkında daha fazla bilgi için bkz. [securityPolicy öğesi (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bcc63-119">For more information about ASP.NET security policy, see [securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>  
  
## <a name="dynamic-compilation"></a><span data-ttu-id="bcc63-120">Dinamik derleme</span><span class="sxs-lookup"><span data-stu-id="bcc63-120">Dynamic Compilation</span></span>  
 <span data-ttu-id="bcc63-121">İçeri aktarma ve kullanmak istiyorsanız <xref:System.Transactions> erişimi dinamik olarak derlenmiş bir ASP.NET uygulamasında, bir başvuru koymalısınız <xref:System.Transactions> derleme yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="bcc63-121">If you want to import and use <xref:System.Transactions> in an ASP.NET application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="bcc63-122">Özellikle, başvuru altında eklenmesi gerekip **derleme**/**derlemeleri** varsayılan kök bölümünü **Web.config** yapılandırma dosyası veya Belirli Web uygulamanın yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="bcc63-122">Specifically, the reference should be added under the **compilation**/**assemblies** section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="bcc63-123">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bcc63-123">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="bcc63-124">Daha fazla bilgi için [derlemeler için derleme (ASP.NET Settings Schema) öğesi ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bcc63-124">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc63-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcc63-125">See also</span></span>

- <span data-ttu-id="bcc63-126">[ASP.NET güven düzeylerini ve ilke dosyaları](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bcc63-126">[ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="bcc63-127">[securityPolicy öğesi (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bcc63-127">[securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="bcc63-128">İşlem Yönetimi Yükseltme</span><span class="sxs-lookup"><span data-stu-id="bcc63-128">Transaction Management Escalation</span></span>](../../../../docs/framework/data/transactions/transaction-management-escalation.md)

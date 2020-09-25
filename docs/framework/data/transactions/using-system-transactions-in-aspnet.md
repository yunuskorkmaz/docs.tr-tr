---
title: ASP.NET’te System.Transactions kullanma
description: Bir ASP.NET uygulamasının içindeki System. Transactions kullanın. Dağıtılmış işlem izinlerini etkinleştirin ve dinamik derleme ile çalışın.
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: b6663e9258e98e94d7b739ee75c826ced1e2f897
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186724"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="f424d-104">ASP.NET’te System.Transactions kullanma</span><span class="sxs-lookup"><span data-stu-id="f424d-104">Using System.Transactions in ASP.NET</span></span>

<span data-ttu-id="f424d-105">Bu konu, <xref:System.Transactions> bir ASP.NET uygulamasının içinde başarıyla nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="f424d-105">This topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>

## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="f424d-106">ASP.NET 'de DistributedTransactionPermission 'ı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="f424d-106">Enable DistributedTransactionPermission in ASP.NET</span></span>

 <span data-ttu-id="f424d-107"><xref:System.Transactions> kısmen güvenilen çağıranları destekler ve `AllowPartiallyTrustedCallers` özniteliğiyle işaretlenir (APTCA).</span><span class="sxs-lookup"><span data-stu-id="f424d-107"><xref:System.Transactions> supports partially trusted callers and is marked with the `AllowPartiallyTrustedCallers` attribute (APTCA).</span></span> <span data-ttu-id="f424d-108">Güven düzeyleri, <xref:System.Transactions> kaynak türleri (örneğin, sistem belleği, paylaşılan işlem genelinde kaynaklar, sistem genelinde kaynaklar ve diğer kaynaklar) temel alınarak tanımlanır <xref:System.Transactions> ve bu kaynaklara erişmek için gerekli olması gereken güven düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f424d-108">The trust levels for <xref:System.Transactions> are defined based on the types of resources (for example, system memory, shared process-wide resources, system-wide resources, and other resources) that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="f424d-109">Kısmi güven ortamında, tam olmayan bir güven derlemesi yalnızca uygulama etki alanı içindeki işlemleri kullanabilir (Bu durumda, korunan tek kaynak sistem belleğidir), verilmediği müddetçe <xref:System.Transactions.DistributedTransactionPermission> .</span><span class="sxs-lookup"><span data-stu-id="f424d-109">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>

 <span data-ttu-id="f424d-110"><xref:System.Transactions.DistributedTransactionPermission> işlem yönetiminin Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından yönetilmek üzere ilerletilidiğinde, talep edilir.</span><span class="sxs-lookup"><span data-stu-id="f424d-110"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="f424d-111">Bu tür bir senaryo işlemi genelinde kaynakları ve MSDTC günlüğünde ayrılmış alandır özellikle bir genel kaynağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f424d-111">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="f424d-112">Bir Web ön uç bir veritabanı veya veritabanı sağladığı hizmetler bir parçası olarak kullanan bir uygulama için bu kullanım örneğidir.</span><span class="sxs-lookup"><span data-stu-id="f424d-112">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>

 <span data-ttu-id="f424d-113">ASP.NET kendi güven düzeylerine sahiptir ve ilke dosyaları aracılığıyla bu güven düzeyleriyle belirli bir izin kümesini ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="f424d-113">ASP.NET has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="f424d-114">Daha fazla bilgi için bkz. [ASP.net Trust Levels and Policy Files](/previous-versions/aspnet/wyts434y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f424d-114">For more information, see [ASP.NET Trust Levels and Policy Files](/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="f424d-115">Windows SDK ilk yüklediğinizde, varsayılan ASP.NET ilkesi dosyalarından hiçbiri ile ilişkili değildir <xref:System.Transactions.DistributedTransactionPermission> .</span><span class="sxs-lookup"><span data-stu-id="f424d-115">When you initially install the Windows SDK, none of the default ASP.NET policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="f424d-116">Bu nedenle, bir ASP.NET uygulamasındaki işlem MSDTC tarafından yönetilmek üzere ilerlediğinde, yükseltme işlemi yoğun bir şekilde başarısız olur <xref:System.Security.SecurityException> <xref:System.Transactions.DistributedTransactionPermission> .</span><span class="sxs-lookup"><span data-stu-id="f424d-116">As such, when your transaction in an ASP.NET application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="f424d-117">ASP.NET kısmi güven ortamında işlem yükseltmeyi etkinleştirmek için, <xref:System.Transactions.DistributedTransactionPermission> ile aynı varsayılan güven düzeylerine sahip olmanız gerekir <xref:System.Data.SqlClient.SqlClientPermission> .</span><span class="sxs-lookup"><span data-stu-id="f424d-117">To enable transaction escalation in an ASP.NET partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="f424d-118">Bunu desteklemek için kendi özel güven düzeyinizi ve ilke dosyanızı yapılandırabilir ya da **Web_hightrust.config** ve **Web_mediumtrust.config**varsayılan ilke dosyalarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f424d-118">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>

 <span data-ttu-id="f424d-119">İlke dosyalarını değiştirmek için, öğesinin `SecurityClass` altındaki öğesine bir öğesi ekleyin `DistributedTransactionPermission` `SecurityClasses` `PolicyLevel` ve `IPermission` `NamedPermissionSet` System. Transactions için ASP.net altına karşılık gelen bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f424d-119">To modify the policy files, add a `SecurityClass` element for `DistributedTransactionPermission` to the `SecurityClasses` element under the `PolicyLevel` element and add a corresponding `IPermission` element under the ASP.NET `NamedPermissionSet` for System.Transactions.</span></span> <span data-ttu-id="f424d-120">Aşağıdaki yapılandırma dosyası bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f424d-120">The following configuration file demonstrates this.</span></span>

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

 <span data-ttu-id="f424d-121">ASP.NET güvenlik ilkesi hakkında daha fazla bilgi için bkz. [SecurityPolicy öğesi (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f424d-121">For more information about ASP.NET security policy, see [securityPolicy Element (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>

## <a name="dynamic-compilation"></a><span data-ttu-id="f424d-122">Dinamik derleme</span><span class="sxs-lookup"><span data-stu-id="f424d-122">Dynamic Compilation</span></span>

 <span data-ttu-id="f424d-123"><xref:System.Transactions>Erişim için dinamik olarak derlenen bir ASP.NET uygulamasında içeri ve kullanmak istiyorsanız, yapılandırma dosyasındaki derlemeye bir başvuru yerleştirmeniz gerekir <xref:System.Transactions> .</span><span class="sxs-lookup"><span data-stu-id="f424d-123">If you want to import and use <xref:System.Transactions> in an ASP.NET application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="f424d-124">Özel olarak, başvuru `compilation/assemblies` varsayılan kök **Web.config** yapılandırma dosyasının bölümünün altına veya belirli bir Web uygulamasının yapılandırma dosyasına eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f424d-124">Specifically, the reference should be added under the `compilation/assemblies` section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="f424d-125">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f424d-125">The following example demonstrates this.</span></span>

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

 <span data-ttu-id="f424d-126">Daha fazla bilgi için bkz. [derleme için derlemeler Için öğe ekleme (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f424d-126">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="f424d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f424d-127">See also</span></span>

- <span data-ttu-id="f424d-128">[ASP.NET güven düzeyleri ve Ilke dosyaları](/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f424d-128">[ASP.NET Trust Levels and Policy Files](/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="f424d-129">[securityPolicy öğesi (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f424d-129">[securityPolicy Element (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="f424d-130">İşlem Yönetimi Yükseltme</span><span class="sxs-lookup"><span data-stu-id="f424d-130">Transaction Management Escalation</span></span>](transaction-management-escalation.md)

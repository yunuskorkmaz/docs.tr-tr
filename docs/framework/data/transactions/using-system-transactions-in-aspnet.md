---
title: ASP.NET'te System.Transactions kullanma
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 7b73ec970776f39a0c056e2a706d4818cda6cd72
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698385"
---
# <a name="using-systemtransactions-in-aspnet"></a>ASP.NET'te System.Transactions kullanma
Bu konu, başarılı bir şekilde nasıl kullanabileceğinizi açıklar <xref:System.Transactions> içinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>ASP.NET DistributedTransactionPermission etkinleştir  
 <xref:System.Transactions> kısmen güvenilen arayanlar destekler ve ile işaretlenen **AllowPartiallyTrustedCallers** özniteliği (APTCA). Güven düzeyleri için <xref:System.Transactions> (için örnek, sistem belleği, paylaşılan işlem genelinde kaynakları, sistem genelinde kaynakları ve diğer kaynakları), bir kaynak türleri göre tanımlanan, <xref:System.Transactions> kullanıma sunan ve gerekli güven düzeyi Bu kaynakları erişmek için. Kısmi güven ortamında, bir tam olmayan güven derleme yalnızca işlemler uygulama etki alanı içinde kullanabilirsiniz (Bu durumda, sistem belleği korumalı yalnızca kaynak olan), verilen sürece <xref:System.Transactions.DistributedTransactionPermission>.  
  
 <xref:System.Transactions.DistributedTransactionPermission> Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından yönetilmek üzere işlem yönetim ilerletilmiş her talep. Bu tür bir senaryo işlemi genelinde kaynakları ve MSDTC günlüğünde ayrılmış alandır özellikle bir genel kaynağı kullanır. Bir Web ön uç bir veritabanı veya veritabanı sağladığı hizmetler bir parçası olarak kullanan bir uygulama için bu kullanım örneğidir.  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kendi güven düzeyleri kümesi vardır ve belirli bir izin kümesi ilke dosyaları aracılığıyla bu güven düzeyleri ile ilişkilendirir. Daha fazla bilgi için [ASP.NET güven düzeylerini ve ilke dosyaları](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1). İlk yüklediğinizde, Windows SDK, varsayılan hiçbiri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ile ilişkili ilke dosyaları <xref:System.Transactions.DistributedTransactionPermission>. Bu nedenle, zaman, işlemde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama ilerletilmiş MSDTC tarafından yönetilmek üzere, yükseltme başarısız olur bir <xref:System.Security.SecurityException> yoğun üzerine <xref:System.Transactions.DistributedTransactionPermission>. İşlem yükseltme içinde etkinleştirmek için bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kısmi güven ortam vermek <xref:System.Transactions.DistributedTransactionPermission> aynı varsayılan güven düzeyleri içinde <xref:System.Data.SqlClient.SqlClientPermission>. Bunu desteklemek için kendi özel güven düzeyini ve ilke dosya ya da yapılandırabilirsiniz veya varsayılan ilkesi dosyaları değiştirebilirsiniz **Web_hightrust.config** ve **Web_mediumtrust.config**.  
  
 İlke dosyaları değiştirmek için ekleme bir **SecurityClass** öğesi için **DistributedTransactionPermission** için **SecurityClasses** öğesi altında  **PolicyLevel** öğesi ve karşılık gelen ekleme **IPermission** öğesi altında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** System.Transactions için. Aşağıdaki yapılandırma dosyası bu gösterir.  
  
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
  
 Hakkında daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] güvenlik ilkesi bakın [securityPolicy öğesi (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba).  
  
## <a name="dynamic-compilation"></a>Dinamik derleme  
 İçeri aktarma ve kullanmak istiyorsanız, <xref:System.Transactions> içinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] erişimi dinamik olarak derlenmiş olan uygulamayı bir başvuru yerleştirin <xref:System.Transactions> derleme yapılandırma dosyası. Özellikle, başvuru altında eklenmesi gerekip **derleme**/**derlemeleri** varsayılan kök bölümünü **Web.config** yapılandırma dosyası veya Belirli Web uygulamanın yapılandırma dosyası. Aşağıdaki örnekte bu gösterir.  
  
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
  
 Daha fazla bilgi için [derlemeler için derleme (ASP.NET Settings Schema) öğesi ekleme](https://msdn.microsoft.com/library/602197e8-108d-4249-b752-ba2a318f75e4).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET güven düzeylerini ve ilke dosyaları](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [securityPolicy öğesi (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba)  
 [İşlem Yönetimi Yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md)

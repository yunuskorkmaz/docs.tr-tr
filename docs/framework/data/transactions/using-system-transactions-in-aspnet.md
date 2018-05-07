---
title: System.Transactions ASP.NET kullanma
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 142f5e18682b02dfb659959a19b79c10fb3110c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-systemtransactions-in-aspnet"></a>System.Transactions ASP.NET kullanma
Bu konu, başarılı bir şekilde nasıl kullanabileceğinizi açıklar <xref:System.Transactions> içinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>ASP.NET DistributedTransactionPermission etkinleştir  
 <xref:System.Transactions> kısmen güvenilen arayanlara destekler ve ile işaretli **AllowPartiallyTrustedCallers** özniteliği (APTCA). Güven düzeyleri için <xref:System.Transactions> (örnek, sistem belleği, paylaşılan işlem genelinde kaynakları, sistem genelinde kaynakları ve diğer kaynaklara ilişkin), kaynak türleri göre tanımlanır, <xref:System.Transactions> çıkarır ve gerekip gerekmeyeceğini güven düzeyi Bu kaynaklara erişmek için. Kısmi güven ortamında, bir tam olmayan güven derleme yalnızca işlemleri uygulama etki alanı içinde kullanabilirsiniz (Bu durumda, sistem belleği korunan yalnızca kaynak değil), onu verilmemişse <xref:System.Transactions.DistributedTransactionPermission>.  
  
 <xref:System.Transactions.DistributedTransactionPermission> işlem yönetimi Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından yönetilecek ilerletilen her talep. Bu tür bir senaryo işlemi genelinde kaynakları ve MSDTC günlüğünde ayrılmış alandır özellikle bir genel kaynağı kullanır. Bir Web ön uç bir veritabanı veya veritabanı sağladığı hizmetler bir parçası olarak kullanan bir uygulama için bu kullanım örneğidir.  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] güven düzeyleri kendi kümesi vardır ve belirli bir izin kümesi ile bu güven düzeyi ilke dosyalar ile ilişkilendirir. Daha fazla bilgi için bkz: [ASP.NET güven düzeyleri ve ilke dosyaları](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1). İlk yüklediğinizde, Windows SDK, varsayılan hiçbiri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ile ilişkili ilke dosyaları <xref:System.Transactions.DistributedTransactionPermission>. Bu nedenle, işlem içinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] MSDTC tarafından yönetilmek üzere uygulama ilerletilen, yükseltme başarısız olur bir <xref:System.Security.SecurityException> yoğun üzerine <xref:System.Transactions.DistributedTransactionPermission>. İşlem yükseltme etkinleştirmek için bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kısmi güven ortamında vermek <xref:System.Transactions.DistributedTransactionPermission> içeriğiyle olarak aynı varsayılan güven düzeylerinde <xref:System.Data.SqlClient.SqlClientPermission>. Bunu desteklemek için kendi özel güven düzeyi ve ilke dosyası ya da yapılandırabilirsiniz ya da olan varsayılan ilke dosyaları değiştirebileceğiniz **Web_hightrust.config** ve **Web_mediumtrust.config**.  
  
 İlke dosyaları değiştirmek için add bir **SecurityClass** öğesi için **DistributedTransactionPermission** için **SecurityClasses** öğesinin altında  **PolicyLevel** öğesi ve karşılık gelen ekleyin **IPermission** öğesinin altında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** System.Transactions için. Aşağıdaki yapılandırma dosyası bu gösterir.  
  
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
  
 Hakkında daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] güvenlik ilkesine bakın [securityPolicy öğesi (ASP.NET Ayarlar Şeması)](http://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba).  
  
## <a name="dynamic-compilation"></a>Dinamik derleme  
 İçeri aktarma ve kullanmak istiyorsanız, <xref:System.Transactions> içinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] erişimi dinamik olarak derlenmiş olan uygulamayı bir başvuru yerleştirin <xref:System.Transactions> derleme yapılandırma dosyası. Özellikle, başvuru altında eklenmesi gereken **derleme**/**derlemeleri** varsayılan kök bölümünü **Web.config** yapılandırma dosyası veya bir Belirli Web uygulamasının yapılandırma dosyası. Aşağıdaki örnekte bu gösterir.  
  
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
  
 Daha fazla bilgi için bkz: [öğesi (ASP.NET Ayarlar Şeması) için derlemeleri add](http://msdn.microsoft.com/library/602197e8-108d-4249-b752-ba2a318f75e4).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET güven düzeyleri ve ilke dosyaları](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [securityPolicy öğesi (ASP.NET Ayarlar Şeması)](http://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba)  
 [İşlem Yönetimi Yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md)

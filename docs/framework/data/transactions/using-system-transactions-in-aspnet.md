---
title: ASP.NET’te System.Transactions kullanma
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: bfc75661ea538ac52b244e38eb10e6ae37a8fd62
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205828"
---
# <a name="using-systemtransactions-in-aspnet"></a>ASP.NET’te System.Transactions kullanma
Bu konu, bir ASP.NET uygulamasının içinde başarıyla <xref:System.Transactions> nasıl kullanabileceğinizi açıklar.  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>ASP.NET 'de DistributedTransactionPermission 'ı etkinleştir  
 <xref:System.Transactions>kısmen güvenilen çağıranları destekler ve **Allowpartiallytrustedçağıranlar** özniteliğiyle (aptca) işaretlenir. Güven düzeyleri <xref:System.Transactions> , kaynak türleri (örneğin, sistem belleği, paylaşılan işlem genelinde kaynaklar, sistem genelinde kaynaklar ve diğer kaynaklar) temel alınarak tanımlanır ve bu <xref:System.Transactions> da gerekli olması gereken güven düzeyini gösterir Bu kaynaklara erişmek için. Kısmi güven ortamında, tam olmayan bir güven derlemesi yalnızca uygulama etki alanı içindeki işlemleri kullanabilir (Bu durumda, korunan tek kaynak sistem belleğidir), verilmediği <xref:System.Transactions.DistributedTransactionPermission>müddetçe.  
  
 <xref:System.Transactions.DistributedTransactionPermission>işlem yönetiminin Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından yönetilmek üzere ilerletilidiğinde, talep edilir. Bu tür bir senaryo işlemi genelinde kaynakları ve MSDTC günlüğünde ayrılmış alandır özellikle bir genel kaynağı kullanır. Bir Web ön uç bir veritabanı veya veritabanı sağladığı hizmetler bir parçası olarak kullanan bir uygulama için bu kullanım örneğidir.  
  
 ASP.NET kendi güven düzeylerine sahiptir ve ilke dosyaları aracılığıyla bu güven düzeyleriyle belirli bir izin kümesini ilişkilendirir. Daha fazla bilgi için bkz. [ASP.net Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)). Windows SDK ilk yüklediğinizde, varsayılan ASP.NET ilkesi dosyalarından hiçbiri ile <xref:System.Transactions.DistributedTransactionPermission>ilişkili değildir. Bu nedenle, bir ASP.NET uygulamasındaki işlem MSDTC tarafından yönetilmek üzere ilerlediğinde, yükseltme işlemi <xref:System.Security.SecurityException> <xref:System.Transactions.DistributedTransactionPermission>yoğun bir şekilde başarısız olur. ASP.net kısmi güven ortamında işlem yükseltmeyi etkinleştirmek için, ile aynı varsayılan güven düzeylerine sahip <xref:System.Transactions.DistributedTransactionPermission> <xref:System.Data.SqlClient.SqlClientPermission>olmanız gerekir. Bunu desteklemek için kendi özel güven düzeyinizi ve ilke dosyanızı yapılandırabilir ya da **Web_hightrust. config** ve **Web_mediumtrust. config**olan varsayılan ilke dosyalarını değiştirebilirsiniz.  
  
 İlke dosyalarını değiştirmek için, **PolicyLevel** öğesi altındaki **Securityclasses** öğesine bir **DistributedTransactionPermission** için **securityClass** öğesi ekleyin ve altına karşılık gelen bir **IPermission** öğesi ekleyin System. Transactions için ASP.NET **NamedPermissionSet** . Aşağıdaki yapılandırma dosyası bunu gösterir.  
  
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
  
 ASP.NET güvenlik ilkesi hakkında daha fazla bilgi için bkz. [SecurityPolicy öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).  
  
## <a name="dynamic-compilation"></a>Dinamik derleme  
 Erişim için dinamik olarak derlenen bir ASP.net <xref:System.Transactions> uygulamasında içeri ve kullanmak istiyorsanız, yapılandırma dosyasındaki <xref:System.Transactions> derlemeye bir başvuru yerleştirmeniz gerekir. Özel olarak, başvuru varsayılan kök **Web. config** yapılandırma dosyasının **derleme**/**derlemeleri** bölümünde veya belirli bir Web uygulamasının yapılandırma dosyasına eklenmelidir. Aşağıdaki örnek bunu gösterir.  
  
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
  
 Daha fazla bilgi için bkz. [derleme için derlemeler Için öğe ekleme (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET güven düzeyleri ve Ilke dosyaları](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))
- [securityPolicy öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [İşlem Yönetimi Yükseltme](transaction-management-escalation.md)

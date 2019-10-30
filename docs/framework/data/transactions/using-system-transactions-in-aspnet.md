---
title: ASP.NET’te System.Transactions kullanma
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 2bddebc13897408839e18f42b17a9fbaefdc5b87
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040418"
---
# <a name="using-systemtransactions-in-aspnet"></a>ASP.NET’te System.Transactions kullanma
Bu konu, bir ASP.NET uygulamasının içinde <xref:System.Transactions> başarıyla kullanabileceğinizi açıklar.

## <a name="enable-distributedtransactionpermission-in-aspnet"></a>ASP.NET 'de DistributedTransactionPermission 'ı etkinleştir
 <xref:System.Transactions> kısmen güvenilen çağıranları destekler ve `AllowPartiallyTrustedCallers` özniteliğiyle (APTCA) işaretlenir. <xref:System.Transactions> için güven düzeyleri, <xref:System.Transactions> kullanıma sunduğu (örneğin, sistem belleği, paylaşılan işlem genelindeki kaynaklar, sistem genelinde kaynaklar ve diğer kaynaklar) temel alınarak tanımlanır ve bu kaynaklara erişmek için gerekli olan güven düzeyini kaynakların. Kısmi güven ortamında, tam olmayan bir güven derlemesi yalnızca uygulama etki alanı içindeki işlemleri kullanabilir (Bu durumda, korunan tek kaynak sistem belleğidir), çünkü <xref:System.Transactions.DistributedTransactionPermission> verilmez.

 <xref:System.Transactions.DistributedTransactionPermission>, işlem yönetiminin Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından yönetilmek üzere ilerletilidiğinde talep edilir. Bu tür bir senaryo işlemi genelinde kaynakları ve MSDTC günlüğünde ayrılmış alandır özellikle bir genel kaynağı kullanır. Bir Web ön uç bir veritabanı veya veritabanı sağladığı hizmetler bir parçası olarak kullanan bir uygulama için bu kullanım örneğidir.

 ASP.NET kendi güven düzeylerine sahiptir ve ilke dosyaları aracılığıyla bu güven düzeyleriyle belirli bir izin kümesini ilişkilendirir. Daha fazla bilgi için bkz. [ASP.net Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)). Windows SDK ilk yüklediğinizde, varsayılan ASP.NET ilke dosyalarından hiçbiri <xref:System.Transactions.DistributedTransactionPermission> ilişkilendirilmez. Bu nedenle, bir ASP.NET uygulamasındaki işleminizi MSDTC tarafından yönetilmek üzere ilerlediğinde, yükseltme işlemi <xref:System.Transactions.DistributedTransactionPermission> yoğun bir <xref:System.Security.SecurityException> ile başarısız olur. ASP.NET kısmi güven ortamında işlem yükseltme işlemini etkinleştirmek için, <xref:System.Transactions.DistributedTransactionPermission> <xref:System.Data.SqlClient.SqlClientPermission> aynı varsayılan güven düzeylerinde vermelisiniz. Bunu desteklemek için kendi özel güven düzeyinizi ve ilke dosyanızı yapılandırabilir ya da **Web_hightrust. config** ve **Web_mediumtrust. config**olan varsayılan ilke dosyalarını değiştirebilirsiniz.

 İlke dosyalarını değiştirmek için, `PolicyLevel` öğesinin altındaki `SecurityClasses` öğesine `DistributedTransactionPermission` için bir `SecurityClass` öğesi ekleyin ve System. Transactions için ASP.NET `IPermission` altına karşılık gelen bir `NamedPermissionSet` öğesi ekleyin. Aşağıdaki yapılandırma dosyası bunu gösterir.

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
 Erişim üzerinde dinamik olarak derlenen bir ASP.NET uygulamasında <xref:System.Transactions> alıp kullanmak istiyorsanız, yapılandırma dosyasındaki <xref:System.Transactions> derlemesine bir başvuru yerleştirmeniz gerekir. Özellikle başvuru, varsayılan kök **Web. config** yapılandırma dosyasının `compilation/assemblies` bölümü veya belirli bir Web uygulamasının yapılandırma dosyası altına eklenmelidir. Aşağıdaki örnek bunu gösterir.

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
